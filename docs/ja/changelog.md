# 更新履歴

## 1.3.2

### 追加

- マージされた ME FX レイヤー使用時の **Auto Rename Object** 機能を追加しました。
- ビルド時に使用する名前を指定できる **Object Name** 項目を追加しました。

### 変更

- **Auto Rename Object Name** を **Auto Rename Object** に名称変更しました。
- 以下の項目に対して、エディター言語連動のローカライズを追加しました。
  - **Auto Rename Object**
  - **Object Name**
- **Auto Rename Object** は **Use Merge ME FX Layer** が有効なときのみ表示されます。
- **Object Name** フィールドも、関連オプションが有効な場合のみ表示されるよう整理しました。
- VRChat SDK の不要なダウングレードを避けるため、VPM パッケージの依存関係の範囲を調整しました。
- **Psha-VPM-Repository** 経由で最新バージョンを導入できるよう、リポジトリ／Listing 配信構成を整理しました。

### 改善

- **名前不一致警告** の表示条件を改善しました。
- **Setup VRC Emote** 実行時に `<br>`、改行、`<color>` などの表示用タグを除去してからオブジェクト名へ適用するよう改善しました。

### 修正

- 以下に関連するコンパイル問題を修正しました。
  - `autoRenameObjectName`
  - `objectName`
  - `GetResolvedBuildObjectName`
- 既存のプレハブやシーンインスタンスでも新オプションが正しく動作するよう、初期化／マイグレーション処理を改善しました。

### メンテナンス

- 一般的なリリースおよび配布まわりのメンテナンスを行いました。
