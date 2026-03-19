# Change Log

## 1.3.5

### Changed

- Renamed **Object Name** to **Build Object Name** to clarify that it is the name applied during avatar build.
- Removed the **Auto Rename Object** option. When **Use Merge ME FX** is enabled, **Build Object Name** is now shown directly.
- **Setup VRC Emote** no longer renames the actual GameObject to match the Emote name.
- Pressing **Setup VRC Emote** now fills **Build Object Name** with the current GameObject name when that field is empty.
- Turning **Use Merge ME FX** off now clears **Build Object Name**, so re-enabling it starts from an empty state like the other related options.
- Updated the editor-language localization for the new **Build Object Name** flow and guidance text.

### Improved

- Replaced the previous name mismatch warning with a shorter guidance message focused on **Build Object Name**.
- Added an **info icon** to **Developer Options** when the **Build Object Name** guidance message is being shown.
- Clarified the guidance for ME FX usage: when **Build Object Name** is left empty, changing the object name later can change animation paths and affect the build result.

## 1.3.2

### Added

- Added **Auto Rename Object** support when using merged ME FX layers.
- Added **Object Name** override support for build-time object renaming.

### Changed

- Renamed **Auto Rename Object Name** to **Auto Rename Object**.
- Added editor-language localization for:
  - **Auto Rename Object**
  - **Object Name**
- The **Auto Rename Object** option is now shown only when **Use Merge ME FX Layer** is enabled.
- The **Object Name** field is shown only when the related options are enabled.
- Updated the VPM package dependency range to avoid forcing an unnecessary downgrade of the VRChat SDK.
- Adjusted repository/listing delivery so the package can be installed through **Psha-VPM-Repository** with the latest version.

### Improved

- Improved the conditions for the **name mismatch warning**.
- Improved **Setup VRC Emote** so formatting-only text such as `<br>`, line breaks, and rich text tags like `<color>` is stripped before applying an object name.

### Fixed

- Fixed compile issues related to:
  - `autoRenameObjectName`
  - `objectName`
  - `GetResolvedBuildObjectName`
- Improved initialization and migration handling for existing prefabs and scene instances.

### Maintenance

- General release and distribution maintenance.
