# KaiTerm for JVM desktop

KaiTerm is a desktop connection manager for local shells, SSH, SFTP, FTP, and MySQL/MariaDB. The JVM app uses Compose Desktop for its interface, JediTerm for terminal rendering, Pty4j for local shells, and a built-in libssh2 SSH client. It runs on Linux, macOS, and Windows.

SSH and SFTP use libssh2 by default. Start KaiTerm with `--no-libssh2` to use the system OpenSSH, `sftp`, and `ftp` programs instead; the Programs settings then appear. SFTP and FTP open in a terminal tab with an sftp-style command line (`ls`, `cd`, `get`, `put`, `mkdir`, `rm`, `rename`, `chmod`). FTP uses TLS when the server offers it.

## Install

Download the package for your system from [kaiterm.dev](https://kaiterm.dev/#download) or the [GitHub releases](https://github.com/kaiterm-dev/KaiTerm/releases).

- Linux: AppImage, DEB, Flatpak, RPM, Snap (classic confinement), or tar.gz.
- macOS: a universal DMG or ZIP. The app is signed ad hoc and not notarized, so macOS may warn on first launch. Open it with right-click, Open, or allow it in System Settings, Privacy & Security.
- Windows: a setup EXE or a portable ZIP.

On first launch KaiTerm opens a workspace with a local shell. Add a connection from the sidebar. Settings and data live in the config directory: `~/Library/Application Support/KaiTerm` on macOS, `%APPDATA%\KaiTerm` on Windows, and `$XDG_CONFIG_HOME/kaiterm` (default `~/.config/kaiterm`) on Linux. `--config-dir <path>` overrides it. It holds `known_hosts.json` (trusted host keys), `sync-state.json` (the sync session), and `automation.sock` (automation only).

## Run and build

The project uses Gradle and a Java 25 toolchain. The build needs a JetBrains Runtime 25 SDK. On Linux, `start.sh` and `build.sh` download one to `~/.cache/kaiterm-build` on first use, or use the one in `JBR_HOME`. On other systems, install JDK 25 first. A launch with `start.sh` uses a separate development configuration at `~/.config/kaiterm-jvm-devel`.

```sh
./start.sh
./gradlew :desktopApp:compileKotlin
```

Build packages on the matching host platform. Files are written to `dist/KaiTerm-<OS>-<version>-<arch>.<ext>` (the macOS arch is `universal`):

```sh
./build.sh linux    # AppImage, DEB, Flatpak, RPM, Snap, tar.gz
./build.sh macos    # universal DMG and ZIP, on an Apple Silicon Mac with Rosetta
./build.sh windows  # setup EXE and portable ZIP, on Windows
./build.sh -v 1.2.3 linux-deb  # one format, with an explicit x.y.z version
```

The macOS build also needs an x64 JetBrains Runtime 25, downloaded automatically unless `X64_JAVA_HOME` is set. AppImage needs `appimagetool`, Flatpak needs `flatpak-builder` and `flatpak`, and Snap needs `snap` and squashfs-tools. Run `build.sh windows` only from an MSYS2 UCRT64 shell.

On Windows, `build-windows.ps1` can install the required build tools and run the Windows packaging steps:

```powershell
powershell -ExecutionPolicy Bypass -File .\build-windows.ps1
```

The portable ZIP contains `KaiTerm.exe`; extract it before launching.

## Automation

Start KaiTerm with `--automation` to let local scripts drive it. The running app listens on `automation.sock` in its config directory, which only the owner of that directory can use. Send one command from the command line with `--automate`, using the same config directory as the running app:

```sh
KaiTerm --config-dir ~/.config/kaiterm --automate state
KaiTerm --config-dir ~/.config/kaiterm --automate open '{"target": "settings", "category": "ssh"}'
```

Scripts can also write one JSON line per request to the socket, such as `{"command": "connect", "args": {"connection": "<uuid>"}}`, and read one JSON line back: `{"ok": true, "result": ...}` or `{"ok": false, "error": "..."}`.

| Command | Arguments | Effect |
| --- | --- | --- |
| `state` | | Returns connections, clusters, selection, open dialogs, terminal tabs, sidebar state, and Pro status. |
| `locate` | `element` (optional) | Returns window-relative bounds for `connection:<uuid>`, `folder:<path>`, `cluster:<uuid>`, or `terminal`, or every visible element. |
| `select` | `connections` | Selects connections in the tree by uuid. |
| `sidebar` | `visible` | Shows or hides the connection sidebar. |
| `open` / `close` | `target`, plus `category` or `uuid` | Opens or closes `settings`, `connection`, `cluster`, `tunnels`, or `runbooks`. |
| `connect` | `connection` or `cluster` | Opens a saved connection or cluster. |
| `shortcut` | `id` | Runs a keyboard shortcut command, such as `split_vertical` or `open_local_terminal`. |
| `terminal-search` | `text` | Searches the active terminal's output. |
| `close-tab` | `tab` (optional) | Closes a terminal tab, the active one by default, without asking for confirmation. |

## Security and privacy

- SSH, SFTP, FTP (FTPS), and MySQL over SSH check the server's host key or certificate. The host key checking setting is `ask`, `accept-new`, `strict`, or `off`, and trusted fingerprints are kept in `known_hosts.json`.
- Secrets and the sync session are encrypted with a key stored in the local settings. Pro sync is encrypted on your device before upload.
- The automation socket can only be used by the owner of the config directory.

## Features

### Connections and workspace

- Organize SSH, SFTP, FTP, and MySQL/MariaDB connections in searchable folders. Create saved clusters or launch a folder as split panes or separate tabs.
- Open local shells and remote sessions in the same workspace. Reorder tabs, split a terminal, swap split panels, change split direction, and pop out or reattach a complete tab.
- Keep SSH tabs individually resumable with tmux or screen. Use proxy jumps, reusable secrets, custom command paths, and connection-specific settings.
- Connect to MySQL/MariaDB directly or through SSH. Configure TLS and run multi-statement queries in the database terminal.
- Search terminal output, copy and paste through the system clipboard, and adjust themes, fonts, cursor, scrollback, shortcuts, and tree colors.

### Actions and automation

- Save local, SSH, and SQL Actions in searchable folders. Use template variables and run actions manually from the sidebar or a connection context menu.
- Run Fleet Runbooks against selected connections or folders. Review per-host output and status, stop a run, and retain output captured up to that point.
- Create managed local, remote, and dynamic SSH tunnels and monitor their status. Start eligible tunnels automatically.
- Stagger cluster connections, Runbook hosts, and action commands using the connection and command stagger setting.

### Pro

Pro adds before-connect and after-connect automation, port probing, comma-separated host failover, and unique SOCKS proxy ports. Open a saved SSH connection with an OpenAI, Grok, Gemini, or Ollama configuration for connection-scoped AI assistance. Proposed commands require review and approval before execution.

Pro also provides client-side encrypted settings sync. Account & Data shows the signed-in account and plan status, and offers sync controls when the current account has Pro. Local backup, restore, and CSV import are available without Pro.

### Standard and Pro limits

| Capability | Standard | Pro |
| --- | --- | --- |
| Local and remote terminals, folders, clusters, Actions, and local backup | Included | Included |
| Hosts per saved connection | One | Multiple with failover |
| Saved managed SSH tunnels | Up to two | Unlimited |
| Saved Fleet Runbooks | Up to two | Unlimited |
| Proxy jumps | Included | Included |
| Unique SOCKS ports, port probing, and startup automation | Requires Pro | Included |
| AI assistance and encrypted cloud sync | Requires Pro | Included |

The same plan limits apply to the Android and iOS apps. When restoring a Pro backup on Standard, KaiTerm retains the first host of each connection. CSV imports that exceed Standard limits are rejected.

## Screenshots

![Connection tree and workspace](https://kaiterm.dev/resources/screenshots/jvm-01-main-window.png)

![Split cluster workspace](https://kaiterm.dev/resources/screenshots/jvm-03-first-cluster.png)

![Terminal output search](https://kaiterm.dev/resources/screenshots/jvm-32-terminal-search.png)

![Connection profile editor](https://kaiterm.dev/resources/screenshots/jvm-04-connection-new.png)

All 33 views are in the [kaiterm.dev gallery](https://kaiterm.dev/#screenshots).

## License

KaiTerm is proprietary software. All rights reserved. See the [Terms and Software Licence](https://kaiterm.dev/terms.html). The About panel in Settings shows the installed version, and the [changelog](CHANGELOG.md) lists what changed.

## Support

Questions and bug reports: [support@kaiterm.dev](mailto:support@kaiterm.dev).
