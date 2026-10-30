# Instalação, verificação e remoção

Material para v0.1.0-alpha.1. Downloads públicos ficam disponíveis somente após
publicação da Release. Não é necessária conta GitHub depois de publicada.

## Integridade

Baixe os arquivos pela [Release oficial](https://github.com/Jaruegames/Jaruwave-Downloads/releases/tag/v0.1.0-alpha.1).
Hashes aprovados dos instaladores originais:

```text
b15cbf25a5db0aaa3db26d93b8459670e0bbf509c7523858135f1d8eab70afeb  Jaruwave-Setup-0.1.0-x64.exe
608134758c3891d8bda9a5bee165916cdd2a87a35e97d94ca2716a00b1330f23  jaruwave-0.1.0.r22.gcc1b507.local20261030021227-1-x86_64.pkg.tar.zst
```

SHA256SUMS também inclui o script install.sh. Não renomeie arquivos antes da
verificação pelo manifesto. Se algum hash divergir, interrompa e descarte o arquivo.

## Windows 10/11 x64

1. Baixe o EXE. Em PowerShell, na pasta de download:

   ```powershell
   Get-FileHash .\Jaruwave-Setup-0.1.0-x64.exe -Algorithm SHA256
   ```

2. Compare o resultado com o hash acima/SHA256SUMS.
3. Abra o instalador. A instalação NSIS é por usuário; depois abra Jaruwave no
   menu Iniciar. Dependências do aplicativo estão incluídas.
4. Autorize microfone nas configurações de privacidade do Windows quando necessário.

O executável usa versão interna 0.1.0 e não possui assinatura digital do Jaruwave.
SHA-256 confirma integridade, não substitui assinatura ou reputação do editor.
Se o Windows bloquear, não desative SmartScreen ou outras proteções para contornar.
Para remover, use Configurações → Aplicativos → Jaruwave → Desinstalar. O instalador
foi configurado para preservar os dados do perfil na remoção normal.

### Limitações do áudio no Windows

A captura de áudio dos aplicativos usa WASAPI e exige Windows x64 com build
**20348 ou superior** e o auxiliar nativo disponível. Confira o build executando
`winver` pelo menu Iniciar. Windows 11 atende ao requisito de build; Windows 10
com build 19045, por exemplo, não atende. Não há fallback para captura global que
possa retransmitir a voz dos participantes.

Mesmo em um build compatível, políticas de Controle de Aplicativos/Smart App
Control podem bloquear o auxiliar `audio-stream.exe`, que não é assinado. Esse
bloqueio já foi observado. Uma amostra local WASAPI funcionou em uma configuração
de teste, mas isso não comprova funcionamento sob outras políticas nem uma
transmissão real da versão instalada. **Não desative proteções para contornar o
bloqueio.** Se a captura de aplicativos estiver indisponível, o compartilhamento
pode continuar somente com vídeo; microfone, voz e recepção remota são recursos
separados. Isso pressupõe que o próprio aplicativo consiga iniciar.

## CachyOS/Arch x86_64

Requer uma sessão gráfica funcional e sistema atualizado. O pacote declara
bibliotecas GTK/NSS/ALSA, Mesa/Wayland/X11, PipeWire, pipewire-pulse, WirePlumber,
xdg-desktop-portal/xdg-desktop-portal-kde, certificados e fontes. Node, pnpm, Git e
cloudflared separado não são necessários para executar o aplicativo.

### Instalação assistida

Baixe install.sh e SHA256SUMS da Release. Na pasta dos downloads, confira o
script antes de executá-lo como usuário comum:

```bash
sha256sum --check --ignore-missing SHA256SUMS && bash ./install.sh
```

O resultado deve incluir `install.sh: OK`. Revise também o conteúdo do script. curl, bash, coreutils, pacman e sudo precisam estar disponíveis. O script:

- Confere Linux x86_64/família Arch e ferramentas necessárias.
- Baixa o nome exato do pacote desta Release por HTTPS.
- Verifica o hash fixado antes de solicitar qualquer instalação.
- Pede confirmação explícita e então executa sudo pacman -U.
- Interrompe em falha; remove apenas sua própria pasta temporária.

Não use curl | bash. Não execute o script inteiro como root. O pacman ainda pode
pedir confirmação das dependências e da transação. Não há flags para ignorar hash,
assinaturas ou dependências, nem modificações de configuração de segurança.

### Instalação manual

Baixe o pacote e SHA256SUMS na mesma pasta. Confira os arquivos presentes:

```bash
sha256sum --check --ignore-missing SHA256SUMS &&
  sudo pacman -U ./jaruwave-0.1.0.r22.gcc1b507.local20261030021227-1-x86_64.pkg.tar.zst
```

Somente execute pacman se a verificação do pacote tiver passado. O pacote local
não é assinado; não altere políticas do sistema para contornar erros de assinatura.
Depois, abra **Jaruwave** no menu KDE ou execute **jaruwave** no terminal.

O pacote usa versão 0.1.0.r22.gcc1b507.local20261030021227-1; a Release é
v0.1.0-alpha.1. Não é necessário modificar o nome do arquivo ou o identificador.
O aplicativo fica em /opt/jaruwave, com atalho global e comando /usr/bin/jaruwave.

### Atalho de desenvolvimento existente

Um atalho de usuário com identificador io.github.Jaruegames.Jaruwave.desktop tem
prioridade sobre o atalho global do pacote e pode abrir uma cópia de desenvolvimento.
Arquive esse atalho de usuário manualmente se quiser usar o instalado. O script não
remove ou altera atalhos pessoais. /usr/bin/jaruwave seleciona o pacote diretamente.

### Remoção

```bash
sudo pacman -R jaruwave
```

O pacote não remove nickname/preferências do perfil Electron do usuário
(~/.config/Jaruwave ou a localização correspondente a XDG_CONFIG_HOME). Não há
serviço ou inicialização automática para desabilitar. Feche o app antes de trocar
ou remover a instalação. Nenhuma rotina de atualização automática é incluída.

## Primeira sala

**Criar sala** inicia a hospedagem e aguarda confirmação de acesso público WSS.
**Cancelar** interrompe a preparação. **Sair** limpa a hospedagem iniciada por essa
sala; uma hospedagem independente é preservada. Quem recebe convite usa **Entrar**.
Na transmissão, escolha qual participante assistir. Diagnósticos fornece detalhes
locais; revise/redija informações pessoais antes de compartilhar capturas ou logs.
