# Privacidade do T1x Stream Hub

Este documento descreve o funcionamento implementado na Beta 0.5.0. Não atribui ao aplicativo certificação ou auditoria de privacidade.

## Tudo roda no seu PC

O Hub abre um servidor local só em `127.0.0.1` (não fica acessível na rede) e conversa com o OBS do mesmo computador pelo WebSocket. Não há conta, cadastro, telemetria, análise de uso nem servidor do Hub na internet.

## Microfone e voz

O microfone só é usado quando você clica em **Ligar motor de voz**. O áudio é processado em memória no próprio PC e enviado ao dispositivo de saída que você escolheu (por exemplo, o cabo virtual que vai para o OBS). O Hub não grava áudio em disco e não envia áudio para fora do computador.

## Câmera

O Hub não abre a sua câmera. A prévia de recorte e de cena é uma imagem pedida ao OBS (cerca de 2 por segundo, só com a prévia ligada) e exibida na janela do app, sem salvar.

## Dados locais

Ficam em `%APPDATA%\T1x Stream Hub` e são preservados nas atualizações:

- **Cofre de credenciais** (`data/vault.enc` + `data/master.key`): senhas e chaves que você salvar no painel, criptografadas com AES-256-GCM. Os valores nunca voltam para a tela; o painel mostra só uma versão mascarada.
- **Configurações**: nomes das fontes do OBS, atalhos, convidados fixados.
- **Clipes**: planilhas `data/clips/AAAA-MM-DD.csv` com horário, tempo da live/gravação e nota.
- **Fundos virtuais**: imagens da pasta `backgrounds`.

A senha do OBS WebSocket, quando o OBS está no mesmo PC, é lida da configuração do próprio OBS no momento da conexão e não é copiada para o cofre nem exibida.

A desinstalação não apaga essa pasta; apague manualmente se quiser remover tudo.

## Atalhos globais

Para os atalhos funcionarem com o jogo em foco, um processo do Hub observa o teclado e compara cada tecla com as combinações configuradas. Nenhuma tecla é gravada, registrada em log ou enviada para fora; teclas que não são atalhos são descartadas na hora.

## Conexões externas

- **GitHub:** o app instalado consulta os arquivos públicos deste repositório para saber se há versão nova e baixa a atualização. Essas requisições chegam à infraestrutura do GitHub (que recebe metadados como IP). Não exigem login.

## Relatos de suporte

Issues e comentários no GitHub são públicos. Remova senhas, chaves de transmissão e dados pessoais de capturas e logs. Para vulnerabilidades, use o canal privado descrito em [Segurança](SEGURANCA.md).
