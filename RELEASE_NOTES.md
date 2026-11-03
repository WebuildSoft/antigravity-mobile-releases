## Novidades da Versão v1.4.1 (Build #49)

Ícones adaptativos com fundo transparente no Android e refinamento do seletor de modelos de IA no chat.

---

### Aplicativo Mobile (Android APK • Build #49)
* **Ícones Adaptativos Nativos (Android):** Suporte completo ao padrão Adaptive Icons com fundo transparente e alta resolução, eliminando bordas brancas e garantindo presença marcante na tela inicial.
* **Seletor de Modelos Dinâmico:** Correção na sensibilidade do toque do seletor de IA, abertura ágil em bottom sheet com altura ajustável e pré-carregamento dos modelos disponíveis.
* **Sincronização em Tempo Real:** Atualização imediata do modelo ativo via WebSocket, eliminando atrasos ou inconsistências na troca de contexto do chat.

---

### Servidor Companion & Workspace (Build #49)
* **Estabilidade & Conexão:** Otimizações contínuas de canais WebSocket e garantia de entrega imediata de mensagens de controle.

---

### Download dos Pacotes da Release

| Plataforma | Pacote Versionado | Tamanho | Inicialização |
| :--- | :--- | :---: | :--- |
| **Android** | `AntigravityMobile-v1.4.1-build49.apk` | 81M | Instalar no dispositivo |
| **Windows** | `antigravity-server-windows-v1.4.1-build49.zip` | 22M | Executar `.\start.ps1` ou `start.bat` |
| **macOS** | `antigravity-server-macos-v1.4.1-build49.zip` | 18M | Executar `./start.sh` |
| **Linux** | `antigravity-server-linux-v1.4.1-build49.zip` | 13M | Executar `./start.sh` |

> [!NOTE]
> Os links fixos de download contínuo (`app-release.apk`, `antigravity-server-windows.zip`, etc.) apontam para estas mesmas compilações oficiais.

---

## Guia de Instalação e Execução

### 1. Dispositivo Móvel (Android)
1. Baixe o instalador oficial `AntigravityMobile-v1.4.1-build49.apk` (ou `app-release.apk`).
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
