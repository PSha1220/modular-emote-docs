# ME Action Layer

`ME Action Layer` は、Modular Emote の **Action マージアルゴリズム**で使用するために用意された **Animator テンプレート（AnimatorController）**です。  
このテンプレートはビルド時に、テンプレート内部の構成（ステート／遷移／パラメータ等）を **サブステートマシン（Sub StateMachine）** 形式へ変換し、アバターの **Action レイヤー**へマージされます。

---

## サンプルの場所

パッケージには基本テンプレートのサンプルが含まれています。

- `Packages/com.psha.modular.emote/Samples/ME Layer Templates`

---

## マージされる位置（概念）

テンプレートはアバターの Action レイヤー内で、**指定された開始／終了ステートの間**に挿入されます。

つまり、流れは次のようになります。

`Prepare Standing` → *(ME Template Sub StateMachine)* → `BlendOut Stand`   

   ![MEActionLayer_A](../../images/MEActionLayer_A.png){ width="600" }

> 開始／終了ステートは、Installer の `開始アクションステート / 終了アクションステート` 設定（または Setup の自動推定）により異なる場合があります。

## テンプレートのパラメータ／条件の置換ルール

ME Action テンプレート内部で遷移（Transition）の条件として使用される **`VRCEmote` パラメータ**は、  
ビルド時に **Installer で指定したスロット値（1～8）** に合わせて自動的に置換されます。 

   ![MEActionLayer_VRCEmoteIndex](../../images/MEActionLayer_VRCEmoteIndex.png){ width="500" }


- 例：テンプレートに `VRCEmote == 1` 条件が含まれていても、  
  ユーザーがスロット 3 にインストールすると、ビルド結果では `VRCEmote == 3` に変換されます。
- この置換は、テンプレート内部の **すべての遷移条件**に適用されます。

> したがってテンプレートを特定スロット番号に固定して作成する必要はなく、  
> 1 つのテンプレートを複数スロットで再利用できます。

---

## 開始ステート → テンプレートサブステートマシン 遷移（Transition）設定

「開始ステートから ME テンプレートサブステートマシンへ入る遷移」の性質（Exit Time / Duration / Interruption など）をテンプレート側で制御したい場合は、  
**`Modular Emote Transition Settings`** Behaviour を使用してください。

### 設定方法

1. ME Action テンプレートに独立したステートを 1 つ追加します。
2. ステート名を次のように指定してください。

   - `[ME] StartState Transition Settings`

3. そのステートに Behaviour を追加します。

   - `Add Behaviour` → `Modular Emote Transition Settings`

4. 원하는遷移値を設定します。
   - Exit Time / Duration / Offset / Interruption
   - Additional Conditions（追加条件）  

   ![MEActionLayer_ModularEmoteTransitionSettings](../../images/MEActionLayer_ModularEmoteTransitionSettings.png){ width="800" } 



> この Behaviour が存在する場合、ビルド時に「開始ステート → テンプレート進入遷移」を設定値に基づいて再構成します。

---

## トラブルシューティング

### Q. Transition Settings を設定してもテンプレートへ素早く切り替わりません。

アバター Action レイヤーで **Entry → ME サブステートマシン**へ向かう経路の途中に、  
`VRC Playable Layer Control` Behaviour により **Blend Duration** を任意に大きくしているステートがあると、この現象が発生する場合があります。

**対処方法（推奨）**  
ME Action テンプレートで **Entry 直後の最初のステート（進入直後ステート）**に `VRC Playable Layer Control` を追加し、  
Blend 設定が意図した切り替え速度になるよう調整してください。

   ![MEActionLayer_VRCPlayableLayerControl](../../images/MEActionLayer_VRCPlayableLayerControl.png){ width="600" }    

---

### Q. Gesture Manager でループアニメーションが不自然に見えます。

現在、一部環境では Gesture Manager のプレビューで **ループアニメーションが正しく表示されないケース**があります。  
プレビュー結果が想定と異なる場合は、**ビルド後にゲーム内で動作を直接テスト**することを推奨します。

---
