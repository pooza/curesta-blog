---
layout: default
title: キュアスタ！Blog
---

# キュアスタ！Blog

[キュアスタ！](https://precure.ml/)は、プリキュアファンのためのMastodonサーバーです。

当サーバーは、番組公式のものではありません。
東映アニメーション様等に、当サーバーについての問い合わせはしないようにお願いします。

## 最新記事

<ul class="post-list">
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <small>({{ post.date | date: "%Y-%m-%d" }})</small>
    </li>
  {% endfor %}
</ul>
