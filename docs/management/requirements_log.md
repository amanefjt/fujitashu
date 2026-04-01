# 移転ログ (Migration Log)

## 2026-04-01: サイト移転と親子連携構成の確立

### 1. 目的
- 旧 URL (`fujita-shu-diary.pages.dev`) から新 URL (`fujitashu.pages.dev`) への完全移転。
- テンプレートと自分用サイトを同一の Google ドライブ内で効率的に管理する構成の確立。

### 2. 構成の詳細
- **親 (template)**: `/Users/shufujita/Library/CloudStorage/GoogleDrive-amanefjt@gmail.com/マイドライブ/simple-diary/template`
- **子 (fujitashu)**: `/Users/shufujita/Library/CloudStorage/GoogleDrive-amanefjt@gmail.com/マイドライブ/simple-diary/fujitashu`

### 3. 日記投稿フロー (具体的Web操作)
ブラウザから直接日記を書く際の手順です。
- **URL**: [日記の新規作成 (GitHub)](https://github.com/amanefjt/fujitashu/new/main/content/diary)
- **手順**:
  1. ファイル名 (File name) に `2026-04-01.md` などの日付を入れる。
  2. 本文を書く（Markdown形式）。
  3. 画面下部の **[Commit changes...]** をクリックして保存。
  4. 数分後にサイトが更新されます。

### 4. エージェント (.agent/ フォルダ) の重複について
**設計意図: スキルの共通化**
`template` と `fujitashu` の両方に同じ指示書（Rules/Skills）を置くことで、エージェント（AI）がどちらのフォルダを触る際も、全く同じ「日記投稿の補助」や「デザイン修正」の能力を安定して発揮できるようにしています。

### 5. 運用上の合意事項
- デザイン改良は `template` 側で行い、`git pull upstream main` で `fujitashu` に反映させる。
- Google ドライブに集約することで、Downloads フォルダに散らばる管理の手間を解消しました。
