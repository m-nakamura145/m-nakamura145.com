---
title: "シェル環境をfishからzshに変えました"
date: 2019-01-11T01:57:57+09:00
description: ""
categories: []
tags: ["zsh"]
draft: false
image: ""
author: "m-nakamura145"
---

1年ほどシェル環境に[fish](http://fishshell.com/)を使ってきましたが自分には合わない部分が少し出てきたので昔から使っている[zsh](http://www.zsh.org/)に戻しました。

<!--more-->

fishのメリットはデフォルトのAutosuggestionsがかなり機敏に効いてくれるところと、themeが良い感じだったところです。

デメリットとしてはとにかくbash互換のスクリプトが軒並み動かなかったところと、環境変数の設定方法が完全に違うのが致命的でした。最近はIDEでコードを書く場合が多かったのでデメリットの部分が薄かったので使い続けていましたが、最近コンソール作業が増えてきたのでこれを機にzshに戻ることにしました。

再設定して入れたツールや設定ファイルなどを書いておきます。

## zshで使っているツール

- [prezto](https://github.com/sorin-ionescu/prezto)
- [z](https://github.com/rupa/z)
- [peco](https://github.com/peco/peco)
- [hub](https://github.com/github/hub)
- [.zshrc](https://gist.github.com/m-nakamura145/4a263f54d574391e65c2a7f0bf2a6109)
- [.gitconfig](https://gist.github.com/m-nakamura145/8f8c0ea8f9bce0aaab4501c1575d7986)