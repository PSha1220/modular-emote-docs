# Modular Emote Transition Settings

`ModularEmoteTransitionSettings` は **ME Action テンプレート**で、  
「StartState → テンプレート Entry」区間の遷移（Transition）設定を **ビルド時に再構成**するための `StateMachineBehaviour` です。

ME Action テンプレート内の特定ステート（例：`[ME] StartState Transition Settings`）にこの Behaviour を付けておくと、  
Pass がこれを検出し、**Exit Time / Duration / Offset / Interruption / 追加条件**を  
Behaviour の値を基準にして再構成します。

---

## 使い方（概要）

1. ME Action テンプレートの「遷移設定用ステート」に `ModularEmoteTransitionSettings` を追加します。
2. 下記 **Transition Settings** の値を、目的に合わせて設定します。
3. 必要に応じて **Additional Conditions** に追加フィルター条件を入れます。

> 참고  
> `VRCEmote == slotIndex` 条件はシステム側で自動処理されます。  
> そのため Additional Conditions は「追加でかけたい条件」だけを入れる用途で使用してください。

---

## Transition Settings

- **Interruption Source**  
  割り込み（中断）判定の基準となる側を指定します。  
  `None / Source / Destination / SourceThenDestination / DestinationThenSource`

- **Has Exit Time**  
  有効にすると Exit Time（0～1）を使用します。

- **Exit Time (0～1)**  
  Has Exit Time がオンのときに適用される終了タイミング（正規化値）です。

- **Transition Duration**  
  遷移の継続時間です。  
  `Fixed Duration` の設定に応じて「秒」または「正規化時間」として解釈されます。

- **Transition Offset (0～1)**  
  遷移先アニメーションの開始オフセット（正規化値）です。

- **Fixed Duration**  
  オンの場合、Transition Duration を **秒単位**で解釈します。  
  オフの場合、**正規化時間（Normalized）**で解釈します。

- **Ordered Interruption**  
  割り込み評価の順序を保証するかどうかです。

---

## Additional Conditions

`conditions` は、遷移に追加で付与される **追加条件の配列**です。

- 基本条件 `VRCEmote == slotIndex` は自動適用されます。
- ここには例として `IsSeated` やカスタムモード用パラメータなど、**追加フィルター**のみを入れることを推奨します。

### 対応タイプ

- Bool
- Int
- Float
- Trigger

### Int/Float 比較モード

- Greater
- Equal
- Less
- NotEqual

---

## 参照サイト

- <a href="https://docs.unity3d.com/Manual/class-Transition.html" target="_blank" rel="noopener noreferrer">Unity Doc (Animation transitions) </a>
