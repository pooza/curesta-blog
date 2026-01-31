---
title: 2019/12/14 Google Public DNSがTLD .ml をキャッシュしない
categories: 障害
date: 2019-12-15
layout: post
permalink: /articles/20191214GooglePublicDNSがTLDmlをキャッシュしない/
---
## 発生時刻
2019/12/14 19:00頃〜23:40

## 現象
[キュア！]({{ "/articles/キュア！/" | relative_url }})（トゥート）が出来ない

## 原因
Google Public DNS（8.8.8.8 / 8.8.4.4）が、トップレベルドメイン .ml 配下のゾーンをキャッシュしなくなりました。
キュアスタ！のサーバはこのサービスを利用して名前解決を行っている為、[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)は `precure.ml` を名前解決して、Mastodonのサービスを見つけるということができなくなっていました。
キュアスタ！では、すべての[キュア！]({{ "/articles/キュア！/" | relative_url }})（トゥート）が、最終的にはモロヘイヤを通じて行われる為、ユーザーの全てのトゥートが影響を受けました。

根本原因である、Google Public DNSが `precure.ml` を名前解決しない件は、12/15現在も未解決。
トップレベルドメイン .ml 配下の他のサービスも影響を受けている模様。

## 応急対応
`/etc/resolv.conf` に、以下追記。
```
nameserver 1.1.1.1
nameserver 1.0.0.1
```
これらのネームサーバは、CloudFlareのパブリックDNS。


## 今後の対応
キュアスタ！側サービスの障害ではない為、根本原因の解決は困難。
長期的には、 `precure.ml` ドメインを他のものに変更する以外の対策は存在しないと考えられます。
