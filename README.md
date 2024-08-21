# Slender Launcher

A multi-platform application designed for launching compiled tibia clients via remote install to the user's appdata. The launcher allows for making updates without any risk of overriding user settings.

- Windows: `%appdata%/Slender` (`C:\Users\{username}\AppData\Roaming\Slender`)
- MacOS: `~/Library/Application Support/Slender`
- Linux: `~/.config/Slender`

It only installs what's in `client.json` and `asset.json` and only downloads files that need updating instead of a whole package. This makes it very fast and efficient. It also makes it so the client can receive updates without any risk of overriding user settings.

Note that these files are compatible with CIP's `package.json` and `assets.json`. If you're repacking a CIP client, you can use the same files, just rename `package.json` to `client.json`. We renamed it to avoid confusion with the node's `package.json` (used elsewhere in the app).

The launcher itself also updates automatically, so you don't have to worry about it. All you need is to have the URL serving the launcher also have the following files alongside the [client](https://github.com/luan/tibia-client).

- Slender.mac (for MacOS) + Slender.mac.sha256
- Slender.exe (for Windows) + Slender.exe.sha256
- Slender (for Linux) + Slender.sha256

## Features

- [x] Windows
- [x] MacOS
- [x] Linux
- [x] Auto updater
  - [x] Auto updater for the launcher
  - [x] Auto updater for the game client
- [x] Map downloader
- [x] Settings page
  - [x] Enable/disable local client launcher
  - [ ] Enable/disable test client updater
  - [ ] Change game client path
- [ ] Server status
- [ ] News view

## How to use

You'll have to modify some code to make it work for your server. The launcher is not ready to be used for any server, but it's easy to modify it.
Look for baseURL in `main.go` and change it to a URL that can serve your game client. The client needs to be repacked in the correct format, you can use this [client-editor](https://github.com/opentibiabr/client-editor) to do that. Checkout https://github.com/luan/tibia-client for an example packed client.

## Screenshots

<img width="761" alt="image" src="https://github.com/luan/slender-launcher/assets/223760/3a486665-3b4f-440c-acea-70ec9262c188">

<img width="761" alt="image" src="https://github.com/luan/slender-launcher/assets/223760/f49993e4-d107-470e-ae78-5fb68176a180">

<img width="761" alt="image" src="https://github.com/luan/slender-launcher/assets/223760/f18d87d8-cc00-44a8-b4b9-d39123e6bbe9">

<img width="761" alt="image" src="https://github.com/luan/slender-launcher/assets/223760/0a44735c-1f87-4e40-8a82-e80c4c48c041">

<img width="761" alt="image" src="https://github.com/luan/slender-launcher/assets/223760/2ca942ca-88b4-45b6-a0ff-70049f9cc009">

```
launcher
├─ .github
│  └─ workflows
│     └─ release.yml
├─ .gitignore
├─ app.go
├─ build
│  ├─ appicon.png
│  ├─ darwin
│  │  ├─ Info.dev.plist
│  │  └─ Info.plist
│  ├─ linux
│  ├─ README.md
│  └─ windows
│     ├─ icon.ico
│     ├─ info.json
│     ├─ installer
│     │  ├─ project.nsi
│     │  └─ wails_tools.nsh
│     └─ wails.exe.manifest
├─ cmd
│  └─ launcher
│     └─ main.go
├─ docs
│  └─ installation.md
├─ frontend
│  ├─ index.html
│  ├─ package-lock.json
│  ├─ package.json
│  ├─ package.json.md5
│  ├─ README.md
│  ├─ src
│  │  ├─ App.svelte
│  │  ├─ assets
│  │  │  ├─ fonts
│  │  │  │  ├─ nunito-v16-latin-regular.woff2
│  │  │  │  └─ OFL.txt
│  │  │  └─ images
│  │  │     ├─ background-artwork.jpg
│  │  │     └─ logo-universal.png
│  │  ├─ BackIcon.svelte
│  │  ├─ CloseIcon.svelte
│  │  ├─ DownloadIcon.svelte
│  │  ├─ main.ts
│  │  ├─ MainScreen.svelte
│  │  ├─ PlayIcon.svelte
│  │  ├─ Settings.svelte
│  │  ├─ SettingsIcon.svelte
│  │  ├─ style.css
│  │  ├─ UpdateIcon.svelte
│  │  └─ vite-env.d.ts
│  ├─ svelte.config.js
│  ├─ tsconfig.json
│  ├─ tsconfig.node.json
│  └─ vite.config.ts
├─ go.mod
├─ go.sum
├─ internal
│  ├─ config
│  │  └─ config.go
│  ├─ launcher
│  │  └─ launcher.go
│  └─ logging
│     └─ logging.go
├─ main.go
├─ README.md
├─ scripts
│  └─ build.sh
├─ Slender.exe
└─ wails.json

```