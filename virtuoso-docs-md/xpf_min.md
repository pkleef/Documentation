<div>

<div>

</div>

<div>

## Name

min — Returns minimum value among all its arguments.

</div>

<div>

## Synopsis

<div>

|                        |                  |
|------------------------|------------------|
| `number `**`min`**` (` | `arg1 ` any ,    |
|                        | `arg2 ` any ,    |
|                        | `... ` ,         |
|                        | `argN ` any `)`; |

<div>

 

</div>

</div>

</div>

<div>

## Description

The function returns the minimum value among all values in all its
arguments, For each node in every argument node-set, it converts the
string-value of the node to a number. If some arguments are not
node-sets, they are converted to numbers. The minimum number found is
returned.

This function is not a part of XPATH 1.0 standard library.

</div>

<div>

## Parameters

<div>

### argI

A node-set of nodes whose string values must be converted to numbers and
added to the result, or single value.

</div>

</div>

<div>

## Return Types

<div>

**Table 24.148. Errors signalled by min()**

<div>

| SQLState                              | Error Code                            | Error Text                                                                                                                              | Description                                                                                             |
|---------------------------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| <span class="errorcode">XP001 </span> | <span class="errorcode">XPF04 </span> | <span class="errortext">Nonempty sequence of values expected as argument of XPATH function min(); min() of nothing is senseless </span> | This happens if the function is called without arguments, or with all arguments set to empty node-sets. |

</div>

</div>

  

</div>

<div>

## Examples

<div>

**Example 24.602. **

<div>

``` screen
min(/report[@type="daily-sales"]/total)
```

</div>

</div>

  

</div>

<div>

## See Also

<a href="xpf_sum.html" class="link" title="sum">sum</a>
<a href="xpf_avg.html" class="link" title="avg">avg</a>
<a href="xpf_max.html" class="link" title="max">max</a>

</div>

</div>
