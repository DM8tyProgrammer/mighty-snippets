---
title: Importing Threejs OrbitControls with Webpack
description: Import OrbitControls with Webpack or es6 style.
keywords: 'import orbitcontrols,webpack,threejs'
tags: three.js
datePublished: '2019-12-29'
---

[OrbitControls](https://threejs.org/docs/#examples/en/controls/OrbitControls) controls camera movements in [Three.js]() ecosystem. When using CDN, the import of OrbitControl is just as `new Three.OribitControls()` but when using with webpack or importing the library with `ES6` style, It is no longer the case.

The following code snippet, import OrbitControls correctly with webpack / ES6:

```javascript
import * as Three from 'three'
import oc from 'three-orbit-controls'
const OrbitControls = oc(Three)
.
.
const controls =  new OrbitControls(camera, renderer.domElement)
```
