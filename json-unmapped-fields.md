---
title: 'Collecting unmapped fields with Object Mapper'
tags: 'json, java, jackson, objectmapper,JsonAnySetter'
description: 'Jackson provides @JsonAnySetter for collecting unmapped or unrecognized fields.'
datePublished: '2019-12-07'
---

# Collecting unmapped fields with Object Mapper

[Jackson](https://github.com/FasterXML/jackson) is a popular Java library to convert JSON to Java Object. It maps JSON field with object field by name or mapping provided by `@JsonProperty`.

Jackson provides [`@JsonAnySetter`](https://fasterxml.github.io/jackson-annotations/javadoc/2.4/com/fasterxml/jackson/annotation/JsonAnySetter.html) for collecting _unmapped_ or _unrecognized_ fields.

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

## In action

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
System.out.println(p.unmatchedFields);

```
