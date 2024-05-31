---
title: 'Java - Iterator to Stream'
description: 'Convert Iterator to Stream in Java 8+'
keywords: stream, iterator, java, iterator to stream, convert iterator to stream, java 8
datePublished: '2019-12-19'
lastModified: '2024-03-31'
---

Converting an Iterator to a Stream can be done in two steps:
1. Convert Iterator to splitIterator
2. Pass the splitIterator to stream

## 1. Converting Iterator to SplitIterator
You can convert an Iterator type to a SplitIterator type through [`Spliterators.spliteratorUnknownSize`](https://docs.oracle.com/javase/8/docs/api/java/util/Spliterators.html#spliteratorUnknownSize-java.util.Iterator-int-) API as:
 
```java
var splitIterator = SplitIterSpliterators.spliteratorUnknownSize(iterator, Spliterator.ORDERED)
```

## 2. SplitIterator to stream 
To convert SplitIterator to Stream, use the [`StreamSupport.stream`](https://docs.oracle.com/javase/8/docs/api/java/util/stream/StreamSupport.html#stream-java.util.Spliterator-boolean-) API, which accepts `SplitIterator` and a `boolean` indicating parallel stream.

```java
 Stream<Integer> stream = StreamSupport.stream(splitIterator, false)
```


> In gist, `iterator` → `spliterator` → `stream`


## Putting everything together in [Rept.it](https://repl.it/@DM8tyProgrammer/iterator-to-stream)

<iframe height="700px" width="100%" src="https://repl.it/@DM8tyProgrammer/iterator-to-stream?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>