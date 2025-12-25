# ME FX Layer

`ME FX Layer` is an **Animator template (AnimatorController)** used in Modular Emote’s **FX merge process**.  
At build time, the template contents (states/transitions/parameters, etc.) are used to **add or merge layers** into the avatar’s **FX controller**.

---

## Sample Location

A sample template is provided in the package:

- `Packages/com.psha.modular.emote/Samples/ME Layer Templates`

---

## Where It Gets Merged (Concept)

The ME FX template is inserted into the avatar’s FX controller as an **additional layer**.  
Its behavior is similar to Modular Avatar’s `MA Merge Animator` workflow, and it also applies the `VRCEmote` index rewrite rules.

   ![MEFXLayer_A](../../images/MEFXLayer_A.png){ width="600" }  

> By default, only **layer 0** of the template is used.

---

## Template Parameter / Condition Rewrite Rules

Any **`VRCEmote` parameter** used as a condition in transitions inside the ME FX template is automatically rewritten at build time to match the **slot value (1–8)** selected in the Installer.

   ![MEFXLayer_VRCEmoteIndex](../../images/MEFXLayer_VRCEmoteIndex.png){ width="500" }  

- Example: even if the template contains a condition `VRCEmote == 1`,
  installing it into slot 3 will produce a build result where the condition becomes `VRCEmote == 3`.
- This rewrite applies to **all transition conditions** inside the template.

---

## Troubleshooting

### Q. The emote timing between the Action layer and the FX layer does not match.

Action and FX run on different layers, so timing can drift depending on the avatar structure and transition setup.  
This becomes especially noticeable when Action switches late (e.g. due to layer blending or intermediate states), while FX reacts immediately.

**Recommended fix**  
To align the “entry timing” between Action ↔ FX, we recommend adding a **shared entry signal parameter** (e.g. a Bool).

1. Add a parameter to both Action/FX templates (e.g. `ME_Enter`).
2. In the Action template’s “entry state”, add `VRC Avatar Parameter Driver` and set `ME_Enter = On` upon entry.
3. In the FX template, add `ME_Enter == True` as a condition on relevant states/transitions so FX follows Action immediately.

   ![MEFXLayer_FAQ_A](../../images/MEFXLayer_FAQ_A.png){ width="600" }  

> The key is to avoid having FX respond immediately only to the `VRCEmote` value,  
> and instead add a gate signal aligned to the Action entry timing.

---

### Q. If I reuse the same ME FX template multiple times, the FX animation does not work correctly.

If the same ME FX template is reused in multiple places, the FX controller may end up with **duplicate/similar layers**,  
which can lead to unintended results (e.g. duplicated Idle entry, or layer conflicts).

**Recommendation**  
Avoid reusing the same FX template when possible. Consolidate FX logic or split templates to reduce conflicts.  
If detected, the Installer shows a warning recommending against duplicate usage.

---

### Q. Loop animations look wrong in Gesture Manager.

In some environments, Gesture Manager previews may not display loop animations correctly.  
If the preview looks different from what you expect, we recommend testing **in-game after building**.

---
