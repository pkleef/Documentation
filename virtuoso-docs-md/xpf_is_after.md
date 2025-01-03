<div>

<div>

</div>

<div>

## Name

is_after — Returns true if the given entity is after the second given
entity in document order, otherwise returns false.

</div>

<div>

## Synopsis

<div>

|                              |                     |
|------------------------------|---------------------|
| `boolean `**`is_after`**` (` | `ent1 ` entity ,    |
|                              | `ent2 ` entity `)`; |

<div>

 

</div>

</div>

</div>

<div>

## Description

The function ensures that both *`ent1`* and *`ent2`* are XML entities
and the returns true if *`ent1`* and *`ent2`* are both in the same XML
document and *`ent1`* is strictly after *`ent2`* in document order. It
returns false if one of them is not an entity but an empty node-set or
if their documents differ or or if they're equal or if one of them is an
ancestor of other or if *`ent1`* is simply before *`ent2`* in document
order.

</div>

<div>

## Parameters

<div>

### ent1

An XML entity or an node-set whose first node is compared.

</div>

<div>

### ent2

An XML entity or an node-set whose first node is compared.

</div>

</div>

<div>

## Return Types

Boolean

</div>

<div>

## Errors

<div>

**Table 24.144. Errors signalled by is_after()**

<div>

| SQLState                              | Error Code                            | Error Text                                                                                                     | Description                                                                                             |
|---------------------------------------|---------------------------------------|----------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| <span class="errorcode">XP001 </span> | <span class="errorcode">XPFB0 </span> | <span class="errortext">First argument of XPATH function is-before() or is-after() must be XML entity </span>  | The value that is neither an XML entity nor an empty node-set may not be compared using document order. |
| <span class="errorcode">XP001 </span> | <span class="errorcode">XPFB1 </span> | <span class="errortext">Second argument of XPATH function is-before() or is-after() must be XML entity </span> | The value that is neither an XML entity nor an empty node-set may not be compared using document order. |

</div>

</div>

  

</div>

<div>

## Examples

<div>

**Example 24.594. **

<div>

Find all chapters that have title after table of content

``` screen
/book/chapter[is-after(toc,title)]
```

</div>

</div>

  

</div>

<div>

## See Also

<a href="xpf_is_before.html" class="link"
title="is_before">is_before()</a>

</div>

</div>
