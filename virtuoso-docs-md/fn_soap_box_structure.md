<div>

<div>

</div>

<div>

## Name

soap_box_structure

</div>

<div>

## Synopsis

<div>

|                                    |                       |
|------------------------------------|-----------------------|
| `any `**`soap_box_structure`**` (` | in `elem1 ` varchar , |
|                                    | in `value1 ` any ,    |
|                                    | in `... ` ,           |
|                                    | in `elem1 ` varchar , |
|                                    | in `value1 ` any `)`; |

<div>

 

</div>

</div>

</div>

<div>

## Description

This function provides a way to encapsulate a structure suitable for
soap serialization. It accepts a name/value pairs which represents name
and value of elements of a structure.

For example structure :

``` programlisting
      {
        varString 'hello',
          varInt  1234 
      }
```

will be represented as soap_box_structure ('varString', 'hello',
'varInt', 1234); furthermore value returned from soap_box_structure
passed as an output parameter to the procedure (named structname)
working as SOAP method will return :

``` programlisting
          <structName>
          <varString>hello</varString>
          <varInt>1234</varInt> 
      </structName> 
```

Please note that this is a one of possibilities to express structures
for SOAP request/response in Virtuoso/PL. The other way to express
structure is to use User Defined Types (see SOAP & WSDL section of the
documentation).

</div>

<div>

## Parameters

<div>

### elem

name which represents name of the member of a structure

</div>

<div>

### value

value which represents value of the member of a structure

</div>

</div>

<div>

## Return Types

The return type of `soap_box_structure() ` is an array representing a
structure.

</div>

</div>
