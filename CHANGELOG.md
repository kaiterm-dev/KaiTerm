# Changelog

## v1.0.1

### Added

- Read update metadata from the public GitHub Releases API so the app can point users directly at release assets.
- Generate platform update feed files during the public release workflow for Linux, macOS, Windows setup, and Windows portable artifacts.
- Allow trusted update download links from the public GitHub release page and release assets.

### Changed

- Improve update detection so a newer version is only marked installable when a compatible package is available for the current platform.
- Route fallback update downloads to the product download page when no matching artifact is listed.

### Fixed

- Import the shared action execution normalizer where remote, local, and hybrid terminal actions are run.

## v1.0.0

### Added

- Initial KaiTerm desktop app for managing SSH-heavy workflows in an Electron terminal workspace.
- Connection tree with folders, search, keyboard navigation, protocol colors, context menus, cloning, editing, and deletion.
- Local terminal sessions plus SSH, Mosh, SFTP, and FTP connection profiles.
- xterm.js workspace with tabs, horizontal and vertical splits, duplicate terminals, tab reordering, pop-out windows, copy/paste, reset, clear, and exit actions.
- Per-connection and global protocol settings for SSH, Mosh, SFTP, and FTP.
- Reusable secrets for passwords, login passwords, and login keys, with encrypted local storage and file loading for private keys.
- Global and per-connection command actions, including remote actions, local actions, template variables, and editable shortcuts.
- Appearance settings for app color mode, terminal themes, fonts, cursor shape, scrollback, bell, sidebar placement, and visible scrollbars.
- Local backup export and restore tools with passphrase validation.
- KaiTerm Pro features including saved clusters, runtime clusters, startup automation, hybrid actions, SSH prepend commands, proxy jumps, SOCKS proxy allocation, port probing, comma-separated host failover, encrypted cloud sync, and CSV import.
- Account and sync support with email verification, passkeys, recovery codes, rotating tokens, conflict reporting, automatic pull on startup, and automatic push after settings changes.
- Public build workflow for Linux, macOS, Windows installer, and Windows portable release artifacts.
