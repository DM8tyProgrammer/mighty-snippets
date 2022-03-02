---
title: 'Gradle - Reusing buildscript Repositories'
description: 'getByName() can be used to reuse gradle repositories from buildscript'
tags: 'gradle,java,reusing buildscript repositories'
headerImage: /post/gradle.png
datePublished: '2019-12-15'
lastModified: '2022-01-03'
---

[Gradle](https://gradle.org/) is a leading build tool. It gets libraries from the specified repositories and downloads them. If you're using plugins, you'll have to define repositories twice (in both `buildscript.repositories` and `repositories`)

It isn't easy to maintain multiple definitions of the same repository, especially in an organisation where repository definition can span multiple lines. Also, there can be many repositories: team-wise, company-wide public or private, 3rd parties vendors, open source etc.

> Avoid doing work twice; _Define Repository Once and use it all over_.

Gradle, thankfully, enables you to name your repositories and gives a nice API for selecting repositories by name.

```groovy

buildscript {
  repositories {

    // start of defination
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
    //end of defination
  }
}

```

## Selective Repository
Use the `getByName()` API to retrieve the above-mentioned repository in `repositories` section, as illustrated in the code below:

```groovy
// this line is going to save the effort
repositories.add(buildscript.repositories.getByName('myRepository1'))

```

## All Repository
Use the following code if you want to reuse all of the defined repositories of `buildscript`:

```groovy
repositories = buildscript.repositories

```
