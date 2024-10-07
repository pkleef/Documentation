<div id="fn_xenc_key_rsa_read" class="refentry">

<div class="titlepage">

</div>

<div class="refnamediv">

## Name

xenc_key_RSA_read — Importing a RSA key into user's repository

</div>

<div class="refsynopsisdiv">

## Synopsis

<div id="fsyn_xenc_key_rsa_read" class="funcsynopsis">

|                                |                             |
|--------------------------------|-----------------------------|
| ` `**`xenc_key_RSA_read`**` (` | in `name ` varchar ,        |
|                                | in `key_data ` varchar `)`; |

<div class="funcprototype-spacer">

 

</div>

</div>

</div>

<div id="desc_xenc_key_rsa_read" class="refsect1">

## Description

This function is used to import an RSA serialized key into user's
repository and register it with a name supplied.

Note that key will not be persisted. It is loaded in the memory only.

</div>

<div id="params_xenc_key_rsa_read" class="refsect1">

## Parameters

<div id="id120309" class="refsect2">

### name

Name of the key to register

</div>

<div id="id120312" class="refsect2">

### key_data

The base64 encoded binary data with RSA key material

</div>

</div>

<div id="ret_xenc_key_rsa_read" class="refsect1">

## Return Types

No return value.

</div>

<div id="examples_xenc_key_rsa_read" class="refsect1">

## Examples

<div id="ex_xenc_key_rsa_read" class="example">

**Example 24.468. Loading a shared secret**

<div class="example-contents">

``` screen
xenc_key_RSA_read ('MyRSAkey', 'MIG..skipped..MBAAE=');
```

</div>

</div>

  

</div>

<div id="seealso_xenc_key_rsa_read" class="refsect1">

## See Also

<a href="fn_xenc_key_rsa_create.html" class="link"
title="xenc_key_RSA_create"><code
class="function">xenc_key_RSA_create() </code></a>

</div>

</div>