<div id="fn___xml_nsexpand_iristr" class="refentry">

<div class="titlepage">

</div>

<div class="refnamediv">

## Name

\_\_xml_nsexpand_iristr — Checks if the string is QName and if it is so
then replaces namespace prefix to the full namespace IRI.

</div>

<div class="refsynopsisdiv">

## Synopsis

<div id="fsyn___xml_nsexpand_iristr" class="funcsynopsis">

|                                    |                        |
|------------------------------------|------------------------|
| ` `**`__xml_nsexpand_iristr`**` (` | in `str ` varchar `)`; |

<div class="funcprototype-spacer">

 

</div>

</div>

</div>

<div id="desc___xml_nsexpand_iristr" class="refsect1">

## Description

Checks if the string is QName and if it is so then replaces namespace
prefix to the full namespace IRI. Otherwise signals error if the
argument is local IRI without a prefix.

</div>

<div id="params___xml_nsexpand_iristr" class="refsect1">

## Parameters

<div id="id103408" class="refsect2">

### str

QName. For ex. if QName is "prefix:local", then conveniently is replaced
"prefix:" with the namespace IRI

</div>

</div>

<div id="examples__xml_nsexpand_iristr" class="refsect1">

## Examples

<div id="ex_xml_nsexpand_iristr_1" class="example">

**Example 24.298. Example with FOAF namespace prefix**

<div class="example-contents">

``` programlisting
SQL> SELECT __xml_nsexpand_iristr ('foaf:knows');
__xml_nsexpand_iristr
VARCHAR
_______________________________________________________________________________

http://xmlns.com/foaf/0.1/knows

1 Rows. -- 0 msec.
```

</div>

</div>

  

<div id="ex_xml_nsexpand_iristr_2" class="example">

**Example 24.299. Example with no namespace prefix**

<div class="example-contents">

``` programlisting
SQL> SELECT __xml_nsexpand_iristr ('no-namespace-prefix-iri');

*** Error 22023: [Virtuoso Driver][Virtuoso Server]SR649:
No XML namespace prefix in string "no-namespace-prefix-iri"
in
__xml_nsexpand_iristr:(BIF),
        __01 => 'no-namespace-prefix-iri',
<Top Level>
at line 5 of Top-Level:
SELECT __xml_nsexpand_iristr ('no-namespace-prefix-iri')
```

</div>

</div>

  

<div id="ex_xml_nsexpand_iristr_3" class="example">

**Example 24.300. Example with namespace prefix "local"**

<div class="example-contents">

``` programlisting
SQL> SELECT __xml_nsexpand_iristr ('no-such-prefix:local');

*** Error 22023: [Virtuoso Driver][Virtuoso Server]SR648:
Unknown XML namespace prefix in IRI "no-such-prefix:local"
in
__xml_nsexpand_iristr:(BIF),
        __01 => 'no-such-prefix:local',
<Top Level>
at line 6 of Top-Level:
SELECT __xml_nsexpand_iristr ('no-such-prefix:local')
```

</div>

</div>

  

<div id="ex_xml_nsexpand_iristr_4" class="example">

**Example 24.301. Example with namespace prefix ""no-such-prefix""**

<div class="example-contents">

``` programlisting
SQL> SELECT __xml_ns_iristr ('no-such-prefix', 'knows');

*** Error 22023: [Virtuoso Driver][Virtuoso Server]SR648: Unknown XML namespace prefix "no-such-prefix"
in
__xml_ns_iristr:(BIF),
        __01 => 'no-such-prefix',
        __02 => 'knows',
<Top Level>
at line 7 of Top-Level:
SELECT __xml_ns_iristr ('no-such-prefix', 'knows')
```

</div>

</div>

  

</div>

<div id="seealso__xml_nsexpand_iristr" class="refsect1">

## See Also

`xml_ns_uname() `

`xml_ns_iristr() `

`xml_get_ns_prefix() `

`xml_get_ns_uri() `

</div>

</div>