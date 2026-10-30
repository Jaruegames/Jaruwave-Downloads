# Jaruwave v0.1.0-alpha.1 — experimental

Primeira distribuição experimental para Windows x64 e CachyOS/Arch Linux x86_64.
Ainda não é uma versão estável nem homologação de todos os dispositivos/redes.

## Arquivos

- Windows: Jaruwave-Setup-0.1.0-x64.exe — 127760620 bytes, versão interna 0.1.0.
- Linux: jaruwave-0.1.0.r22.gcc1b507.local20261030021227-1-x86_64.pkg.tar.zst —
  132242281 bytes, build 0.1.0.r22.gcc1b507.local20261030021227-1.
- install.sh — instalação assistida Arch/CachyOS, com hash fixado e confirmação.
- SHA256SUMS — integridade dos dois instaladores e do script.

Os instaladores originais foram preservados, sem renomear ou recompilar. As versões
internas distintas pertencem à mesma Release v0.1.0-alpha.1.

## Recursos disponíveis

- Voz Opus P2P para até cinco participantes, mute e volumes independentes.
- Transmissão seletiva: cada usuário escolhe uma transmissão para assistir.
- Vídeo e áudio de desktop separados da voz; tela cheia e volumes até 200%.
- Captura de áudio de aplicativos via PipeWire no Linux e WASAPI no Windows,
  com exclusão da reprodução do próprio Jaruwave.
- Configurações de AEC, AGC e redução de ruído Chromium/RNNoise.
- Orçamento de upload de vídeo 8/12/16 Mbps com teto de 4 Mbps por espectador.
- Criar sala com hospedagem automática e confirmação WSS antes da entrada.
- Electron, servidor de sinalização, processamento RNNoise e cloudflared incluídos.

## Instalação e remoção

Baixe os arquivos anexados nesta Release e confira os hashes em **SHA256SUMS**.
SHA-256 verifica integridade; não substitui assinatura digital do editor.

- **Windows:** verifique o EXE com `Get-FileHash .\Jaruwave-Setup-0.1.0-x64.exe -Algorithm SHA256`, compare o
  resultado com SHA256SUMS e abra o instalador. Depois use o menu Iniciar.
  Para remover: Configurações → Aplicativos → Jaruwave → Desinstalar.
- **Arch/CachyOS x86_64:** baixe `install.sh` e `SHA256SUMS` na mesma pasta.
  Execute `sha256sum --check --ignore-missing SHA256SUMS` e confira `install.sh: OK`.
  Revise o script e execute `bash ./install.sh` somente se a verificação passou.
  O script verifica o pacote e pede confirmação antes de `sudo pacman -U`.
  Para remover: `sudo pacman -R jaruwave`.

Não são necessários Node.js, pnpm, Git ou conta GitHub após a publicação. No Linux,
PipeWire, WirePlumber, portal KDE e bibliotecas do sistema continuam necessários;
as dependências são declaradas pelo pacote. Nickname e preferências são preservados
na remoção normal. Não execute o script inteiro como root nem use `curl | bash`.

## Validação e limitações

Os instaladores e o funcionamento básico foram aprovados manualmente. No pacote
CachyOS foram confirmados pacman, terminal/menu KDE, sala com Cloudflare real,
compartilhamento de tela e captura PipeWire. Isso não garante desempenho sustentado
com cinco pessoas, todas as combinações de hardware ou eficácia acústica universal.

Mesh P2P multiplica codificação/upload por espectador. Orçamentos são tetos de
vídeo, excluem overhead e não garantem redução proporcional de CPU. Redes restritas
podem exigir TURN. Endereços de Quick Tunnel são temporários e dependem do serviço.
Compartilhar uma janela pode incluir áudio de outros aplicativos elegíveis.

**Áudio no Windows:** a captura WASAPI exige Windows x64 build **20348 ou superior**
e auxiliar nativo disponível. Windows 10 build 19045 não atende; confira com
`winver`. Não há fallback de captura global. O auxiliar não assinado já foi
bloqueado por políticas de Controle de Aplicativos/Smart App Control. Uma amostra
local funcionou em configuração de teste, sem garantir compatibilidade com outras
políticas nem transmissão real instalada. Se apenas o áudio do desktop falhar,
voz e vídeo são independentes; o próprio aplicativo também está sujeito às
políticas de execução do Windows.

Os componentes próprios e instaladores não são assinados digitalmente. Confira SHA256SUMS; não
altere proteções de segurança para contornar bloqueios. Não há atualizações
automáticas. O repositório é de distribuição e não publica o código-fonte do app.

Enquanto esta Release estiver em draft, seus links públicos não funcionarão.
Leia também os avisos e licenças de terceiros distribuídos com os instaladores.

## Documentação

- [Instalação, requisitos e remoção](https://github.com/Jaruegames/Jaruwave-Downloads/blob/main/INSTALL.md)
- [Guia de uso](https://github.com/Jaruegames/Jaruwave-Downloads/blob/main/README.md)
- [Avisos de terceiros](https://github.com/Jaruegames/Jaruwave-Downloads/blob/main/THIRD_PARTY_NOTICES.md)
- [Licenças completas](https://github.com/Jaruegames/Jaruwave-Downloads/tree/main/licenses)
