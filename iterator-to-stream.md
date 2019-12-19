---
title: 'Iterator to Stream'
description: 'Convert Iterator to Stream in Java 8+'
tags: stream, iterator, java, convert iterator
datePublished: '2019-12-19'
---

# Iterator to Stream

There is no direct API available to convert `iterator` to `stream` in Stream interface. However, there are an indirect path available for the same.

There is [`StreamSupport.stream`](https://docs.oracle.com/javase/8/docs/api/java/util/stream/StreamSupport.html#stream-java.util.Spliterator-boolean-) API which accepts `splititerator`. You can convert iterator to splititerator thru'
[`Spliterators.spliteratorUnknownSize`](https://docs.oracle.com/javase/8/docs/api/java/util/Spliterators.html#spliteratorUnknownSize-java.util.Iterator-int-)

> In gist, `iterator` -> `splititerator` -> `stream`

```java
  Stream<Integer> stream = StreamSupport.stream(
      Spliterators.spliteratorUnknownSize(iterator, Spliterator.ORDERED),
      false);
```

# Play code: [Rept.it](https://repl.it/@DM8tyProgrammer/iterator-to-stream)

<iframe height="400px" width="100%" src="https://repl.it/@DM8tyProgrammer/iterator-to-stream?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>
