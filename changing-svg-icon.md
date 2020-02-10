---
title: FontAwesome - Changing SVG icons programmatically
description: 'Change FontAwesome SVG icons with JavaScript'
tags: 'font-awesome, javascript'
datePublished: '2020-02-10'
lastModified: '2020-02-10'
---

[FontAwesome](https://fontawesome.com/) is the most famous icon library. SVG is one good performant option to render icons when you are using a few numbers of its on your website.

FontAwesome replaces icon tag with SVG on rendering, which makes changing the icon challenge.

```html
<i class="dot far fa-circle"></i>
```

Result in

```html
<svg
  class="svg-inline--fa fa-circle fa-w-16 dot"
  aria-hidden="true"
  focusable="false"
  data-prefix="far"
  data-icon="circle"
  role="img"
  xmlns="http://www.w3.org/2000/svg"
  viewBox="0 0 512 512"
  data-fa-i2svg=""
>
  . .
</svg>
```

Note down

- `dot` is custom class, and it became part of SVG class.
  It is helpful to target SVG.

* `far` became data-prefix of SVG.
* `circle` became data-icon

## Technique

1. Fetch the SVG through class/id which is added in the icon tag.
2. Change `data-prefix` or `data- icon` according to your requirement.

```javascript
//	1. Fetch SVG
let dot = document.querySelector('.dot')

// 2 . Change  data-prefix or data-icon
let icon = dot.getAttribute('data-prefix') === 'far' ? 'fas' : 'far'
dot.setAttribute('data-prefix', icon)
```
