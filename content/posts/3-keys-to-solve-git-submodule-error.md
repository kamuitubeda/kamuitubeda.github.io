---
title: "3 Key Syntax for Solving Git Submodule Error"
subtitle: ""
date: 2023-08-19T13:52:54+07:00
lastmod: 2023-08-19T13:52:54+07:00
draft: false
authors: []
description: ""

tags: []
categories: []
series: []

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: ""
featuredImagePreview: ""

toc:
  enable: true
math:
  enable: false
lightgallery: false
license: ""
---

<!--more-->
git submodule status
-----------------------------
This is the key for error debugging on git submodule error. So, before anything else, always check the status first. 
```
git submodule status
```

git rm --cached
-----------------------------
In case we already added submodule and want to remove it, this is the syntax to use.
```
git rm --cached path/to/submodule
```


git submodule add
-----------------------------
Sometimes, problems can be solved by removing and adding it again. So this is why this syntax will always be the final key. 
```
git submodule add -b main git@github.com:username/username.github.io.git public
```

