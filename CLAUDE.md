# CLAUDE.md

藤田周の個人サイト（`https://fujitashu.pages.dev/`）のリポジトリ。Hugo の静的サイトで、GitHub `amanefjt/fujitashu` の `main` に push すると Cloudflare Pages が自動でビルド・公開する。最終改訂：2026-11-07。

## 前提（先に読む）

- **日記は GitHub の Web 画面から直接書いている**。ローカルは常に古い可能性がある。**作業の最初に必ず `git pull`**（2026-10-03 に Cultivator から作業したとき、GitHub 側が日記 71 コミット先行していた）。
- **他のリポジトリからも触る**。Cultivator（`~/Code/Cultivator`）のセッションから、喚起的編集ページなどを直したことがある。その場合も、このファイルの内容（pull してから、ビルド確認、push の前に確認）に従う。
- **匿名ではない**。2026-10-15 にサイト名を「Shu Fujita 藤田周」にし、2026-11-07 に実名公開を前提とすると藤田が確認した。`authorName` 等は埋めてある。古い文書に「匿名性」「タイトルは『日記』」とあれば古い前提。
- **push は確認してから**。`.claude/settings.local.json`（ルート側）は `git push *` を許可しているが、藤田に確認せずに push しない。
- 作業対象は `fujitashu/` のみ。隣の `template/`（汎用テンプレート）は 2026-04-03 以降更新しておらず、運用終了予定。

## コマンド

```bash
hugo server                 # ローカルプレビュー
hugo --minify -d /tmp/x     # ビルド確認（public/ を汚さない出力先を指定）
hugo new content/diary/YYYY-MM-DD.md
```

ローカルの Hugo は新しい（0.167）が、Cloudflare は環境変数 `HUGO_VERSION=0.146.6`。**どちらでも動く書き方にする**（新しい関数を使わない）。

## 構成

- `hugo.toml` — サイト設定。`[params]` の `metaDescription`（検索結果の説明文）、`authorName`、`sameAs`（JSON-LD に出る外部プロフィールのリスト）を含む
- `content/diary/` — 日記（159 本、`YYYY-MM-DD.md`）
- `content/about.md`（`/about/`）、`en.md`（`/en/`）— プロフィール日英
- `content/evocative.md`（`/evocative/`）、`evocative-en.md`（`/en/evocative/`）— 喚起的編集のページ日英。画像は `static/images/evocative/`
- `layouts/_default/baseof.html` — 共通の枠。ナビは `/en/` 以下で英語用に切り替わる。meta description・canonical・OGP・JSON-LD（トップのみ）もここ
- `layouts/home.html`（日記 30 件ずつ全文）、`diary/list.html`、`_default/single.html`、`page/single.html`（`type: page` 用）、`404.html`
- `static/style.css`（バニラ CSS のみ）、`static/robots.txt`
- `.github/workflows/bluesky-notify.yml` — 日記が**新規追加**されたら Bluesky に自動投稿（Secrets は GitHub 側）
- `.agent/` — AI エージェント向けの規則とスキル。`docs/management/` — 2026-04 の移転ログ（歴史的記録）

## 日記のフォーマット

```markdown
---
title: "YYYY年M月D日（曜）タイトル"
date: YYYY-MM-DD
slug: "YYYY-MM-DD"
draft: false
---
```

- ファイル名 `content/diary/YYYY-MM-DD.md`。**既存ファイルを上書きしない**。同名があれば確認する
- `publishFuture = true` なので未来日付も公開される
- Markdown 内に生 HTML を書ける（`unsafe = true`）

## 検索（SEO）まわり

- ページごとの description：日記は本文の冒頭 120 字から自動。固定ページは frontmatter の `description:`。ないものはサイト共通の `metaDescription`
- 新しいプロフィール先（ORCID、Academia、Bluesky、立命館の教員ページ）ができたら、`hugo.toml` の `sameAs` に URL を足す
- Google Search Console は藤田の Google アカウントで登録する（HTML タグ方式。`pages.dev` は DNS 認証ができない）。登録後にタグを `baseof.html` の `<head>` に足す必要がある

## 設計方針

- 設定値（名前・説明文・リンク）は `hugo.toml` の `[params]` から参照し、テンプレートに直書きしない
- CSS は `static/style.css` のみ。外部フレームワークは入れない
- プロフィール類は「〇〇を講演一覧に加えて」のような指示で、該当の `##` 見出しの節を編集する。新しい固定ページは `content/` に置いて `type: page` を指定する
