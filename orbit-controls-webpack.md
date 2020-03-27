---
title: Importing Threejs OrbitControls
description: Import OrbitControls with Webpack or es6 style.
keywords: ‘import orbitcontrols,webpack,threejs, import orbit controls webpack, import oribitcontrols typescript, import orbitcontrols es6’
tags: three.js
datePublished: ‘2019-12-29’
lastModified: ‘2020-03-28’
---

[OrbitControls](https://threejs.org/docs/#examples/en/controls/OrbitControls) is a [Three.js](https://threejs.org/) submodule to move or zoom or drag the camera around a point.

## Option 1: With CDN

The CDN distribution variant of `Three.js` is prepacked with OrbitControls module.

Just create the Object of `OrbitControls` as:

```javascript
const controls = new Three.OrbitControls(camera, renderer.domElement)
```

## Option 2: Webpack + `three-orbit-controls` module

`three-orbit-controls` presents `OrbitControls` as a separate module. It requires the instance of `Three` for initialization.

The module can be used when using a bundler like webpack or Parcel or plain ES6; the following is a step-by-step guide to import and initialize Orbit Controls using this module:

1. Download `three-orbit-controls`

```sh
npm install three-orbit-controls —save-dev
```

```sh
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

## Option 3: Bundler - Without any external Module

`Three.js` npm library distribution contains examples directory which holds secondary 3d components; OrbitControls is one of them.

Just import `OrbitControls` from `examples/jsm` as:

```javascript
import { OrbitControls } from '@/node_modules/three/examples/jsm/controls/OrbitControls'

.
.
.
const controls =  new OrbitControls(camera, renderer.domElement)
```

This approach also works with TypeScript.
