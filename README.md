# curesta-blog

このリポジトリは、Hexo から Jekyll に移行した静的ブログです。GitHub Pages（GitHub Actions）でビルド・公開します。

## 全体像
- 記事: `/_posts/` に配置（Jekyll 標準）
- 画像: `/images/` に集約（記事フォルダ名で整理）
- 生成物: `/_site/` に出力（公開対象）
- URL: `/articles/:title/` 形式
- カテゴリ一覧: `/categories/`
- ビルド/公開: `.github/workflows/pages.yml`

## 主要ディレクトリ
- `_posts/` 記事（`YYYY-MM-DD-<slug>.md`）
- `images/` 画像（`images/<記事名>/...`）
- `_layouts/` レイアウト
- `assets/` スタイル等
- `docs/` 手順書（移行メモなど）

## 記事の書き方
### ファイル名
```
_posts/2026-01-30-実況.md
```

### front‑matter（最小）
```
---
title: 実況
date: 2026-01-30
categories: 実況
---
```
`layout` は `_config.yml` の defaults で自動付与されます。

### リンク（記事同士）
```
[リンクテキスト]({{ "/articles/記事スラッグ/" | relative_url }})
```

### 画像
```
![]({{ "/images/記事名/画像.png" | relative_url }})
```

## 普段行う操作
### ローカルプレビュー
```
bundle exec jekyll serve --livereload
```
ブラウザ: `http://127.0.0.1:4000/curesta-blog/`

### ビルド確認
```
bundle exec jekyll build
```

## GitHub Pages / Actions
- `dev` では build のみ
- `main` で deploy

## Ruby/Jekyll 環境
このリポジトリでは rbenv を使用します。
```
rbenv local 3.3.10
bundle install
```

## 注意点
- `permalink` は原則書かない（`_config.yml` のデフォルトを使う）
- 既存URL維持が必要なら、`permalink` を残すこと

---
詳しい移行手順は [`docs/migration-jekyll.md`](docs/migration-jekyll.md) を参照。
