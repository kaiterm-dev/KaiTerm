# Changelog

## v5.0.3

- **2026-10-25**:
  - Avoid cloud sync conflicts caused by settings defaults added after the last sync.
  - Show original action, AI, and MCP commands instead of their history and status wrappers.
  - Keep settings editor action buttons visible when their contents exceed the window height.
  - Pad the connection search icon and close the search with Escape.
  - Pack desktop picker and editor dialogs to their contents, with scrolling for longer lists and output.
  - Size desktop popups to fit their contents, including cloud sync conflict recovery buttons.
  - Keep commands KaiTerm types for you (actions, AI assistant, MCP) out of the shell history on bash and zsh; the first one of a session may stay recorded on zsh.
  - Add a "Hide KaiTerm commands from shell history" terminal setting, on by default.
  - Replace the per-AI "Suppress commands from Bash history" setting with it.

- **2026-10-24**:
  - Let MCP clients run a command in the background and check on it later, so long commands are no longer stopped at the timeout.
  - Let MCP clients run one command on every host of a cluster and get each host's result.
  - Let MCP clients wait for output to match a pattern, search the whole scrollback, and interrupt a session.
  - Let MCP clients read a session's working directory, user, host, OS, and shell, and whether it is busy.
  - Let MCP clients rename a session's tab.
  - Give MCP clients a connection's approved AI memories when they open it, or on request.
  - Report how long each MCP command took, and its exit code.
  - Let MCP clients list, read, write, upload, and download remote files over SFTP without opening a tab.
  - Let MCP clients read only the output that is new since their last read.
  - Let MCP clients save a connection memory, marked as saved through MCP.
  - Let MCP clients read a connection's non-secret settings, jump host, post-connection actions, clusters, tunnels, and open sessions.
  - Tell MCP clients whether a session's post-connection actions finished or failed.
  - Block MCP tools that change anything with a Read-only switch in the MCP Server settings.

- **2026-10-23**:
  - Run an action chosen from a clustered terminal's context menu in every terminal in that cluster.
  - Keep desktop prompts and confirmations visible above terminal content.
  - Remove a runtime cluster when its final terminal leaves or closes.
  - Drag all selected connections together between desktop sidebar folders without the initiating click collapsing the selection.
  - Drop desktop sidebar folders and connections onto the intended folder header, including a parent of a nested folder.
  - Fade desktop sidebar folder drop feedback instead of switching its colour abruptly.
  - Open desktop prompts, editors, confirmations, and pickers in the centre of their parent window.
  - Keep the desktop title bar colour unchanged when opening, closing, or hovering terminal tabs.
  - Choose KaiTerm or system window decorations on every desktop platform from Appearance settings, applying the choice after restart.
  - Keep the desktop tab strip visible and aligned with the sidebar collapse control when using system window decorations.
  - Keep unused tab-strip space non-draggable when using system window decorations.
  - Pad the tab strip from the window frame when using system window decorations.
  - Restore a blinking block cursor when a saved desktop cursor setting is missing or invalid.
  - Restore the cursor when reconnecting a retained desktop terminal session.
  - Pack desktop prompts, including backup-password entry, to their content instead of leaving fixed empty space.

## v5.0.2

- **2026-10-22**:
  - Open searchable desktop choices in a focused picker with a search field and scrollable results, instead of a dropdown that can cover its source field.
  - Restore clicks on fixed-choice desktop fields.
  - Close fixed-choice desktop dropdowns when their field is clicked again.
  - Use compact rows for fixed-choice desktop dropdown options.
  - Let fixed-choice desktop menus choose their own on-screen position.
  - Focus and select the searchable picker query when it opens, so typing starts filtering immediately.
  - Make the desktop color picker compact and cancel it when it loses focus.
  - Show terminal tab and cluster naming prompts inside the desktop app.
  - Show desktop confirmations and small naming prompts inside the app.
  - Keep spacing compact and consistent across desktop popups.

- **2026-10-21**:
  - Show only the first host in the connection list when a connection has several comma-separated hosts, as an IP address in full or a name without its domain.
  - Show the full labels and correctly sized actions in desktop cluster, tab, and folder naming dialogs.
  - Keep removed desktop settings list items removed until the user saves or cancels the editor.
  - Keep the desktop responsive while a local action runs in the background.

## v5.0.1

- **2026-10-20**:
  - Align fixed Settings, Tunnel Manager, and Runbooks tabs with the workspace when the connection sidebar is on the left.
  - Use correct singular and plural wording in counts and messages.
  - Show every confirmation and prompt in the same bordered window, centered over the app window, so none are hidden behind the terminal or hard to see.
  - Keep the port typed for a new connection when switching between the connection editor pages, instead of resetting it to the default.
  - Stop text fields from sometimes reverting to the previous text while typing, such as a connection name.
  - Relay a middle-click paste in a cluster to every terminal, even when the clicked terminal did not have keyboard focus.
  - Make "Open as SFTP" open an SFTP file transfer again instead of a second SSH terminal.
  - Complete commands and remote or local file names with Tab in SFTP and FTP tabs, listing the choices when there are several.
  - Use KaiTerm's built-in SSH client without an external SSH fallback.

## v5.0.0

- **2026-10-20**:
  - Use KaiTerm's built-in SSH client for connections, file transfers, runbooks, and SSH tunnels.
  - Verify SSH host keys consistently for terminal connections, runbooks, and tunnels.
  - Remove unsupported SSH and SFTP options from connection and bulk-edit settings.
  - Keep remote SSH tunnels working with the built-in SSH client.
  - Split every open desktop tab into one tab, or separate every split terminal into its own tab.
  - Cancel transient desktop naming popups with Escape.
  - Make all connection, automation, tunnel, Runbook, host failover, and AI features available without a paid tier.
  - Remove paid-account messaging and plan checks from desktop account and sync flows.

- **2026-10-19**:
  - Open searchable dropdown lists below their input fields.
  - Open non-searchable dropdowns only when clicking their field, not their label.
  - Filter SSH actions, SQL actions, runbooks, and tunnels by their names, folders, hosts, and commands.
  - Filter tunnel and runbook runner lists before starting or stopping an item.
  - Clear every desktop search field with its clear button or Escape without closing its dialog.
  - Open Settings, Tunnel Manager, and Fleet Runbooks as fixed, closable workspace tabs instead of popups.

## v4.1.2

- **2026-10-19**:
  - Resize the sidebar and split terminals with Compose split panes and standard resize cursors.
  - Show visible dividers and wider resize grips between split terminals.
  - Use Compose tabs for terminal tabs.
  - Keep visible terminal tabs in place when switching between them.
  - Use Material 3 text fields and menus in settings and other desktop forms.
  - Use Material 3 controls throughout the desktop app, including buttons, selections, navigation, dialogs, tabs, and progress indicators.
  - Keep Material 3 fields and buttons at KaiTerm's compact desktop size.
  - Keep Material 3 switches and checkboxes compact in settings rows.
  - Use Material 3 sliders in the colour picker and dismiss picker dialogs with Escape.

## v4.1.1

- **2026-10-15**:
  - Make Unique SOCKS proxy serve connections in built-in libssh2 SSH terminals.

## v4.1.0

- **2026-10-12**:
  - Rename a tab from its right-click menu with Rename tab; a chosen name replaces a cluster name and is kept when the tab leaves the cluster.
  - Paste the selected text with a middle click on macOS, within KaiTerm only and without changing the clipboard, like Terminal.app.
  - Add an MCP Server setting that lets AI apps such as Claude Code and Codex connect to the running KaiTerm over local HTTP; it is off by default and starts or stops immediately.
  - Protect the MCP server with an access token that you can regenerate in Settings > MCP Server, and listen on this computer only.
  - Choose the MCP server port in Settings > MCP Server, and show why the server could not start, for example when the port is busy.
  - Add KaiTerm to Claude Code or Codex with one Add button in Settings > MCP Server.
  - Show the commands that the Add button ran and their result, without revealing the access token.
  - Show a ready-to-copy JSON snippet for other MCP clients in Settings > MCP Server.
  - Let AI apps list your connections and open terminal sessions through MCP.
  - Let AI apps run commands in a session and read the result, with a timeout that interrupts commands that do not finish.
  - Rename a tab to the cluster name when creating a cluster from the whole tab, and restore its name when the cluster is broken or the tab leaves it.
  - Ask for a name when opening several connections in a split tab, for Open all and Open as cluster.
  - Let AI apps send keystrokes to a session and read its screen and scrollback as text.
  - Let AI apps close terminal sessions through MCP.

- **2026-10-10**:
  - Show the Run card when an AI model writes its proposed command as JSON text instead of a tool call, as some Cloudflare Workers AI models do.
  - Sort AI configurations by name in Settings and in the Open with AI menu.
  - Add new AI configurations at the top of the list.
  - Add Cloudflare Workers AI as an AI provider; it needs your Cloudflare account ID alongside the API token.
  - Fix an "index: 0, size: 0" error when running a command proposed by the AI assistant.
  - Run AI-proposed commands in SSH terminals that use the built-in libssh2 connection; Run did nothing there before.
  - Keep what you type into a libssh2 SSH terminal while it is still connecting, and send it once the connection opens.
  - Show only the proposed command in the terminal when running an AI command, instead of the long wrapper KaiTerm types around it.
  - Start the AI assistant's environment check after the connection's post-connection commands finish, so it sees the user and environment they set up.
  - Show the AI assistant panel as soon as a connection opens with AI, with what it is waiting for until it is ready to chat.

- **2026-10-09**:
  - Show the dragged tab lifted with a shadow under the pointer while the other tabs slide aside to make room.
  - Add NVIDIA (Nemotron and other NVIDIA-hosted models) and Groq as AI providers.
  - Copy the whole highlighted words or lines after a double- or triple-click drag on Linux, so a middle-click paste no longer stops where the pointer was.
  - Fix the Windows app hanging on the startup splash with high CPU use.
  - Show an error and quit instead of spinning forever when startup fails.
  - Add a Start menu entry and a desktop shortcut from the Windows installer.
  - Fix saving the local settings PIN on Windows.
  - Fill the Settings window edge to edge instead of drawing a rounded panel inside the frame.
  - Match the hover and click highlight of sidebar buttons to their square shape instead of a circle.
  - Show a setup wizard in the Windows installer to choose the install folder, instead of installing silently.
  - Use the KaiTerm icon for the Windows app and installer.
  - Include the Java modules the packaged app needs, such as SQL support for database terminals.
  - Fire every shortcut wherever focus is, including Shift+Left and Shift+Right to switch tabs from a terminal; change or clear a shortcut in Settings to give its keys back to the terminal or text field.
  - Show shortcuts in Settings with the platform's key names, such as Ctrl+Shift+C or Cmd+Shift+C, instead of Primary.
  - Change a shortcut in Settings by clicking it and pressing the new keys; Backspace clears it.
  - Warn in Settings when two actions share a shortcut.
  - Reset a shortcut to its default from Settings.
  - Allow F1 to F12, Page Up, Page Down, Home, End and punctuation keys in shortcuts.
  - Show shortcuts that were never changed in Settings when only some were customised, instead of "Not set".
  - Follow customised Copy, Paste and New Local Terminal shortcuts in the macOS menu bar.

## v4.0.0

- **2026-10-08**:
  - Type characters made with the Option key on macOS, such as # with Option+3 on a UK keyboard, instead of sending Escape sequences.
  - Apply a changed terminal font family or size to every open terminal right away, as the theme already was.
  - Ask "Discard changes?" when Esc closes a connection, cluster, folder rename, secret, bulk edit or Settings dialog with unsaved changes; close at once when nothing changed.
  - Stop Shift-only and Alt-only shortcuts from firing while a text field has focus.
  - Stop the sidebar taking focus back after a click elsewhere while the connection filter is open.
  - Add a "Don't ask again" checkbox to the quit confirmation, shared by Cmd+Q and closing the window.
  - Add Select All to the Edit menu for the terminal.
  - Keep running an action's commands after a Password step opens an interactive shell such as su -: the next command is sent once the new shell's prompt appears, instead of waiting forever for the first command's exit status.
  - Space out the sidebar action buttons when they are laid out horizontally.
  - Send terminal input to libssh2 sessions in order through one writer, so a paste can no longer lose or reorder characters (such as the first letter of a line).
  - Hide private keys in the secrets editor and the connection editor until revealed.
  - Show or hide every password, passphrase, and private key field with an eye icon button.
  - Skip the connection port probe when a connection has a single host, which fixes intermittent "Unable to exchange encryption keys" errors on servers using socket-activated sshd.
  - Wait for the connection stagger after a successful connection port probe before connecting, so a socket-activated sshd has time to finish the probe's connection; no wait when the stagger is 0.
  - Rename the stagger setting to "Connections, commands, and port probe stagger".
  - Keep typed characters in the sidebar type-ahead search instead of replacing the query with the last one.
  - Let Shift+Arrow and Alt+E reach the shell when a terminal has focus, since only shortcuts with Ctrl or Cmd now fire from a terminal.
  - Let copy, Ctrl+C, selection, and scroll keys work in a disconnected terminal: only Enter and Esc answer the restart or close prompt.
  - Add an Edit menu with Copy and Paste for the terminal (Cmd+Shift+C and Cmd+Shift+V on macOS, Ctrl+Shift+C and Ctrl+Shift+V elsewhere).
  - Do not send an AI chat message with Enter while an input method composition is active.
  - Read the default keyboard shortcuts from the shared library, so they match the other apps.

- **2026-10-07**:
  - Restarting a failed or closed connection with Enter reads the saved connection again, so settings edited in the meantime apply, while the terminal history is kept.
  - Fix the "Index 0 out of bounds for length 0" error when a popped-out tab is reattached: each window now hosts the terminal in its own panel.
  - On macOS, stop the system dragging the whole window from the tab bar, so dragging a tab reorders it (or pops it out) and a second double-click on the bar restores a maximized window.
  - Verify the downloaded JetBrains Runtime against JetBrains' SHA-512 checksum before unpacking it.
  - Fix a connection's port and other number settings not taking effect: the editors stored them as 22.0, which the shared connection code read as missing and replaced with the default. Whole numbers are now stored as integers and shown without .0.
  - Pop a tab out into its own window by dragging it up or down away from the tab bar.
  - When the AI assistant says a command needs approval but never proposes one, ask it once for the real proposal so the approval card appears.
  - Say whether an AI request never connected or was sent but got no reply, with the times, instead of one generic timeout message.
  - Save the connection editor, Settings, cluster editor, bulk edit, and New secret dialogs when Enter is pressed in a single-line text field.
  - Download the JetBrains Runtime 25 SDK on macOS and Windows too, so `build.sh` no longer fails there with "Cannot find a Java installation ... vendor JetBrains".

- **2026-10-06**:
  - Open and close tree and terminal context menus with the `menu` and `close-menu` automation commands.

- **2026-10-07**:
  - Keep the connection filter and sidebar open when you click a filtered connection, so it can be double-clicked to open.

- **2026-10-05**:
  - Verify the downloaded JetBrains Runtime against JetBrains' SHA-512 checksum.
  - Give libssh2 terminals the window's real size as soon as they connect, instead of 100×30 until the next manual resize, so vim and other full-screen programs start at the right size.
  - Run Fleet Runbooks with the shared engine (same order, statuses, skipping and cancellation as before).
  - No visible change: the desktop's tunnel proxy and port-forward code now has a shared counterpart that Android uses.
  - Take the Fleet Runbook status roll-up and skip/cancel messages from the shared library.
  - Use the shared library for host key verification, tunnel validation and forwarding, command variables, cluster and search rules, output cleanup and default settings, so connections behave the same as on Android and iOS.
  - Offer the universal macOS app as a ZIP download alongside the DMG.
  - Offer updates from the release asset that matches the installed package's platform, so the Windows portable ZIP and the macOS ZIP are never mixed up.
  - SFTP and FTP connections no longer launch the `sftp` and `ftp` programs: SFTP runs on libssh2 and FTP on the shared client Android and iOS use, in a terminal tab with an sftp-style command line (ls, cd, pwd, get, put, mkdir, rm, rmdir, lls, lcd, lpwd, help, bye). `--no-libssh2` keeps the external programs.
  - MySQL over SSH opens its tunnel with libssh2 instead of launching `ssh -L`.
  - The SFTP and FTP command line gains rename/mv, chmod, wildcards (`*`, `?`, `[..]`) in ls/get/put/rm, recursive `get -r`, `put -r` and `rm -r`, and shows the absolute remote directory in pwd.
  - Ask before trusting an unknown SSH or SFTP host key or FTPS certificate (and again if it changes) for libssh2 terminals, SFTP, FTP and MySQL over SSH; trusted fingerprints are kept in known_hosts.json.
  - FTP connections use explicit TLS (FTPS) when the server offers it, with the new FTP "TLS (FTPS)" setting (use when offered, required, off); the command line warns when a connection is not encrypted.
  - MySQL over SSH serves every connection a client opens, not just the first one.
  - Hide the OpenSSH-only connection options (X11 forwarding, verbose, very verbose, force PTY, additional options) unless the app starts with `--no-libssh2`; libssh2 connections still apply the additional options they support (ciphers, MACs, key exchange, host key algorithms, timeout, compression, keepalive, StrictHostKeyChecking) and ignore the rest.
  - Add a "Host key checking" setting (ask, trust new and refuse changed, don't check) to the global SSH and SFTP settings, and "Certificate checking" to FTP, each overridable per connection; MySQL over SSH follows its SSH connection.
  - Add libssh2 settings to the global SSH and SFTP pages and the connection overrides: keepalive interval and unanswered-keepalive count (0 turns keepalives off), ciphers, MACs, key exchange and host key algorithms, address family, an SSH agent socket path, and a known_hosts file whose matching keys are trusted without asking (OpenSSH plain, wildcard and hashed entries; it never blocks a connection). They are hidden with `--no-libssh2`.
  - Verify the proxy-jump host's key before authenticating to it, using that connection's own host key checking and known_hosts file, and use its SSH agent socket; previously jump hosts were accepted without a check, and a hop's options could overwrite the target's timeout and address family.
  - Resolve libssh2 SSH, SFTP, FTP and MySQL connections with the same resolver Android uses, so settings, secrets, proxy jumps, host failover and the Standard limits behave the same: a missing proxy-jump connection is now an error instead of a silent direct connection, host failover and probing work with libssh2, a MySQL TLS mode outside disabled/trust/verify falls back to verify, and an unknown or duplicated secret slug fails instead of sending an empty value.
  - Add a "strict" host key mode (refuse unknown hosts) next to ask, accept-new and off; host names are compared case-insensitively.
  - Remove the X11 forwarding setting; the unique SOCKS proxy stays here as the desktop-only option it is.
  - Run startup actions, AI chats, cloud sync and backups on the same code Android and iOS run: one prompt-driven action engine, one AI chat session (same prompts, tools, redaction and Ollama support), and one sync engine (same conflict rules, session refresh and backup format). Saved actions no longer run through a desktop-only copy, and AI commands, backups and CSV imports behave the same everywhere.
  - Check tunnels, runbooks, actions and AI configurations when saving settings, and open SFTP from an SSH connection with its host key, keepalive and algorithm settings.
  - Remove Bitwarden and Keeper: the four secret types, their item and field settings, and the Bitwarden/Keeper CLI path settings.
  - Show Settings > Programs only when the app starts with `--no-libssh2`, and list only the programs the app actually launches (SSH, SFTP, FTP); remove the unused SSH agent, ssh-add and "use SSH agent" settings and move "Shell program" to Terminal.
  - Make every single-line field and dropdown (text inputs, plain and searchable dropdowns, bulk-edit and add-action pickers) exactly the same height with the same padding, and use Material 3 with compact typography so text is no longer widely spaced.
  - Update pty4j to 0.14.0, slf4j-simple to 2.0.20 and Gradle to 9.8.0, and rebuild the vendored macOS libssh2/OpenSSL libraries against OpenSSL 3.6.5 (the vendor script now targets 3.6.5; the Linux libraries still need rebuilding on Linux).
  - Drop the Jewel UI library: the app now uses plain Compose (Material 3 widgets under its own `KaiTermTheme` and `DesktopUi` wrappers) with the same palette, compact controls and light/dark switching.
  - Use one shared `HttpClient` for the account server and the AI providers instead of three hand-rolled `HttpURLConnection` clients; the AI Stop button now cancels the request itself.
  - Cluster broadcast now relays exactly what is typed or pasted, using JediTerm's own user-input flag instead of matching reply text (this also stops terminal auto-replies reaching SSH and MySQL cluster siblings).
  - Make the "Reset terminal" menu item work (it called a JediTerm action that does not exist).
  - Open links with Cmd/Ctrl+click by reading the click's own modifiers instead of tracking the key globally (no more stale modifier after switching windows).
  - Detect the system light/dark appearance at startup natively (macOS, Windows and Linux) instead of running `defaults`.
  - Minimise through the window state, use FlatLaf's property constants, and drop duplicate JSON helpers.
  - Open a searchable dropdown when its field is clicked, scrolled to and highlighting the current value, and stop cutting its list at 80 entries.
  - Remove the "Open local terminal" button; when every tab is popped out the main window shows the standard workspace content.
  - Keep the main window's terminal visible when a popped-out window is selected or one of its panes is closed.
  - Remove a popped-out tab from the tab bar (it lives in its own window until that window is closed or the tab is reattached), and move on to a neighbouring tab.
  - Replace the settings dropdowns with ones that move with Up/Down, pick with Enter, and close with Escape without closing the dialog.
  - Fill in a new secret's slug as its label is typed (until the slug is edited by hand).
  - Add new secrets at the top of the Secrets list, from both the Secrets settings and a connection's "New secret".

- **2026-10-03**:
  - Stop Shift from opening connection search with a blank character when Shift+clicking a range in the connection tree.
  - Open dropdown menus at exactly the width of their field instead of extending past both edges.
  - Select the existing query when the connection search or terminal search shortcut is used again.
  - Show new SSH and SQL Actions at the top of the list, and move an action to its folder only after Settings are saved.
  - Show actions added in the connection editor's SSH Actions immediately instead of inside a collapsed folder.
  - Open fixed-choice dropdowns on any click without a text cursor, and list their choices in their natural order, such as Text, Hidden, Password for action commands.
  - Show each action's folder in the connection Startup lists and sort the action choices alphabetically.
  - Add opt-in local automation with `--automation`, and send automation commands from the command line with `--automate`.

- **2026-10-02**:
  - Stop highlighting URLs in terminals; Ctrl/Cmd+click still opens them.
  - Post-connection actions: recognise `>` and `%` (and a bare `$`, `#`, `>` or `%`) as shell prompts and any line mentioning a password or passphrase followed by a colon as a password prompt (shared with Android).
  - Make Password steps wait for such a prompt before sending, instead of firing as soon as the previous command was echoed; fail the action if none appears within 30 seconds, like Android, iOS and Electron.
  - Pause between cluster/folder connections and between Fleet Runbook commands with the stagger setting.
  - Rename the "Connection stagger" setting to "Connections and commands stagger" and also use it as the pause between post-connection commands (still used between Fleet Runbook hosts).
  - Make macOS native dialogs (file open/save, such as Export KaiTerm Backup) follow the app's light/dark mode, including after it changes while the app is running.
  - Select the first result in tree order, not saved order, when searching the connection tree.
  - Enable multi-statement queries in the MySQL terminal (`select 1; select 2;`) and show the result of every statement.
  - Clip terminal text selections at the last character containing output.
  - Clarify the connection stagger unit and adjustment increment in its setting label.
  - Compact secret identity and credential fields into shared rows while keeping key fields full-width.
  - Show the connection editor's Password next to Username as a single-line field, and make Key passphrase single-line.
  - Add inset padding inside multiline text editors.
  - Add more space after the secret list.
  - Add bottom padding below the last field of expanded settings list items such as secrets.

- **2026-10-02**:
  - Add "Swap split panels" and "Switch split direction" to the terminal and tab context menus and the Terminal menu: a terminal acts on its innermost split, a tab on its outermost.

- **2026-10-01**:
  - Add an "Extra word separators" terminal setting controlling where a double-click selection stops (default `=;`).
  - On Linux, selecting text fills the X11 primary selection and middle-click pastes it, without touching the Ctrl+C / Ctrl+V clipboard.
  - Add build-windows.ps1, which installs the Windows build dependencies (MSYS2, JDK 25, WiX), builds the libssh2 libraries and packages the app.
  - Add a Windows (x86_64, MinGW-w64) build of the libssh2 library and enable the built-in SSH client on Windows too.
  - Use the built-in libssh2 client for SSH terminals by default on macOS and Linux; pass `--no-libssh2` to use the system ssh instead.
  - Send cluster keystrokes to libssh2 SSH terminals.

- **2026-10-01**:
  - Restore the borderless JVM main window with integrated window controls and draggable tab header.
  - Keep unused tab header space draggable after opening terminals, including when tabs overflow.
  - Place the connection sidebar below the header when it shares the window controls side, and let it reach the top on the opposite side.
  - Allow window controls on either side on Linux and Windows.

- **2026-09-30**:
  - Show the signed-in email and Pro status in JVM Account & Data settings.
  - Hide cloud sync controls when the signed-in account does not include Pro.
  - Check the current Pro entitlement before saving a cloud sync passphrase.
  - Auto-start only the managed tunnels available to Standard accounts.
  - Show the KaiTerm icon on the update dialog instead of the Java icon.
  - Match the JVM launcher to its XWayland window class and native Wayland app ID.
  - Show KaiTerm as the JVM window class in Linux window managers.
  - Fix the JVM desktop launcher's Exec entry so desktop menus can run it.

- **2026-09-29**:
  - Set the JVM app version to 1.0.0 (single source in desktopApp/build.gradle.kts, used by the package and the About panel).
  - Check GitHub releases for updates at startup and offer Download, Skip Release, or Cancel, like the Electron app.
  - Check exit codes for non-Password steps in startup, Fleet Runbook, sidebar, and context-menu actions without requiring password prompts.
  - Tie hidden status markers to the command they measure so commands that request passwords finish before their status is read.
  - Keep Password action input hidden regardless of the current remote prompt.
  - Avoid status markers for Password-only actions.
  - Prefix non-Password remote action commands with a space to avoid shell history where supported.
  - Run manual Password actions immediately and resolve their named secret placeholders before sending them.

- **2026-09-22**:
  - Use a crisp macOS-style squircle icon for the JVM launcher, running app, splash screen, empty workspace, and packaged app.
  - Keep JVM right-click menus responsive when opening or leaving grouped actions.
  - Keep macOS window maximize and restore transitions smooth.
  - Use the operating system's own window decoration and dragging instead of a custom title bar on every platform.
  - Fix the main window's title bar not matching dark mode when following the system appearance.
  - Stop repeating the "Sync problem" error on every launch after a session expires; sign in again instead.
  - Update Kotlin, Compose Multiplatform, Jewel, JediTerm, and other dependencies to their current stable releases, and remove dead code left behind by earlier fixes.

- **2026-09-21**:
  - Keep macOS half-screen window tiling smooth when terminals are open.
  - Keep JVM interface icons legible in light and dark modes.
  - Prevent handled JVM shortcuts from also triggering conflicting macOS window actions.
  - Reorder JVM terminal tabs by dragging them without moving the application window.
  - Start JVM word and line selection on multi-click press and preserve those boundaries while dragging.

- **2026-09-20**:
  - Remove the new-local-terminal plus button from the top bar.
  - Keep consistent space between terminal tabs and the window edge.
  - Show left and right controls when terminal tabs overflow the available width.
  - Keep Linux window dragging stable with the native draggable title-bar behavior.
  - Keep Linux and Windows window controls legible in light and dark modes.
  - Keep right-side connection-tree controls and dividers clear of the window controls.
  - Keep the complete title bar draggable above a right-side connection tree.
  - Use KaiTerm window decorations for Settings, editors, managers, and terminal popouts on Linux and Windows.
  - Keep terminal tab context menus above embedded terminal content.

- **2026-09-19**:
  - Expand parent folders before revealing the focused terminal's saved connection.
  - Select and reveal the focused terminal's saved connection in the connection tree.
  - Order Cluster and Fleet Runbook folder and connection pickers alphabetically.
  - Use the full dialog width for Cluster forms below macOS window controls.
  - Add an included-only filter to Fleet Runbook host selection.
  - Order Runbook targets and action controls consistently.
  - Keep action commands at the end of their settings form.
  - Keep Runbook and Cluster target lists independently scrollable.
  - Keep action command, mode, and removal controls aligned on one line without redundant labels.
  - Match settings dropdown widths to their fields.
  - Show connection terminals before host probing completes and keep every cluster member visible when another member fails.
  - Arrange split clusters in the same balanced grid used by Electron.
  - Redistribute split terminal space evenly when a pane closes.
  - Focus another split terminal after closing a disconnected pane so Enter and Escape remain usable.

- **2026-09-18**:
  - Keep the JVM development launcher settings isolated from the regular app configuration.
  - Filter the focused connection tree when typing.
  - Focus the connection tree on an empty workspace so typing starts its filter.
  - Navigate connection-tree search results in their visible order.
  - Focus newly opened terminals so they accept input immediately.
  - Make the active terminal tab indicator wider.
  - Use an integrated title bar with app window controls on Linux and Windows.
  - Match Electron terminal tab sizing, controls, and active indicator spacing.
  - Center terminal tab labels.
  - Use platform-appropriate Swing scrollbar styling in terminals.

- **2026-09-18**:
  - Stop saved actions at the first failed command, including startup and runbook actions.
  - Continue runbooks on remaining hosts after a host or action fails.
  - Group runbook results into collapsed Connection and action panels.
  - Use consistent passed, skipped, and failed colors in runbook results.
  - Expand individual hosts to show command output and failure details.
  - Keep captured action output visible after failures, timeouts, and cancellation.
  - Hide internal printf probes from terminal and runbook output.
  - Keep one shell prompt without extra blank lines after post-SSH password actions.
  - Wait for the shell prompt before starting the next remote action command.
  - Keep connection-tree hosts alongside their connection names.
  - Open the complete terminal tab context menu reliably on right-click.
  - Serialize cloud sync operations to prevent local sync request conflicts.
  - Save settings to cloud sync without false upload/download conflicts.
  - Preserve completed uploads when another settings change restarts automatic sync.
  - Offer immediate Download Cloud or Upload Local recovery for sync conflicts.
  - Clear stale sync error messages after a later automatic sync succeeds.
  - Submit Account & Data email, verification-code, and sync-passphrase fields with Enter.

- **2026-09-17**:
  - Show complete IP addresses and concise first-label hostnames in the connection tree.
  - Render connection-tree hosts as smaller secondary text.
  - Keep Fleet Runbook result panels collapsed until explicitly opened.
  - Make Action Library icons visible in settings pickers.
  - Match Electron's branded empty workspace guidance and shortcut hints.
  - Open SFTP and FTP connections with saved credentials, protocol options, proxy jumps, and local startup actions.
  - Encrypt locally saved passwords, private keys, passphrases, and API keys with an OS-protected JVM application key.
  - Integrate dark macOS title bars into the main window, Settings, connection editor, and terminal popouts.
  - Render terminal selections with the configured selection color instead of inverse white blocks.
  - Show cloud sync state in the connection-tree footer and run manual sync from the indicator.
  - Persist encrypted cloud sign-in, passphrase, revision, and conflict state in sync-state.json across launches.
  - Check cloud revisions at startup and after local changes, automatically synchronizing clean histories without overwriting conflicts.
  - Show the persisted cloud sync error in Account & Data and on the sync control.
  - Keep downloaded cloud settings on the same clean sync baseline after restarting the JVM app.
  - Open Account & Data when the sync control reports an error.
  - Keep sidebar buttons clickable by removing pointer-intercepting popup tooltips and retained focus styling.
  - Use the Compose double-click handler for title-bar maximize and restore.
  - Add macOS Dock and Linux desktop development launchers with isolated settings and visible startup diagnostics.
  - Edit, clone, delete, and reopen saved connections from the connection tree, including opening SSH profiles as SFTP.
  - Create, edit, delete, and launch cluster presets as split terminals or separate tabs.
  - Keep edited cluster membership current at launch and prevent runtime cluster input from corrupting parallel connection startup.
  - Start, stop, auto-start, copy endpoints, and open saved SSH tunnels with automatic local port allocation.
  - Run and stop saved Fleet Runbooks across SSH hosts with per-host status and captured output.
  - Match the Electron startup splash artwork, logo, copy, and loading indicator while the JVM workspace starts.
  - Render the Electron splash artwork and logo from PNG assets without opaque artifacts.
  - Use consistent labelled add buttons and red removal icons throughout Settings collections.
  - Keep tunnel and Fleet Runbook runner dialogs focused on running saved items with normal content insets below macOS controls.
  - Size confirmation dialogs to their content instead of using a large fixed window.
  - Trust HTTPS certificate authorities accepted by macOS Keychain or the Windows system store in addition to Java defaults.
  - Keep terminal tabs clear of macOS window controls with either sidebar placement, including when collapsed.
  - Use rounded, draggable terminal tabs aligned with macOS window controls, complete tab context actions, connection status, and a clear active-tab accent.
  - Scroll overflowing terminal tabs while keeping the new-terminal button accessible.
  - Give the sidebar, toolbar buttons, and tabs distinct blue-toned surfaces in light and dark mode.
  - Keep the sidebar toggle neutral and align all collapsed sidebar buttons on the same center line.
  - Separate popup action buttons with consistent spacing.
  - Probe SSH, SFTP, and FTP hosts concurrently and select the first reachable host in the configured order.
  - Expand SSH aliases when probing and select reachable jump hosts for SSH and SFTP connections.
  - Honor numeric ports and probe timeouts saved by the settings editor.
  - Keep connection, cluster, and tunnel launches responsive while hosts are being checked.
  - Highlight connections and clusters immediately on press while preserving double-click to open.
  - Add and edit complete SSH and SQL actions inside the connection editor.
  - Include connection actions and local post-connect actions in startup action choices.
  - Open searchable settings choices from their dropdown buttons and show selected names.
  - Space settings action editors, command rows, and additional options consistently.
  - Apply the selected terminal theme to selection foreground and background colors.
  - Stop terminal text from retaining the previous theme's background color after a theme change.
  - Apply the selected theme background to terminal text from the first rendered character.
  - Confirm before quitting KaiTerm while terminal sessions are open.
  - Use a compact header aligned with native macOS window controls and larger sidebar buttons.
  - Center larger native macOS window controls in the JVM header.
  - Resize the connection sidebar from either side and remember its width.
  - Maximize or restore the main window by double-clicking its header.
  - Match Fleet Runbook step, host, status, and ANSI-colored output presentation with Electron.
  - Use consistent spacing between form labels, controls, collection cards, and settings sections.
  - Add stable Electron-compatible folder and multi-connection context menus with open, cluster, bulk edit, rename, and delete actions.
  - Complete cluster preset cloning and terminal and tab join, leave, and break controls.
  - Keep dialog headings and popped-out terminal content clear of macOS window controls.
  - Apply a consistent modern light or dark FlatLaf theme to Swing menus and embedded terminal controls.
  - Apply Jewel's IntelliJ theme and controls consistently across the Compose desktop interface.
  - Use the macOS Keychain trust store for secure dependency downloads from the local development launcher.
  - Apply the configured accent color to sidebar actions and selected Settings and connection editor pages.
  - Match Electron's outlined sidebar controls and show sync readiness with a green or red dot.
  - Separate JVM footer action groups to match Electron.
  - Extend the sidebar through the title bar only when it is opposite the macOS window controls.
  - Keep the sidebar surface and divider below same-side macOS window controls.
  - Vertically center macOS window controls in the Settings header.
  - Keep Settings and connection and cluster editors attached above the main window and close them with Escape.
  - Use a more compact cluster editor layout.
  - Show cluster members as protocol plus their complete folder and connection name.
  - Keep connection search hidden until typing begins and dismiss an empty search on blur or Escape.
  - Use the shared compact desktop form controls throughout the JVM application.
  - Widen connection and cluster editors and use neutral inactive toggle colors.
  - Match Electron connection fields for credentials, SSH persistence, proxy jumps, probing, startup actions, and protocol overrides.
  - Split connection editing into General, Connection, Startup, and action pages matching Electron.
  - Open the selected connection or cluster with Enter and dismiss connection search.
  - Remove redundant close controls and save instructions from integrated dialog headers.
  - Run every configurable application shortcut across Compose and terminal focus.
  - Apply split, search, copy, paste, and duplicate shortcuts to the focused terminal pane.
  - Start SSH and SQL action groups collapsed and close every dialog with Escape, including manager and popup-backed Settings screens.
  - Filter Secrets by name, slug, and username.
  - Use labelled add controls for Settings collections and SQL statements.
  - Use an overlapping double-plus icon for creating clusters.
  - Focus compact dialog inputs automatically and submit valid name and password forms with Enter.
  - List connections before child folders and add filtering plus an included-only toggle to cluster editing.
  - Connect to MySQL and MariaDB directly or through a saved SSH connection.
  - Configure verified TLS, trust-all TLS, CA certificate secrets, connection timeouts, and a dedicated MySQL tree color.
  - Create SSH and MySQL connections from the connection-tree action.
  - Show saved CA certificates in the global MySQL settings selector.
  - Run SQL in terminal tabs with history, cursor editing, vertical results, custom delimiters, warnings, source files, output logs, and query interruption.
  - Keep pasted SQL queries ordered while earlier queries run.
  - Manage separate SSH and SQL actions and run SQL actions from database terminals.
  - Hide fragmented and colorized hidden-command echoes before they enter the terminal or transcript.
  - Replace automatic reconnect with consistent Wait for key and Close immediately disconnect choices.
  - Optionally retain terminal scrollback when reconnecting through Terminal settings.

- **2026-09-04**:
  - Paint the complete terminal surface with the selected terminal theme before the first input arrives.
  - Add `{host_rslv}` for actions that need the selected host as a resolved IP address.
  - Show pinned actions as a flat, left-aligned `folder/name` list in the expanded connection tree.
  - Expand connection variables before sending pinned action commands to the active terminal.
  - Resize terminal surfaces to fill their workspace and update the PTY dimensions with the window.
  - Show terminal close, error, and cluster prompts above the Swing terminal surface.
  - Switch the visible terminal surface whenever the active tab changes.
  - Show a simple cluster-name input when creating runtime clusters.
  - Reserve a different dynamic SOCKS port for every terminal session, including repeated and split opens of the same connection.
  - Hide pinned actions during connection-tree searches and wrap Up/Down navigation through matching connections and clusters.
  - Run SSH pre-connect actions with Electron-compatible variables, secret placeholders, platform filtering, and stop-on-failure behavior.
  - Run mixed local and remote SSH post-connect actions in saved order, preserving text, hidden, and password command modes while waiting between commands.
  - Give repeated and split persistent SSH connections independent screen or tmux session names.

- **2026-09-02**:
  - Added JVM SSH terminal connections using OpenSSH with saved password, private-key, key-passphrase and agent authentication; global and per-connection overrides; compression, X11 and agent forwarding; PTY, verbosity, timeout, arbitrary options, proxy jump, host failover probing, unique SOCKS proxy and screen/tmux persistence.
  - Added SSH before/after startup actions, automatic credential prompt responses, same-connection reconnect and split behavior, double-click connection launch, and visible launch errors.

- **2026-09-01**:
  - Applied terminal font, text size, colour theme, cursor, scrollback, scroll-on-keystroke, scrollbar, and bell preferences to JVM terminal sessions.
  - Refined JVM fields, tree rows, icons, menus, sidebar actions, internal padding, typography, and toggles for desktop-appropriate density.
  - Moved compact field labels outside their input outlines so labels never cover entered values.
  - Fixed encrypted Secrets entries failing to expand in JVM Settings while preserving untouched saved values.
  - Matched Electron secret fields and local versus remote Action Library behavior, including platform multi-selection.
  - Added Escape-to-close for JVM Settings and restored normal window stacking.
  - Fixed local terminals failing to render when unlimited scrollback is selected.
  - Kept Settings above active terminal surfaces in its own desktop window.

- **2026-08-31**:
  - Added the native JVM desktop application with Electron-compatible persistence, cache and window geometry; theme-aware neutral surfaces and native dialogs; compact global settings with complete Secrets, foldered Action Library, Runbooks, Tunnels, AI, account, backup, sync, and CSV editors; per-command text, hidden, and password modes; a loose-connections-first collapsible folder tree with saved cluster presets; bundled themes and icons; and persistent JediTerm and Pty4J terminal tabs with a single application context menu, reliable disconnect strategies, terminal and tab menus, nested splits, unsplit, popout, and reattach.
