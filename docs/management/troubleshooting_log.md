# トラブルシューティング ログ (2026-04-01)

## 1. Cloudflare Pages の URL 切り替え
- **事象**: プロジェクト名を `fujitashu` に変更したが、以前の `fujita-shu-diary.pages.dev` が生き続け、新 URL が `NXDOMAIN` (名前解決不能) になった。
- **原因**: 
  1. DNS propagation (反映) に時間がかかる。
  2. プロジェクト名を変更しても、内部のリポジトリ ID との紐付けが「古い名前」で残っていると、ビルドが走らない場合がある。
- **解決策**: Cloudflare Pages で**一度プロジェクトを削除し、新しい名前で再作成（GitHub 接続をやり直し）する**のが最も確実かつ迅速な解決法として機能した。

## 2. ローカル Git フォルダの親子連携 (Upstream)
- **事象**: テンプレートを磨きながら、自分用の日記も書きたいが、同期が面倒。
- **解決策**: 
  - `git remote add upstream ../template` を自分用フォルダで実行。
  - デザイン変更時は `git pull upstream main` で引き込む構成を採用。
  - Google ドライブ上で相対パス (`../template`) を使うことで、クラウド同期環境でも壊れない連携を構築。

## 3. AI エージェントのパス検証制限
- **事象**: AI が Downloads フォルダ外（Google ドライブ）のコマンドを実行しようとすると「path is not in a workspace」でエラーになる。
- **解決策**: 
  - ユーザーに「ワークスペースパスの検証 (Workspace Path Validation)」をオフにしてもらう。
  - それでも通らない場合は、AI が `setup.sh` を作成してユーザーにターミナルで実行してもらう方法が有効。
