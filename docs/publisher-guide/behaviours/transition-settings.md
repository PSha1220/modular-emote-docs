# Modular Emote Transition Settings

`ModularEmoteTransitionSettings` is a `StateMachineBehaviour` used in the **ME Action template** to
**rebuild transition settings at build time** for the “StartState → Template Entry” segment.

If you attach this Behaviour to a specific state in the ME Action template
(e.g. `[ME] StartState Transition Settings`), the Pass detects it and reconstructs
the transition using the Behaviour values for **Exit Time / Duration / Offset / Interruption / additional conditions**.

---

## How to Use (Summary)

1. Add `ModularEmoteTransitionSettings` to the “transition settings state” in your ME Action template.
2. Configure the values under **Transition Settings** as desired.
3. If needed, add extra filter conditions under **Additional Conditions**.

> Note  
> The condition `VRCEmote == slotIndex` is handled automatically by the system.  
> Use Additional Conditions only for **extra constraints** you want to apply.

---

## Transition Settings

- **Interruption Source**  
  Select which side is used as the basis for interruption evaluation.  
  `None / Source / Destination / SourceThenDestination / DestinationThenSource`

- **Has Exit Time**  
  When enabled, uses Exit Time (0–1).

- **Exit Time (0–1)**  
  The exit timing (normalized value) applied when Has Exit Time is enabled.

- **Transition Duration**  
  The duration of the transition.  
  Interpreted as **seconds** or **normalized time** depending on `Fixed Duration`.

- **Transition Offset (0–1)**  
  The start offset of the destination animation (normalized value).

- **Fixed Duration**  
  When enabled, Transition Duration is interpreted in **seconds**.  
  When disabled, it is interpreted as **normalized time**.

- **Ordered Interruption**  
  Whether to preserve the interruption evaluation order.

---

## Additional Conditions

`conditions` is an **array of additional conditions** applied to the transition.

- The base condition `VRCEmote == slotIndex` is applied automatically.
- Use this for extra filters such as `IsSeated`, custom mode parameters, etc.

### Supported Types

- Bool
- Int
- Float
- Trigger

### Int/Float Compare Modes

- Greater
- Equal
- Less
- NotEqual

---

## Reference

- <a href="https://docs.unity3d.com/Manual/class-Transition.html" target="_blank" rel="noopener noreferrer">Unity Doc (Animation transitions)</a>
