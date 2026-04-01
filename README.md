# ユーザー個人サイト (fujitashu) - 運用マニュアル

このリポジトリは、`my-simple-diary` テンプレートをベースにした、あなた専用の個人サイトです。

---

## ✍️ 日記を書く手順 (Workflow)

一番簡単な方法は、GitHub のブラウザ画面から直接書くことです。

1. **投稿用URLを開く**: [新規日記作成](https://github.com/amanefjt/fujitashu/new/main/content/diary)
2. **ファイル名を決める**: `2026-04-01.md` のように日付にします。
3. **内容を書く**: Markdown 形式で自由に書きます。
4. **保存する**: 画面下の **[Commit changes...]** をクリック。
5. **完了**: 数分後に `https://fujitashu.pages.dev/` に反映されます。

---

## 🌟 テンプレートとの同期方法 (Advanced Sync)

このサイトは、隣にある `template` フォルダを「親」として登録しています。テンプレート側のデザインを最新にアップデートしたい時は、以下のコマンドを実行するだけで日記を消さずにデザインだけを同期できます。

```bash
git pull upstream main
```

---

## 🧐 困ったときは (Troubleshooting)

### サイトが更新されない・繋がらない
- **反映待ち**: Cloudflare のビルド完了後、URL が有効になるまで数分かかることがあります。
- **リポジトリ名変更時の注意**: GitHub のリポジトリ名を変えた場合は、Cloudflare Pages の設定画面でリポジトリを「選び直す（再連携）」必要があります。反映されない時は「一度プロジェクトを消して作り直す」のが最も確実です。

---

## 🤖 管理情報
このサイトの構築経緯や技術的な詳細は、以下のログに記録されています。
- [移転・要件ログ](docs/management/requirements_log.md)
- [トラブルシューティング記録](docs/management/troubleshooting_log.md)
