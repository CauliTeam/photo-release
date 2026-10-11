# Cauli Photo 0.0.1-alpha.1

[简体中文](README.zh-CN.md)

Alpha test release · Build 1

## Source reference

Application source: `release/0.0.1-alpha.1` on the source repository's `main`, commit `b277d6bfcd461250bea7f82a60ec4b5763fda27a`. This repository's `v0.0.1-alpha.1` tag identifies these release notes.

## Downloads

| Platform | Package | Checksum |
| --- | --- | --- |
| macOS · Apple Silicon | [dmg](https://github.com/CloudSir/cauli-photo-release/releases/download/v0.0.1-alpha.1/CauliPhoto_0.0.1-alpha.1_aarch64.dmg) | [SHA-256](https://github.com/CloudSir/cauli-photo-release/releases/download/v0.0.1-alpha.1/CauliPhoto_0.0.1-alpha.1_aarch64.dmg.sha256) |
| Windows · x64 | [exe](https://github.com/CloudSir/cauli-photo-release/releases/download/v0.0.1-alpha.1/CauliPhoto_0.0.1-alpha.1_x64-setup.exe) | [SHA-256](https://github.com/CloudSir/cauli-photo-release/releases/download/v0.0.1-alpha.1/CauliPhoto_0.0.1-alpha.1_x64-setup.exe.sha256) |
| Linux · x64 | [deb](https://github.com/CloudSir/cauli-photo-release/releases/download/v0.0.1-alpha.1/CauliPhoto_0.0.1-alpha.1_amd64.deb) | [SHA-256](https://github.com/CloudSir/cauli-photo-release/releases/download/v0.0.1-alpha.1/CauliPhoto_0.0.1-alpha.1_amd64.deb.sha256) |
| Linux · x64 | [AppImage](https://github.com/CloudSir/cauli-photo-release/releases/download/v0.0.1-alpha.1/CauliPhoto_0.0.1-alpha.1_amd64.AppImage) | [SHA-256](https://github.com/CloudSir/cauli-photo-release/releases/download/v0.0.1-alpha.1/CauliPhoto_0.0.1-alpha.1_amd64.AppImage.sha256) |

## Changes

- Initial public alpha test release for macOS, Windows, and Linux.
- Photo culling with folder scanning, RAW + JPEG grouping, previews, ratings, pick/reject marks, and protection marks.
- Linux AppImage includes GStreamer for video playback.

## Installation

### macOS

Open the DMG, drag **Cauli Photo.app** into **Applications**, then launch the installed app.

This test app is ad-hoc signed and not notarized. If macOS blocks it, verify the download and try **System Settings → Privacy & Security → Open Anyway** after attempting to launch. If it still reports “damaged,” re-download and check the checksum. For a trusted, verified test copy, check its signature before removing quarantine only from this app:

```sh
codesign --verify --deep --strict --verbose=2 '/Applications/Cauli Photo.app'
# Continue only if signature verification succeeds.
xattr -dr com.apple.quarantine '/Applications/Cauli Photo.app'
open '/Applications/Cauli Photo.app'
```

Do not re-sign the app or disable system-wide security checks. Downloaded-app Gatekeeper handling has not been tested in a normal enabled Gatekeeper environment.

A Keychain prompt may appear on first launch or after replacing the app. It protects the local encrypted database key (`app.cauli.photo.desktop` / `application-state-key-v1`). Use your login Keychain password and allow access only for the trusted Cauli Photo app. Prompts may recur; do not delete the key or reset the Keychain to suppress them.

### Windows

Run the installer and launch Cauli Photo. If SmartScreen blocks the trusted, checksum-verified installer, choose **More info → Run anyway** when that option is available. Do not disable Windows security protections; managed policies may prevent installation. Follow the installer if it requests Microsoft WebView2 Runtime. The browser-download SmartScreen path has not been tested.

### Linux

For deb, install from the downloaded file so apt resolves dependencies:

```sh
sudo apt install './CauliPhoto_0.0.1-alpha.1_amd64.deb'
```

For AppImage on Ubuntu 22.04:

```sh
sudo apt install libfuse2 imagemagick libheif1
chmod +x './CauliPhoto_0.0.1-alpha.1_amd64.AppImage'
'./CauliPhoto_0.0.1-alpha.1_amd64.AppImage'
```

## Verification

Download your package and its matching `.sha256` into the same folder.

macOS:

```sh
shasum -a 256 -c 'CauliPhoto_0.0.1-alpha.1_aarch64.dmg.sha256'
```

Linux: use `sha256sum -c '<package filename>.sha256'`. Windows: use `Get-FileHash -Algorithm SHA256 -LiteralPath '<package filename>'` and compare the hash with the first field in the matching `.sha256` file.
