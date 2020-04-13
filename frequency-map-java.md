---
title: 'Frequency Map in Java 8+'
description: 'Calculating the frequency of items in Java 8 or above using stream and collector APIs'
dataPublished: '2020-04-14'
lastModified: '2020-04-14'
keywords: 'frequency map, java 8, java 9, java 11, java 14'
tags: 'java'
---

Frequency Map in Java 8 or above can be created concisely with the help of `Stream` and `Collectors.groupingBy` API.

A general method to count frequency of elements:

```java
<T> Map<T, Long>  frequencyMap(Stream<T> elements) {
return elements.collect(
  Collectors.groupingBy(
    Function.identity(),
    HashMap::new, // can be skipped
    Collectors.counting()
  )
);
}
```

Any streamable and countable collection can utilise the above method to count the frequency of elements.

## Frequency Map of List Elements

```java
List<String> words = Arrays.asList("hello", "hello", "mighty");
frequencyMap(words.stream())
```

## Frequency Map of Array Elements

```java
Character[] letters = {'a', 'b', 'b', 'c', 'c', 'c'};
frequencyMap(Arrays.stream(letters))
```
