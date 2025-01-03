<div>

<div>

</div>

<div>

## Name

uddi_find_service — Retrieves *`serviceList `* message matching search
criteria

</div>

<div>

## Syntax

``` screen
<uddi_find_service
  businessKey="uuid_key"
  generic="1.0"
  [ maxRows ="nn" ]
  xmlns="urn:uddi-org:api" >
    [<findQualifiers/>]
    <name/> | <categoryBag/> | <tModelBag/>
</uddi_find_service>
  
```

</div>

<div>

## Attributes & Children

The *`name`* , *`categoryBag`* , and *`tModelBag`* arguments are
mutually exclusive.

<div>

### maxRows

This optional integer value allows the requesting program to limit the
number of results returned.

</div>

<div>

### businessKey

This *`uuid_key`* is used to specify a particular *`BusinessEntity `*
instance.

</div>

<div>

### findQualifiers

This collection of *`findQualifier`* elements can be used to alter the
default behavior of search functionality.

</div>

<div>

### name

This string value represents a partial name. Any *`businessService`*
data contained in the specified *`businessEntity `* with a matching
partial name value gets returned.

</div>

<div>

### categoryBag

This is a list of category references. The returned *`serviceList`*
contains *`businessInfo`* structures matching all of the categories
passed (logical AND).

</div>

<div>

### tModelBag

This is a list of *`tModel `* *`uuid_key `* values that represent the
technical fingerprint the server should locate within a
*`bindingTemplate`* structure contained within any *`businessService`*
contained by the *`businessEntity`* specified. If more than one
*`tModel`* key is specified in this structure, only *`businessServices`*
that contain *`bindingTemplate`* information that matches all of the
*`tModel`* keys specified will be returned (logical AND).

</div>

</div>

<div>

## Return Types

This function returns a *`serviceList`* on success. In the event that no
matches were located for the specified criteria, the *`serviceList`*
structure returned will contain an empty *`businessServices`* structure.
This signifies zero matches.

In the event of a large number of matches, a UDDI-enabled server may
truncate the result set. If this occurs, the *`serviceList`* will
contain the *`truncated`* attribute with the value of this attribute set
to true.

Searching using *`tModelBag`* will return serviceInfo structures for all
qualifying *`businessService`* data, including matches due to
*`hostingRedirector`* references. In other words, if the
*`businessEntity`* whose *`businessKey`* is passed as an argument
contains a *`bindingTemplate`* with a *`hostingRedirector`* value, and
that value references a *`bindingTemplate`* that matches the *`tModel`*
search requirements, then the *`serviceInfo`* for the
*`businessService`* containing the *`hostingRedirector`* will be
returned.

</div>

<div>

## Errors

<div>

**Table 24.92. Errors signalled by uddi_find_service**

<div>

| Error Code                                         | Description                                                                                                                                                                          |
|----------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span class="errorcode">E_invalidKeyPassed </span> | signifies that the *`uuid_key `* value passed did not match with any known *`businessKey`* or *`tModel`* key values. The error structure will signal which condition occurred first. |
| <span class="errorcode">E_nameTooLong </span>      | signifies that the partial name value passed exceeds the maximum name length designated by the server.                                                                               |
| <span class="errorcode">E_tooManyOptions </span>   | signifies that more than one mutually exclusive argument was passed.                                                                                                                 |
| <span class="errorcode">E_unsupported </span>      | signifies that one of the *`findQualifier `* values passed was invalid.                                                                                                              |

</div>

</div>

  

</div>

</div>
