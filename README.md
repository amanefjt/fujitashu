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

## 💰 記事の有料化 (codoc)

このテンプレートは [codoc](https://codoc.jp/) に対応しています。

### 有料記事の作成手順
1. **codoc アカウント作成**: 公開サイト設定を完了させます。
2. **有料記事のID取得**: codocダッシュボードで記事を作成し、`data-id` をコピーします。
3. **日記に貼り付け**: 日記の Markdown 内で以下のように記述します。

```markdown
{{< codoc id="取得した記事ID" >}}
{{< codoc-paywall >}}
```

> [!TIP]  
> 記事の途中に `codoc-paywall` を置くと、そこから上が「無料の試し読み」、下が「有料エリア」になります！

## 🧐 困ったときは (Troubleshooting)

### サイトが更新されない・繋がらない
- **反映待ち**: Cloudflare のビルド完了後、URL が有効になるまで数分かかることがあります。
- **リポジトリ名変更時の注意**: GitHub のリポジトリ名を変えた場合は、Cloudflare Pages の設定画面でリポジトリを「選び直す（再連携）」必要があります。反映されない時は「一度プロジェクトを消して作り直す」のが最も確実です。

---

## 🤖 管理情報
このサイトの構築経緯や技術的な詳細は、以下のログに記録されています。
- [移転・要件ログ](docs/management/requirements_log.md)
- [トラブルシューティング記録](docs/management/troubleshooting_log.md)

---

## 📅 更新履歴 (Latest Updates)

### 2026-04-01
- **有料化対応 (codoc 統合)**: `{{< codoc >}}` および `{{< codoc-paywall >}}` ショートコードを追加。
- **お引越し完了**: Google ドライブへの完全移行と親子連携設定の完了。
