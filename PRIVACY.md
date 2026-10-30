# T1x Stream Hub privacy

🇧🇷 [Versão em português](PRIVACIDADE.md)

This document describes how the current Beta version works. It does not claim any privacy certification or audit for the app.

## Everything runs on your PC

The Hub opens a local server on `127.0.0.1` only (not reachable from the network) and talks to OBS on the same computer through the WebSocket. There is no account, sign-up, telemetry, usage analytics or Hub server on the internet. The only external connections are the ones you turn on (Twitch and YouTube chat) and the update check, described below.

## Microphone and voice

The microphone is only used when you click **Ligar motor de voz** (turn on voice engine). Audio is processed in memory on your PC and sent to the output device you chose (for example, the virtual cable that goes to OBS). The Hub does not record audio to disk and does not send audio off the computer.

## Voice commands (Voice Macros)

Off until you turn them on. While on, the app keeps the microphone open, but audio is only used while you hold the command button: up to 0.4 s before the press stays in memory (so the start of the phrase is not cut) and is continuously discarded. Recognition runs 100% on your PC (Vosk, Portuguese model shipped with the app); nothing is written to disk or sent to the internet. The recognized text is shown in the panel and not saved.

## Soundboard

Sounds live in `%APPDATA%\T1x Stream Hub\sounds`. Files you add are copied into that folder and do not leave the PC.

## Chat and AI Chat Shield

The Shield analyzes messages only on your PC, with local rules (words, links, CAPS, flooding). No message is sent to any AI service. Recent messages are kept in memory only while the app is open.

## Camera

The Hub does not open your camera. The chroma and scene preview is an image requested from OBS (up to 30 per second, only while the preview is on) and shown in the app window, without saving it.

## Local data

Stored in `%APPDATA%\T1x Stream Hub` and kept across updates:

- **Credential vault** (`data/vault.enc` + `data/master.key`): passwords and keys you save in the panel, encrypted with AES-256-GCM. Values are never shown again; the panel only shows a masked version.
- **Settings**: OBS source names, hotkeys, pinned guests.
- **Twitch sign-in**: the access and refresh tokens are kept in the same encrypted vault; **Sair da conta** (sign out) deletes and revokes the token.
- **Chat and Shield**: Twitch channel, YouTube live link, word list and allowed sites (`data/chat.json`, `data/shield.json`).
- **Clips**: spreadsheets `data/clips/YYYY-MM-DD.csv` with time, stream/recording timecode and note.
- **Virtual backgrounds**: images in the `backgrounds` folder.

When OBS is on the same PC, the OBS WebSocket password is read from OBS's own configuration at connection time. It is not copied to the vault or shown.

Uninstalling does not delete this folder; delete it manually if you want to remove everything.

## Global hotkeys

For hotkeys to work while a game is focused, a Hub process watches the keyboard and mouse buttons and compares each key with the configured combinations. No key is recorded, logged or sent anywhere; keys that are not hotkeys are discarded immediately.

## External connections

- **Twitch** (only if you connect the chat): the app connects to Twitch's official chat to read messages from the channel you typed. With **Entrar com a Twitch** (sign in), login happens on Twitch's website (the Hub never sees your password) and the app uses the Twitch API to send messages and moderate when you ask.
- **YouTube** (only if you connect the chat): the app uses Google's YouTube Data API with **your** key to read the chat of the live you chose. The key is only sent to Google.
- **GitHub:** the installed app reads the public files of this repository to find new versions and download updates. These requests reach GitHub's infrastructure (which receives metadata such as your IP). No login is required.

## Support reports

GitHub issues and comments are public. Remove passwords, stream keys and personal data from screenshots and logs. For vulnerabilities, use the private channel described in [Security](SECURITY.md).
