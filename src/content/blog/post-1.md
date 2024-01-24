---
title: "Astroでポートフォリオを兼ねたブログを作る"
meta_title: ""
description: "this is meta description"
date: 2024-01-21T16:03:00Z
image: "/images/image-placeholder.png"
categories: ["memo", "Tech"]
author: "25master"
tags: ["astro", "github"]
draft: false
---

Astroは、効率的かつ高速に静的なウェブサイトを構築するためのツールです。
このサイトは Astro を使用して構築されたポートフォリオテンプレートをカスタマイズして作成しています。
以下は、その手順の記録です。

## 1. Astroのインストール

1. [公式サイトのテーマ](https://astro.build/themes/)からお気に入りを選ぶ。
2. Get started をクリックし、Githubのリポジトリからテーマを clone する。

```bash
git clone https://github.com/zeon-studio/astroplate.git my-project-name

cd my-project-name

npm install
```

## 2. デプロイ先の準備

1. [Cloudflare pages](https://pages.cloudflare.com/) を使って運用するため、アカウントを作成する。
2. Github のリポジトリを作成する。

## 3. 開発用ローカルサーバー起動

- 初回の npm run dev は起動不可だった。
- package.json を確認、"scripts"には デフォルトで yarn が設定されているので、 npm run に変更。
- http//localhost:4321/ にアクセス。

```bash
npm run dev

local http//localhost:4321/
```
## 4. Github に push

- リモートリポジトリを書き換えてから push。

```bash
git remote -v 

origin https://github.com/zeon-studio/astroplate.git (fetch)
origin https://github.com/zeon-studio/astroplate.git (push)

git remote set-url origin https://github.com/chum9625/my-repository/

git add .
git commit -m "first commit"
git push -u origin main
```

## 5. AstroサイトをCloudflare Pagesにデプロイする

- [Cloudflare公式](https://docs.astro.build/ja/guides/deploy/cloudflare/)に沿って進める

1. Wrangler CLIをインストール。
2. wrangler loginを使ってCloudflareアカウントでWranglerを認証。
3. ビルドコマンドを実行。
4. npx wrangler pages deploy dist を使ってデプロイ。

```bash
npm install -g wrangler 

wrangler login

npm run build

npx wrangler pages deploy dist
```

❣️プロジェクトの要件やデザインに応じ、さらに詳細なカスタマイズをしていく。
