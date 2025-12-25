# VRC Emote Installer

This document is a reference that explains **the VRC Emote Installer inspector layout** and what each item means,
including auto-detection and validation behavior.

> Assumptions
>
> - This component is designed to work with an avatar that uses an **Emote structure driven by the `VRCEmote` (Int) parameter**.
> - This document assumes you already understand the basics of Unity Animator (layers / states / transitions / parameters).

---

## Basic Workflow

`VRC Emote Installer` merges ME templates (AnimatorController) into the avatar’s **Action/FX layers** and builds the final Emote behavior at build time.

![EmoteInstaller_Creator_Basis](../../images/EmoteInstaller_Creator_Basis.png){ width="250" }

- If the object (Installer) is **disabled**, it will be **skipped** during the build process.
- If multiple Installers exist for the same slot, the one **higher in the hierarchy (closer to the root)** takes priority.

---

## Inspector Layout at a Glance

The inspector is organized in the following order:

1. **Content**
2. **Developer Options**
3. **Setup VRC Emote** / **Default**
4. **Show Applied Changes (Preview)**
5. **Editor Language**

---

## 1) Content

This section is for quickly checking “what is currently configured”.

- **Name**  
  Displays the emote name (`emoteName`). **(A)**  
  (This value is linked to *Developer Options → Menu Settings → Emote Name*.)

- **Icon Preview**  
  Previews the menu icon (`menuIcon`). **(B)**

- **Target Slot No. (1 to 8)**  
  Sets the target slot (`slotIndex`). **(C)**  
  (This value is used as the condition `VRCEmote == slot` when merging menus/animators.)

![EmoteInstaller_Creator_Content](../../images/EmoteInstaller_Creator_Content.png){ width="500" }

---

## 2) Developer Options

This section includes auto-detection, validation, and advanced configuration.  
If an issue is detected, its status is shown with **warning/error icons** on the right. **(A)**

  ![EmoteInstaller_Creator_Dev_1](../../images/EmoteInstaller_Creator_Dev_1.png){ width="500" }

### 2-1) VRC Emote Settings

- **Target VRC Emote Menu**  
  Sets the Emote menu field to customize.  
  This uses **auto-detection**.

---

### 2-2) Menu Settings

These are the items that are actually applied to the menu.

- **Emote Name**  
  The name shown in the VRC Emote menu.

- **Menu Icon**  
  The icon shown in the VRC Emote menu.  
  If the icon is not a Texture2D asset, or its import settings are likely to fail VRC validation,
  an **error box** may appear along with the **Fix Icon Settings (256, Compressed)** button.

- **Type**  
  The control type. `None` keeps the existing type.

- **Value** (Read-only)  
  The value corresponding to the selected slot number.

- **Parameter** (Read-only)  
  Displayed as `VRCEmote, Int`.

---

### 2-3) Avatar Layer Settings

Specifies the target avatar layer controllers.

- **Avatar Action Layer**  
  Uses the avatar descriptor Action layer setting via **auto-detection**.

- **Avatar FX Layer**  
  Uses the avatar descriptor FX layer setting via **auto-detection**.

---

### 2-4) ME Layer Merge Settings

- **ME Action Layer**  
  Assign the Action template (AnimatorController) to merge.  
  The template contents (states/transitions/parameters, etc.) are converted into a Sub StateMachine and inserted/replaced
  in the avatar Action layer between the configured range (Start → End).  
  Any conditions in the template that use the `VRCEmote` parameter are converted to the **selected slot value**.  
  By default, only **layer 0** of the template is used.

- **ME FX Layer**  
  This field is enabled only when **Use Merge ME FX** is enabled in Advanced Options.  
  Assign the FX template (AnimatorController) to merge.  
  The prepared ME FX template (states/transitions/parameters, etc.) is merged/added to the avatar FX controller as a **new layer**.  
  Any conditions in the template that use the `VRCEmote` parameter are converted to the **selected slot value**.  
  By default, only **layer 0** of the template is used.

  > If multiple objects share the same ME FX layer, a warning may be shown because results can vary depending on configuration/naming.

---

### 2-5) State Settings

- **Start Action State**  
  The state name that marks where the emote branch begins in the avatar Action layer. **(A)**  
  You can auto-detect it with **Setup VRC Emote** or enter it manually.  
  If this is empty and the Action layer is Default (or Null), `Prepare Standing` is assumed by default.  
  If invalid, an error is shown.

- **End Action State**  
  The state name that marks where the emote branch ends in the avatar Action layer. **(B)**  
  You can auto-detect it with **Setup VRC Emote** or enter it manually.  
  If this is empty and the Action layer is Default (or Null), `BlendOut Stand` is assumed by default.  
  If invalid, an error is shown.

    ![EmoteInstaller_Creator_State_1](../../images/EmoteInstaller_Creator_State_1.png){ width="500" }

- **Action SM Root**  
  Shown only when **Action SM Root Tracking** is enabled in Advanced Options. **(C)**  
  If auto-tracking determines a scope is required, running **Setup VRC Emote** may automatically enable this field.  
  If your Action structure is non-standard, or the Start/End states are inside a Sub StateMachine, set the root manually.

    ![EmoteInstaller_Creator_State_2](../../images/EmoteInstaller_Creator_State_2.png){ width="500" }

---

### 2-6) ME Write Default OFF

- **ME Write Default OFF**  
  Forces all Write Defaults handling inside ME layers toward OFF. (Default: true)

---

## 3) Advanced Options

Advanced Options covers auto-tracking, merge scope, and FX merge extension.

- **Action SM Root Tracking**  
  Helps scope-based detection when the Action structure is complex. (Used with Action SM Root)  
  When enabled, an additional field becomes available (**Action SM Root**).

- **Use Merge ME FX**  
  Use an ME FX layer when you want to include non-motion effects such as facial expressions, object animation, FX, or sounds.  
  When enabled, an additional field becomes available (**ME FX Layer**).

- **+ Additional ME FX**  
  Adds extra FX templates for extension (up to 2).  
  Performance/optimization guidance is displayed together.

- **Replace ME Menu Icon**  
  Automatically replaces the top-level Emote menu icon with the ME icon. (Default: true)

---

## 4) Setup VRC Emote / Default

### Setup VRC Emote

This button is designed to automatically fill settings as much as possible.

**What it does**

1. Find the avatar descriptor
2. Auto-set Action/FX layers (if needed)
3. Auto-detect the Emote menu (if needed)
4. Auto-estimate Start/End Action States (when possible)
5. (Depending on conditions) Auto-set values needed for Action SM Root Tracking

When something is wrong, the fastest workflow is usually to **run Setup VRC Emote first**.

  ![Setup VRC Emote](../../images/EmoteInstaller_User_SetupEmote.png){ width="500" }

### Default

Resets the current component values to defaults and records Undo.

---

## 5) Show Applied Changes (Preview)

Before building, you can preview “what changes will be applied to the menu” in a table.

Table columns:

- **No.**
- **Name →→** / **Name (After)**
- **Type →→** / **Type**

Slots actually modified by this component are emphasized in the “After” values.

  ![EmoteInstaller_Creator_Preview](../../images/EmoteInstaller_Creator_Preview.png){ width="500" }

---

## 6) Editor Language

Select the inspector UI language.
