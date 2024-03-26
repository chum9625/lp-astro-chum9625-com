---
title: "FTPデプロイを自動化する"
meta_title: ""
description: "this is meta description"
date: 2024-03-26T20:19:00Z
image: "/images/blog-2024032601.png"
categories: ["Memo", "Tech"]
author: "25master"
tags: ["github-actions", "github" , "ci/cd"]
draft:  false
---

FTPアップロードをGitHub Actionsを使って自動化する手順を記録。

## GitHubでワークフローファイルを作成する

1. GitHub のリポジトリのActionsタブを選択し、set up a workflow yourself をクリックするとワークフローファイルの作成エディターが開く。
2. main.yml に以下のコードを記述。

```yml
on:
  push:
    branches:
      - main
name: 🚀 Deploy website on push
jobs:
  web-deploy:
    name: 🎉 Deploy
    runs-on: ubuntu-latest
    steps:
    - name: 🚚 Get latest code
      uses: actions/checkout@v4.0.0

    - name: 📂 Sync files
      uses: SamKirkland/FTP-Deploy-Action@4.3.4
      with:
        server: ${{ secrets.FTP_SERVER }}
        username: ${{ secrets.FTP_USERNAME }}
        password: ${{ secrets.FTP_PASSWORD }}
        server-dir: ${{ secrets.FTP_SERVER_DIR }}
        exclude: |
          **/.git*
          **/.git*/**
          **/node_modules/**
          .gitignore
          README.md
          **.json
```
- [チェックアウトアクション](https://github.com/actions/checkout)
- [FTPデプロイアクション](https://github.com/SamKirkland/FTP-Deploy-Action)
※上記２つのアクションは常に最新を使う

## GitHub Secretsを設定する

1. Setting＞Secrets and variables＞Actions の「New repository secret」ボタンをクリック。
2. キー名（FTP_SERVERなど）と設定値を登録する。

## GitHub Actionを動作させる

developブランチで開発をし、mainブランチにプルリクしてマージすることで発動。
