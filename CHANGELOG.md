# Changelog

## v1.1.0

- **2026-07-15** : Refresh the README and website for the upcoming 1.1.0 feature set with current screenshots and complete coverage of Fleet Runbooks, managed SSH tunnels, folder-backed targets, sync recovery, status indicators, and update handling.
- **2026-07-15** : Improve tree context menus by adding new connections directly from a folder with the selected folder prepopulated and consistently styling cluster deletion as a destructive action.
- **2026-07-15** : Add encrypted sync recovery that can replace cloud settings from the most up-to-date computer, guide other computers to download with the new passphrase, recover an unreadable machine-local sign-in without changing local configuration, warn with repair instructions when Settings contains an unreadable secret, use value snapshots to require genuinely changed settings to be saved before opening Account & Data, show a subtle green sync status dot when healthy or red when an error needs attention, and keep explicit uploads available when background sync is disabled.
- **2026-07-15** : Add Fleet Runbooks as a KaiTerm Pro feature with editable definitions in Settings, unnamed one-line command steps, and a read-only standalone operational manager for running and stopping saved workflows across path-sorted SSH host or recursive folder targets, with dynamic folder membership shared by cluster configuration, a full-width stacked searchable multi-select, controlled concurrency, step-boundary stop-on-failure or failed-host exclusion when continuing, skipped transport failures, cooperative cancellation, a run-focused output view, nested collapsible command and host results, compact add and delete controls beside their related settings, persistent passed, skipped, and failed counts with status colors, captured output, and live per-host status.
- **2026-07-15** : Add SSH tunnel management as a KaiTerm Pro feature with editable definitions in Settings and a read-only standalone operational manager for starting and stopping saved tunnels, plus a subtle green status dot while tunnels are active, path-sorted searchable host selection, collapsible status panels, compact add and delete controls beside their related settings, aligned fields, local, remote, and dynamic forwarding, automatic local-port allocation, optional startup with KaiTerm, endpoint copying, and automatic opening of configured URLs after forwarding is ready.
- **2026-07-14** : Restore GitHub release update detection and expand the update prompt with Cancel, Download, and persistent Skip Release choices.
- **2026-07-14** : Simplify application internals by removing unused code and redundant pass-through helpers.

## v1.0.1

- **2026-07-14** : Added read update metadata from the public GitHub Releases API so the app can point users directly at release assets.
- **2026-07-14** : Generate platform update feed files during the public release workflow for Linux, macOS, Windows setup, and Windows portable artifacts.
- **2026-07-14** : Allow trusted update download links from the public GitHub release page and release assets.
- **2026-07-14** : Improve update detection so a newer version is only marked installable when a compatible package is available for the current platform.
- **2026-07-14** : Route fallback update downloads to the product download page when no matching artifact is listed.
- **2026-07-14** : Fix import the shared action execution normalizer where remote, local, and hybrid terminal actions are run.

## v1.0.0

- **2026-07-13** : Initial KaiTerm desktop app for managing SSH-heavy workflows in an Electron terminal workspace.
- **2026-07-13** : Connection tree with folders, search, keyboard navigation, protocol colors, context menus, cloning, editing, and deletion.
- **2026-07-13** : Local terminal sessions plus SSH, Mosh, SFTP, and FTP connection profiles.
- **2026-07-13** : xterm.js workspace with tabs, horizontal and vertical splits, duplicate terminals, tab reordering, pop-out windows, copy/paste, reset, clear, and exit actions.
- **2026-07-13** : Per-connection and global protocol settings for SSH, Mosh, SFTP, and FTP.
- **2026-07-13** : Reusable secrets for passwords, login passwords, and login keys, with encrypted local storage and file loading for private keys.
- **2026-07-13** : Global and per-connection command actions, including remote actions, local actions, template variables, and editable shortcuts.
- **2026-07-13** : Appearance settings for app color mode, terminal themes, fonts, cursor shape, scrollback, bell, sidebar placement, and visible scrollbars.
- **2026-07-13** : Local backup export and restore tools with passphrase validation.
- **2026-07-13** : KaiTerm Pro features including saved clusters, runtime clusters, startup automation, hybrid actions, SSH prepend commands, proxy jumps, SOCKS proxy allocation, port probing, comma-separated host failover, encrypted cloud sync, and CSV import.
- **2026-07-13** : Account and sync support with email verification, passkeys, recovery codes, rotating tokens, conflict reporting, automatic pull on startup, and automatic push after settings changes.
- **2026-07-13** : Public build workflow for Linux, macOS, Windows installer, and Windows portable release artifacts.
