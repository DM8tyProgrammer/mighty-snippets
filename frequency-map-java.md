---
title: 'Frequency Map in Java 8+'
description: 'Calculating the frequency of items in Java 8 or above using stream and collector APIs'
dataPublished: '2020-04-14'
lastModified: '2020-05-12'
keywords: 'frequency map, java 8, java 9, java 11, java 14'
tags: 'java'
---

Frequency Map in Java 8 or above can be created concisely with the help of `Stream` and `Collectors.groupingBy()` API.

A general method to count frequency of elements:

```java
import java.util.stream.*;
import java.util.*;
import java.util.function.*;
```

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

A list can be converted to stream by calling `stream()`.

```java
List<String> words = Arrays.asList("hello", "hello", "mighty");
frequencyMap(words.stream());
```

## Frequency Map of Characters Array

An array of Character can be converted to Stream using `Arrays.stream()`

```java
Character[] letters = {'a', 'b', 'b', 'c', 'c', 'c'};
frequencyMap(Arrays.stream(letters));
```

## Frequency Map of Characters from String

String characters can be converted to stream `chars()`. However, it returns intergers stream instead of charcters stream; Each integer needs to be converted back to character using `maptoObj` method as:

```java
String aString = "abc"
frequencyMap(aString.chars().mapToObj(c -> (char) c));
```

## Frequency Map of Integers Array or unboxed type

An array of unboxed typed elements can be converted to Stream using `Arrays.stream()` and calling `boxed()`

```java
int [] numbers = {1, 2, 3};
frequencyMap(Arrays.stream(numbers).boxed());
```

See it in action →
[https://repl.it/@DM8tyProgrammer/frequency](https://repl.it/@DM8tyProgrammer/frequency)
