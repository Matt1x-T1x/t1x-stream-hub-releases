<p align="center"><img src="assets/icon.png" width="96" alt="T1x Stream Hub"></p>

<h1 align="center">T1x Stream Hub</h1>

<p align="center"><b>Windows x64 · Beta · distribuição oficial / official distribution</b></p>

<p align="center"><a href="#-português">🇧🇷 Português</a> · <a href="#-english">🇺🇸 English</a></p>

<p align="center"><a href="https://github.com/mathadoor23/t1x-stream-hub-releases/releases/latest"><b>⬇ Baixar a versão mais recente · Download the latest version</b></a></p>

![Painel do T1x Stream Hub](assets/painel.jpg)

---

## 🇧🇷 Português

Painel de controle para lives: OBS, voz com efeito, câmera e chroma key, mixer de convidados e marcador de clipes, tudo numa janela só.

### Como instalar

1. Abra [**a versão mais recente**](https://github.com/mathadoor23/t1x-stream-hub-releases/releases/latest), vá em **Assets** e baixe **T1x-Stream-Hub-Setup-VERSAO.exe**. Execute. Ele instala no seu usuário do Windows, sem pedir administrador. Os arquivos `latest.yml`, `.blockmap` e `SHA256SUMS.txt` servem para a atualização automática e para conferência; não é preciso abri-los.
2. Se aparecer "O Windows protegeu o computador" / "editor desconhecido", clique em **Mais informações → Executar assim mesmo**. O app ainda não tem certificado de editor (veja [Segurança ao baixar](#segurança-ao-baixar)).
3. **OBS Studio 28 ou mais novo:** ligue o WebSocket em *Ferramentas → Configurações do Servidor WebSocket → Ativar servidor WebSocket*. Com o OBS no mesmo PC, o Hub conecta sozinho.
4. **Voz com efeito (opcional):** instale o **VB-Audio Virtual Cable**, grátis, pelo site oficial <https://vb-audio.com/Cable/>. Extraia o zip, abra `VBCABLE_Setup_x64.exe` como administrador, clique em **Install Driver** e reinicie o PC. Só é necessário para o T1x Voicer; cenas, câmera, mixer e clipes funcionam sem ele.
5. **Confira o som do Windows** em *Configurações → Sistema → Som*: a **Saída** deve ser o seu fone/caixa e a **Entrada** o seu microfone. O "CABLE" não deve ficar como padrão de nada; o Hub envia a voz para ele sozinho. Se algum app insistir no dispositivo errado: *Painel de Controle → Som*, abas **Reprodução** e **Gravação**, botão direito no dispositivo certo → **Definir como dispositivo padrão**.
6. Abra o Hub, vá em **Conexões & Credenciais → Fontes do OBS** e clique em **Criar o que falta**. Isso cria a fonte da voz no cabo virtual e o fundo virtual atrás da webcam.

Não precisa de Node, Java nem conta GitHub.

### O que tem

| Módulo | O que faz |
|---|---|
| **Controle do OBS** | Cenas, live, gravação e mute do microfone com o estado real do OBS. |
| **T1x Voicer** | Voz com efeito em tempo real (Grave, Esquilo, Robô, Rádio, Caverna), botão **PANIC** e indicador fixo no topo. Se o app fechar ou travar, o OBS volta sozinho para o microfone direto. |
| **Camera & Chroma Key Studio** | Filtro de chroma (similaridade, suavização, spill, opacidade), fundos virtuais e prévia. O filtro nasce desligado. |
| **Mixer de Convidados** | Volume, corte e medidor de cada fonte de áudio do OBS; fixe convidados no topo. |
| **Instant Clip Marker** | Um clique ou atalho grava o momento em planilha, cria capítulo na gravação e salva o Replay Buffer. |
| **Modo Streamer** | Esconde senhas e chaves da tela. Começa ligado. |

**Atalhos globais** (funcionam com o jogo em foco, remapeáveis): `Ctrl+Shift+F1…F6` vozes · `F9` clipe · `F10` mic · `F12` PANIC.

### Atualizações

O app procura versões novas ao abrir e a cada 4 horas. Um ponto dourado no botão de versão, no topo, avisa quando há novidade: clique em **Baixar** e depois em **Instalar e reiniciar** (pede confirmação e fecha o app). Os dados ficam em `%APPDATA%\T1x Stream Hub` e são preservados. O que mudou em cada versão está em [Releases](https://github.com/mathadoor23/t1x-stream-hub-releases/releases).

### Segurança ao baixar

- Use só os downloads deste repositório oficial. Não use executáveis reenviados por terceiros.
- Ainda não há certificado Authenticode de editor. Hospedar no GitHub não certifica que um programa é seguro.
- Não desative antivírus ou SmartScreen. Se o Windows bloquear de vez, pare e reporte.
- Cada versão inclui **SHA256SUMS.txt**. Para conferir o instalador no PowerShell:

```powershell
Get-FileHash -Algorithm SHA256 -LiteralPath '.\T1x-Stream-Hub-Setup-VERSAO.exe'
```

Compare com a linha do `SHA256SUMS.txt` da mesma versão. Hash igual confirma que o arquivo é o publicado; não comprova ausência de malware.

### Privacidade e suporte

Leia [Privacidade](PRIVACIDADE.md) e [Segurança](SEGURANCA.md). Problemas de uso vão nas [Issues](https://github.com/mathadoor23/t1x-stream-hub-releases/issues): informe versão, Windows, passos e mensagem de erro, sem senhas, chaves de transmissão ou dados pessoais.

Versão Beta, testada com o OBS 33 num PC real e com testes automatizados. Este repositório contém só documentação e arquivos de distribuição; o código-fonte não está publicado aqui.

---

## 🇺🇸 English

Control panel for live streams: OBS, voice effects, camera and chroma key, guest mixer and clip marker, all in one window. The app interface is in Portuguese.

### How to install

1. Open [**the latest version**](https://github.com/mathadoor23/t1x-stream-hub-releases/releases/latest), go to **Assets** and download **T1x-Stream-Hub-Setup-VERSION.exe**. Run it. It installs for your Windows user, with no administrator prompt. The `latest.yml`, `.blockmap` and `SHA256SUMS.txt` files are used by auto-update and for verification; you do not need to open them.
2. If Windows shows "Windows protected your PC" / "unknown publisher", click **More info → Run anyway**. The app does not have a publisher certificate yet (see [Download safety](#download-safety)).
3. **OBS Studio 28 or newer:** turn on the WebSocket in *Tools → WebSocket Server Settings → Enable WebSocket server*. When OBS runs on the same PC, the Hub connects automatically.
4. **Voice effects (optional):** install **VB-Audio Virtual Cable**, free, from the official site <https://vb-audio.com/Cable/>. Extract the zip, run `VBCABLE_Setup_x64.exe` as administrator, click **Install Driver** and restart the PC. It is only needed for T1x Voicer; scenes, camera, mixer and clips work without it.
5. **Check Windows sound** in *Settings → System → Sound*: **Output** must be your headset/speakers and **Input** your microphone. "CABLE" must not be the default for anything; the Hub sends the voice to it by itself. If an app keeps using the wrong device: *Control Panel → Sound*, **Playback** and **Recording** tabs, right-click the correct device → **Set as Default Device**.
6. Open the Hub, go to **Conexões & Credenciais → Fontes do OBS** and click **Criar o que falta** ("create what is missing"). This creates the voice source on the virtual cable and the virtual background behind the webcam.

No Node, Java or GitHub account needed.

### Features

| Module | What it does |
|---|---|
| **OBS control** | Scenes, stream, recording and mic mute, with the real OBS state. |
| **T1x Voicer** | Real-time voice effects (Deep, Chipmunk, Robot, Radio, Cave), **PANIC** button and a fixed indicator at the top. If the app closes or freezes, OBS switches back to the direct mic by itself. |
| **Camera & Chroma Key Studio** | Chroma filter (similarity, smoothness, spill, opacity), virtual backgrounds and preview. The filter starts disabled. |
| **Guest Mixer** | Volume, mute and meter for each OBS audio source; pin guests to the top. |
| **Instant Clip Marker** | One click or hotkey logs the moment to a spreadsheet, adds a recording chapter and saves the Replay Buffer. |
| **Streamer Mode** | Hides passwords and keys from the screen. On by default. |

**Global hotkeys** (work while the game is focused, remappable): `Ctrl+Shift+F1…F6` voices · `F9` clip · `F10` mic · `F12` PANIC.

### Updates

The app checks for new versions on start and every 4 hours. A gold dot on the version button at the top tells you: click **Baixar** (download) and then **Instalar e reiniciar** (install and restart; asks for confirmation and closes the app). Data lives in `%APPDATA%\T1x Stream Hub` and is kept. Changes for each version are listed in [Releases](https://github.com/mathadoor23/t1x-stream-hub-releases/releases).

### Download safety

- Only use downloads from this official repository. Do not use executables re-uploaded by others.
- There is no Authenticode publisher certificate yet. Being hosted on GitHub does not certify that a program is safe.
- Do not disable antivirus or SmartScreen. If Windows blocks it outright, stop and report it.
- Every version includes **SHA256SUMS.txt**. To check the installer in PowerShell:

```powershell
Get-FileHash -Algorithm SHA256 -LiteralPath '.\T1x-Stream-Hub-Setup-VERSION.exe'
```

Compare it with the matching line of `SHA256SUMS.txt` for the same version. A matching hash confirms the file is the published one; it does not prove the absence of malware.

### Privacy and support

Read [Privacy](PRIVACY.md) and [Security](SECURITY.md). Usage problems go to [Issues](https://github.com/mathadoor23/t1x-stream-hub-releases/issues): include version, Windows version, steps and error message, without passwords, stream keys or personal data.

Beta version, tested with OBS 33 on a real PC and with automated tests. This repository only holds documentation and distribution files; the source code is not published here.
