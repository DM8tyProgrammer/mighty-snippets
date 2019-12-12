# Collecting unmapped fields with Object Mapper

Jackson is popular Java library to convert json to Java Object. It matches json field by Java Object field by name or mapping provided by `@JsonProperty`.

Sometimes, you want to map or collect the fields which are not mapped. `@JsonAnySetter` is useful in this case.

```java

class Profile {

  String name;
  Map<String, String> unmatchedFields = new HashMap<>();

  public void setName(String name) {
    this.name = name;
  }


  // for collecting unmapped field
  @JsonAnySetter
  public void unmappedFields(String key, String value){
    // ... Do what you want
    unmatchedFields.put(key, value);
  }
}
```

```java
/*
Say following json
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
