# ==============================================================================
# CAMPO 1: RELEASE TITLE (Copie e cole no campo "Release title" do GitHub)
# ==============================================================================
Antigravity Mobile & Server v1.4.0 (Build #25) - Rolagem Inteligente no Chat e Suporte Universal de Workspace

# ==============================================================================
# CAMPO 2: DESCRIBE THIS RELEASE (Copie e cole no campo "Describe this release")
# ==============================================================================
## Novidades da Versão v1.4.0 (Build #25)

Esta atualização traz melhorias críticas de usabilidade no **Chat do Aplicativo Mobile** e a **resolução universal de workspace** para servidores locais e remotos no **Linux**, **macOS** e **Windows**.

---

### Aplicativo Mobile (Android APK • Build #25)
* **Rolagem Inteligente (Smart Auto-Scroll):** A tela preserva a posição de leitura quando o usuário rola para cima para consultar mensagens anteriores durante a geração de respostas pela IA.
* **Botão Flutuante de Retorno:** Exibição suave de botão de ação para retornar imediatamente à mensagem mais recente com um único toque.
* **Rolagem Automática ao Enviar:** Deslocamento suave até o final da conversa sempre que uma nova mensagem for submetida.
* **Estabilização de Renderização:** Otimização no fluxo de streaming de tokens em tempo real, eliminando oscilações visuais na lista de mensagens.
* **Gerenciamento de Sessão:** Carregamento assíncrono das contas conectadas sem bloqueio da interface gráfica.

---

### Servidor Companion & Workspace (Build #25)
* **Resolução Canônica de Diretório Home (`~`):** Implementação da função `ExpandHome` para tratar caminhos com til (`~`, `~/`, `~\`) de forma consistente entre plataformas.
* **Normalização do Explorador de Projetos:** Correção do mapeamento da raiz do projeto para requisições do cliente móvel, eliminando erros de `stat .../~: no such file or directory`.
* **Segurança e Isolamento de Diretórios:** Validação rigorosa contra Directory Traversal aplicada nos endpoints `/api/workspace/tree`, `/api/workspace/file` e no canal WebSocket.
* **Binários Nativos Otimizados:** Compilação em Go puro (sem runtime CGO) com suporte Universal no macOS (Apple Silicon e Intel).

---

### Download dos Pacotes da Release

| Plataforma | Pacote Versionado | Tamanho | Inicialização |
| :--- | :--- | :---: | :--- |
| **Android** | `AntigravityMobile-v1.4.0-build25.apk` | 73 MB | Instalar no dispositivo |
| **Windows** | `antigravity-server-windows-v1.4.0-build25.zip` | 13 MB | Executar `.\start.ps1` ou `start.bat` |
| **macOS** | `antigravity-server-macos-v1.4.0-build25.zip` | 17 MB | Executar `./start.sh` |
| **Linux** | `antigravity-server-linux-v1.4.0-build25.zip` | 12 MB | Executar `./start.sh` |

> [!NOTE]
> Os links fixos de redirecionamento (`app-release.apk`, `antigravity-server-windows.zip`, etc.) apontam para estes mesmos binários.

---

## Guia de Instalação e Execução

### 1. Dispositivo Móvel (Android)
1. Baixe o instalador `AntigravityMobile-v1.4.0-build25.apk`.
2. Se solicitado pelo sistema operacional, confirme **"Fazer download mesmo assim"** e habilite a permissão de instalação nas opções de segurança do navegador.
3. Abra o aplicativo:
   - Usuário existente: realize login com seu e-mail e senha.
   - Novo usuário: toque em **"Criar Conta"** para cadastrar seu perfil de acesso.

### 2. Servidor Companion (Computador)

#### Windows
Execute o script no **PowerShell**:
```powershell
irm https://raw.githubusercontent.com/WebuildSoft/antigravity-server/main/install.ps1 | iex
```
*Alternativa manual:* Extraia o arquivo `.zip` e execute `.\start.ps1` no PowerShell (ou clique em `start.bat`).

#### macOS e Linux
Execute o script no **Terminal**:
```bash
curl -sSL https://raw.githubusercontent.com/WebuildSoft/antigravity-server/main/install.sh | bash
```

### 3. Pareamento
1. O terminal exibirá um código QR com os endereços de conexão local e remoto.
2. No aplicativo móvel, toque em **"Conectar Servidor"** e aponte a câmera para o terminal.
3. O workspace e as conversas serão carregados automaticamente.

---

## Diagnóstico e Solução de Problemas

### 1. Alerta de Segurança no Windows (SmartScreen ou Antivírus)
* **SmartScreen ("O Windows protegeu o seu computador"):**
  Clique em **"Mais informações"** e selecione **"Executar assim mesmo"**.
* **Arquivo bloqueado pelo antivírus:**
  Acesse *Segurança do Windows > Proteção contra vírus e ameaças > Histórico de proteção* e clique em *Ações > Permitir no dispositivo / Restaurar*.
* **Recomendação técnica:**
  Execute diretamente o script nativo `.\start.ps1` no PowerShell para evitar alertas automáticos associados a arquivos em lote `.bat`.

### 2. Autenticação com a Conta Google no Antigravity CLI (`agy`)
> [!WARNING]
> O comando `agy auth login` **não existe** no CLI e resultará em erro de sintaxe.

* Para autenticar ou renovar credenciais, execute no terminal da sua máquina:
  ```bash
  agy
  ```
  O Antigravity abrirá e fornecerá o link de autorização do Google no navegador.
* Para validar a conectividade e os modelos de IA disponíveis:
  ```bash
  agy models
  ```

### 3. Conexão Local Bloqueada por Firewall (Porta 4040)
Caso o celular não localize o servidor na mesma rede Wi-Fi, abra o **PowerShell como Administrador** e execute:
```powershell
New-NetFirewallRule -DisplayName "Antigravity Server (Porta 4040)" -Direction Inbound -LocalPort 4040 -Protocol TCP -Action Allow
```
*(No Linux com UFW: `sudo ufw allow 4040/tcp`)*.

### 4. Redes Públicas, Corporativas ou Conexão 4G/5G
Se a rede local possuir isolamento de clientes (AP Isolation) ou você estiver fora de casa, o servidor gera automaticamente um Quick Tunnel seguro (`.trycloudflare.com`). Utilize o código QR correspondente à URL pública para conexão direta.
