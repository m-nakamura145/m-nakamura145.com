---
title: "CircleCIでdangerを動かすときのOnly Build Pull RequestsとDirty Hack"
date: 2018-11-26T01:25:40+09:00
description: ""
categories: []
tags: ["ruby", "circleci"]
draft: false
image: ""
author: "m-nakamura145"
---

[danger](https://github.com/danger/danger)は設定したリポジトリにPull Requestが作成された後に様々なcode reviewを行うgemです。

dangerはPlugin構造になっており、[danger-mention](https://github.com/danger/danger-mention)や[danger-rubocop](https://github.com/ashfurrow/danger-rubocop)などのpluginが作られています。トレタではtoreta-railsというメインAPIリポジトリでdangerを使ってbotに最低限のcode reviewを任せています。

このdangerをCircleCIで動かすときに少しハマるポイントがあります。

## Pull Requestの作成とCircleCIのpushのタイミングが合わない

CircleCIはデフォルトの状態だとcommitをpushしたらすぐCIが起動します。dangerはCIの起動をフックにしてPull Requestを確認するため、以下のような現象が発生します。

1. commitをpush
1. CI起動
1. danger起動
1. Pull Requestが無いためdangerの実行がskipされる

この現象を回避するために、dangerではCircleCIのOnly build pull requestsを有効にすることを[勧めています](https://github.com/danger/danger/blob/master/lib/danger/ci_source/circle.rb#L9)。

### Only build pull requestsの挙動

- Pull Requestが存在しない状態だとgithubにpushしただけではCIが走らなくなる
- Pull RequestをopenしたタイミングでCIが走る
- Pull Requestをopenした状態であれば、そのPull Requestのbranchに追加でpushするたびにCIが走る

しかし、この設定を有効にするとDeploy Flowに影響を与えてしまいました。

### トレタのDeploy Flow
    
- developが開発用branch。developのcommitはdevelopにmergeされたらstaging環境にdeployされる。default branch。
- masterが本番用branch。masterのcommitはmasterにmergeされたらproduction環境にdeployされる

default branchはOnly build pull requestsの影響を受けません。しかし、master branchはmergeしたらCIが起動して欲しいのにCIが起動しない状態になってしまいました。

### CI起動用Pull Requestをopenし続ける

私はdangerを使ってcode reviewを自動化したかったのですが、既存のDeploy Flowは特に問題なかったため変えたくありませんでした。調べたところ、以下のようなhackで期待する挙動になりました。

masterから、masterから切った適当なbranchのPull Requestを作成します。このPull Requestをopenにし続けることで、Pull Requestをopenした状態であれば、そのPull Requestのbranchに追加でpushするたびにCIが走るという条件に当てはまり、developからmasterにmergeするときに無事にdeployできるようになりました。
    



   
