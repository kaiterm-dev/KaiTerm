# KaiTerm

KaiTerm is a desktop connection manager for SSH-heavy workflows. It combines an
xterm.js terminal workspace with a searchable connection tree, reusable secrets,
scripted actions, local backup/restore tools, and optional KaiTerm Pro features
for unlimited Fleet Runbooks and managed SSH tunnels, startup automation,
advanced connection workflows, connection-scoped AI assistance, and encrypted
sync.

For interface testing, start with `npm start -- --size 1200x800` to ignore the
cached window bounds for that run. Using `--size` without dimensions opens at
the 900x600 default. Temporary launch dimensions are not saved to the cache.

![KaiTerm split terminal workspace](https://kaiterm.dev/resources/screenshots/03-first-cluster.png)

## Features

### Connection Manager

KaiTerm stores connections in a folder tree. Connections are color-coded by
protocol, and folders can be expanded, collapsed, filtered, and navigated from
the keyboard. Saved clusters appear in a dedicated cluster section.

![Organized folders and clusters](https://kaiterm.dev/resources/screenshots/01-main-window.png)

- SSH, Mosh, SFTP, and FTP connection types.
- Folder-based organization with nested folder paths.
- Optional protocol labels in the tree, such as `[ssh]`.
- Configurable tree colors for folders, SSH, Mosh, SFTP, and FTP.
- Type anywhere in the focused tree to search, or use the search shortcut for
  fast connection lookup. On macOS the search field shares the title bar; on
  platforms with right-side window controls it appears above the tree while in
  use.
- Ctrl/Cmd-click individual connections or Shift-click a range, then open,
  bulk edit, or delete the selected connections from one context menu.
- Context menu actions for starting, editing, cloning, and deleting
  connections.
- Folder context menu for creating a connection with its folder prepopulated or
  applying one field value to every connection in that folder and its nested
  subfolders.
- Folder context actions for deleting every nested connection and launching the
  folder as a new split-tab or separate-tabs runtime cluster.
- A grouped sidebar footer keeps Settings, sync, runbooks, tunnels, connection
  creation, cluster creation, and the local terminal close to the tree.
- Saved clusters, runtime terminal clusters, cluster tree colors, and a cluster
  toolbar action.

### Terminal Workspace

KaiTerm uses xterm.js and node-pty to run real terminal sessions inside the
desktop app. Local terminals and remote sessions share the same workspace.

![Single terminal session](https://kaiterm.dev/resources/screenshots/02-first-connection.png)

![Multi-pane terminal split](https://kaiterm.dev/resources/screenshots/03-first-cluster.png)

- Open local shell sessions.
- Open remote SSH, Mosh, SFTP, and FTP sessions.
- Duplicate the active terminal into a new tab.
- Split terminals horizontally or vertically.
- Combine multiple terminals in one tab.
- Drag terminal tabs to reorder them.
- Pop a terminal out into a separate window and reattach it later.
- Copy, paste, clear, reset, and exit from the terminal context menu.
- Configurable terminal font, font size, cursor shape, scrollback,
  scroll-on-keystroke behavior, audible bell, and disconnect behavior.
- Bell and connection-state indicators on tabs.
- Inset pill-style tabs share the draggable title area while preserving clear
  native window-control space on macOS, Linux, and Windows.

### Clusters

Clusters let you launch multiple saved connections together. A cluster can open
as a single split terminal tab or as separate tabs.

![Cluster editor](https://kaiterm.dev/resources/screenshots/05-overlay-new-cluster.png)

- Save reusable groups of connections.
- Search and select individual connections or recursive folders from a compact
  multi-select. Folder-backed clusters resolve their current membership when
  launched, so connection additions, removals, and moves are reflected automatically.
- Choose split-tab or separate-tab launch mode.
- Create ad hoc runtime clusters from an open terminal or from every split in a
  tab.
- Join terminals or whole tabs to an existing runtime cluster.
- Remove a terminal or tab from a runtime cluster.
- Stagger connection startup to avoid launching many sessions at the exact same
  moment.

### AI Mode (Pro)

Create named AI configurations in Settings, then use Open with AI in a saved
SSH connection's tree context menu to pair an interactive terminal with the
selected connection-scoped OpenAI, Grok, Gemini, or Ollama chat.

![AI provider configurations](https://kaiterm.dev/resources/screenshots/19-settings-ai.png)

- Ask the assistant to inspect logs, diagnose problems, or make changes on the
  current host.
- Add optional AI context to an SSH connection, such as "This is a Proxmox
  server" or "This web server runs Nginx," to give every AI configuration a
  useful starting point. KaiTerm labels this as unverified context and still
  requires the assistant to confirm command availability and actual services.
- Select terminal output and send a message such as "analyze this" to include
  that selection automatically without copying it through the clipboard. The
  chat shows how much selection context was included, consumes the selection
  once, redacts sensitive values, and treats the content as untrusted output.
- Review every proposed shell command, its explanation, and its risk level
  before choosing Run command or Skip.
- Before writing an approved command, require a visible shell prompt and block
  execution while xterm is using an alternate screen for Less, Vim, Nano,
  `top`, or another full-screen terminal application. A blocked command remains
  available to retry after returning to the shell.
- Run approved commands visibly in the terminal and automatically return their
  captured output to the assistant for analysis and follow-up proposals. AI
  commands can run for minutes or hours without a completion timeout; use the
  Abort button to send Ctrl+C, repeating it when a process needs another
  interrupt, and wait for the shell prompt before continuing. Output streams
  live in the terminal while KaiTerm retains a bounded tail for AI analysis.
- Discover `/etc/os-release`, `lsb_release`, the current user and groups, PATH,
  sudo availability, and the kernel when the AI terminal connects, so later
  proposals fit the host and its privilege model. The assistant avoids invented
  absolute executable paths and checks uncertain commands with `command -v` or
  `type` before relying on them.
- Type directly in the terminal, including Ctrl+C, Ctrl+D, and `exit`, so manual
  work can be interleaved with AI-proposed commands.
- Keep the session pinned to the connection that opened it. AI terminals cannot
  join clusters, enter split layouts, duplicate, or pop out.
- Save multiple named OpenAI, Grok (xAI), Gemini, and Ollama configurations in
  Settings > AI.
  OpenAI configurations contain a name, API key, and model selected from the
  models available to that key through `GET /v1/models`. Grok configurations
  provide the same fields using xAI's API and model endpoint. Gemini
  configurations use a Gemini API key and show models that support
  `generateContent`. Ollama configurations contain a name and a model selected
  from `ollama list`.
- To configure OpenAI, sign in to the [OpenAI Platform](https://platform.openai.com/),
  open API keys, create a new secret key, copy it into Settings > AI, and select
  Refresh to load the models available to it.
- To configure Gemini, sign in to [Google AI Studio](https://aistudio.google.com/app/apikey),
  open API Keys, choose Create API key, copy the new key into Settings > AI,
  and select Refresh to load the models available to it.
- Choose the required configuration from the connection's Open with AI submenu.
  Different AI terminals can use different providers, keys, or models.
- Optionally suppress approved AI commands from Bash history for any provider.
  KaiTerm configures the active Bash session's `HISTCONTROL` with `ignorespace`,
  removes the configuration command from history when necessary, and sends each
  AI command with a leading space. Commands typed manually are sent unchanged.
- Store every hosted-provider API key through Electron secure local storage.
  Saved keys are not returned to the renderer and use the same passphrase
  encryption as passwords and private keys in cloud sync and encrypted backup
  exports.
- Use the OpenAI Responses API with your own OpenAI API key, xAI's compatible
  Responses API with your own xAI key, Google's Gemini API with your own Gemini
  key, or Ollama's local chat API at `127.0.0.1:11434`. Only startup environment
  discovery and output from approved commands are added to the selected
  provider's conversation.

### Connection Profiles

Each connection profile can use global defaults or override connection-specific
settings.

![Connection general settings](https://kaiterm.dev/resources/screenshots/04-overlay-new-connection.png)

![Global connection defaults](https://kaiterm.dev/resources/screenshots/10-settings-connections.png)

- Name, folder, host, port, type, and UUID fields.
- Per-connection secret selection.
- Inline username, password, private key, and key passphrase fields when no
  reusable secret is selected.
- Per-connection overrides for SSH, Mosh, SFTP, and FTP options.
- Manual per-connection SSH actions.
- SSH/SFTP proxy jump selection.
- Standard connections use a single host. KaiTerm Pro adds port probing,
  comma-separated host failover, before-connect local actions for SSH, Mosh,
  SFTP, and FTP, plus after-connect SSH and Mosh startup actions.

### Secrets

Reusable secrets keep authentication details separate from connection profiles
and provide slugged values for command templates.

![Secret management](https://kaiterm.dev/resources/screenshots/11-settings-secrets.png)

- Store password, login password, and login key secrets.
- Load private key text from a file picker.
- Attach a secret to any SSH, Mosh, SFTP, or FTP connection.
- Hide per-connection auth fields when a secret is selected.
- Preserve stored secret values without showing them back in plain text.

### SSH, Mosh, SFTP, and FTP Options

KaiTerm exposes protocol-specific flags globally and per connection.

![SSH settings](https://kaiterm.dev/resources/screenshots/12-settings-ssh.png)

![Mosh settings](https://kaiterm.dev/resources/screenshots/13-settings-mosh.png)

![SFTP settings](https://kaiterm.dev/resources/screenshots/14-settings-sftp.png)

![FTP settings](https://kaiterm.dev/resources/screenshots/15-settings-ftp.png)

SSH options include:

- Agent forwarding.
- Compression.
- X11 forwarding.
- Verbose and very verbose modes.
- Forced PTY allocation.
- Connect timeout.
- Additional raw SSH options.
- SSH/SFTP proxy jump support.
- KaiTerm Pro: unique SOCKS proxy allocation with a dynamic local port.
- KaiTerm Pro: port probing and comma-separated host failover.

Mosh options include:

- Local echo prediction mode: adaptive, always, or never.

SFTP options include:

- Agent forwarding.
- Compression.
- Verbose mode.
- Connect timeout.
- Additional raw SFTP options.

FTP options include:

- Active mode.
- Passive mode.
- Trace mode.
- Verbose mode.

### Commands and Actions

Actions are named command snippets that can be run manually from a terminal or
used as startup automation.

![Command action settings](https://kaiterm.dev/resources/screenshots/16-settings-commands.png)

- Global and per-connection SSH actions.
- Choose whether each action appears in the terminal right-click menu. Hidden
  actions remain available to startup automation, which keeps startup-only
  commands out of established terminal sessions.
- Remote actions that run on the remote SSH session.
- Local actions that run on the local machine, with optional Linux, macOS, or
  Windows targeting so desktop-specific commands only appear and run on the
  selected platforms.
- KaiTerm Pro: before-connect local actions selected from local actions and run
  before SSH, Mosh, SFTP, or FTP starts.
- KaiTerm Pro: after-connect startup action templates for SSH and Mosh connections.
- KaiTerm Pro: startup output capture, prompt detection, and status reporting.
- Variable expansion for reusable command templates.

Supported template variables include:

- `{name}`, `{type}`, `{folder}`, `{host}`, `{port}`
- `{identity_user}`, `{identity_password}`, `{identity_key_file}`, `{identity_key_passphrase}`
- `{proxy_port}`, `{proxy_host}`, `{proxy_url}`
- `{uuid}`, `{connection_path}`, `{user_host}`, `{host_port}`
- `{home}`, `{config_dir}`
- `{password slug}`, `{user slug}`, `{key_file slug}`, `{key_passphrase slug}` for saved secrets by slug

### Fleet Runbooks

Fleet Runbooks execute ordered command workflows across a saved selection of SSH
hosts without opening a terminal for every connection. Standard includes two
saved runbooks; KaiTerm Pro removes that limit.

![Fleet Runbook manager](https://kaiterm.dev/resources/screenshots/06-overlay-runbooks.png)

![Fleet Runbook settings](https://kaiterm.dev/resources/screenshots/18-settings-runbooks.png)

- Save reusable runbooks with a name, fleet, and ordered one-line commands.
- Search for fleet hosts above the selected-host list, which remains sorted by
  connection path.
- Target individual SSH hosts or recursive folders. Folder targets resolve when
  a run starts and remain saved even while the folder is empty.
- Run remote and local steps across selected hosts.
- Limit host concurrency while keeping step ordering consistent across the fleet.
- Finish the current step across every eligible host, then either stop later
  steps after a command failure or continue with failed hosts excluded.
- Treat unreachable ports, SSH authentication problems, DNS failures, and other
  connection failures as skipped hosts. Only commands that execute and fail are
  counted as failures.
- Inspect live pending, running, passed, failed, and skipped status for every
  step and host, including captured command output.
- Collapse runbook settings automatically when execution starts so the live
  output summary stays in focus. Results are grouped into collapsible steps with
  nested collapsible hosts, persistent passed, skipped, and failed counts, and
  green, yellow, or red step status. Open groups remain open during live updates.
- Cancel a run to prevent new commands from starting while active commands finish.
- Open the read-only standalone manager from the sidebar toolbar to run or stop
  saved runbooks; edit their definitions only in Settings.

### SSH Tunnel Manager

Saved SSH tunnels reuse KaiTerm connection profiles, credentials, private keys,
and proxy jumps. KaiTerm Pro also lets tunnel host selection use configured
host failover.
Standard includes two managed tunnels; KaiTerm Pro removes that limit.

![SSH Tunnel Manager](https://kaiterm.dev/resources/screenshots/07-overlay-tunnels.png)

![SSH tunnel settings](https://kaiterm.dev/resources/screenshots/17-settings-tunnels.png)

- Local (`-L`), remote (`-R`), and dynamic SOCKS (`-D`) forwarding.
- Start and stop tunnels independently from terminal sessions.
- Automatic collision-checked local port allocation when port `0` is used.
- Live starting, running, stopping, and error status with the active endpoint.
- Dedicated read-only tunnel-manager toolbar access for starting and stopping
  saved tunnels; edit tunnel definitions and host selection only in Settings.
- Optional tunnel startup when KaiTerm launches.
- Automatically open configured HTTP or HTTPS URLs after a tunnel starts, with
  a manual reopen action and `{port}` as the allocated-port placeholder.
- SSH keepalives and exit-on-forwarding-failure behavior.

### Appearance and Terminal Preferences

KaiTerm can be tuned for different terminal habits and layouts.

![Terminal settings](https://kaiterm.dev/resources/screenshots/09-settings-terminal.png)

- Terminal theme selection from bundled theme definitions.
- Light, dark, or system-following app color mode.
- Configurable interface accent plus compact, aligned colors for folders,
  clusters, SSH, Mosh, SFTP, and FTP entries.
- Font family and font size controls.
- Block, underline, and bar cursor shapes.
- Configurable scrollback lines and scroll-on-keystroke behavior.
- Optional audible bell.
- Sidebar on the right or left.
- Optional visible scrollbar.
- Responsive settings and terminal layouts for narrower desktop windows.
- Terminal themes remain independent from the app color mode, so terminal colors
  can be chosen separately from the surrounding UI.

![Appearance settings](https://kaiterm.dev/resources/screenshots/08-settings-appearance.png)

### Keyboard Shortcuts

Keyboard shortcuts can be edited in the settings dialog, with duplicate shortcut
validation before saving.

![Keyboard shortcuts](https://kaiterm.dev/resources/screenshots/21-settings-shortcuts.png)

Default editable shortcuts use Ctrl on Linux and Windows, or Command on macOS:

| Shortcut | Action |
| --- | --- |
| `Alt+E` | Edit the selected connection or cluster |
| `Ctrl/Cmd+F` | Focus connection search |
| `Ctrl/Cmd+Alt+H` | Split the active terminal horizontally |
| `Ctrl/Cmd+Alt+V` | Split the active terminal vertically |
| `Ctrl/Cmd+Shift+C` | Copy terminal selection |
| `Ctrl/Cmd+Shift+V` | Paste into terminal |
| `Ctrl/Cmd+Shift+D` | Duplicate terminal |
| `Ctrl/Cmd+T` | Open a local terminal |
| `Shift+ArrowLeft` | Previous tab |
| `Shift+ArrowRight` | Next tab |

The tree and editors also provide fixed keyboard interactions:

- `Escape` closes the editor or clears/hides search.
- `Enter` starts the selected connection or cluster.
- `Arrow Up` / `Arrow Down` moves through visible connections and clusters.

### Standard and Pro Features

| Feature | Standard | Pro |
| --- | --- | --- |
| Local terminal workspace, tabs, splits, and pop-outs | Yes | Yes |
| SSH, Mosh, SFTP, and FTP profiles | Yes | Yes |
| Folder tree, search, local backup, and reusable secrets | Yes | Yes |
| Manual local and remote actions | Yes | Yes |
| AI configurations, connection context, model discovery, interactive assistance, and approved command execution | No | Yes |
| Managed SSH tunnels with status and automatic startup | Up to 2 | Unlimited |
| Fleet Runbooks with per-host status and controlled concurrency | Up to 2 | Unlimited |
| Saved and runtime clusters | Yes | Yes |
| Connection stagger for cluster launches | Yes | Yes |
| Encrypted cloud sync | No | Yes |
| CSV connection import | Yes | Yes |
| Before-connect and after-connect startup automation | No | Yes |
| Proxy jumps | Yes | Yes |
| Unique SOCKS proxy ports | No | Yes |
| Port probing and comma-separated host failover | No | Yes |

### Sync, Backup, and Restore

KaiTerm includes free local backup tools and KaiTerm Pro encrypted settings sync.

![Account, encrypted sync, backup, and import settings](https://kaiterm.dev/resources/screenshots/23-settings-sync.png)

- First-time email verification, after which the user can enroll a passkey in
  the system browser.
- Passkey sign-in, one-use recovery codes, and email account recovery.
- Atomic replacement of an existing passkey and its recovery-code set.
- Short-lived access tokens with rotating refresh tokens stored through
  Electron secure storage.
- KaiTerm Pro entitlement check before cloud sync.
- Initial download-or-upload choice when cloud settings already exist.
- Explicit passphrase recovery by replacing cloud settings from the computer
  with the most up-to-date local configuration.
- Local sign-in recovery when Electron secure storage can no longer unlock the
  saved session, without changing local settings.
- A Settings warning with repair instructions when a locally saved secret can
  no longer be unlocked.
- A value-based unsaved-changes check before opening Account & Data so explicit
  sync actions use the settings currently shown in the editor without prompts
  caused only by panel rendering.
- Automatic pull on startup after Pro sync is configured.
- Automatic push after settings changes for Pro accounts.
- Conflict reporting when cloud settings changed since the last pull.
- A sidebar sync control with a subtle green status when sync is healthy and a
  red status when an error needs attention.
- Explicit local-settings uploads remain available when automatic background
  sync has been disabled for the current launch.
- Local sync passphrase storage through Electron secure storage.
- Plaintext backup export containing the complete portable configuration,
  including passwords, private keys, and API keys, after an explicit warning.
- Optional whole-file backup encryption with an independent backup password.
- File-first restore that detects encrypted backups and requests their backup
  password without reading or changing the sync passphrase.
- Sync logout.
- CSV import for external connection migrations.

Sensitive sync data is encrypted client-side before upload using aes-256-gcm
with a pbkdf2-sha256 derived key. Locally stored passwords, private keys, and
key passphrases are encrypted with Electron `safeStorage`. Encrypted backups
wrap the entire portable settings document in a separate aes-256-gcm envelope
derived only from the user-provided backup password; plaintext backups contain
their portable secret values unencrypted.

### Updates

KaiTerm checks the public GitHub releases feed after launch and only offers an
update when a compatible package exists for the current platform.

- Cancel the update prompt and continue using the current version.
- Open the matching release download when a compatible package is available.
- Skip one specific release while allowing later releases to be offered.
- Fall back to the KaiTerm download page if a matching release asset cannot be
  selected.

### Program Paths

The app can use custom executable paths for the command-line tools it launches.

![Program path settings](https://kaiterm.dev/resources/screenshots/20-settings-programs.png)

- SSH path.
- SSH agent path and SSH add path.
- Option to use an SSH agent for stored private keys.
- Mosh path.
- SFTP path.
- FTP path.

### About

The About panel shows the app version, license, homepage, and repository. The
homepage and repository links open in the system browser.

![KaiTerm About panel](https://kaiterm.dev/resources/screenshots/24-settings-about.png)

## Screenshots

| Screenshot | Shows |
| --- | --- |
| ![KaiTerm splash screen](https://kaiterm.dev/resources/screenshots/00-splashscreen.png) | Screen-centered startup while settings and cloud state load |
| ![Connection tree](https://kaiterm.dev/resources/screenshots/01-main-window.png) | Main workspace, folder tree, empty state, and grouped footer actions |
| ![Single terminal](https://kaiterm.dev/resources/screenshots/02-first-connection.png) | Single open terminal tab |
| ![Split terminal](https://kaiterm.dev/resources/screenshots/03-first-cluster.png) | Multi-pane split terminal tab |
| ![Connection editor](https://kaiterm.dev/resources/screenshots/04-overlay-new-connection.png) | Per-connection profile editor |
| ![Cluster editor](https://kaiterm.dev/resources/screenshots/05-overlay-new-cluster.png) | Saved cluster editor with connection and folder targets |
| ![Fleet Runbooks](https://kaiterm.dev/resources/screenshots/06-overlay-runbooks.png) | Running and stopping saved Fleet Runbooks |
| ![Tunnel Manager](https://kaiterm.dev/resources/screenshots/07-overlay-tunnels.png) | Starting, stopping, and monitoring saved SSH tunnels |
| ![Appearance](https://kaiterm.dev/resources/screenshots/08-settings-appearance.png) | App theme, fonts, and tree colors |
| ![Terminal settings](https://kaiterm.dev/resources/screenshots/09-settings-terminal.png) | Terminal behavior preferences |
| ![Connection settings](https://kaiterm.dev/resources/screenshots/10-settings-connections.png) | Connection defaults |
| ![Secrets](https://kaiterm.dev/resources/screenshots/11-settings-secrets.png) | Reusable secret management |
| ![SSH settings](https://kaiterm.dev/resources/screenshots/12-settings-ssh.png) | Global SSH options |
| ![Mosh settings](https://kaiterm.dev/resources/screenshots/13-settings-mosh.png) | Global Mosh options |
| ![SFTP settings](https://kaiterm.dev/resources/screenshots/14-settings-sftp.png) | Global SFTP options |
| ![FTP settings](https://kaiterm.dev/resources/screenshots/15-settings-ftp.png) | Global FTP options |
| ![Commands](https://kaiterm.dev/resources/screenshots/16-settings-commands.png) | Global action commands |
| ![Tunnel settings](https://kaiterm.dev/resources/screenshots/17-settings-tunnels.png) | Saved SSH tunnel definitions |
| ![Runbook settings](https://kaiterm.dev/resources/screenshots/18-settings-runbooks.png) | Fleet targets, concurrency, commands, and failure behavior |
| ![AI settings](https://kaiterm.dev/resources/screenshots/19-settings-ai.png) | Named OpenAI, Grok, Gemini, and Ollama configurations |
| ![Programs](https://kaiterm.dev/resources/screenshots/20-settings-programs.png) | External program paths |
| ![Shortcuts](https://kaiterm.dev/resources/screenshots/21-settings-shortcuts.png) | Editable keyboard shortcuts |
| ![Variables](https://kaiterm.dev/resources/screenshots/22-settings-variables.png) | Command template variable reference |
| ![Account and data](https://kaiterm.dev/resources/screenshots/23-settings-sync.png) | Pro account, encrypted sync, backup, restore, and CSV import |
| ![About](https://kaiterm.dev/resources/screenshots/24-settings-about.png) | Version, license, homepage, and repository |
| ![Multiple selected connections](https://kaiterm.dev/resources/screenshots/25-tree-multi-selection.png) | Primary and secondary connection selection with a stable count |
| ![Bulk connection actions](https://kaiterm.dev/resources/screenshots/26-tree-multi-selection-menu.png) | Open, bulk edit, and delete actions for selected connections |
| ![Connection context menu](https://kaiterm.dev/resources/screenshots/27-connection-menu.png) | Start, open as SFTP, edit, clone, and delete actions for one connection |
| ![Folder context menu](https://kaiterm.dev/resources/screenshots/28-folder-menu.png) | Add, rename, launch, bulk edit, and delete actions for a folder |
| ![Terminal context menu](https://kaiterm.dev/resources/screenshots/29-terminal-menu.png) | Clipboard, SFTP, action, split, cluster, pop-out, reset, and exit controls |

## License

The Electron package currently declares `Proprietary`.
