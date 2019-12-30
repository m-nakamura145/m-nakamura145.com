---
title: "Algoliaのコマンドラインツールを作りました"
date: 2018-11-22T01:14:27+09:00
description: ""
categories: []
tags: ["ruby", "algolia"]
draft: false
image: ""
author: "m-nakamura145"
---

[Algolia](https://www.algolia.com/)という検索SaaSをコマンドラインから操作できる[algolia-indices](https://github.com/m-nakamura145/algolia-indices)というgemを作りました。

Algoliaは高機能な検索機能を提供しているSaaSです。データを入れてクエリを投げるといい感じの検索結果が返ってきます。かなり細かく検索方法をカスタマイズできるので詳しくは[document](https://www.algolia.com/doc/)を確認してください。

algolia-indicesでサポートしているコマンドは

- 指定したindexにyamlで記述したデータをimport
- 指定したindexのデータをclear

の2つです。引き続き機能を追加していきます。
