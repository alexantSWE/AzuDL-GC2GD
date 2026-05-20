# Changelog

All notable changes to **AzuDl - GC2GD** will be documented in this file.

This project follows a simple release history format. Versions are listed from newest to oldest.

---

## `1.4.20 GUI Beta`

### Added

- Added GitHub repository downloader tab.
- Added Official project repository tab for `https://github.com/TheGreatAzizi/AzuDL-GC2GD`.
- Added GitHub token field inside the GUI.
- Added GitHub token save, clear, and status actions.
- Added GitHub API rate-limit status display.
- Added support for latest release, all releases, specific release tag, and default branch source downloads.
- Added GitHub README and license download options.
- Added Google Drive verified transfer workflow for GitHub and YouTube outputs.
- Added chunk-based Google Drive copy with `fsync`, system `sync`, and post-copy visibility verification.
- Added Force Drive sync action in Maintenance.
- Added System Diagnostic action.
- Added diagnostic checks for direct download access, GitHub API access, YouTube metadata access, and aria2 torrent engine startup.
- Added separate Official tab instead of mixing the official project repository into the generic GitHub tab.
- Added mobile-friendly tab overflow behavior.
- Added improved button styling, hover states, disabled states, and role-based colors.
- Added safer GitHub token template file.

### Changed

- Kept the version naming style as `GUI Beta`.
- Improved GUI button design across the full project.
- Improved Maintenance tab layout.
- Improved Official repository workflow.
- Improved GitHub downloader workflow.
- Improved Drive transfer reliability by using local temporary processing before Google Drive transfer where needed.
- Improved YouTube transfer reliability by verifying final files after copy.
- Improved GitHub transfer reliability by verifying final files after copy.
- Improved user-facing text so it targets public end users rather than internal development notes.
- Improved Help text for YouTube cookies, PO Token, GitHub tokens, Drive visibility, diagnostics, and official repository downloads.
- Improved mobile usability for narrow displays.

### Fixed

- Fixed GitHub token recursion issue.
- Fixed GitHub repository info recursion issue.
- Fixed Official repository info recursion issue.
- Fixed Maintenance handler name mismatches.
- Fixed missing Diagnostic button in Maintenance.
- Fixed syntax issue caused by stale duplicated notebook cells.
- Fixed Official repository default download behavior so it can fall back to default branch source ZIP.
- Fixed cases where GitHub download reported success with only README when no release assets existed.
- Fixed Google Drive copy verification being too weak for Drive UI sync delays.
- Fixed accidental temporary folder display in torrent output.
- Fixed raw traceback display for common GUI validation errors.

### Notes

- Google Drive web/app UI may show files slightly later than the Colab mount. AzuDl verifies files on the mounted Drive path and includes a Force Drive sync action.
- For private GitHub repositories or higher API limits, use the GitHub token field in the GitHub tab.
- Real cookies, PO tokens, visitor data, GitHub tokens, aria2 secrets, and private tracker files must stay private.

---

## `1.3.0 GUI Beta`

### Added

- Added the first Google Colab widget-based graphical interface.
- Added default GUI launch mode.
- Added classic CLI fallback.
- Added tab-based GUI layout.
- Added Dashboard tab.
- Added Auto download tab.
- Added Direct download tab.
- Added YouTube download tab.
- Added Torrent tab.
- Added Batch download tab.
- Added Files and checksum tab.
- Added Archives tab.
- Added Maintenance tab.
- Added Developer tab.
- Added Guide tab.
- Added Google Drive storage cards.
- Added used/free storage progress display.
- Added output console inside the GUI.
- Added GUI buttons for common actions.
- Added GUI form fields for links, folders, file names, headers, speed limits, quality selection, and options.
- Added GUI controls for YouTube audio-only mode, playlist mode, and metadata saving.
- Added GUI controls for torrent private mode and seeding.
- Added GUI access to aria2 status.
- Added GUI access to save aria2 session.
- Added GUI access to clear stopped aria2 tasks.
- Added GUI access to remove aria2 GID.
- Added GUI access to download history.
- Added GUI access to latest file view.
- Added GUI access to file listing.
- Added GUI access to SHA256 tools.
- Added GUI access to ZIP folder tools.
- Added GUI access to YouTube cookie help.
- Added GUI access to YouTube PO Token help.
- Added GUI access to developer and project links.
- Added GitHub-ready user-facing text for the beta GUI release.

### Changed

- Changed the default interface from CLI-first behavior to GUI-first behavior.
- Improved public-facing help text.
- Improved GUI labels, descriptions, and button text.
- Improved layout for new users who do not want to type CLI menu numbers.
- Improved guidance around cookies, tokens, and private files.
- Updated version label to `1.3.0 GUI Beta`.

### Notes

- This is a beta GUI release.
- The classic CLI is still available with `main()`.
- CLI mode can also be forced with:

```python
import os
os.environ["AZUDL_INTERFACE"] = "cli"
```

---

## `1.2.8`

### Added

- Added torrent InfoHash detection before adding `.torrent` files.
- Added duplicate torrent detection.
- Added resume or monitor behavior for existing aria2 torrent tasks.
- Added automatic removal of existing errored torrent tasks.
- Added improved aria2 status output with InfoHash.

### Changed

- Improved torrent reliability.
- Improved duplicate torrent handling.
- Improved handling of aria2 `InfoHash is already registered` errors.

### Kept

- Kept dedicated Torrent Tools menu.
- Kept private torrent mode.
- Kept live seeding status.
- Kept aria2 session persistence.
- Kept YouTube audio format fix.
- Kept ZIP, SHA256, history, and file tools.

---

## `1.2.7`

### Fixed

- Fixed tqdm boolean evaluation error during seeding status display.

---

## `1.2.6`

### Changed

- Moved torrent features into a dedicated Torrent Tools menu.
- Improved CLI organization for torrent-related actions.

---

## `1.2.5`

### Added

- Added live torrent seeding status.
- Added upload speed display during seeding.
- Added uploaded size display during seeding.
- Added ratio display during seeding.
- Added seeding elapsed time display.
- Added aria2 session persistence.
- Added resume-friendly aria2 settings.

---

## `1.2.4`

### Fixed

- Fixed invalid infinite `seed-time=-1` issue.
- Replaced invalid infinite seed time with a long valid seed time.

### Notes

- AzuDl uses `525600` minutes as a practical long seeding time.
- Google Colab will usually disconnect long before that, so this effectively means seeding continues while the runtime is alive.

---

## `1.2.3`

### Improved

- Improved `.torrent` download validation.
- Improved aria2 RPC error messages.
- Improved handling of invalid torrent file responses.

---

## Suggested Commit Messages

For the GUI beta release:

```text
release: AzuDl GC2GD v1.4.20 GUI Beta
```

Alternative:

```text
feat(gui): improve GUI beta with GitHub downloader diagnostics and Drive transfer verification
```

For security/documentation files:

```text
docs: add security contributing changelog and issue templates
```
