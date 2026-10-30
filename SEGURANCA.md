# Segurança e distribuição

🇺🇸 [English version](SECURITY.md)

## Canal oficial

Baixe por https://github.com/mathadoor23/t1x-stream-hub-releases/releases/latest . O GitHub hospeda a distribuição; isso não equivale a aprovação, auditoria ou certificado de editor emitido pelo GitHub.

O instalador é gerado por um runner Windows do GitHub Actions a partir do código-fonte privado. A atualização automática confere o hash SHA-512 do instalador informado no `latest.yml` antes de instalar. Ainda não há assinatura criptográfica própria dos metadados nem certificado Authenticode de editor; não desative antivírus ou SmartScreen para contornar um bloqueio. Uma alteração indevida no arquivo é motivo para interromper a instalação e reportar.

## Como o app se protege

- O servidor local escuta só em `127.0.0.1` e recusa pedidos com `Host` ou `Origin` de fora (proteção contra DNS rebinding e CSRF). Ações só por POST.
- Credenciais salvas ficam num cofre AES-256-GCM e nunca voltam para a tela; o **Modo Streamer** começa ligado e esconde o bloco de credenciais.
- O microfone é liberado só para o painel local do próprio app.
- O processo de atalhos globais roda isolado: se ele falhar, o Hub continua no ar.

## Reportar vulnerabilidade em privado

Use [Report a vulnerability](https://github.com/mathadoor23/t1x-stream-hub-releases/security/advisories/new). Esse canal é privado para o responsável pelo repositório. Informe versão, passos mínimos para reproduzir e impacto observado, sem credenciais ou dados de terceiros.

Problemas comuns de uso podem ir para as Issues. Não publique detalhes de exploração ou dados sensíveis nelas. Não há programa de recompensa ou prazo de resposta anunciado.

## Estado do produto

Versão Beta, com testes automatizados e testes num PC real com OBS 33. Não há declaração de certificação de segurança. Mantenha o aplicativo atualizado.
