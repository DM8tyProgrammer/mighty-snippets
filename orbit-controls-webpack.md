---
title: Importing Threejs OrbitControls with Webpack
description: Import OrbitControls with Webpack or es6 style.
keywords: 'import orbitcontrols,webpack,threejs, import orbit controls webpack, import oribitcontrols typescript, import orbitcontrols es6'
tags: three.js
datePublished: '2019-12-29'
lastModified: '2020-01-19'
---

[OrbitControls](https://threejs.org/docs/#examples/en/controls/OrbitControls) controls camera movements in [Three.js]() ecosystem. When using CDN, the import of OrbitControl is just as `new Three.OribitControls()` but when using with webpack or importing the library with `ES6` style, It is no longer the case.

The following code snippet, import OrbitControls correctly with webpack / ES6:

## Approach 1: With `three-orbit-controls` module

1. Download `three-orbit-controls`

   ```yarn
   yarn add -D three-orbit-controls
   ```

2. Import the module as:

   ```javascript
   import * as Three from 'three'
   import oc from 'three-orbit-controls'

   const OrbitControls = oc(Three)
   .
   .
   const controls =  new OrbitControls(camera, renderer.domElement)
   ```

## Approach 2: Without external Module

Just import file from installed location.

```javascript
import { OrbitControls } from '@/node_modules/three/examples/jsm/controls/OrbitControls'
```

This approach also works with TypeScript.
