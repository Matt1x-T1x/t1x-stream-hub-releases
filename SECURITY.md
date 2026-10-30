# Security and distribution

🇧🇷 [Versão em português](SEGURANCA.md)

## Official channel

Download from https://github.com/mathadoor23/t1x-stream-hub-releases/releases/latest . GitHub hosts the distribution; that does not mean approval, audit or a publisher certificate issued by GitHub.

The installer is built by a GitHub Actions Windows runner from the private source code. Auto-update checks the installer's SHA-512 hash listed in `latest.yml` before installing. There is no own cryptographic signature of the metadata and no Authenticode publisher certificate yet; do not disable antivirus or SmartScreen to get around a block. A tampered file is a reason to stop the installation and report it.

## How the app protects itself

- The local server listens on `127.0.0.1` only and rejects requests with an outside `Host` or `Origin` (protection against DNS rebinding and CSRF). Actions are POST only.
- Saved credentials live in an AES-256-GCM vault and are never shown again; **Streamer Mode** starts on and hides the credentials block.
- The microphone is only allowed for the app's own local panel. Voice commands are recognized in an isolated local process (Vosk), which only receives audio while the button is held.
- Twitch sign-in uses the official device-code flow: the password is only typed on Twitch's website. Tokens stay in the vault and are never shown.
- Chat is rendered as plain text (never as HTML), so messages cannot run code in the panel.
- The global hotkey process runs isolated: if it fails, the Hub stays up.

## Report a vulnerability privately

Use [Report a vulnerability](https://github.com/mathadoor23/t1x-stream-hub-releases/security/advisories/new). This channel is private to the repository owner. Include version, minimal steps to reproduce and observed impact, without credentials or third-party data.

Common usage problems can go to Issues. Do not post exploit details or sensitive data there. There is no bounty program or announced response time.

## Product status

Beta version, with automated tests and tests on a real PC with OBS 33. No security certification is claimed. Keep the app updated.
