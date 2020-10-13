---
title: 'Trimming String in Swift'
description: 'trimmingCharacters is used to trim strings'
tags: 'Swift'
datePublished: '2020-10-13'
lastModified: '2020-10-13'
---

## Using UIKit
UIKit has defined string trimming API: `trimmingCharacters`, is little* verbose.  It accepts a `CharacterSet`, explaining which characters to cut off the boundary of a string.   Character Set also defines predefined constants to explain frequently used character sets.

* `.whitespaces` explains whitespaces  character ( space and tab)
* `.whitespacesAndNewlines`  explaines all whitespaces characters 
* `decimalDigits` explaines numbers


To trim off whitespaces:

```swift

import UIKIT
let name = "  Superman  "
let trimmedName = name. trimmingCharacters(in: CharacterSet.whitespacesAndNewlines)

print(trimmedName)
```

Output of the above code
```
Superman
```

## Using Foundation
Foundation also defined the same API for trimming strings, but this can be used using `NSCharacterSet` class for explaining the characters.

```swift

import Foundation
let name = "  Superman  "
let trimmedName = name.trimmingCharacters(in: NSCharacterSet.whitespacesAndNewlines)

print(trimmedName)
```

The output of above code
```
Superman
```