# fujitashu

藤田周（Shu Fujita）の個人サイトのソース。<https://fujitashu.pages.dev/>

Hugo で作った静的サイトで、日記、プロフィール（日英）、喚起的編集のページ（日英）からなる。`main` ブランチに push すると Cloudflare Pages が自動で公開する。

## 日記を書く

GitHub の Web 画面で書く。

1. <https://github.com/amanefjt/fujitashu/new/main/content/diary> を開く
2. ファイル名を `YYYY-MM-DD.md` にする
3. 次のひな形を貼って、本文を書く
4. **Commit changes** を押す。数分後にサイトが更新され、Bluesky にも自動投稿される

```markdown
---
title: "2026年11月7日（土）タイトル"
date: 2026-11-07
slug: "2026-11-07"
draft: false
---

本文
```

## ローカルで確かめる

```bash
git pull          # 日記は Web で書くので、まず最新にする
hugo server       # http://localhost:1313/
```

## 構成と作業の決まりごと

AI エージェント（Claude Code など）向けの詳しい説明は [`CLAUDE.md`](CLAUDE.md) にある。ページの構成、フォーマット、検索（SEO）の設定、他リポジトリから触るときの注意はそちらを読む。

このサイトは、汎用テンプレート `my-simple-diary`（<https://github.com/amanefjt/my-simple-diary>）から派生した。テンプレートの使い方（Cloudflare Pages の設定、Markdown の書き方の案内）は、そちらの README に残っている。
