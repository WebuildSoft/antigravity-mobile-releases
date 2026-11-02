<div align="center">

<img src="https://raw.githubusercontent.com/WebuildSoft/antigravity-mobile-site/main/icons/Icon-192.png" width="88" height="88" alt="Antigravity Mobile Logo" />

# Antigravity Mobile & Server

Companion mobile client e servidor local de alta performance para o Google Antigravity.

[![Latest Release](https://img.shields.io/github/v/release/WebuildSoft/antigravity-mobile-releases?color=0284c7&style=flat-square)](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest)
[![Platform](https://img.shields.io/badge/platform-Android%20%7C%20Windows%20%7C%20macOS%20%7C%20Linux-334155?style=flat-square)](#download-dos-pacotes-v140--build-40)
[![Go Server](https://img.shields.io/badge/server-Go%201.24-00ADD8?style=flat-square&logo=go&logoColor=white)](https://github.com/WebuildSoft/antigravity-server)
[![Flutter](https://img.shields.io/badge/client-Flutter-02569B?style=flat-square&logo=flutter&logoColor=white)](https://github.com/WebuildSoft/antigravity-mobile-releases)
[![Developer](https://img.shields.io/badge/developer-WebuildSoft-0284c7?style=flat-square)](https://github.com/WebuildSoft)

</div>

---

## Download dos Pacotes (v1.4.0 • Build #40)

Os binários compilados estão disponíveis diretamente na aba de [Releases](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest):

| Plataforma | Pacote Versionado | Tamanho | Inicialização |
| :--- | :--- | :---: | :--- |
| **Android** | [`AntigravityMobile-v1.4.0-build40.apk`](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest/download/app-release.apk) | 77 MB | Instalar no dispositivo |
| **Windows** | [`antigravity-server-windows-v1.4.0-build40.zip`](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest/download/antigravity-server-windows.zip) | 13 MB | Executar `.\start.ps1` ou `start.bat` |
| **macOS** | [`antigravity-server-macos-v1.4.0-build40.zip`](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest/download/antigravity-server-macos.zip) | 17 MB | Executar `./start.sh` |
| **Linux** | [`antigravity-server-linux-v1.4.0-build40.zip`](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest/download/antigravity-server-linux.zip) | 12 MB | Executar `./start.sh` |

> [!NOTE]
> Os links fixos (`app-release.apk`, `antigravity-server-windows.zip`, etc.) redirecionam sempre para a compilação estável do release atual.

---

## Arquitetura do Sistema

O ecossistema divide-se em dois módulos complementares:

1. **Cliente Mobile (Android):** Interface nativa em Flutter com suporte a multi-contas Google, reconhecimento de voz contínuo, visualizador de diffs e acompanhamento em tempo real do raciocínio da IA.
2. **Servidor Companion (Desktop):** Binário em Go de baixíssima latência que conecta diretamente ao Antigravity CLI oficial (`agy`), sincroniza conversas SQLite locais e gera túneis seguros Zero Trust.

> [!IMPORTANT]
> O servidor utiliza a autenticação local do Antigravity CLI já presente na sua máquina de desenvolvimento. As requisições de IA consomem as cotas e permissões da sua conta Google associada.

---

## Guia de Instalação e Execução

### 1. Dispositivo Móvel (Android)
1. Baixe o instalador `AntigravityMobile-v1.4.0-build40.apk` (ou `app-release.apk`).
2. Se o navegador exibir o aviso de instalação de fontes desconhecidas, selecione **"Fazer download mesmo assim"** e autorize o navegador nas opções de segurança do sistema.
3. Abra o aplicativo instalado e aponte a câmera para o QR Code gerado pelo servidor companion.

### 2. Servidor Companion (Computador)

#### Windows
Execute o script de automação via PowerShell:
```powershell
irm https://raw.githubusercontent.com/WebuildSoft/antigravity-server/main/install.ps1 | iex
```
*Alternativa manual via arquivo ZIP:*
1. Extraia o pacote `antigravity-server-windows-v1.4.0-build40.zip`.
2. Abra a pasta no PowerShell e inicie o servidor:
   ```powershell
   .\start.ps1
   ```
   *(ou execute o utilitário `start.bat`)*.

#### macOS e Linux
Execute o script oficial via Terminal:
```bash
curl -sSL https://raw.githubusercontent.com/WebuildSoft/antigravity-server/main/install.sh | bash
```
*Alternativa manual via arquivo ZIP:*
1. Extraia o pacote `antigravity-server-macos-v1.4.0-build40.zip` (ou `linux`).
2. Abra a pasta no Terminal e inicie o servidor:
   ```bash
   ./start.sh
   ```

---

## Estrutura dos Arquivos de Configuração

Ao iniciar pela primeira vez, o servidor cria automaticamente os arquivos necessários:

```text
antigravity-server/
├── bin/
│   └── cloudflared           # Binário do Cloudflare Tunnel
├── data/
│   ├── antigravity.db        # Banco de dados local SQLite
│   └── .machine_id           # Identificador anônimo para telemetria
├── uploads/                  # Armazenamento de anexos e imagens
├── .env                      # Variáveis de ambiente
├── start.sh (ou start.ps1)   # Script de inicialização
└── antigravity-server        # Executável compilado
```

---

Desenvolvido por WebuildSoft • Todos os direitos reservados © 2026
