# VRC Emote Installer

`VRC Emote Installer` is a tool that lets you distribute animations in a **“prefab-modular”** form.  
Users can install the released ME prefab into their avatar and set it up easily—**without complex Animator editing**—to use Emotes (slots 1–8).

---

## Requirements (Supported Scope)

This tool assumes an avatar that uses **VRCEmote (Emote Radial Menu)**.

You can expect it to work properly on avatars that meet the following conditions:

- An avatar that plays emotes through the radial menu using the `VRCEmote` parameter
- An avatar that uses the **VRChat default Action layer**, or
  an Action layer that already has an Emote branching structure based on the `VRCEmote` parameter

> Note: “Using `VRCEmote`” typically means that  
> when you select an Emote in the in-game radial menu, the `VRCEmote` value (1–8) changes and drives the animation.

---

## Quick Setup

1. Place the **avatar** you want to apply the animation to in the scene.
2. Place the released **ME prefab** in the scene.
3. Drag the ME prefab **under the avatar (as a child)**. **(A)**
4. In the Installer, set **Target Slot No. (1 to 8)**. **(B)**

    ![Emote Installer quick setup (A: drag under avatar, B: set slot index)](../../images/EmoteInstaller_User_A.png){ width="500" }

5. **Build the avatar** from the VRChat SDK menu.
6. In-game, open the **Radial Menu** (default: hold **R**) → **Emote** to confirm it works. **(C)**

    ![Emote Installer quick setup (C: Radial Menu)](../../images/EmoteInstaller_User_C.png){ width="500" }


---

## Setup Video

<iframe width="580" height="580" src="https://www.youtube.com/embed/phu5HNi_exg" frameborder="0" allowfullscreen sandbox="allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox allow-presentation"></iframe>


---

## If the avatar is not supported / if you run into issues

You may run into issues if you try to apply a released ME prefab to an avatar **outside the supported scope**,  
or if something goes wrong during the setup process.

In that case, open **Developer Options** first,  
check the status icons/messages shown there, and follow the recommended flow below.

### Recommended fix: `Setup VRC Emote`

In most cases, pressing the **`Setup VRC Emote` button once** in Developer Options is enough.  
It is designed to automatically resolve issues as much as possible within the script’s capabilities.

- Try running `Setup VRC Emote` first.
- If something cannot be handled automatically, you can adjust it manually in Developer Options.

  ![Setup VRC Emote](../../images/EmoteInstaller_User_SetupEmote.png){ width="500" }

---

## Notes / Limitations

The following cases may not produce correct results:

- Applying to an **unsupported avatar**
- The animation does not match due to the avatar’s **body shape** (retargeting/scale differences)
- Applying a prefab that includes **FX layer merging** to an avatar with a non-standard structure
- Even if the avatar uses `VRCEmote`, the Action layer contains a **very complex Sub StateMachine structure**  
  (the tracking algorithm may fail to reliably locate the start/end flow, causing the merge to fail)

Also, the current version primarily targets the following scope:

- Supports **Stand emote slots 1–8** (the 8 slots in the radial menu)

---
