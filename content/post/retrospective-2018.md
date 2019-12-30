---
title: "2018年振り返り"
date: 2018-12-31T01:38:59+09:00
description: ""
categories: []
tags: ["retrospective"]
draft: false
image: ""
author: "m-nakamura145"
---

2018年にやったことを振り返ります。

## Work

今年はとにかく激動の年でした。エンジニアの退職者が過去最多(元々人数が少ない)で、サービス規模の割に圧倒的に人が足りない状態になってしまいました。この状況を悲観せず、ビジネスを前に進めるために自分で考えた結果として、いろいろタイミングも重なって友人のソフトウェアエンジニア達を3人業務委託で雇用することに成功しました。

それぞれ各チームで最大のパフォーマンスを出してもらうために、私が全員のテクニカルディレクションを行いました。各人はそれぞれのタスクに専念してもらう状況を作りコードに慣れてもらい、徐々にタスクマネジメントを移譲して自走してもらうことに成功しました。おかげで会社のプロジェクト進行もかなり安定しました。この経験で大きくテクニカルディレクション力が向上したと思います。今は少しずつエンジニアも増えてきているので、やれることも増えました。

また、さらにRubyとRailsのスペシャリストの方にお手伝いいただき、一緒にRails Upgradeタスクを進めました。私の役割は主にほぼ全てのPull Requestのコードレビューと社内QA調整、デプロイタイミング調整です。

こちらも想定以上のスピードで進みコアAPIのリポジトリがRails 4.2.8からRails 5.2.2最新まで上げることができました。同時にRspec実行の高速化やCIの整備、Rubocopの整備やコードのリファクタリングなど今まで手を付けられていなかった部分を大幅に改善していただき、5年もののAPIとは思えないほど綺麗なコードベースになってきました。Rubyも来年には2.5系に上がる予定です。

その他にも自分で書いたコードや新しく取り組んだ技術については以下です

- 新規サービスのAPI開発(Go、kubernetes、gRPC、Firebase、Algolia)
- コアデータモデルの設計、実装
- リリースマネージャー
- AWS Auroraの運用
- CircleCI2.0化
- AWS SNSを用いたPush通知基盤の構築
- Sidekiq実行環境の改善、高速化
- Rspecの実行速度改善

既存のコードがパフォーマンス上問題になるものが多く、例えば深夜バッチが頻繁に落ちる現象が多かったです。おかげでスケーラブルな設計を意識し、改善するきっかけになったと思います。

## Output

- [Ebisu.rb#20 でSidekiq Worker設計のコツについてLTしました #ebisurb](https://www.m-nakamura145.com/post/2018/11/29/ebisu-rb-20/)
- [表参道.rb#41 でSaaSのDBリファクタリングについてLTしました #omotesandorb](https://www.m-nakamura145.com/post/2018/12/06/omotesando-rb-41/)

サービス開発中に考えてることをLTでアウトプットしてみると評判が良かったので、来年はどんどん登壇していきます。

## OSS

- [Algoliaのコマンドラインツールを作りました](https://www.m-nakamura145.com/post/2018/11/22/algolia-command-line-tool/)
- [Pull Requests時にGitHubのReview Requestsを自動でアサインするdanger plugin](https://www.m-nakamura145.com/post/2018/12/01/danger-review-requests/)

小さいけどPull Requestを出したのは以下のリポジトリです。

- https://github.com/rubygems/rubygems
- https://github.com/rurema/doctree

## 2019

SRE周りの仕事をできるようになりたいので周辺技術を追っていき、社内の各サービスをコンテナ化していきます。またGoでのサービス開発をもっと推し進めたいです。Microservicesは社内で既にやっているものの、上手くできてるとは言えないのでより良くしていきます。
