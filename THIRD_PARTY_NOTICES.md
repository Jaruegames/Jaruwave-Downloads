# Avisos de terceiros

Jaruwave inclui software de terceiros. Seus avisos de copyright e textos de licença
continuam aplicáveis aos respectivos componentes; não representam licença geral
para o código original do Jaruwave. Este repositório distribui binários experimentais.

| Componente | Licença / avisos |
| --- | --- |
| Electron 44.7.2 | [MIT](licenses/LICENSE-electron.txt); Chromium e demais componentes têm avisos próprios em [LICENSES.chromium.html](licenses/LICENSES.chromium.html) |
| ws 8.22.0 | MIT, conforme [LICENSE-ws.txt](licenses/LICENSE-ws.txt) |
| RNNoise | BSD de três cláusulas, conforme [COPYING.rnnoise](licenses/COPYING.rnnoise) |
| Integração Jitsi RNNoise/WASM | Apache-2.0, conforme [LICENSE.jitsi](licenses/LICENSE.jitsi) |
| cloudflared oficial | Apache-2.0, conforme [LICENSE-cloudflared.txt](licenses/LICENSE-cloudflared.txt) |

Os textos completos acompanham a pasta [licenses/](licenses/) deste material.
Electron/Chromium incluem outras licenças: não substituir [LICENSES.chromium.html](licenses/LICENSES.chromium.html)
pela tabela resumida acima. Respeitar os avisos e copyrights originais.

No Linux instalado, os avisos ficam em /usr/share/licenses/jaruwave e nos recursos
do aplicativo em /opt/jaruwave. No Windows, acompanham os recursos do aplicativo
instalado, incluindo assets/rnnoise, node_modules/ws e os avisos Electron/Chromium.
Os arquivos já presentes nos instaladores não foram modificados nesta preparação.

As versões cloudflared dos instaladores foram fixadas em cada empacotamento;
o pacote Linux inclui 2026.10.6. Não há download ou instalação de drivers de GPU.
PipeWire, bibliotecas de sistema Linux e componentes do Windows pertencem aos
respectivos sistemas e não são substituídos pelos instaladores.
