---
title: "開発チームだけで機能開発を行わないSaaSサービス改善の手法"
date: 2018-11-19T01:09:16+09:00
description: ""
categories: []
tags: ["saas"]
draft: false
image: ""
author: "m-nakamura145"
---

プロダクトを改善していくために、開発チームは毎日機能開発を行っていますが、時には既存の仕様の変更の場面に遭遇します。

<!--more-->

これらは少なからず既存顧客に対して影響を与えるため、顧客とのコミュニケーションが必須になってきます。

トレタのサポートチームやカスタマーサクセスチームは毎日既存顧客とのコミュニケーションを行っており、顧客との信頼関係が確立されています。これらのチームと開発チームが協力して機能開発を行うことによって、顧客影響をなるべく最小にするように取り組んでいます。

トレタで実際にあったケースを例に見ていきます。

## CSVファイルのソート順の仕様変更
   
トレタを利用している店舗が、今までトレタで入力してきた予約データをCSVファイルとしてダウンロードする機能があります。CSVの生成はSidekiqのWorkerが深夜に生成する実装になっています。

このWorkerがたまに正常に動作しない状態が続いていました。詳しく調査すると、**発行しているクエリのORDER BYを外せば直るけど、このORDER BYはなぜつけられているのか？これは仕様なのかわからない**ということが判明しました。

このWorkerの実装はかなり古く、仕様を決めた実装者も退職済みという状態で誰にも正解がわかりません。しかし、正常に可動させるためにソート順は外したいです。

影響範囲の店舗は調査済みですが、実際にこのソート順を変えて困る店舗がどのくらいいるのかは開発チームだけではわかりません。そこでサポートチームとカスタマーサクセスチームに相談しに行くと、このCSVをダウンロードした後の各店舗ごとの詳しい使い方を教えてくれ、「**仕様を変更して大丈夫だと思う。問い合わせがあってもなんとかする**」と言ってくれました。

この力強い言葉で開発チームは無事に仕様変更することを決定でき、機能改善することができました。常にチーム間でコミュニケーションを取っているので、これらの決定は原因発覚から決定まで1〜2時間程度で終わりました。

SaaS開発では、複数のチームが顧客との信頼関係を構築します。大幅な仕様変更を行うときも、開発チームだけで考えるのではなく、サポートチームやカスタマーサクセスチームも含めて施策を考えることで、柔軟な対応を行うことが可能です。
