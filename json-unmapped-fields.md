---
title: 'Collecting unmapped fields with Object Mapper'
keywords: 'json, java, jackson, objectmapper,JsonAnySetter,unmapped fields, unmapped fields with Jackson, unmapped fields with objectmapper'
description: 'Jackson provides @JsonAnySetter for collecting unmapped or unrecognized fields.'
datePublished: '2019-12-07'
lastModified: '2022-03-01'
---

[Jackson](https://github.com/FasterXML/jackson) is a well-known Java library for converting JSONs into Java Objects. It maps JSON fields with object fields by name or mapping provided by `@JsonProperty`.

Jackson provides an annotation named [`@JsonAnySetter`](https://fasterxml.github.io/jackson-annotations/javadoc/2.4/com/fasterxml/jackson/annotation/JsonAnySetter.html) for collecting _unmapped_ or _unrecognized_ fields. This annotation is applied to a method having key-value pairs as arguments. 

## In action
Consider a class `Profile` that might have unmapped fields:
```java

class Profile {

  String name;
  Map<String, String> unmappedFields = new HashMap<>();

  public void setName(String name) {
    this.name = name;
  }


  // for collecting unmapped field
  @JsonAnySetter
  public void unmappedFields(String key, String value){
    // ... Do what you want
    unmappedFields.put(key, value);
  }
}
```
Unmapped json fields (name and value) are received and stored in a collection via  `unmappedFields` method.

```java
/* Consider JSON
{
  "name": "m8ty",
  "handler": "@DM8tyProgrammer"
}
*/
Profile p = objectmapper.read(json, Profile.class);

// print "m8ty"
System.out.println(p.name);

// print "{handler=@DM8tyProgrammer}"
System.out.println(p.unmappedFields);

```
`handler` field is not mapped to any Java Object field, so it is collected through `JsonAnySetter`.
