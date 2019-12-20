---
title: 'Gradle - Reusing buildscript Repositories'
description: 'getByName() can be used to reuse gradle repositories from buildscript'
tags: 'gradle,java,reusing repository,buildscript repositories'
datePublished: '2019-12-15'
---

# Gradle - Reusing `buildscript` Repositories

[Gradle](https://gradle.org/) is a leading build tool. It downloads libraries from the declared repositories. It has a flaw that you have to declare repositories twice (`buildscript.repositories` and `repositories`) if you are using plugins.

Especially in an enterprise, It is _cumbersome_ to deal as the definition of a repository can be more than a single line or there could be multiple repositories (public/private).

> Avoid doing work twice; _Define Repository Once and used it all over_.

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

// this line is going to save the effort
repositories.add(buildscript.repositories.getByName('myRepository1'))

```
