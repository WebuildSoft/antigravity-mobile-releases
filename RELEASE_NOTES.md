# ==============================================================================
# CAMPO 1: RELEASE TITLE (Copie e cole no campo "Release title" do GitHub)
# ==============================================================================
Antigravity Mobile & Server v1.4.0 (Build #40) - Multi-Contas, Diffs Inteligentes e Telemetria Edge

# ==============================================================================
# CAMPO 2: DESCRIBE THIS RELEASE (Copie e cole no campo "Describe this release")
# ==============================================================================
## Novidades da Versão v1.4.0 (Build #40)

Esta atualização traz suporte completo a **Multi-Contas Google**, motor avançado de **Diffs Inteligentes com realce de sintaxe**, comando de voz com visualizador de ondas sonoras, telemetria anônima de inicialização via **Cloudflare Workers** com dashboard em tempo real, e estabilidade aprimorada no instalador e nos binários nativos.

---

### Aplicativo Mobile (Android APK • Build #40)
* **Gerenciamento Multi-Contas Google:**
  * Suporte nativo para alternar entre 3+ contas Google com atualização imediata de cotas e limites de IA.
  * Fluxo de autenticação assistida com captura automática de tokens OAuth.
* **Diffs Inteligentes & Code Editor:**
  * Reconstrução precisa da versão base para diffs na visualização de edições sugeridas pela IA.
  * Realce de sintaxe colorido (Syntax Highlighting) com preservação de indentação.
* **Comando de Voz & Áudio:**
  * Reconhecimento contínuo de voz com visualizador de ondas dinâmicas integrado ao botão de envio.
* **Prevenção de Mensagens Duplicadas:**
  * Proteção por debounce (bloqueio de toques múltiplos em sequência rápida).
  * Deduplicação automática de mensagens por ID no gerenciador de estado.
* **Verificação de Atualização Direta:** Consulta em tempo real via GitHub Releases (`version.json`) com fallback local.

---

### Servidor Companion & Workspace (Build #40)
* **Telemetria de Inicialização na Nuvem (Edge Analytics):**
  * Despacho não-bloqueante de pings anônimos de inicialização diretamente para Cloudflare Worker (`https://telemetry.lnki.pro`).
  * Dashboard protegido com métricas de servidores ativos, sistemas operacionais e geolocalização.
* **Instaladores Inteligentes:**
  * Interface limpa de instalação no Windows (`install.ps1`) e macOS/Linux (`install.sh`), com detecção automática de arquitetura e túnel seguro.
* **Sincronização de Conversas:**
  * Mapeamento retroativo de sessões locais e preservação de histórico por usuário logado.
* **Binários Nativos Otimizados:**
  * Compilação Go puro com suporte Universal no macOS (Apple Silicon M1/M2/M3 e Intel x86_64), Linux (amd64/arm64) e Windows (amd64).

---

### Download dos Pacotes da Release

| Plataforma | Pacote Versionado | Tamanho | Inicialização |
| :--- | :--- | :---: | :--- |
| **Android** | `AntigravityMobile-v1.4.0-build40.apk` | 77 MB | Instalar no dispositivo |
| **Windows** | `antigravity-server-windows-v1.4.0-build40.zip` | 13 MB | Executar `.\start.ps1` ou `start.bat` |
| **macOS** | `antigravity-server-macos-v1.4.0-build40.zip` | 17 MB | Executar `./start.sh` |
| **Linux** | `antigravity-server-linux-v1.4.0-build40.zip` | 12 MB | Executar `./start.sh` |

> [!NOTE]
> Os links fixos de download contínuo (`app-release.apk`, `antigravity-server-windows.zip`, `antigravity-server-macos.zip`, `antigravity-server-linux.zip`) apontam diretamente para os binários oficiais da Build #40.

---

## Guia de Instalação e Execução

### 1. Dispositivo Móvel (Android)
1. Baixe o instalador `AntigravityMobile-v1.4.0-build40.apk` (ou `app-release.apk`).
2. Se solicitado pelo sistema operacional, confirme **"Fazer download mesmo assim"** e habilite a permissão de instalação nas opções de segurança do navegador.
3. Abra o aplicativo e conecte-se ao seu servidor apontando a câmera para o QR Code no terminal.

### 2. Servidor Companion (Computador)

#### Windows (PowerShell)
```powershell
irm https://raw.githubusercontent.com/WebuildSoft/antigravity-server/main/install.ps1 | iex
```

#### macOS e Linux (Terminal)
```bash
curl -sSL https://raw.githubusercontent.com/WebuildSoft/antigravity-server/main/install.sh | bash
```
