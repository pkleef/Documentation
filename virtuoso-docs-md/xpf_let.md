<div>

<div>

</div>

<div>

## Name

let — Creates temporary variables and calculates an expression that uses
these variables

</div>

<div>

## Synopsis

<div>

|                     |                         |
|---------------------|-------------------------|
| `any `**`let`**` (` | `var1name ` string ,    |
|                     | `var1value ` sequence , |
|                     | `var2name ` string ,    |
|                     | `var2value ` sequence , |
|                     | `... ` ,                |
|                     | `varNname ` string ,    |
|                     | `varNvalue ` sequence , |
|                     | `retval ` any `)`;      |

<div>

 

</div>

</div>

</div>

<div>

## Description

For every pair of arguments, the function calculates values of these
arguments and then creates a new temporary local variable whose name is
the string value of the first argument in pair and the value assigned is
the value of the second argument in pair. Obviously, the argument for
variable name is usually a constant string of alphanumeric characters.
The expression for a value of variable number I may refer to variables
created during steps 1 to I-1. When all pairs of arguments are turned
into temporary variables, the last argument is calculated and its value
is returned as the value of the whole expression.

Temporary variables are destroyed on return.

This function is used in the implementation of "LET" control operator in
XQUERY, so you will probably use that operator in XQUERY expressions,
not the function. This function may be useful in XPATH expressions and
in XSLT stylesheets. It is not a part of library of standard XQUERY 1.0
functions.

</div>

<div>

## Parameters

<div>

### varIname

Expression for the name for the I-th temporary variable

</div>

<div>

### varIvalue

Expression for the value for the I-th temporary variable

</div>

<div>

### retval

Expression for the value to be returned

</div>

</div>

<div>

## Return Types

Any, depending on the type of *`retval `* expression.

</div>

<div>

## Errors

<div>

**Table 24.146. Errors signalled by let()**

<div>

| SQLState                              | Error Code                            | Error Text                                                                                                      | Description                                                                                                                              |
|---------------------------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| <span class="errorcode">42000 </span> | <span class="errorcode">XPF02 </span> | <span class="errortext">Wrong number of arguments for XPATH function let(), maybe internal XQuery error </span> | The function should have odd number of arguments: even number of arguments that describe variables plus one for the returned expression. |

</div>

</div>

  

</div>

<div>

## Examples

<div>

**Example 24.598. **

<div>

These two expressions are equivalent, but first may be used in any XPATH
while second is written in XQUERY syntax

``` screen
let('baseprice', /item/price, 'discount', 0.20, $baseprice * (1.0 - $discount))
LET  $baseprice := /item/price, $discount := 0.20 RETURN $baseprice * (1.0 - $discount)
```

</div>

</div>

  

</div>

<div>

## See Also

<a href="xpf_for.html" class="link" title="for">for()</a>

</div>

</div>
