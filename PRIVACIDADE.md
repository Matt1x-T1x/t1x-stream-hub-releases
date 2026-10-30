# Privacidade do T1x Stream Hub

🇺🇸 [English version](PRIVACY.md)

Este documento descreve o funcionamento implementado na versão Beta atual. Não atribui ao aplicativo certificação ou auditoria de privacidade.

## Tudo roda no seu PC

O Hub abre um servidor local só em `127.0.0.1` (não fica acessível na rede) e conversa com o OBS do mesmo computador pelo WebSocket. Não há conta, cadastro, telemetria, análise de uso nem servidor do Hub na internet. As únicas conexões externas são as que você liga (chat da Twitch e do YouTube) e a verificação de atualizações, descritas abaixo.

## Microfone e voz

O microfone só é usado quando você clica em **Ligar motor de voz**. O áudio é processado em memória no próprio PC e enviado ao dispositivo de saída que você escolheu (por exemplo, o cabo virtual que vai para o OBS). O Hub não grava áudio em disco e não envia áudio para fora do computador.

## Comandos de voz (Voice Macros)

Ficam desligados até você ligar. Com eles ligados, o microfone fica aberto pelo app, mas o áudio só é usado enquanto você segura o botão de comando: até 0,4 s antes do toque fica em memória (para não cortar o começo da frase) e é descartado continuamente. O reconhecimento roda 100% no seu PC (Vosk, modelo em português que vem com o app); nada é gravado em disco nem enviado para a internet. O texto reconhecido aparece no painel e não é salvo.

## Soundboard

Os sons ficam em `%APPDATA%\T1x Stream Hub\sounds`. Os arquivos que você adiciona são copiados para essa pasta e não saem do PC.

## Chat e AI Chat Shield

O Shield analisa as mensagens só no seu PC, com regras locais (palavras, links, CAPS, flood). Nenhuma mensagem é enviada a serviço de IA. As últimas mensagens ficam só na memória enquanto o app está aberto.

## Câmera

O Hub não abre a sua câmera. A prévia de recorte e de cena é uma imagem pedida ao OBS (até 30 por segundo, só com a prévia ligada) e exibida na janela do app, sem salvar.

## Dados locais

Ficam em `%APPDATA%\T1x Stream Hub` e são preservados nas atualizações:

- **Cofre de credenciais** (`data/vault.enc` + `data/master.key`): senhas e chaves que você salvar no painel, criptografadas com AES-256-GCM. Os valores nunca voltam para a tela; o painel mostra só uma versão mascarada.
- **Configurações**: nomes das fontes do OBS, atalhos, convidados fixados.
- **Login da Twitch**: o token de acesso e o de renovação ficam no mesmo cofre criptografado; **Sair da conta** apaga e revoga o token.
- **Chat e Shield**: canal da Twitch, link da live do YouTube, lista de palavras e sites liberados (`data/chat.json`, `data/shield.json`).
- **Clipes**: planilhas `data/clips/AAAA-MM-DD.csv` com horário, tempo da live/gravação e nota.
- **Fundos virtuais**: imagens da pasta `backgrounds`.

A senha do OBS WebSocket, quando o OBS está no mesmo PC, é lida da configuração do próprio OBS no momento da conexão e não é copiada para o cofre nem exibida.

A desinstalação não apaga essa pasta; apague manualmente se quiser remover tudo.

## Atalhos globais

Para os atalhos funcionarem com o jogo em foco, um processo do Hub observa o teclado e os botões do mouse e compara cada tecla com as combinações configuradas. Nenhuma tecla é gravada, registrada em log ou enviada para fora; teclas que não são atalhos são descartadas na hora.

## Conexões externas

- **Twitch** (só se você conectar o chat): o app conecta ao chat oficial da Twitch para ler as mensagens do canal que você digitou. Com **Entrar com a Twitch**, o login é feito no site da Twitch (o Hub não vê sua senha) e o app usa a API da Twitch para enviar mensagens e moderar quando você pede.
- **YouTube** (só se você conectar o chat): o app usa a YouTube Data API do Google com a **sua** chave para ler o chat da live indicada. A chave é enviada só ao Google.
- **GitHub:** o app instalado consulta os arquivos públicos deste repositório para saber se há versão nova e baixa a atualização. Essas requisições chegam à infraestrutura do GitHub (que recebe metadados como IP). Não exigem login.

## Relatos de suporte

Issues e comentários no GitHub são públicos. Remova senhas, chaves de transmissão e dados pessoais de capturas e logs. Para vulnerabilidades, use o canal privado descrito em [Segurança](SEGURANCA.md).
