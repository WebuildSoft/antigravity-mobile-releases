# ==============================================================================
# CAMPO 1: RELEASE TITLE (Copie e cole no campo "Release title" do GitHub)
# ==============================================================================
Antigravity Mobile & Server v1.4.0 (Build #40) - Multi-Contas Google, Diffs Inteligentes e Telemetria Edge

# ==============================================================================
# CAMPO 2: DESCRIBE THIS RELEASE (Copie e cole no campo "Describe this release")
# ==============================================================================
## Novidades da Versão v1.4.0 (Build #40)

Esta atualização traz suporte completo a **Multi-Contas Google**, motor avançado de **Diffs Inteligentes com realce de sintaxe colorido**, comando de voz com visualizador de ondas dinâmicas, telemetria anônima de inicialização via **Cloudflare Workers** com dashboard em tempo real protegido por login, e melhorias de estabilidade em todas as plataformas.

---

### Aplicativo Mobile (Android APK • Build #40)
* **Gerenciamento Multi-Contas Google:**
  * Suporte nativo para conectar e alternar instantaneamente entre 3+ contas Google.
  * Atualização e exibição em tempo real de limites e cotas de requisições de IA para cada conta.
  * Fluxo de autenticação assistida com captura e renovação de tokens OAuth.
* **Diffs Inteligentes & Code Editor:**
  * Reconstrução precisa da versão base para diffs na visualização de edições sugeridas pela IA.
  * Realce de sintaxe colorido (Syntax Highlighting) com preservação de indentação e espaçamento.
* **Comando de Voz & Áudio:**
  * Reconhecimento contínuo de voz com visualizador de ondas dinâmicas integrado ao botão de envio.
* **Prevenção de Mensagens Duplicadas:**
  * Proteção por debounce (bloqueio de toques múltiplos em sequência rápida).
  * Desativação preventiva do campo de texto e botão de envio enquanto a resposta da IA estiver sendo processada.
  * Deduplicação automática de mensagens por ID no gerenciador de estado.
* **Verificação de Atualização Direta:** Consulta em tempo real via GitHub Releases (`version.json`) com fallback inteligente local.

---

### Servidor Companion & Workspace (Build #40)
* **Telemetria de Inicialização na Nuvem (Edge Analytics):**
  * Despacho assíncrono de pings anônimos de inicialização diretamente para Cloudflare Worker (`https://telemetry.lnki.pro`).
  * Dashboard visual moderno (Dark Mode) protegido por login com contagem de servidores únicos, ativos 24h e geolocalização.
  * Ativação padrão de mercado (opt-out configurável via `.env` ou flag `--no-telemetry`).
* **Instaladores Inteligentes:**
  * Novo instalador do Windows (`install.ps1`) com função nativa `Safe-Download` em .NET (imune a falhas de aspas no curl).
  * Visual renovado e minimalista no Windows e macOS/Linux (caixa ciano, checklist elegante `●`, zero emojis soltos).
* **Sincronização de Conversas:**
  * Mapeamento retroativo de sessões locais e preservação de histórico por usuário logado.
  * Isolamento de diretórios contra Directory Traversal e normalização de caminhos com til (`~`).
* **Binários Nativos Otimizados:**
  * Compilação em Go puro com suporte Universal no macOS (Apple Silicon M1/M2/M3 e Intel x86_64), Linux (amd64/arm64) e Windows (amd64).

---

### Download dos Pacotes da Release

| Plataforma | Pacote Versionado | Tamanho | Inicialização |
| :--- | :--- | :---: | :--- |
| **Android** | `AntigravityMobile-v1.4.0-build40.apk` | 77 MB | Instalar no dispositivo |
| **Windows** | `antigravity-server-windows-v1.4.0-build40.zip` | 13 MB | Executar `.\start.ps1` ou `start.bat` |
| **macOS** | `antigravity-server-macos-v1.4.0-build40.zip` | 17 MB | Executar `./start.sh` |
| **Linux** | `antigravity-server-linux-v1.4.0-build40.zip` | 12 MB | Executar `./start.sh` |

> [!NOTE]
> Os links fixos de redirecionamento (`app-release.apk`, `antigravity-server-windows.zip`, `antigravity-server-macos.zip`, `antigravity-server-linux.zip`) apontam diretamente para estas mesmas compilações estáveis oficiais.

---

## Guia de Instalação e Execução

### 1. Dispositivo Móvel (Android)
1. Baixe o instalador `AntigravityMobile-v1.4.0-build40.apk`.
2. Se solicitado pelo sistema operacional, confirme **"Fazer download mesmo assim"** e habilite a permissão de instalação nas opções de segurança do navegador.
3. Abra o aplicativo:
   - Usuário existente: realize login com seu e-mail e senha.
   - Novo usuário: toque em **"Criar Conta"** para cadastrar seu perfil de acesso.

### 2. Servidor Companion (Computador)

#### Windows (PowerShell)
Execute o script de automação:
```powershell
irm https://raw.githubusercontent.com/WebuildSoft/antigravity-server/main/install.ps1 | iex
```
*Alternativa manual via arquivo ZIP:* Extraia `antigravity-server-windows-v1.4.0-build40.zip` e execute `.\start.ps1` (ou clique em `start.bat`).

#### macOS e Linux (Terminal)
Execute o script oficial:
```bash
curl -sSL https://raw.githubusercontent.com/WebuildSoft/antigravity-server/main/install.sh | bash
```
*Alternativa manual via arquivo ZIP:* Extraia `antigravity-server-macos-v1.4.0-build40.zip` e execute `./start.sh`.

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
