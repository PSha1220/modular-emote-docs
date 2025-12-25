<figure markdown>
  ![Hero](images/hero.png){ width="720" }
</figure>

# Modular Emote

**Modular Emote** は、アニメーションをアバターへ簡単に導入するための手法から考案された、  
VRChat SDK3 Avatar 向けの **NDMF ベース Non-destructive アニメーションパッチツール**です。

## 特徴

- **元の AnimatorController アセットを変更せず**、  
  NDMF の **VirtualAnimatorController レベルでのみ** グラフをマージします。
- **非破壊（Non-destructive）** の原則に従い、元のメニュー／コントローラアセットを直接変更しません。
- ビルドパイプライン（NDMF）で **仮想コントローラを編集**し、最終結果のみを反映します。
