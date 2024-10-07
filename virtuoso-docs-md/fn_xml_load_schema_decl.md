<div id="fn_xml_load_schema_decl" class="refentry">

<div class="titlepage">

</div>

<div class="refnamediv">

## Name

xml_load_schema_decl — returns a string with list of errors detected by
XML Schema processor on reading given XML Schema definition document.

</div>

<div class="refsynopsisdiv">

## Synopsis

<div id="fsyn_xml_load_schema_decl" class="funcsynopsis">

|                                   |                                     |
|-----------------------------------|-------------------------------------|
| ` `**`xml_load_schema_decl`**` (` | in `base_uri ` varchar ,            |
|                                   | in `document_uri ` varchar ,        |
|                                   | in `content_encoding ` varchar ,    |
|                                   | in `content_language ` varchar `)`; |

<div class="funcprototype-spacer">

 

</div>

</div>

</div>

<div id="desc_xml_load_schema_decl" class="refsect1">

## Description

Loads given file using base_uri. Try to parse file of XML Schema
definition and check it for correctness to XML Schema specification.

</div>

<div id="params_30" class="refsect1">

## Parameters

<div id="id123047" class="refsect2">

### base_uri

in HTML parser mode change all absolute references to relative from
given base_uri (http://\<host\>:\<port\>/\<path\>)

</div>

<div id="id123050" class="refsect2">

### content_encoding

string with content encoding type of \<document\>; valid are 'ASCII',
'ISO', 'UTF8', 'ISO8859-1', 'LATIN-1' etc., defaults are 'UTF-8' for XML
mode and 'LATIN-1' for HTML mode

</div>

<div id="id123053" class="refsect2">

### content_language

string with language tag of content of \<document\>; valid names are
listed in IETF RFC 1766, default is 'x-any' (it means 'mix of words from
various human languages)

</div>

<div id="id123056" class="refsect2">

### dtd_validator_config

configuration string of the validator, default is empty string meaning
that DTD validator should be fully disabled and only critical errors
should be reported

</div>

</div>

<div id="ret_08_01" class="refsect1">

## Return Types

Human readable list of errors if applicable as a varchar.

</div>

<div id="examples_14_01" class="refsect1">

## Validating XML Against a XML Schema

<div id="ex_xml_load_schema_decl" class="example">

**Example 24.513. Simple Use**

<div class="example-contents">

``` programlisting
declare _result varchar;
_result := xml_load_schema_decl (
  'http://localhost.localdomain/xmlrepository',
  'persons.xsd', 'UTF-8', 'x-any');

if (_result = '') _result := 'NO ERRORS DETECTED';
```

</div>

</div>

  

</div>

<div id="seealso_39" class="refsect1">

## See Also

<a href="fn_xml_validate_schema.html" class="link"
title="xml_validate_schema"><code
class="function">xml_validate_schema() </code></a>

<a href="fn_xml_auto_schema.html" class="link"
title="xml_auto_schema"><code
class="function">xml_auto_schema() </code></a>

<a href="fn_xml_view_schema.html" class="link"
title="xml_view_schema"><code
class="function">xml_view_schema() </code></a>

<a href="fn_xml_validate_dtd.html" class="link"
title="xml_validate_dtd"><code
class="function">xml_validate_dtd() </code></a>

</div>

</div>