---
title: 'Custom Bootstrap Button with Sass/Scss'
description: Create customized color button with bootstrap
dataPublished: '2020-01-05'
lastModified: '2020-01-19'
keywords: 'customized boostrap button, bootstrap button, sass, bootstrap button color change'
tags: 'sass'
---

Bootstrap 4 Sass module provides mixin parameterized `button-variant`, which can be used to create customized coloured buttons.

The mixin declaration is as:

```scss
@mixin button-variant(
  $background,
  $border,
  $hover-background,
  $hover-border,
  $active-background,
  $active-border
);
```

`$background` and `$border` parameters must be provided, and rest are optional parameters.
It automatically generates button text color in contrast to the provided background color

## In action

```scss
@import node_modules/bootstrap/scss/mixin;

$feature-bg: #ffd803;

.btn-feature {
  @include button-variant($feature-bg, darken($feature-bg, 3%));

  // optitional
  // color: #fff; #uncomment and add your color
}
```

```html
<button class="btn btn-feature">Feature</button>
```

> Subscription button that you see on this site has been made using the above technique.
