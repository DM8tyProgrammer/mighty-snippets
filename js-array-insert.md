---
title: Javascript - Insert at any index in an array
description: 'splice api can be used to insert in an array at any index'
tags: 'javascript, insert array, array insert in javascript, array, array insert, splice'
datePublished: '2019-12-27'
---

# Javascript - Insert at any index in an array

There is no straightforward API to insert in an array at any index in Javascript. Through [`splice`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) API, it can be simulated as:

```javascript
// extending the Array
Array.prototype.insert = function(i, e) {
  this.splice(i, 0, e)
}
```

## In action

```javascript
a = [2]

// insert 1 at 0th position
a.insert(0, 1)

// insert 3 at 2th position
a.insert(2, 3)

// insert 5 at 5th position
// wil it be error -> run it?
a.insert(5, 5)
```

## Repl it

Check out `script.js` file.

<iframe height="400px" width="100%" src="https://repl.it/@DM8tyProgrammer/js-array-insert?lite=true&outputonly=1" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>
