# ==============================================================================
# CAMPO 1: RELEASE TITLE (Copie e cole no campo "Release title" do GitHub)
# ==============================================================================
Antigravity Mobile v1.4.0 (Build #24) - Suporte Windows, Linux, macOS e Isolamento Multi-Usuário

# ==============================================================================
# CAMPO 2: DESCRIBE THIS RELEASE (Copie e cole no campo "Describe this release")
# ==============================================================================
## 🚀 Novidades da Versão v1.4.0 (Build #24)

Esta atualização traz melhorias críticas de isolamento de sessão, correções na navegação de arquivos e expansão do suporte a servidores locais com executáveis dedicados de alta performance para **Windows**, **macOS** e **Linux**.

---

### 📱 Aplicativo Mobile (Android APK - Build #24)
* **🔒 Isolamento Total de Sessão por Conta:** Configurações de servidor, limites e histórico agora são isolados por UID. Ao deslogar, todos os dados locais da conta anterior são completamente limpos da memória e do armazenamento local.
* **📂 Correção no Explorer de Projetos:** Inclusão de tokens de autenticação Bearer em todas as requisições da árvore de diretórios e leitura de código, eliminando erros de autorização (HTTP 401/403).
* **⚡ Estabilidade na Tela de Limites & Cotas:** Corrigido o carregamento infinito na visualização de consumo quando desconectado do servidor.
* **📷 Pareamento Rápido via QR Code:** Conexão instantânea via câmera apontando para o servidor local ou online.

---

### 🖥️ Servidores Locais Autônomos (Multi-Plataforma)

Todos os pacotes de servidor incluem o **binário nativo compilado em Go (sem necessidade de Node.js)**, a interface web do app e scripts inteligentes de inicialização:

| Plataforma | Pacote ZIP Versionado | Tamanho | Como Iniciar |
|---|---|:---:|---|
| 🪟 **Windows** | `antigravity-server-windows-v1.4.0-build24.zip` | **12 MB** | 2 cliques em `start-windows.bat` |
| 🍎 **macOS** | `antigravity-server-macos-v1.4.0-build24.zip` | **12 MB** | Executar `./start.sh` no terminal |
| 🐧 **Linux** | `antigravity-server-linux-v1.4.0-build24.zip` | **12 MB** | Executar `./start.sh` no terminal |

> **Nota:** Os links fixos (`antigravity-server-windows.zip`, etc.) continuam funcionando normalmente para quem utiliza downloads automatizados ou redirecionamentos.

---

### 🪟 Destaques Especiais da Versão Windows
* **🛡️ Permissão de Administrador Automática (UAC):** Ao iniciar o `start-windows.bat`, ele solicita autorização visual na tela do Windows ("Deseja permitir?"), garantindo que o terminal nunca mais feche sozinho.
* **🔥 Liberação Automática no Firewall:** Adiciona a regra para a porta `4040` (`profile=any`) silenciosamente, permitindo que seu celular no Wi-Fi conecte sem bloqueios.
* **🧹 Limpeza de Conflitos (Porta & Túnel):** Detecta se outro processo ou instância do Cloudflare ficou presa em segundo plano e libera a conexão automaticamente.
* **💿 Suporte a Instalador Inno Setup:** Script `installer/antigravity_setup.iss` pronto para quem desejar compilar o instalador `Setup.exe`.

---

### ⚡ Como Iniciar / Instalar:

#### No Windows:
1. Baixe e extraia `antigravity-server-windows-v1.4.0-build24.zip`.
2. Dê dois cliques em **`start-windows.bat`** (ou `start-online-windows.bat` para acesso remoto Cloudflare).
3. Clique em **SIM** na permissão do Windows e abra o link exibido no navegador do celular.

#### No Linux e macOS:
```bash
unzip antigravity-server-macos-v1.4.0-build24.zip
./start.sh
```
