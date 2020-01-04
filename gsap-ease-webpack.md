---
title: 'Importing GSAP-3 Ease with Webpack'
description: Ease can't be used straightforward. By altering the way of importing Gsap, Ease can be used.
keywords: 'gsap, import gsap ease,  gsap ease with webpack, gsap ease with babel, gsap ease with es6 import, animation, webpack, javascript, es6, babel'
datePublished: '2019-12-25'
---

Using [GSAP ease](https://greensock.com/docs/v3/Eases) with Webpack / babel is not straightforward.
Webpack needs to know independent references to link and optimize javascript.

## Example

The following example leads to _error_ when using with webpack:

```javascript
import gsap from 'gsap'
gsap.to(elment, { duration:1, rotation: 180 ease: Power0.easeNone  })
```

### Error message

The following error message is displayed in webpack build:

```
'Power0' is not defined
```

## Solution

Gsap (`gsap`) is a module or namespace. It works if _you import the whole module_. Just change the way you import Gsap and use `Gsap.<Ease>`.

```javascript
import * as Gsap from 'gsap'
Gsap.gsap.to(elment, { duration:1, rotation: 180 ease: Gsap.Power0.easeNone  })

```
