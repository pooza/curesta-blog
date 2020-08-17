---
title: NowPlaying
date: 2020-08-17
categories: 機能
---

本来Mastodonにない、多くのナウプレ機能を内蔵しています。
積極的に曲紹介していきましょう。

## 曲名指定

`#nowplaying ガンバランスdeダンス〜夢みる奇跡たち〜 宮本佳那子`

こんな感じの[キュア！](/articles/キュア！)を入力すると、対応サービスから楽曲を検索し、該当曲に関する情報追記などが行われます。

曲名だけの指定でも動作しますが、誤判定が多くなる様です。極力、アーティストを省略せずに指定してください。

![曲名指定](曲名指定.png)

### 対応サービス

- iTunes Store / Apple Music
- Spotify

### 技術的な詳細
- https://github.com/pooza/mulukhiya-toot-proxy/wiki/ItunesNowplayingHandler
- https://github.com/pooza/mulukhiya-toot-proxy/wiki/SpotifyNowplayingHandler

## URL指定

`#nowplaying https://music.apple.com/jp/album//1299587212?i=1299587213`

こんな感じの[キュア！](/articles/キュア！)を入力すると、該当曲に関する情報追記などが行われます。

![URL指定](URL指定.png)

### 対応サービス

以下のURLに対応しています。

- iTunes Store / Apple Music 楽曲/アルバムのURL
- YouTube Music 楽曲URL
- Amazon Music 楽曲URL
- Spotify 楽曲/アルバムのURL

上記は概ね、同じ再生数で権利者に貢献できる額が多い順になっています。（2020年8月現在）
曲紹介はアーティストへの応援も込めているはず。同じ曲が複数のサービスに存在する場合は、上記の優先順位での曲紹介をご検討頂けると幸いです。

特にSpotifyは、曲数が豊富で使いやすいのは確かですが、アーティストへの貢献が最も少ないサービスです。
また、プリキュア関連楽曲の公開を、短期間ですがやめていた時期があります。今後この様なことが度々起きるならば、曲紹介には使いづらい面があると管理人個人は感じます。

### 技術的な詳細
- https://github.com/pooza/mulukhiya-toot-proxy/wiki/ItunesURLNowplayingHandler
- https://github.com/pooza/mulukhiya-toot-proxy/wiki/AmazonURLNowplayingHandler
- https://github.com/pooza/mulukhiya-toot-proxy/wiki/YouTubeURLNowplayingHandler
- https://github.com/pooza/mulukhiya-toot-proxy/wiki/SpotifyURLNowplayingHandler



