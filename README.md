# KaiTerm

KaiTerm is a connection manager for SSH, SFTP, FTP, and MySQL/MariaDB. It is available for Linux, macOS, Windows, and Android. Each app keeps SSH and SFTP inside KaiTerm with its built-in libssh2 client.

## Download and install

Choose the package for your device from the release assets.

- Linux: AppImage, DEB, Flatpak, RPM, Snap, or tar.gz.
- macOS: a universal DMG or ZIP. The app is signed ad hoc and not notarized, so macOS may warn on first launch. Open it with right-click, Open, or allow it in System Settings, Privacy & Security.
- Windows: a setup EXE or portable ZIP. Extract the ZIP before launching `KaiTerm.exe`.
- Android: the universal `KaiTerm-Android-<version>-universal.apk`. Android may ask you to allow installs from the browser or file manager used to open it.

On first launch, add a connection from the connection list or home screen. KaiTerm supports local shells, SSH, SFTP, FTP, and MySQL/MariaDB sessions. Sign in under Account & Data to use encrypted cloud sync, or use local backup, restore, and CSV import instead.

## Usage

1. Select New connection and choose SSH, SFTP, FTP, or MySQL/MariaDB.
2. Enter the host and authentication details, then verify the host key or certificate when prompted.
3. Open the saved connection from the connection list. SSH and database connections open terminals, while SFTP and FTP open a file-transfer view.
4. Use Fleetbook to organize connections, Actions to save repeatable commands, and Fleet Runbooks to run an action across selected hosts.

All features are available to every account. Account & Data provides encrypted cloud sync after sign-in, plus local backup, restore, and CSV import.

## Features

- Organize connections, clusters, actions, tunnels, and Fleet Runbooks in searchable folders.
- Open local shells, remote SSH sessions, database sessions, SFTP, and FTP transfers from one workspace.
- Use host-key and certificate verification, proxy jumps, host failover, reusable secrets, and connection-specific settings.
- Run saved Actions and Fleet Runbooks, manage SSH tunnels, and use connection-scoped AI assistance.
- Connect desktop AI tools through the optional MCP server to work with sessions, clusters, and remote files, with a read-only mode available.
- Hide commands typed by KaiTerm for Actions, AI, and desktop MCP from bash and zsh history by default. The first command in a zsh session may still be recorded.
- Encrypt cloud-synced settings on your device before they are uploaded. All features are available to every account.

## Screenshots

### Desktop and Android

<img src="https://kaiterm.dev/resources/screenshots/jvm-01-main-window.png" width="640" alt="KaiTerm desktop connection workspace">
<img src="https://kaiterm.dev/resources/screenshots/android-01-home.png" width="202" alt="KaiTerm Android home screen">

More product views are available in the [KaiTerm gallery](https://kaiterm.dev/#screenshots).

## Security and privacy

- SSH, SFTP, FTP (FTPS), and MySQL over SSH verify the server's host key or certificate. Host key checking can ask, accept new keys, require an existing key, or be disabled.
- Secrets and sync sessions are encrypted in device-local storage. Cloud sync is encrypted on the device before upload.

## License

KaiTerm is proprietary software. All rights reserved. See the [Terms and Software Licence](https://kaiterm.dev/terms.html).

## Support

Questions and bug reports: [support@kaiterm.dev](mailto:support@kaiterm.dev).
