<div>

<div>

</div>

<div>

## Name

is_timezoneless — returns 1 for timezoneless arguments, zero for
timezoned

</div>

<div>

## Synopsis

<div>

|                                      |                        |
|--------------------------------------|------------------------|
| `datetime `**`is_timezoneless`**` (` | in `dt ` datetime `)`; |

<div>

 

</div>

</div>

</div>

<div>

## Description

The function returns 1 for timezoneless arguments, zero for timezoned.

</div>

<div>

## Parameters

<div>

### dt

Datetime value.

</div>

</div>

<div>

## Examples

<div>

**Example 24.59. Simple example**

<div>

``` screen
SQL> select is_timezoneless (cast ('1999-12-31 11:59' as datetime));
INTEGER
 0
No. of rows in result: 1
```

</div>

</div>

  

</div>

<div>

## See Also

<a href="fn_now.html" class="link" title="now"><code
class="function">now </code></a>

<a href="fn_timezone.html" class="link" title="timezone"><code
class="function">timezone </code></a>

<a href="fn_forget_timezone.html" class="link"
title="forget_timezone"><code
class="function">forget_timezone </code></a>

<a href="fn_adjust_timezone.html" class="link"
title="adjust_timezone"><code
class="function">adjust_timezone </code></a>

<a href="fn_rdf_now_impl.html" class="link" title="rdf_now_impl"><code
class="function">rdf_now_impl </code></a>

<a href="fn_current_timestamp.html" class="link"
title="current_timestamp"><code
class="function">current_timestamp </code></a>

<a href="fn_curdatetime.html" class="link" title="curdatetime"><code
class="function">curdatetime </code></a>

<a href="fn_curdatetimeoffset.html" class="link"
title="curdatetimeoffset"><code
class="function">curdatetimeoffset </code></a>

<a href="fn_curutcdatetime.html" class="link"
title="curutcdatetime"><code class="function">curutcdatetime </code></a>

<a href="fn_sysutcdatetime.html" class="link"
title="sysutcdatetime"><code class="function">sysutcdatetime </code></a>

<a href="fn_stringdate.html" class="link" title="stringdate"><code
class="function">stringdate </code></a>

<a href="fn_datestring.html" class="link"
title="datestring , datestring_gmt ,"><code
class="function">datestring </code></a>

</div>

</div>
