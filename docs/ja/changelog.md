# 更新履歴

## 1.3.5

### 変更

- **Object Name** を、アバタービルド時に適用される名前であることが分かりやすい **Build Object Name** に変更しました。
- **Auto Rename Object** オプションを削除しました。**ME FX マージを使用** を有効にすると、**Build Object Name** が直接表示されます。
- **Setup VRC Emote** で実際の GameObject 名をエモート名に変更する動作を廃止しました。
- **Build Object Name** が空欄の場合、**Setup VRC Emote** を押すと現在の GameObject 名が自動入力されるようになりました。
- **ME FX マージを使用** をオフにすると **Build Object Name** もクリアされ、再度オンにしたときは他の関連項目と同じく空の状態から始まります。
- 新しい **Build Object Name** のフローと案内文に合わせて、エディター言語ローカライズを更新しました。

### 改善

- 以前の名前不一致警告を、**Build Object Name** を案内する短いガイダンスメッセージに置き換えました。
- **Build Object Name** の案内が表示されている間、**開発者オプション** の右側に **情報アイコン** を表示するよう改善しました。
- ME FX 使用時の案内を整理し、**Build Object Name** が空欄のままだと後からオブジェクト名を変更した際にアニメーションパスが変わり、ビルド結果に影響する可能性があることを明確化しました。

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
