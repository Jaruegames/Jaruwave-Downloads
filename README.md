# Jaruwave — downloads experimentais

Aplicativo desktop simples para conversar por voz e compartilhar tela com amigos.
Este repositório distribui instaladores; não contém o código-fonte do aplicativo.

**v0.1.0-alpha.1 é experimental.** Os instaladores Windows e Linux foram testados
manualmente, mas ainda podem existir falhas e diferenças entre máquinas e redes.
Enquanto a Release estiver em rascunho, os links públicos abaixo não funcionarão.

## Downloads

Acesse [v0.1.0-alpha.1](https://github.com/Jaruegames/Jaruwave-Downloads/releases/tag/v0.1.0-alpha.1).

| Plataforma | Arquivo |
| --- | --- |
| Windows 10/11 x64 | Jaruwave-Setup-0.1.0-x64.exe |
| CachyOS/Arch x86_64 | jaruwave-0.1.0.r22.gcc1b507.local20261030021227-1-x86_64.pkg.tar.zst |
| Instalação assistida Arch/CachyOS | install.sh |
| Integridade dos instaladores e script | SHA256SUMS |

**Versões:** ambos pertencem à Release v0.1.0-alpha.1. A versão interna Windows
permanece 0.1.0; o pacote Linux tem identificador próprio de build
0.1.0.r22.gcc1b507.local20261030021227-1. Os nomes originais foram preservados.

## Instalação rápida

Windows: baixe o EXE, confira o SHA-256 e abra o instalador. Não é necessário Node,
pnpm, Git ou conta GitHub. O instalador não é assinado digitalmente; não desative
proteções do Windows para contornar bloqueios.

Arch/CachyOS x86_64: baixe **install.sh** e **SHA256SUMS** da Release. Na pasta dos
downloads, confira o resultado `install.sh: OK`, revise o script e execute:

```bash
sha256sum --check --ignore-missing SHA256SUMS && bash ./install.sh
```

O script baixa somente o pacote fixado desta Release, verifica seu SHA-256 e pede
confirmação antes de sudo pacman -U. Não desativa verificações de TLS ou do pacman.
No estado draft o download público falhará; o script interrompe sem instalar.

Veja [instalação e remoção detalhadas](INSTALL.md), [notas da versão](RELEASE_NOTES.md)
e [avisos de terceiros](THIRD_PARTY_NOTICES.md). SHA-256 verifica integridade; os
instaladores não têm assinatura digital própria do Jaruwave.

## Limitações importantes no Windows

O áudio de aplicativos exige Windows x64 build **20348 ou superior**; Windows 10
build 19045 não oferece esse recurso. Confira com `winver`. Os componentes próprios
não são assinados e políticas de segurança podem bloquear o aplicativo ou seu
auxiliar de áudio. Já houve bloqueio desse auxiliar em teste. Não desative proteções
para contornar bloqueios. Veja os detalhes e alternativas em [INSTALL.md](INSTALL.md).
Microfone, vídeo e recepção remota são independentes da captura de áudio do desktop.

## Uso

Abra Jaruwave, escolha seu nickname local e clique **Criar sala**. Aguarde a sala
ficar pronta e use **Copiar convite**. Seus amigos colam o convite em **Entrar**,
sem hospedar outro servidor. Servidores externos continuam opcionais.

Voz para até cinco pessoas. Cada pessoa pode transmitir tela; cada espectador
escolhe uma transmissão. Voz e áudio da transmissão têm volumes independentes.
AEC/AGC e redução de ruído Chromium/RNNoise são configuráveis. Não há contas ou chat.

Ao compartilhar uma janela, o áudio compartilhado pode incluir outros aplicativos
elegíveis do desktop, não apenas aquela janela. A captura só começa após ação de
compartilhamento e autorização. Não compartilhe conteúdo pessoal inadvertidamente.
A reprodução do próprio Jaruwave é excluída pelo capturador; eco acústico com caixas
continua dependendo do microfone, ambiente e processamento selecionado.

Electron, processamento de voz e cloudflared vêm incluídos. No Linux, bibliotecas,
PipeWire/WirePlumber e o portal KDE continuam sendo dependências do sistema.
Salas/endereços são temporários. Não compartilhe convites publicamente. P2P pode
precisar de TURN em redes restritivas; hospedagem e TURN externos podem ter custos.
Não há atualizações automáticas.
