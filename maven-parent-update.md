---
title: Maven Parent Version Update
description: 'Versions plugin of maven can be used to update project parent version.'
tags: 'maven, maven parent'
datePublished: '2021-12-18'
lastModified: '2021-02-08'
---

[Maven](https://maven.apache.org) is a popular build tool in Java Eco System. Often we need to update the parent version in child modules when working with a multi-modules project. [Versions](https://www.mojohaus.org/versions-maven-plugin/) is a Maven plugin that can automate updating the parent version.

The following commands update the parent version in child modules:  

```sh
mvn versions:update-parent
mvn versions:commit
```

## How it works
`mvn versions:update-parent`   

---
1. It picks the version from the local maven repository.
2. It updates the parent versions declared in the child module pom.xml on which the command is run. 
3. It produces `pom.xml.versionsBackup` as the backup pom file.

If you want to pick the latest version of the parent from the remote maven repository, then run `mvn versions:update-parent -U`. 

`mvn versions:commit`   

---
It cleans up `pom.xml.versionsBackup`. 


The following command is helpful if you need to revert to the previous parent version: 
```sh
mvn versions:revert
```
It cleans up `pom.xml.versionsBackup` and reverts the parent version update.  

_Note: This command will only function if the file `pom.xml.versionsBackup` exists; If you accidentally deleted the backup file, you'll need to restore the previous version manually._

## Drawback
The only disadvantage of Versions plugin is that it must be run from the root of the child module. With the increased number of child modules, this may appear to be excessive. However, this limitation  can be overcome using other utility commands: 


```sh
ls -l | grep ^d | awk '{print $9}' | \
xargs -I {}  mvn -f {}/pom.xml versions:update-parent
```

The above command runs the `versions:update-parent` in each subdirectory of the current directory.

