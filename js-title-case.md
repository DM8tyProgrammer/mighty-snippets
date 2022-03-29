---
title: Javascript - TitleCase
description: 'Find how many ways of adding titleCase utility in Javascript.'
keywords: 'title case'
tags: 'javascript'
headerImage: /post/javascript.png
datePublished: '2022-03-29'
lastModified: '2022-03-29'
---

**Title Case** is a type of capitalization in which the first letter of a word is capitalized, and the rest of the letters are lowercase. 

This rule might not apply to non-relevant terms from articles, pronouns classes. We'll consider any word, regardless of whether it's an article or a pronoun.

## Titling one word
The following function converts a single word into the Title Case:

```javascript
function titleCase(word) {
   return word.charAt(0).toUpperCase() + word.substr(1).toLowerCase();
}
```
The code is self-explanatory.

### In action
```javascript
> titleCase("dm8ty")
"Dm8ty"

> titleCase("i am dm8tyProgrammer")
"I am dm8tyProgrammer"
```

## Titling all the words in a sentence. 
The following function converts each word of a given sentence to TitleCase:

```javascript
function titleCase(sentence)  {
   return sentence.replace(/\w+/g, word => word.charAt(0).toUpperCase() + word.substr(1).toLowerCase());
}
``` 
The code takes each matching word (`\w+`) and runs the titling expression over it. 

### In action
```javascript
> titleCase("dm8ty")
"Dm8ty"

> titleCase("i am dm8tyProgrammer")
"I Am Dm8typrogrammer"
```


## Adding TitleCase as an extension of String
The following code illustrates adding the title case method to the existing string construct: 

```javascript
String.prototype.toTitleCase = function () {
  return this.replace(/\w+/g, word => word.charAt(0).toUpperCase() + word.substr(1).toLowerCase());
};
```
We just attached the last piece of code to the String [prototype](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object_prototypes). 

### In action
```javascript
> "dm8ty".toTitleCase()
"Dm8ty"

> "i am dm8tyProgrammer".toTitleCase()
"I Am Dm8typrogrammer"
```

## Excluding Titling of irrelevant words
Maintain a collection (array or set) of irrelevant words, and check the presence of the word in the collection before titling. 

```javascript
// make a collection of words
let irrelevance = ['a', 'an', 'the', 'am']


String.prototype.toTitleCase = function() {

  // check the presence of the word in the irr collections and, if present, exclude titling.
  return this.replace(/\w+/g, word => irrelevance.includes(word)? word : word.charAt(0).toUpperCase() + word.substr(1).toLowerCase());
};
```
### In action
```javascript
> "dm8ty".toTitleCase()
"Dm8ty"

> "i am dm8tyProgrammer".toTitleCase()
"I am Dm8typrogrammer"
```
What if "The" article falls at the beginning of a sentence?