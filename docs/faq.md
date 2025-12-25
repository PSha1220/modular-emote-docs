# FAQ

## Q. Can I use Emote Installer on an avatar that does not use VRC Emote?

No. Currently, `VRC Emote Installer` assumes an avatar structure that uses the **`VRCEmote` parameter (1–8)**.

To use it, your avatar must meet one of the following:

- **Create an Emote menu / Action layer structure that uses the `VRCEmote` parameter**, or
- Modify the avatar to use the **VRChat default Action layer**.

> In short, your avatar needs a structure where selecting an Emote in the radial menu changes the `VRCEmote` value.

---

## Q. I pressed `Setup VRC Emote`, but it looks like the state settings were not applied correctly.

On some avatars, automatic tracking can fail if the Action layer structure is complex. For example:

- The avatar has **multiple branches** that use `VRCEmote` in different places, or
- The Action layer contains **deep / complex Sub StateMachines**, making it difficult to reliably locate the start/end flow.

In that case, we recommend the following:

1. **Manually enter the `Start Action State` / `End Action State` names.**  
   (Even if auto-tracking fails, merging can still work with manual state names.)

2. If the Emote branch is located **inside a Sub StateMachine**,  
   enable **action root tracking (merge scope)** in Advanced Options and  
   manually set the `Action Merge Scope (Action Sub StateMachine Root)` path/name.

> Summary: If auto-setup doesn’t work, it is usually resolved by **manual state names + merge scope**.

---

## Q. Can I modularize my work with this tool and distribute it commercially?

Yes. However, we do not recommend redistributing this tool package itself.  
Instead, we recommend guiding users to install it through an official route (such as VCC).

---

## Q. What about support or liability for issues and damages?

We do not assume liability for issues or damages caused by using this tool, except in cases of willful misconduct or gross negligence.

That said, since this is an indie project, we will review feedback and try to maintain the tool where possible.
