## Novidades da Versão v1.4.0 (Build #44)

Isolamento multi-servidor: limpeza e recarregamento automático das conversas ao alternar entre Windows, Linux e Mac

---

### Aplicativo Mobile (Android APK • Build #44)
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

### Servidor Companion & Workspace (Build #44)
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
| **Android** | `AntigravityMobile-v1.4.0-build44.apk` | 81M | Instalar no dispositivo |
| **Windows** | `antigravity-server-windows-v1.4.0-build44.zip` | 22M | Executar `.\start.ps1` ou `start.bat` |
| **macOS** | `antigravity-server-macos-v1.4.0-build44.zip` | 17M | Executar `./start.sh` |
| **Linux** | `antigravity-server-linux-v1.4.0-build44.zip` | 13M | Executar `./start.sh` |

> [!NOTE]
> Os links fixos de download contínuo (`app-release.apk`, `antigravity-server-windows.zip`, etc.) apontam para estas mesmas compilações oficiais.

---

## Guia de Instalação e Execução

### 1. Dispositivo Móvel (Android)
1. Baixe o instalador oficial `AntigravityMobile-v1.4.0-build44.apk` (ou `app-release.apk`).
2. Se o navegador exibir o aviso de fontes desconhecidas, selecione **"Fazer download mesmo assim"** e autorize a instalação.
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
