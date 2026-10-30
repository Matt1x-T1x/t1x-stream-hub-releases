# T1x Stream Hub privacy

🇧🇷 [Versão em português](PRIVACIDADE.md)

This document describes how the current Beta version works. It does not claim any privacy certification or audit for the app.

## Everything runs on your PC

The Hub opens a local server on `127.0.0.1` only (not reachable from the network) and talks to OBS on the same computer through the WebSocket. There is no account, sign-up, telemetry, usage analytics or Hub server on the internet.

## Microphone and voice

The microphone is only used when you click **Ligar motor de voz** (turn on voice engine). Audio is processed in memory on your PC and sent to the output device you chose (for example, the virtual cable that goes to OBS). The Hub does not record audio to disk and does not send audio off the computer.

## Camera

The Hub does not open your camera. The chroma and scene preview is an image requested from OBS (about 2 per second, only while the preview is on) and shown in the app window, without saving it.

## Local data

Stored in `%APPDATA%\T1x Stream Hub` and kept across updates:

- **Credential vault** (`data/vault.enc` + `data/master.key`): passwords and keys you save in the panel, encrypted with AES-256-GCM. Values are never shown again; the panel only shows a masked version.
- **Settings**: OBS source names, hotkeys, pinned guests.
- **Clips**: spreadsheets `data/clips/YYYY-MM-DD.csv` with time, stream/recording timecode and note.
- **Virtual backgrounds**: images in the `backgrounds` folder.

When OBS is on the same PC, the OBS WebSocket password is read from OBS's own configuration at connection time. It is not copied to the vault or shown.

Uninstalling does not delete this folder; delete it manually if you want to remove everything.

## Global hotkeys

For hotkeys to work while a game is focused, a Hub process watches the keyboard and compares each key with the configured combinations. No key is recorded, logged or sent anywhere; keys that are not hotkeys are discarded immediately.

## External connections

- **GitHub:** the installed app reads the public files of this repository to find new versions and download updates. These requests reach GitHub's infrastructure (which receives metadata such as your IP). No login is required.

## Support reports

GitHub issues and comments are public. Remove passwords, stream keys and personal data from screenshots and logs. For vulnerabilities, use the private channel described in [Security](SECURITY.md).
