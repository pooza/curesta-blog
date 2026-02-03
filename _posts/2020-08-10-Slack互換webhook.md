---
title: Slack互換webhook
date: 2020-08-10
categories: 機能
---
ボットや自動投稿を作る方の便宜の為、webhookを提供しています。
仕様上は、Slackの同名機能のサブセットです。簡単なSlackボットなら、既存のものを無改造でキュアスタ！対応にできるかもしれません。

## 利用の手順

[「東映アニメーション プリキュア公式」の新着情報ボット](https://precure.ml/@toei_bot)のAtomフィードを、[IFTTT](https://ifttt.com/)を使ってwebhookに転送する例で説明します。

### RSS/Atomフィードを調べる。

このボットは、以下のAtomフィードをもとに[キュア！](/articles/キュア！/)を行っています。
https://precure.b-shock.org/feed/v1.0/site/toei

### webhookのURLを調べる。

[モロヘイヤHOME](https://precure.ml/mulukhiya)で、webhookのURLを調べられます。
その端末でトークンの登録（アプリケーションの認証）をまだ行っていなかったら、最初に実行してください。
スマホアプリの設定でおなじみの画面が出てきますので、指示に従ってください。

トークンが登録済みなら、「環境設定」画面にwebhookのURLがあるはずです。

![](/images/Slack互換webhook/手順5.png)

画面にも赤字で書かれていますが、このURLは決して他人に教えてはいけません。たとえ相手が管理人であっても。

ここまでで事前準備は終了。このあと実際に、[IFTTT](https://ifttt.com/)で登録を行っていきます。

### トリガー

[IFTTT](https://ifttt.com/)の画面上で、[Create](https://ifttt.com/create)を実行します。
`rss` 等の検索語で __RSS Feed__ トリガーを検索し、これを選択。

![](/images/Slack互換webhook/手順1.png)

そして、先ほどのフィードURLを設定。
AtomフィードもRSSの一種とみなされ、登録可能です。今さら野暮を言う様ですが。

![](/images/Slack互換webhook/手順2.png)

### アクション

`webhook` 等の検索語で __Webhooks__ アクションを検索し、これを選択。

![](/images/Slack互換webhook/手順3.png)

設定内容は、こんな感じ。

![](/images/Slack互換webhook/手順4.png)

URLは、先ほど調べたwebhookのURL。
Bodyには、たとえば以下の様なJSONを。

```
{"text":"<<<{{EntryTitle}}>>>\n<<<{{EntryUrl}}>>>"}
```

保存して実行しましょう。以上です。
