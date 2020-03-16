---
title: FontAwesome - Changing SVG icons programmatically
description: 'Change FontAwesome SVG icons with JavaScript'
tags: 'font-awesome, javascript'
datePublished: '2020-02-10'
lastModified: '2020-03-16'
---

[FontAwesome](https://fontawesome.com/) is the most famous icon library. SVG is one good performant option to render icons when you are using a few numbers of its on your website.

While working on Article: [Custom Event with RxJS](https://themightyprogrammer.dev/article/custom-event-js); I learnt that FontAwesome replaces icon tag with SVG on rendering, which makes changing the icon tricky.

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

Note down:

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

### In Action

<iframe
     data-src="https://codesandbox.io/embed/eager-gates-dp26m?fontsize=14&hidenavigation=1&theme=dark&view=preview"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="eager-gates-dp26m"
     allow="geolocation; microphone; camera; midi; vr; accelerometer; gyroscope; payment; ambient-light-sensor; encrypted-media; usb"
     sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"
></iframe>
