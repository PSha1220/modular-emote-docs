# Change Log

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
