<div>

<div>

<div>

<div>

## 9.29. SQL Inverse Functions

</div>

</div>

</div>

Many virtual database application scenarios require performing various
conversions on data in legacy tables. An example of this is currency
conversions, conversions between British and metric units, replacing
complex composite keys with single numeric row id's and so forth.

SQL views are the normal way of implementing such conversions. However,
when making queries with selection criteria referencing the results of
these conversions we often need to first convert and then test, possibly
having to bring data from the source system to the virtual database.
Further, we will not be able to use indices that may exist on the legacy
system if we first have to convert and only then test the value of a
column.

Virtuoso introduces an SQL extension for dealing with these issues.
Virtuoso allows the definition of two SQL functions that are inverses of
each other, for example `dollar_to_euro` and `euro_to_dollar` would be
examples of inverse functions.

Thus, when we define a view like:

``` programlisting
create view euro_item as Select I_id, dollar_to_euro (I_price) as I_price, I_name from item;
```

We can further declare:

``` programlisting
db..sinv_create_inverse ('euro_to_dollar', 'dollar_to_euro', 1);
```

and perform the query:

``` programlisting
select * from euro_item where I_price > 100;
```

Normally, this would internally perform the query:

``` programlisting
select * from item where dollar_to_euro (I_price) > 100;
```

Now however it will make use of the inverse function information and we
get:

``` programlisting
select * from item where I_price > euro_to_dollar (100)
```

The second form is substantially more efficient since only one function
call needs to be done for the whole query, not to mention the fact that
if the currency conversion function were only defined on the vdb and the
item table were linked from another server, all data would have to be
brought over to the vdb for the conversion.

Now if the conversion function were defined only on the vdb, the amount
of euros would be converted to dollars and then passed as a parameter to

``` programlisting
Select * from item where I_price > ?
```

Many simple conversions can be efficiently handled by this method. For
most unit and data type conversions, the conversion preserves collation
order. Amount a will be greater than amount b whether a and b be
expressed in euros or dollars, as long as both a and b are in the same
currency. Some other conversions such as compression, encryption, hashes
and mappings of arbitrary unique ids to another set of ids do not
preserve collation. Whether a particular mapping preserves collation is
indicated by the third argument of
<a href="fn_sinv_create_inverse.html" class="link"
title="sinv_create_inverse"><code
class="function">sinv_create_inverse</code></a> . In the above example
we see a value of 1, meaning that collation is preserved. Zero specifies
that collation is not preserved.

Sometimes it will be desirable to map multi-part keys into a single key
for convenience of querying or for compatibility with another database
schema.

We will use the orders and customer tables from the TPC C benchmark
schema to illustrate the feature. Both tables have a primary key
consisting of three parts, a warehouse id, a district id and then a
customer or order id. The order references the customer with a foreign
key consisting of its own warehouse and district id and of a customer
id.

Now we may wish to simplify the situation and make a one-column order id
and a one column foreign key reference to customer for presenting the
system to an outside reporting application. We will do this completely
without touching the original database, all logic taking place on the
virtual database.

In this case, the original keys consist of three numbers: n digits of
warehouse id, 2 digits of district id and 9 digits of order or customer
id. We can simply concatenate these numbers into a single decimal. To do
this, we define the following functions:

``` programlisting
create function num_truncate (in n numeric)
{
  return cast (cast (n as numeric) - 0.5 as numeric (40, 0));
}

create function num_mod (in x numeric, in y numeric)
{
  return (x - num_truncate (cast (x as numeric) / y) * y);
}

/* This function takes the three key parts and returns a numeric where each occupies a fixed range of digits. */

create function o_iid (in w_id int, in d_id int, in o_id int) returns numeric
{
  return (w_id * 100000000000 + d_id * 1000000000 + o_id);
}

/* The below three functions retrieve each of the fields encoded in the numeric produced by o_iid */

create function o_iid_w_id (in iid numeric) returns int
{
  return cast (num_truncate (iid / 100000000000) as int);
}

create function o_iid_d_id (in iid numeric) returns int
{
  return cast (num_mod (num_truncate (iid / 1000000000), 100) as int);
}

create function o_iid_o_id (in iid numeric)
{
  return cast (num_mod (iid, 1000000000) as int);
}

db..sinv_create_inverse ('O_IID', VECTOR ('O_IID_W_ID', 'O_IID_D_ID', 'O_IID_O_ID'), 0);
```

The <a href="fn_sinv_create_inverse.html" class="link"
title="sinv_create_inverse"><code
class="function">sinv_create_inverse</code></a> now defines an accessory
for each of the arguments of o_iid. The first function in the vector
retrieves the first argument of a call to o_iid, the second the second
and so forth. Since we are talking about mapping a set of values into
one value it does not make sense to speak of preserving a collation,
thus the last argument is 0. When making this declaration we also assert
that for each distinct combination of arguments of o_iid, we get a
distinct value from which all the original arguments can be retrieved
using the functions mentioned.

Now we define the same functions for constructing a synthetic one-part
customer id. The functions are exactly the same as for the order id.

``` programlisting
create function c_iid (in w_id int, in d_id int, in c_id int) returns numeric
{
  return (w_id * 100000000000 + d_id * 1000000000 + c_id);
}

create function c_iid_w_id (in iid numeric) returns int
{
  return cast (num_truncate (iid / 100000000000) as int);
}

create function c_iid_d_id (in iid numeric) returns int
{
  return cast (num_mod (num_truncate (iid / 1000000000), 100) as int);
}

create function c_iid_c_id (in iid numeric)
{
  return cast (num_mod (iid, 1000000000) as int);
}

db..sinv_create_inverse ('C_IID', VECTOR ('C_IID_W_ID', 'C_IID_D_ID', 'C_IID_C_ID'), 0);
```

Now we have defined functions for producing the synthetic keys we wish
to use. Now we bind these functions to the original database using
views. We assume that the original orders and customer tables are
attached from a remote database under the names orders and customer.

``` programlisting
create view  orders_2 as select o_iid (o_w_id, o_d_id, o_id) as o_iid numeric, c_iid (o_w_id, o_d_id, o_c_id) as o_c_iid numeric, * from orders;

create view customer_2 as select c_iid (c_w_id, c_d_id, c_id) as c_iid numeric, * from customer;
```

As a simple test, let us get the synthetic o_c_iid from an order using
the synthetic o_iid key.

``` screen
SQL> select o_c_iid from orders_2 where o_iid = 102000000002;

returns________

102000000935
```

The order \#2 in district \#2 of warehouse \#1 refers to customer \#935
or district \#2 of warehouse \#1.

``` screen
SQL> explain ('select o_c_iid from orders_2 where o_iid = 102000000002');

returns

{

Precode:
      0: $25 "callret" := Call O_IID_O_ID (<constant (102000000002)>)
      7: $26 "callret" := Call O_IID_D_ID (<constant (102000000002)>)
      14: $27 "callret" := Call O_IID_W_ID (<constant (102000000002)>)
      21: BReturn 0
Remote  SELECT "t2"."O_C_ID", "t2"."O_D_ID", "t2"."O_W_ID" FROM "DBA"."ORDERS" "t2"  where "t2"."O_ID" = ? and "t2"."O_D_ID" = ? and "t2"."O_W_ID" = ?
Params ($25 "callret", $26 "callret", $27 "callret")
Output ($29 "t1.O_C_ID", $30 "t1.O_D_ID", $31 "t1.O_W_ID")

After code:
      0: $40 "O_C_IID" := Call C_IID ($31 "t1.O_W_ID", $30 "t1.O_D_ID", $29 "t1.O_C_ID")
      7: BReturn 0
Select ($40 "O_C_IID")
}
```

In this query execution plan we see that the virtual database first
decomposes the synthetic o_iid into its component parts, passes these to
a query run on the remote database, retrieves the components of the
synthetic o_c_iid and finally assembles this and returns it to the
client.

We may also use this mapping in more complex queries:

``` programlisting
select count (*) from orders_2, customer_2 where o_c_iid = c_iid;
```

This uses the synthetic foreign and primary keys for joining. Normally,
since the functions for making these keys are only defined on the vdb
side, each order would have to be retrieved and then the corresponding
customer fetched. Now however we can take advantage of the inverse
declaration and decompose the comparison of the synthetic keys into
comparisons of each of their arguments:

``` screen
SQL> explain ('select count (*) from orders_2, customer_2 where o_c_iid = c_iid');

returns

{
Remote  SELECT COUNT ( *) FROM "DBA"."ORDERS" "t2" , "DBA"."CUSTOMER" "t4"  where "t4"."C_ID" = "t2"."O_C_ID" and "t4"."C_D_ID" = "t2"."O_D_ID" and "t4"."C_W_ID" = "t2"."O_W_ID"
Output ($26 "aggregate")
Select ($26 "aggregate")
}
```

We see that the SQL compiler decomposed the comparison of the c_iid's
into a comparison of the original arguments of the function. This can be
done because we earlier asserted that each distinct argument combination
would produce a unique result of the function.

The examples covered thus far are simple in that there is a clear way of
mapping the data back and forth using SQL functions. This is not always
possible, for example if we wish to generate unique numeric id's from
keys consisting of arbitrary strings.

To this effect, Virtuoso provides a mechanism for automatically
generating mapping functions, which take a combination of n arguments of
an arbitrary searchable data type and generate a unique id for each
distinct combination. The ids are assigned as needed and the mapping is
persisted in an automatically generated table.

We could have generated the o_iid, o_iid_w_id, o_iid_d_id and o_iid_o_id
functions with the following single call:

``` programlisting
db..sinv_create_key_mapping ('O_IID', vector ('W_ID', 'int', 'D_ID', 'int', 'O_ID', 'int'));
```

The first argument is the name of the mapping function to generate. The
following vector lists the arguments of this function and their data
types. The name of each argument is appended to the name of the mapping
function, separated by an underscore for forming the inverse functions,
one for each argument. Thus the functions are named exactly as in the
previous example where we defined them manually.

Internally, this generates a table for keeping the w_id, d_id and o_id
for each allocated o_iid. The o_iid's come from a sequence object. The
functions manage this table automatically, without requiring developer
intervention. The name of the sequence is the same as that of the
mapping, thus sequence_set can be used for setting the sequence counter.
Note that sequence names are case sensitive.

When a new combination of w_id, d_id, o_id is seen by o_iid, it inserts
a row in the mapping table and assigns this a new unique number. This
update of the mapping table is committed at the same time the enclosing
transaction commits. The table is normally read with read committed
isolation and updated with serializable isolation. This guarantees that
when a single w_id, d_id, o_id combination is seen at the same time on
two threads the result will be the same id being given on both threads.

Any value returned by the mapping function may at all times be used for
the inverse functions. The inverse functions will return NULL if given a
value that was at no time returned by the mapping function.

The table created for the mapping is named MAP\_\<name of the mapping
function\>. The system does not define an automatic cleanup function for
removing established mappings because the efficient way of implementing
this is quite application dependent. Such a function can however be
easily written by the developer if one is needed.

Because comparison of mapping functions is reduced into pair-wise
comparison of their arguments, the query

``` programlisting
select count (*) from orders, customer where o_c_iid = c_iid
```

Will work even if all orders or customers have not been assigned a
mapping on the vdb side. If a virtual database application wishes to
retrieve rows from a remote database using a synthetic key made by
functions defined with
<a href="fn_sinv_create_key_mapping.html" class="link"
title="sinv_create_key_mapping"><code
class="function">sinv_create_key_mapping</code></a> , any value returned
by the mapping function in a transaction that was successfully committed
is valid and will retrieve the data intended.

<div>

<div>

<div>

<div>

### 9.29.1. Updating through Inverses

</div>

</div>

</div>

A view that selects calls to functions, which have inverses, is
updateable. This means that the SQL compiler will use the inverse
function on the value being assigned before assigning the column. This
is done for both insert and update operations. No special declaration is
needed. If the function with inverse has multiple arguments, all of
which are columns, then assigning the function will assign all the
argument columns, having called the appropriate inverse for getting each
of the separate argument values.

For example:

``` screen
SQL> insert into orders_2 (o_iid) values (1102000000003);

Done. -- 1 msec.
SQL> select * from orders_2 where o_w_id = 11;
O_IID            O_C_IID          O_ID              O_D_ID            O_W_ID            O_C_ID      O_ENTRY_D   O_CARRIER_ID  O_OL_CNT    O_ALL_LOCAL
DECIMAL          DECIMAL          INTEGER NOT NULL  INTEGER NOT NULL  INTEGER NOT NULL  INTEGER     DATE        INTEGER     INTEGER     INTEGER
_______________________________________________________________________________

1102000000003    NULL             3                 2                 11                NULL        NULL        NULL        NULL        NULL

1 Rows. -- 1 msec.
SQL> update item_euro set i_price = 120 where i_id = 1234;
```

<div>

|                              |                                                                                                                                                                                                                                                                                                                                                                                                     |
|:----------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![\[Note\]](images/note.png) | Conclusions                                                                                                                                                                                                                                                                                                                                                                                         |
|                              | The examples in this document used tables attached from remote databases because the features discussed here are most likely to be useful in such contexts. Also the query execution plans clearly show which operations take place where. The inverse function mechanism is however in no way limited to virtual database applications. All the examples will work equally well with local tables. |

</div>

</div>

</div>
