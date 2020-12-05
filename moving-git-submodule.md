---
title: Changing the path of a Git Submodule
description: 'with git mv command git submodule can be recolated'
keywords: 'git, git submodule, submodule, moving submodule'
tags: 'git'
headerImage: '/post/git.png'
datePublished: '2020-12-06'
lastModified: '2020-12-06'
---

Git Submodules are like disk mounting: these are mounted to locations inside parent repository. With time preferences changes: style or tooling or any reasons which may lead you to change the location of a submodule. 

Git being flexible supports this use case and  provide `mv` command which does the magic:

```sh
git mv <source> <destination>
```

By style, `git mv` command is similar to Unix `mv` command.

## In Action

Let’s try `git mv` on an existing submodule. There exist git submodule on path `pages/article`; it is required to be moved to a new path `content/article`.

```sh
$ git submodule                          

 bd6cd4271e782cf1200bbeb263a6d897666cd785 pages/article (heads/master)
```

moving submodule to the new location: `content/article`
```sh
$ git mv pages/article content/article 
$ git submodule

 bd6cd4271e782cf1200bbeb263a6d897666cd785 content/article (heads/master)
```

Voila, the submodule has been relocated !!