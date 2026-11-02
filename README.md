<div align="center">

<img src="https://raw.githubusercontent.com/WebuildSoft/antigravity-mobile-site/main/icons/Icon-192.png" width="88" height="88" alt="Antigravity Mobile Logo" />

# Antigravity Mobile & Server

Companion mobile client e servidor local de alta performance para o Google Antigravity.

[![Latest Release](https://img.shields.io/github/v/release/WebuildSoft/antigravity-mobile-releases?color=0284c7&style=flat-square)](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest)
[![Platform](https://img.shields.io/badge/platform-Android%20%7C%20Windows%20%7C%20macOS%20%7C%20Linux-334155?style=flat-square)](#download-dos-pacotes-v14.0--build-40)
[![Go Server](https://img.shields.io/badge/server-Go%201.24-00ADD8?style=flat-square&logo=go&logoColor=white)](https://github.com/WebuildSoft/antigravity-server)
[![Flutter](https://img.shields.io/badge/client-Flutter-02569B?style=flat-square&logo=flutter&logoColor=white)](https://github.com/WebuildSoft/antigravity-mobile-releases)
[![Developer](https://img.shields.io/badge/developer-WebuildSoft-0284c7?style=flat-square)](https://github.com/WebuildSoft)

</div>

---

## Download dos Pacotes (v1.4.0 • Build #40)

Os binários compilados estão disponíveis diretamente na aba de [Releases](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest):

| Plataforma | Pacote Versionado | Tamanho | Inicialização |
| :--- | :--- | :---: | :--- |
| **Android** | [`AntigravityMobile-v1.4.0-build40.apk`](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest/download/app-release.apk) | 81M | Instalar no dispositivo |
| **Windows** | [`antigravity-server-windows.zip`](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest/download/antigravity-server-windows.zip) | 13M | Executar `.\start.ps1` ou `start.bat` |
| **macOS** | [`antigravity-server-macos.zip`](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest/download/antigravity-server-macos.zip) | 17M | Executar `./start.sh` |
| **Linux** | [`antigravity-server-linux.zip`](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest/download/antigravity-server-linux.zip) | 13M | Executar `./start.sh` |

---

## Guia de Instalação e Execução

### 1. Dispositivo Móvel (Android)
1. Baixe o instalador [`app-release.apk`](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest/download/app-release.apk).
2. Se o navegador exibir aviso de segurança, selecione **"Fazer download mesmo assim"** e autorize a instalação.
3. Conecte-se ao seu servidor apontando a câmera para o QR Code gerado no terminal.

### 2. Servidor Companion (Computador)

#### Windows (PowerShell)
```powershell
irm https://raw.githubusercontent.com/WebuildSoft/antigravity-server/main/install.ps1 | iex
```

#### macOS e Linux (Terminal)
```bash
curl -sSL https://raw.githubusercontent.com/WebuildSoft/antigravity-server/main/install.sh | bash
```

---

Desenvolvido por WebuildSoft • Todos os direitos reservados © 2026
