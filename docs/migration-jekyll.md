# Hexo → Jekyll 移行手順（GitHub Pages）

この手順は Hexo ベースのブログを GitHub Pages の Jekyll に移行するための記録です。
このリポジトリ（curesta-blog）の構成・運用を基準にしています。

## 前提
- 既存リポジトリは Hexo 構成（`source/`, `themes/`, `scaffolds/` 等）
- 公開URLは `/articles/:title/` 形式を維持
- 画像は `images/` 配下の共通フォルダ運用
- GitHub Pages は GitHub Actions でデプロイ

## 1. ブランチ作成
```
git switch -c dev
```

## 2. Ruby/Jekyll 環境
```
rbenv install 3.3.10
rbenv local 3.3.10

gem install bundler
```

### Gemfile
```
source "https://rubygems.org"

gem "jekyll", "~> 4.3"
```

```
bundle install
```

## 3. Jekyll 設定
### `_config.yml`
```
title: <ブログタイトル>
description: ''
author: <作者>
lang: ja
timezone: Asia/Tokyo
url: https://<user>.github.io
baseurl: /<repo>

permalink: /articles/:title/

defaults:
  - scope:
      path: ""
      type: posts
    values:
      layout: post

markdown: kramdown
kramdown:
  input: GFM

exclude:
  - node_modules
  - package.json
  - yarn.lock
  - scaffolds
  - themes
  - _config.hexo.yml
  - source
  - public
```

### レイアウト
- `_layouts/default.html`
- `_layouts/post.html`

（このリポジトリの内容を流用）

### CSS
- `assets/main.css` を作成（このリポジトリの内容を流用）

## 3.5 テーマ（Mastodon風）
このブログの見た目を流用する場合は、以下をコピーします。
- `_layouts/default.html`
- `assets/main.css`

必要に応じて、サイト説明文やナビ項目を変更します。

## 4. 投稿の移行
### 4-1. `source/_posts` → `/_posts`
- ファイル名を `YYYY-MM-DD-<slug>.md` に変更
- `permalink:` は削除（既存URL維持なら不要）
- `layout:` は削除（defaults で指定済み）

### 4-2. front‑matter
- `date` のフォーマットは `YYYY-MM-DD` に統一
- `data:` など誤字は `date:` に修正

## 5. リンク修正
### 5-1. Hexoの `{% post_link %}`
- Jekyllリンクに置換
```
[表示名]({{ "/articles/スラッグ/" | relative_url }})
```

### 5-2. 旧ドメインの絶対URL
- `https://blog.precure.ml/articles/...` は上と同様に変換

## 6. 画像移行
### 共通フォルダ運用
- `source/_posts/<記事>/` → `images/<記事>/` へ移動
- `![](/images/...)` に統一
```
![]({{ "/images/<記事>/<画像>" | relative_url }})
```

## 7. index / categories
- `index.md` を用意（ホーム）
- `categories.md` を用意（カテゴリ一覧）

## 8. GitHub Actions
- `/.github/workflows/pages.yml` を Jekyll ビルドに変更
- `dev` では build のみ、`main` で deploy

## 9. Hexo関連の整理
```
rm -rf themes scaffolds package.json yarn.lock _config.hexo.yml
```

## 10. ローカル確認
```
bundle exec jekyll build
bundle exec jekyll serve --livereload
```

## 11. GitHub Pages 設定
- Settings → Pages → Source: GitHub Actions
- `dev` で build が通ることを確認
- `main` にマージして公開

## 12. 注意点
- 既存の `permalink` を削除するとURLが変わる場合がある
- `:title` はファイル名のスラッグが使われる

---

必要に応じて、この手順を他リポジトリに合わせて調整する。
