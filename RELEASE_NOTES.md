# ==============================================================================
# CAMPO 1: RELEASE TITLE (Copie e cole no campo "Release title" do GitHub)
# ==============================================================================
Antigravity Mobile & Server v1.4.0 (Build #25) - Suporte Universal de Workspace (Linux, macOS, Windows)

# ==============================================================================
# CAMPO 2: DESCRIBE THIS RELEASE (Copie e cole no campo "Describe this release")
# ==============================================================================
## 🚀 Novidades da Versão v1.4.0 (Build #25)

Esta atualização traz a **resolução universal de workspace** para servidores locais e remotos, corrigindo em definitivo a navegação na tela de "Arquivos do Projeto" no aplicativo móvel em **Linux**, **macOS** e **Windows**.

---

### 📁 Correções e Melhorias no Servidor (Build #25)
* **🌐 Resolução Canônica de Tilde (`~`) Multiplataforma:** Implementada a função nativa `ExpandHome`, que expande com segurança caminhos iniciados por `~`, `~/` e `~\` de forma agnóstica para qualquer sistema operacional.
* **📂 Correção no Explorer de Projetos:** O servidor agora normaliza o caminho raiz ao receber requisições do aplicativo móvel, eliminando o erro `stat .../~: no such file or directory`.
* **🛡️ Proteção Completa e Chroot/Jail:** Tratamento rigoroso contra Directory Traversal aplicado nas rotas HTTP `/api/workspace/tree`, `/api/workspace/file` e no canal WebSocket.
* **⚡ Binários Nativos Otimizados:** Compilados em Go puro (sem CGO e sem dependência de Node.js) com executável Universal no macOS (suporte nativo a Apple Silicon M1/M2/M3 e processadores Intel).

---

### 🖥️ Servidores Locais Autônomos (Multi-Plataforma)

Todos os pacotes de servidor incluem o **binário nativo compilado em Go**, a interface web do app e scripts inteligentes de inicialização:

| Plataforma | Pacote ZIP Versionado | Tamanho | Como Iniciar |
|---|---|:---:|---|
| 🪟 **Windows** | `antigravity-server-windows-v1.4.0-build25.zip` | **13 MB** | 2 cliques em `start-windows.bat` |
| 🍎 **macOS** | `antigravity-server-macos-v1.4.0-build25.zip` | **17 MB** | Executar `./start.sh` no terminal |
| 🐧 **Linux** | `antigravity-server-linux-v1.4.0-build25.zip` | **12 MB** | Executar `./start.sh` no terminal |
| 📱 **Android** | `AntigravityMobile-v1.4.0-build24.apk` | **70 MB** | Instalar no smartphone |

> **Nota:** Os links fixos (`antigravity-server-windows.zip`, `antigravity-server-macos.zip`, `antigravity-server-linux.zip`) foram atualizados para a Build #25.

---

### ⚡ Como Iniciar / Instalar:

#### No Windows:
1. Baixe e extraia `antigravity-server-windows-v1.4.0-build25.zip`.
2. Dê dois cliques em **`start-windows.bat`** (ou `start-online-windows.bat` para acesso remoto Cloudflare).
3. Abra a tela de arquivos do projeto no celular: ela carregará imediatamente sem erros de caminho.

#### No Linux e macOS:
```bash
unzip antigravity-server-macos-v1.4.0-build25.zip
./start.sh
```
