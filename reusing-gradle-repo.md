---
title: 'Gradle - Reusing buildscript Repositories'
description: 'getByName() can be used to reuse gradle repositories from buildscript'
tags: 'gradle,java,reusing buildscript repositories'
headerImage: /post/gradle.png
datePublished: '2019-12-15'
lastModified: '2020-01-31'
---

[Gradle](https://gradle.org/) is a leading build tool. It downloads libraries from the declared repositories. It has a flaw that you have to declare repositories twice (`buildscript.repositories` and `repositories`) if you are using plugins.

Especially in an enterprise, It is _cumbersome_ to deal as the definition of a repository can be more than a single line or there could be multiple repositories (public/private).

> Avoid doing work twice; _Define Repository Once and use it all over_.

```groovy

buildscript {
  repositories {
    maven {
      // Define name of repository
      name 'myRepository1'
      url 'https://repo.mycompany.com/maven'
      metadataSources: {
        mavenPom()
      }
      credentials {
        username "user"
        password "password"
      }
    }
  }
}

```

## Selective Repository

```groovy
// this line is going to save the effort
repositories.add(buildscript.repositories.getByName('myRepository1'))

```

## All Repository

```groovy
repositories = buildscript.repositories

```
