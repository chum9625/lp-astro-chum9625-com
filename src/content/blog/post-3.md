---
title: "robots.txt の書き方"
meta_title: ""
description: "robots.txt の書き方"
date: 2024-04-14T09:45:00Z
image: ""
categories: ["Memo", "Tech"]
author: "25master"
tags: ["seo"]
draft: false
---

robots.txt：Webサイトを巡回するクローラーの動作を制御するために記述するテキストファイルのこと。

下記コードを記述したrobots.txtをサーバーにアップする。

##  基本の記述

```bash

User-agent: *
Disallow:
```

## クロールを制限する記述例

```bash

User-agent: *
Allow: /

Disallow: /api/*
```
