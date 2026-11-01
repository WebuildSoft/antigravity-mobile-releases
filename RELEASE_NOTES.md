# ==============================================================================
# CAMPO 1: RELEASE TITLE (Copie e cole no campo "Release title" do GitHub)
# ==============================================================================
Antigravity Mobile & Server v1.4.0 (Build #26) - Correção de Mensagens Duplicadas e Atualização Direta via GitHub

# ==============================================================================
# CAMPO 2: DESCRIBE THIS RELEASE (Copie e cole no campo "Describe this release")
# ==============================================================================
## 🚀 Novidades da Versão v1.4.0 (Build #26)

Esta atualização traz correções essenciais de persistência e estabilidade no **Chat do Aplicativo Mobile**, desduplicação idempotente de histórico e o novo sistema de **atualização direta 100% via GitHub Releases**.

---

### 📱 Aplicativo Mobile (Android APK - Build #26)
* **🚫 Eliminação de Mensagens Duplicadas:** Correção na raiz do problema que exibia a mesma mensagem enviada duas vezes na tela.
* **🛡️ Trava Anti-Duplo Envio (Debounce Guard):** Prevenção automática contra duplo clique acidental no botão de envio.
* **🌐 Atualização Direta pelo GitHub Releases:** Verificação e download de novas versões diretamente pelo GitHub (`antigravity-mobile-releases`) com fallback automático para o servidor local se estiver offline.
* **📜 Rolagem Inteligente & Sem Flicker:** Manutenção da posição de leitura enquanto o agente transmite pensamentos e ferramentas em tempo real.

---

### 📁 Servidor Companheiro (Build #26)
* **🔄 Sincronização Idempotente (`ImportSingleConversationTranscript`):** Evita que a releitura do arquivo de log do Antigravity CLI recrie mensagens com IDs duplicados no SQLite.
* **🧹 Limpeza Automática do Banco de Dados:** Rotina de inicialização que detecta e remove mensagens redundantes mantendo a integridade de todas as `tool_calls`.
* **⚡ Filtro de Entrega em Memória:** Garantia absoluta de que nenhuma mensagem duplicada é enviada aos clientes conectados.
* **🌐 Servidor Web Integrado:** Painel web atualizado com as correções mais recentes compiladas.

---

### 📦 Arquivos da Release para Download:

| Plataforma | Pacote Versionado | Tamanho | Como Iniciar |
|---|---|:---:|---|
| 📱 **Android** | `AntigravityMobile-v1.4.0-build26.apk` | **70 MB** | Baixar e instalar no celular |
| 🪟 **Windows** | `antigravity-server-windows-v1.4.0-build26.zip` | **13 MB** | 2 cliques em `start.bat` ou `.\start.ps1` |
| 🍎 **macOS** | `antigravity-server-macos-v1.4.0-build26.zip` | **17 MB** | Executar `./start.sh` no terminal |
| 🐧 **Linux** | `antigravity-server-linux-v1.4.0-build26.zip` | **12 MB** | Executar `./start.sh` no terminal |

> **Nota:** Os links fixos (`app-release.apk`, `antigravity-server-windows.zip`, etc.) apontam sempre para estes arquivos da Build #26.

---

# 📖 Manual de Instalação, Configuração e Uso

### 🏗️ Como Funciona
O Antigravity Mobile é composto pelo **aplicativo Android** e pelo **servidor companion Go** no seu computador. O servidor faz a ponte direta com o seu **Antigravity CLI oficial (`agy`)** instalado na sua máquina.

> ⚠️ **Conta Google / Antigravity:** O servidor usa as credenciais e cotas da sua conta Google já conectada no seu computador para responder aos comandos de IA.

---

## 🚀 Passo a Passo de Instalação

### 1️⃣ No Celular (Android):
1. Baixe o arquivo **`AntigravityMobile-v1.4.0-build25.apk`** (ou `app-release.apk`).
2. Se o navegador exibir o aviso de segurança do Android, escolha **"Fazer download mesmo assim"**.
3. Abra o arquivo baixado e clique em **Instalar** (ative *"Permitir desta fonte"* se solicitado).
4. Abra o aplicativo:
   - **Já tem cadastro:** Faça login com seu e-mail e senha.
   - **Novo usuário:** Toque em **"Criar Conta"** para registrar seu acesso seguro.

---

### 2️⃣ No Computador (Iniciando o Servidor):

* 🪟 **No Windows:**
  Recomendamos abrir o **PowerShell** e rodar o instalador automático:
  ```powershell
  irm https://raw.githubusercontent.com/WebuildSoft/antigravity-server/main/install.ps1 | iex
  ```
  *(Ou extraia o `.zip`, abra o PowerShell na pasta e execute `.\start.ps1` ou clique em `start.bat`)*

* 🍎 **No Mac ou 🐧 Linux:**
  Abra o **Terminal** e execute:
  ```bash
  curl -sSL https://raw.githubusercontent.com/WebuildSoft/antigravity-server/main/install.sh | bash
  ```

---

### 3️⃣ Conectar e Usar:
1. O terminal do seu computador desenhará um **QR Code**.
2. No app do celular, toque em **Conectar Servidor** e aponte a câmera para o QR Code no terminal.
3. Pronto! O workspace e o chat do Antigravity serão carregados no seu celular.

---

## 🛠️ Resolução de Dúvidas e Problemas Comuns

### 🛡️ 1. O Windows Defender ou Antivírus bloqueou o `start.bat` ou o executável?
* **Motivo:** O servidor é um projeto open source recente e não possui assinatura de certificado comercial pago da Microsoft. Além disso, o arquivo `.bat` usa `-ExecutionPolicy Bypass`, o que aciona o alerta de antivírus.
* **Se aparecer a tela azul do SmartScreen:** Clique em **"Mais informações"** e depois em **"Executar assim mesmo"**.
* **Se o antivírus apagou ou bloqueou o arquivo:** Acesse *Segurança do Windows > Proteção contra vírus e ameaças > Histórico de proteção*, localize o bloqueio e clique em *Ações > Restaurar*.
* **Melhor alternativa para Windows:** Execute o script nativo direto no PowerShell:
  ```powershell
  .\start.ps1
  ```

---

### 🔑 2. Como conectar a conta Google no Antigravity CLI (`agy`)?
> 🛑 **Atenção:** O comando `agy auth login` **não existe** e retornará erro.

* Para conectar ou autorizar sua conta Google, digite no terminal do seu computador:
  ```bash
  agy
  ```
  O Antigravity abrirá e fornecerá a janela/link oficial do Google para autorizar seu acesso no navegador.
* **Como testar se está tudo certo:**
  Digite no terminal:
  ```bash
  agy models
  ```
  Se a lista de modelos de IA for exibida, sua máquina está 100% pronta.

---

### 🧱 3. O celular não conecta no Wi-Fi? (Liberar o Firewall na Porta 4040)
Se o firewall do Windows bloqueou a porta local `4040`, abra o **PowerShell como Administrador** e execute:
```powershell
New-NetFirewallRule -DisplayName "Antigravity Server (Porta 4040)" -Direction Inbound -LocalPort 4040 -Protocol TCP -Action Allow
```
*(No Linux com UFW ativo: `sudo ufw allow 4040/tcp`)*.

---

### 🌐 4. Usando fora de casa ou em Wi-Fi de Faculdade/Empresa (Túnel Cloudflare)
Se você estiver no 4G/5G ou em redes com **Isolamento de AP** (onde o roteador impede dispositivos de se comunicarem diretamente):
- O servidor gera automaticamente uma URL de túnel seguro com final `.trycloudflare.com`.
- Basta escanear o QR Code de túnel no celular para se conectar de qualquer lugar do mundo.
