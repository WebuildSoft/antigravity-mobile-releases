# ==============================================================================
# CAMPO 1: RELEASE TITLE (Copie e cole no campo "Release title" do GitHub)
# ==============================================================================
Antigravity Mobile & Server v1.4.0 (Build #40)

# ==============================================================================
# CAMPO 2: DESCRIBE THIS RELEASE (Copie e cole no campo "Describe this release")
# ==============================================================================
## Novidades da Versão v1.4.0 (Build #40)

Ativar telemetria anônima padrão de mercado com opt-out e Safe-Download nativo

---

### Download dos Pacotes da Release

| Plataforma | Pacote Versionado | Tamanho | Inicialização |
| :--- | :--- | :---: | :--- |
| **Android** | `AntigravityMobile-v1.4.0-build40.apk` | 81M | Instalar no dispositivo |
| **Windows** | `antigravity-server-windows.zip` | 13M | Executar `.\start.ps1` ou `start.bat` |
| **macOS** | `antigravity-server-macos.zip` | 17M | Executar `./start.sh` |
| **Linux** | `antigravity-server-linux.zip` | 13M | Executar `./start.sh` |

---

## Guia de Instalação e Execução

### 1. Dispositivo Móvel (Android)
Baixe o instalador oficial `AntigravityMobile-v1.4.0-build40.apk` (ou `app-release.apk`) e aponte a câmera para o QR Code gerado pelo servidor.

### 2. Servidor Companion (Computador)

#### Windows (PowerShell)
```powershell
irm https://raw.githubusercontent.com/WebuildSoft/antigravity-server/main/install.ps1 | iex
```

#### macOS e Linux (Terminal)
```bash
curl -sSL https://raw.githubusercontent.com/WebuildSoft/antigravity-server/main/install.sh | bash
```
