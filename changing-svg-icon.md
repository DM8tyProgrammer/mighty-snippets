---
title: FontAwesome - Changing SVG icons programmatically
description: 'Learn how to change FontAwesome SVG icons with JavaScript'
tags: 'font-awesome, javascript'
datePublished: '2020-02-10'
lastModified: '2022-04-22'
---

[FontAwesome](https://fontawesome.com/) is the most famous icon library. When you only need a few icons, SVG is a fantastic alternative for rendering them. 

While working on Article: [Custom Event with RxJS](/article/custom-event-js),  I discovered that FontAwesome renders the icon tag as SVG, making changing the icon difficult. Changing the class of `<i>` tag alone is not a solution. To alter the icon programmatically, you must first understand "how it is rendered."


## Rendering of icon

```html
<i class="dot far fa-circle"></i>
```
It's worth noting that `dot` isn't a FontAwesome-specific class. Any class can be added; it is used to demonstrate a technique that you will learn about in the subsequent section. The SVG code for the aforementioned "icon tag" is as follows:

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

### Elements of SVG

- `dot` is a custom class; FontAwesome made this custom class as one of the classes of rendered SVG. This mechanism is helpful to target SVG.
- `far` became data-prefix of SVG.
- `circle` became data-icon. 

## Technique

1. Fetch the SVG through class/id which is added in the icon tag.
2. Change `data-prefix` or `data- icon` according to your requirement.

```javascript
//	1. Fetch SVG
// We added `dot` as custome class <i class="dot far fa-circle"></i>
let dot = document.querySelector('.dot')

// 2 . Change  data-prefix or data-icon
let icon = dot.getAttribute('data-prefix') === 'far' ? 'fas' : 'far'
dot.setAttribute('data-prefix', icon)
```

### In Action

<iframe
     src="https://codesandbox.io/embed/eager-gates-dp26m?fontsize=14&hidenavigation=1&theme=dark&view=preview"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="eager-gates-dp26m"
     allow="geolocation; microphone; camera; midi; vr; accelerometer; gyroscope; payment; ambient-light-sensor; encrypted-media; usb"
     sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"
></iframe>
