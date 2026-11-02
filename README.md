<div align="center">

<img src="https://raw.githubusercontent.com/WebuildSoft/antigravity-mobile-site/main/icons/Icon-192.png" width="88" height="88" alt="Antigravity Mobile Logo" />

# Antigravity Mobile & Server

Companion mobile client e servidor local de alta performance para o Google Antigravity.

[![Latest Release](https://img.shields.io/github/v/release/WebuildSoft/antigravity-mobile-releases?color=0284c7&style=flat-square)](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest)
[![Platform](https://img.shields.io/badge/platform-Android%20%7C%20Windows%20%7C%20macOS%20%7C%20Linux-334155?style=flat-square)](#download-dos-pacotes-v14.0--build-41)
[![Go Server](https://img.shields.io/badge/server-Go%201.24-00ADD8?style=flat-square&logo=go&logoColor=white)](https://github.com/WebuildSoft/antigravity-server)
[![Flutter](https://img.shields.io/badge/client-Flutter-02569B?style=flat-square&logo=flutter&logoColor=white)](https://github.com/WebuildSoft/antigravity-mobile-releases)
[![Developer](https://img.shields.io/badge/developer-WebuildSoft-0284c7?style=flat-square)](https://github.com/WebuildSoft)

</div>

---

## Download dos Pacotes (v1.4.0 • Build #41)

Os binários compilados estão disponíveis diretamente na aba de [Releases](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest):

| Plataforma | Pacote Versionado | Tamanho | Inicialização |
| :--- | :--- | :---: | :--- |
| **Android** | [`AntigravityMobile-v1.4.0-build41.apk`](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest/download/app-release.apk) | 81M | Instalar no dispositivo |
| **Windows** | [`antigravity-server-windows-v1.4.0-build41.zip`](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest/download/antigravity-server-windows.zip) | 13M | Executar `.\start.ps1` ou `start.bat` |
| **macOS** | [`antigravity-server-macos-v1.4.0-build41.zip`](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest/download/antigravity-server-macos.zip) | 17M | Executar `./start.sh` |
| **Linux** | [`antigravity-server-linux-v1.4.0-build41.zip`](https://github.com/WebuildSoft/antigravity-mobile-releases/releases/latest/download/antigravity-server-linux.zip) | 13M | Executar `./start.sh` |

> [!NOTE]
> Os links fixos (`app-release.apk`, `antigravity-server-windows.zip`, etc.) redirecionam sempre para a compilação estável do release atual.

---

## Arquitetura do Sistema

O ecossistema divide-se em dois módulos complementares:

1. **Cliente Mobile (Android):** Interface nativa em Flutter focada em visualização do raciocínio em tempo real, navegação no explorador de arquivos, edição de código com visualizador de diffs, reconhecimento de voz e alternância rápida entre múltiplas contas Google.
2. **Servidor Companion (Desktop):** Binário em Go puro de alta performance e latência zero que atua como ponte com o Antigravity CLI oficial (`agy`), sincroniza conversas locais no SQLite embarcado e gerencia os canais WebSocket com criptografia TLS via túneis Cloudflare Zero Trust.

> [!IMPORTANT]
> O servidor utiliza a autenticação local do Antigravity CLI já presente na sua máquina de desenvolvimento. As requisições de IA consomem as cotas e permissões da sua conta Google associada.

---

## Guia de Instalação e Execução

### 1. Dispositivo Móvel (Android)
1. Baixe o instalador `AntigravityMobile-v1.4.0-build41.apk` (ou `app-release.apk`).
2. Se o navegador exibir o aviso de instalação de fontes desconhecidas, selecione **"Fazer download mesmo assim"** e autorize o navegador nas opções de segurança do sistema.
3. Abra o aplicativo instalado:
   - Caso já possua conta: faça login com seu e-mail e senha.
   - Caso seja seu primeiro uso: selecione **"Criar Conta"** para cadastrar seu perfil de acesso.

### 2. Servidor Companion (Computador)

#### Windows
Execute o script de automação via PowerShell:
```powershell
irm https://raw.githubusercontent.com/WebuildSoft/antigravity-server/main/install.ps1 | iex
```
*Alternativa manual via arquivo ZIP:*
1. Extraia o pacote `antigravity-server-windows-v1.4.0-build41.zip`.
2. Abra a pasta no PowerShell e inicie o servidor:
   ```powershell
   .\start.ps1
   ```
   *(ou execute o utilitário `start.bat`)*.

#### macOS e Linux
Execute o script oficial via Terminal:
```bash
curl -sSL https://raw.githubusercontent.com/WebuildSoft/antigravity-server/main/install.sh | bash
```
*Alternativa manual via arquivo ZIP:*
1. Extraia o pacote `antigravity-server-macos-v1.4.0-build41.zip` (ou `linux`).
2. Abra a pasta no Terminal e inicie o servidor:
   ```bash
   ./start.sh
   ```

### 3. Pareamento
1. Após a inicialização, o terminal exibirá as rotas locais, a URL de túnel e um código QR em ASCII.
2. No aplicativo móvel, toque em **"Conectar Servidor"** e aponte a câmera para o código no terminal.
3. A conexão será estabelecida automaticamente via WebSocket autenticado.

---

## Diagnóstico e Solução de Problemas

### 1. Alerta de Segurança no Windows (SmartScreen ou Antivírus)
* **Causa:** O binário é uma compilação de código aberto recente e não inclui assinatura digital comercial corporativa da Microsoft. O utilitário `.bat` também utiliza parâmetros de bypass de política de execução, o que ativa heurísticas preventivas.
* **SmartScreen ("O Windows protegeu o seu computador"):**
  1. Clique em **"Mais informações"**.
  2. Selecione **"Executar assim mesmo"**.
* **Arquivo retido pelo antivírus:**
  Acesse *Segurança do Windows > Proteção contra vírus e ameaças > Histórico de proteção* e selecione *Ações > Permitir no dispositivo / Restaurar*.
* **Recomendação técnica:**
  Execute diretamente o script nativo `.\start.ps1` no PowerShell para evitar alertas automáticos associados a arquivos em lote `.bat`:
  ```powershell
  .\start.ps1
  ```

### 2. Autenticação com a Conta Google no Antigravity CLI (`agy`)
> [!WARNING]
> O comando `agy auth login` **não existe** no CLI e resultará em erro de sintaxe (`unexpected argument "auth"`).

* Para autenticar sua conta, execute no terminal da sua máquina:
  ```bash
  agy
  ```
  O utilitário abrirá uma sessão interativa e exibirá o link de autorização OAuth do Google no navegador.
* Para verificar o status da autenticação e validar os modelos disponíveis:
  ```bash
  agy models
  ```
  A listagem de modelos confirma que o ambiente local está apto a receber instruções do aplicativo móvel.

### 3. Bloqueio de Conexão Local por Firewall (Porta 4040)
Caso o dispositivo móvel não consiga se comunicar com o computador através da rede Wi-Fi local:
* **Windows (PowerShell com privilégios de Administrador):**
  ```powershell
  New-NetFirewallRule -DisplayName "Antigravity Server (Porta 4040)" -Direction Inbound -LocalPort 4040 -Protocol TCP -Action Allow
  ```
* **Linux (com firewall UFW ativo):**
  ```bash
  sudo ufw allow 4040/tcp
  ```
* **macOS:**
  Acesse *Ajustes do Sistema > Rede > Firewall* e garanta que o processo `antigravity-server` está habilitado para conexões de entrada.

### 4. Redes com Isolamento de Cliente (AP Isolation) e Conexões Remotas
Em redes corporativas, acadêmicas ou públicas, o roteador pode impedir a comunicação ponto a ponto entre dispositivos na mesma rede local.
* O servidor inicializa automaticamente um Quick Tunnel criptografado via Cloudflare com terminação `.trycloudflare.com`.
* Utilize o código QR correspondente à URL pública para rotear o tráfego de forma transparente mesmo em redes móveis (4G/5G) ou redes com isolamento ativo.

---

<div align="center">

Desenvolvido por WebuildSoft • Todos os direitos reservados © 2026

</div>
