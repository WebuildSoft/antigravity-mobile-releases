# ==============================================================================
# CAMPO 1: RELEASE TITLE (Copie e cole no campo "Release title" do GitHub)
# ==============================================================================
Antigravity Mobile & Server v1.4.0 (Build #25) - Rolagem Inteligente no Chat e Suporte Universal de Workspace

# ==============================================================================
# CAMPO 2: DESCRIBE THIS RELEASE (Copie e cole no campo "Describe this release")
# ==============================================================================
## 🚀 Novidades da Versão v1.4.0 (Build #25)

Esta atualização traz melhorias críticas de usabilidade no **Chat do Aplicativo Mobile** e a **resolução universal de workspace** para servidores locais e remotos no **Linux**, **macOS** e **Windows**.

---

### 📱 Aplicativo Mobile (Android APK - Build #25)
* **📜 Rolagem Inteligente (Smart Auto-Scroll):** A tela não puxa mais para baixo à força quando você rola para cima para ler mensagens anteriores enquanto a IA digita.
* **⬇️ Botão Flutuante de Retorno:** Quando você rola para ler o histórico, um botão flutuante surge suavemente para levá-lo de volta à mensagem mais recente com um único toque.
* **🚀 Rolagem Automática ao Enviar:** Toda vez que você envia uma mensagem, o chat desce suavemente até o final da conversa.
* **✨ Redução de Flicker / Piscar:** Otimização na renderização das mensagens durante o streaming em tempo real, eliminando oscilações visuais na tela.
* **🔐 Gerenciamento de Contas:** Carregamento fluido das contas Google conectadas sem travar a interface.

---

### 📁 Servidor & Workspace (Build #25)
* **🌐 Resolução Canônica de Tilde (`~`) Multiplataforma:** Função nativa `ExpandHome` que expande com segurança caminhos iniciados por `~`, `~/` e `~\` de forma agnóstica para qualquer sistema operacional.
* **📂 Correção no Explorer de Projetos:** O servidor agora normaliza o caminho raiz ao receber requisições do aplicativo móvel, eliminando o erro `stat .../~: no such file or directory`.
* **🛡️ Proteção Completa e Chroot/Jail:** Tratamento rigoroso contra Directory Traversal aplicado nas rotas HTTP `/api/workspace/tree`, `/api/workspace/file` e no canal WebSocket.
* **⚡ Binários Nativos Otimizados:** Compilados em Go puro (sem CGO e sem dependência de Node.js) com executável Universal no macOS (Apple Silicon + Intel).

---

### 📦 Arquivos da Release para Download:

| Plataforma | Pacote Versionado | Tamanho | Como Iniciar |
|---|---|:---:|---|
| 📱 **Android** | `AntigravityMobile-v1.4.0-build25.apk` | **73 MB** | Baixar e instalar no celular |
| 🪟 **Windows** | `antigravity-server-windows-v1.4.0-build25.zip` | **13 MB** | 2 cliques em `start-windows.bat` |
| 🍎 **macOS** | `antigravity-server-macos-v1.4.0-build25.zip` | **17 MB** | Executar `./start.sh` no terminal |
| 🐧 **Linux** | `antigravity-server-linux-v1.4.0-build25.zip` | **12 MB** | Executar `./start.sh` no terminal |

> **Nota:** Os links fixos (`app-release.apk`, `antigravity-server-windows.zip`, etc.) apontam sempre para estes arquivos da Build #25.
