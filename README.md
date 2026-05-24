# 🚀 DIO Lab Azure - Guia Completo de Criação de Máquina Virtual

![Azure VM Lab](https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completo-brightgreen?style=for-the-badge)
![Versão](https://img.shields.io/badge/Version-1.0.0-blue?style=for-the-badge)

## 📖 Sobre este Laboratório

Este é um **guia prático e ilustrado** para criar, configurar e conectar uma **Máquina Virtual no Microsoft Azure**. O laboratório faz parte do **BootCamp Java & Cloud Azure** oferecido pela **DIO em parceria com Bradesco**.

A documentação inclui **18 passos detalhados com imagens**, cobrindo todo o processo desde a criação do recurso até a conexão remota bem-sucedida.

---

## 🎯 Objetivos do Laboratório

Ao concluir este laboratório, você será capaz de:

✅ Navegar pelo Portal Azure  
✅ Criar uma Máquina Virtual do zero  
✅ Configurar todos os aspectos da VM (rede, disco, segurança)  
✅ Implementar segurança com autenticação SSH  
✅ Configurar monitoramento e gerenciamento  
✅ Conectar remotamente via SSH  
✅ Resolver problemas de conectividade  
✅ Otimizar configurações para diferentes cenários  

---

## 📋 Pré-requisitos

Antes de começar, você precisa ter:

- ☑️ **Conta Azure ativa** com assinatura válida
- ☑️ **Acesso ao Portal Azure** (https://portal.azure.com)
- ☑️ **Cliente SSH instalado** localmente:
  - Windows: Git Bash, PuTTY ou Windows Terminal
  - Linux/Mac: SSH nativo do terminal
- ☑️ **Permissões de criação de recursos** na assinatura
- ☑️ **Créditos ou orçamento** Azure disponível
- ☑️ **Conhecimento básico** de redes e Linux/Windows

---

## 📚 Estrutura da Documentação

Este repositório contém os seguintes arquivos:

```
Dio-Lab-Azure/
├── README.md                          # 📄 Este arquivo
├── PASSO_A_PASSO_DETALHADO.md        # 📝 Guia detalhado em Markdown
├── Passo_a_Passo_Lab_Azure.html      # 🎬 Apresentação interativa em HTML
├── imagens/                            # 📸 Pasta com todas as imagens
│   ├── 1º Dio-Lab-Azure-Create.jpg
│   ├── 2º Dio-Lab-Azure-Create01.jpg
│   ├── ... (18 imagens no total)
│   └── 18º Dio-Lab-Azure-Conected.jpg
└── [Código e recursos do projeto]
```

---

## 🎓 Como Usar Esta Documentação

### 📱 Opção 1: Apresentação Interativa (Recomendado)
1. Abra o arquivo `Passo_a_Passo_Lab_Azure.html` em seu navegador
2. Use os botões **Anterior** e **Próximo** para navegar
3. As imagens aparecem em tempo real
4. Use as **setas do teclado** (← →) para navegação rápida

**Vantagens:**
- Visual e intuitivo
- Imagens em alta qualidade
- Navegação suave
- Indicadores de progresso

### 📖 Opção 2: Documento Markdown Detalhado
1. Abra `PASSO_A_PASSO_DETALHADO.md` em seu editor favorito (VS Code, GitHub, etc)
2. Use o **índice** para pular para passos específicos
3. Leia as explicações técnicas detalhadas
4. Consulte os **comandos exemplificados**

**Vantagens:**
- Conteúdo textual completo
- Fácil pesquisar por palavras-chave
- Explicitações técnicas profundas
- Código e exemplos

### 📄 Opção 3: Este README
1. Leia este arquivo para uma **visão geral**
2. Consulte seções específicas conforme necessário
3. Use como **referência rápida**

**Vantagens:**
- Resumido e direto
- Bom para revisão rápida
- Checklist e dicas práticas
- Troubleshooting

---

## 🔄 Os 18 Passos - Resumo Visual

### **BLOCO 1: CRIAÇÃO E SELEÇÃO (Passos 1-2)**

#### 1️⃣ Iniciando a Criação de Recurso no Azure
![Passo 1](Docs/imagens/1º%20Dio-Lab-Azure-Create.jpg)

**O que fazer:**
- Acesse https://portal.azure.com
- Clique em **"Criar um recurso"** (Create a resource)
- Você será direcionado ao Marketplace

**Dicas:**
- Certifique-se que a assinatura correta está selecionada (canto superior direito)
- Pode usar a barra de pesquisa para encontrar recursos

---

#### 2️⃣ Seleção de Máquina Virtual
![Passo 2](Docs/imagens/2º%20Dio-Lab-Azure-Create01.jpg)

**O que fazer:**
- Busque por **"Virtual Machine"** ou **"Máquina Virtual"**
- Selecione a opção oficial da Microsoft
- Clique em **"Criar"**

**Dicas:**
- Existem opções de imagens pré-configuradas
- Você pode filtrar por sistema operacional
- Recomendamos Ubuntu 20.04 LTS para iniciantes

---

### **BLOCO 2: CONFIGURAÇÃO BÁSICA (Passos 3-4)**

#### 3️⃣ Configuração Básica - Parte 1
![Passo 3](Docs/imagens/3º%20Dio-Lab-Azure-Create02.jpg)

**Campos a preencher:**

| Campo | Valor Exemplo | Notas |
|-------|---------------|-------|
| **Subscription** | Sua assinatura ativa | Impacta o billing |
| **Resource Group** | rg-dio-vm | Crie novo se necessário |
| **VM Name** | dio-vm-lab | Sem espaços, 1-64 caracteres |
| **Region** | East US | Afeta latência e conformidade |
| **Image** | Ubuntu 20.04 LTS | SO base da máquina |
| **Architecture** | x64 | Padrão para servidores |

**Dicas Importantes:**
```
- Nome único por região
- Região mais próxima = menos latência
- Ubuntu LTS = suporte prolongado
- Selecione a geração mais recente de VM
```

---

#### 4️⃣ Configuração Básica - Parte 2
![Passo 4](Docs/imagens/4º%20Dio-Lab-Azure-Create03.jpg)

**Campos a preencher:**

| Campo | Recomendação | Descrição |
|-------|--------------|-----------|
| **Size** | B1s ou B2s | CPU/RAM apropriado |
| **Authentication** | SSH | Mais seguro que senha |
| **Username** | azureuser | Usuário admin |
| **SSH Public Key** | Gerar novo | Será explicado no Passo 12 |

**Comparação de Tamanhos Populares:**
```
B1s   → 1 vCPU, 1 GB RAM   → $0.01/h (desenvolvimento)
B2s   → 2 vCPU, 4 GB RAM   → $0.05/h (produção pequena)
D2s   → 2 vCPU, 8 GB RAM   → $0.10/h (aplicações maiores)
D4s   → 4 vCPU, 16 GB RAM  → $0.20/h (workloads intensivas)
```

**Dicas de Segurança:**
```
✓ Sempre escolha SSH ao invés de Senha
✓ SSH usa criptografia de chave pública
✓ Senha é susceptível a força bruta
```

---

### **BLOCO 3: ARMAZENAMENTO (Passo 5)**

#### 5️⃣ Configuração de Disco
![Passo 5](Docs/imagens/5º%20Dio-Lab-Azure-Disk.jpg)

**Opções de Disco:**

| Tipo | Performance | Custo | Caso de Uso |
|------|-------------|-------|------------|
| **Premium SSD** | Muito Alto | Alto | Banco de dados, produção |
| **Standard SSD** | Alto | Médio | Servidores web, apps |
| **Standard HDD** | Baixo | Baixo | Backup, teste |

**Configurações Recomendadas:**

```yaml
OS Disk Type: Premium SSD (recomendado)
Disk Size: 30 GB (suficiente para SO + apps)
Encryption: Habilitar (padrão)
Delete with VM: SIM (para economizar)
Disk IOPS: 1100 (Premium padrão)
Throughput: 125 MB/s (Premium padrão)
```

**Dicas de Custo:**
```
- Premium SSD: ~$0.15/GB/mês
- Standard SSD: ~0.08/GB/mês
- Standard HDD: ~0.03/GB/mês
- Múltiplos discos adicionam custo
```

---

### **BLOCO 4: REDE (Passos 6-7)**

#### 6️⃣ Configuração de Rede - Parte 1
![Passo 6](Docs/imagens/6º%20Dio-Lab-Azure-Network.jpg)

**Componentes de Rede:**

```
┌─────────────────────────────────┐
│   Virtual Network (VNet)        │
│   ┌──────────────────────────┐  │
│   │ Subnet-1 (10.0.0.0/24)  │  │
│   │ ┌────────────────────┐  │  │
│   │ │   Sua VM           │  │  │
│   │ │   (10.0.0.4)      │  │  │
│   │ └────────────────────┘  │  │
│   └──────────────────────────┘  │
└─────────────────────────────────┘
```

**Campos a configurar:**

| Campo | Descrição |
|-------|-----------|
| **Virtual Network** | Crie nova (ex: vnet-dio) ou use existente |
| **Subnet** | Segmentação da rede (ex: 10.0.0.0/24) |
| **Public IP** | Necessário para acesso SSH da internet |
| **Network Security Group** | Firewall da VM |

**Configuração Sugerida:**
```
VNet: vnet-dio (10.0.0.0/16)
Subnet: default (10.0.0.0/24)
Public IP: Create new → pip-dio-vm
NSG: Create new → nsg-dio-vm
```

**⚠️ Importante:**
```
SEM IP PÚBLICO = Sem acesso remoto via SSH
COM IP PÚBLICO = Acessível da internet (com regras NSG)
```

---

#### 7️⃣ Configuração de Rede - Parte 2
![Passo 7](Docs/imagens/7º%20Dio-Lab-Azure-Network01.jpg)

**Regras de Firewall (NSG):**

```
Porta 22 (SSH)        → ABRIR   (acesso remoto)
Porta 80 (HTTP)       → ABRIR   (web não seguro)
Porta 443 (HTTPS)     → ABRIR   (web seguro)
Porta 3389 (RDP)      → FECHAR  (somente se Windows)
Outras               → FECHAR  (princípio least privilege)
```

**Exemplo de Regra SSH:**
```
Name:               AllowSSH
Source:             Seu IP pessoal (ou * para abrir)
Source Port:        *
Destination:        *
Destination Port:   22
Protocol:           TCP
Action:             Allow
Priority:           100
```

**Dicas de Segurança:**
```
✓ Restrinja SSH apenas ao seu IP (ex: 203.0.113.5/32)
✓ Não abra portas desnecessariamente
✓ Mude SSH para porta não-padrão em produção
✓ Use IP Whitelist quando possível
```

---

### **BLOCO 5: GERENCIAMENTO (Passos 8-9)**

#### 8️⃣ Configuração de Gerenciamento - Parte 1
![Passo 8](Docs/imagens/8º%20Dio-Lab-Azure-Management.jpg)

**Ferramentas de Monitoramento:**

| Ferramenta | O que faz | Obrigatório? |
|-----------|-----------|-------------|
| **Azure Monitor** | Coleta métricas (CPU, RAM, disco) | Recomendado |
| **Log Analytics** | Centraliza logs da VM | Opcional |
| **Update Manager** | Patches automáticos | Recomendado |
| **Boot Diagnostics** | Diagnóstico de inicialização | Recomendado |

**Configuração Sugerida:**
```
✓ Enable Azure Monitor: SIM
✓ Log Analytics Workspace: Criar novo
✓ Azure Update Manager: SIM (updates automáticas)
✓ Boot Diagnostics: SIM (Storage account necessário)
```

**Benefícios:**
```
Monitoramento:
  → Alertas automáticos
  → Gráficos de performance
  → Histórico de métricas

Updates:
  → Patches de segurança automáticas
  → Menos vulnerabilidades
  → Zero downtime em alguns casos
```

---

#### 9️⃣ Configuração de Gerenciamento - Parte 2
![Passo 9](Docs/imagens/9º%20Dio-Lab-Azure-Management01.jpg)

**Gerenciamento Avançado:**

```yaml
Tags:
  environment: development
  project: dio-lab
  cost-center: bootcamp
  owner: seu-nome

Access Control (RBAC):
  Owner: seu email
  Readers: colegas (se desejar)

Policies:
  Apply corporate standards
  Enforce encryption
  Restrict regions
```

**Por que Tags são Importantes:**
```
1. BILLING: Rastrear custos por projeto
2. ORGANIZATION: Filtrar e agrupar VMs
3. AUTOMATION: Scripts baseados em tags
4. COMPLIANCE: Enforçar padrões
```

**Exemplo de RBAC:**
```
Owner        → Controle total
Contributor  → Criar/editar, não deletar
Reader       → Apenas visualizar
Custom Role  → Permissões específicas
```

---

### **BLOCO 6: FERRAMENTAS DE REDE (Passos 10-11)**

#### 🔟 Configuração de NOC - Parte 1
![Passo 10](Docs/imagens/10º%20Dio-Lab-Azure-Noc.jpg)

**Network Operations Center (NOC):**

```
Funções:
├── Monitoramento de Tráfego
├── Análise de Performance
├── Diagnóstico de Conectividade
├── Visualização de Topologia
└── Resolução de Problemas
```

**Recursos Disponíveis:**

| Recurso | Propósito | Quando Usar |
|---------|----------|------------|
| **Network Watcher** | Diagnóstico de rede | Problemas de conectividade |
| **Connection Troubleshoot** | Teste de conectividade | Verificar alcançabilidade |
| **Network Performance Monitor** | Análise de latência | Otimizar performance |
| **Traffic Analytics** | Visualização de fluxo | Entender padrões de tráfego |

**Como Acessar:**
```
Portal Azure → Sua VM → Networking → Network Watcher
```

---

#### 1️⃣1️⃣ Configuração de NOC - Parte 2
![Passo 11](Docs/imagens/11º%20Dio-Lab-Azure-Noc01.jpg)

**Ferramentas Avançadas de Diagnóstico:**

```
Packet Capture:
  → Captura pacotes de rede
  → Analisa com Wireshark
  → Identifica padrões/problemas

NSG Flow Logs:
  → Registra todas conexões
  → Permitidas e bloqueadas
  → Útil para auditoria

Connection Troubleshoot:
  → Teste ponto-a-ponto
  → Identifica gargalos
  → Simula conectividade

IP Flow Verify:
  → Valida regras NSG
  → Mostra por que tráfego é bloqueado
```

**Exemplo de Troubleshooting:**
```
Problema: Não consigo conectar via SSH

Passos:
1. Verificar que NSG permite porta 22
2. Usar "Connection Troubleshoot" para VM → seu IP
3. Executar "IP Flow Verify"
4. Se ainda assim falhar, capturar pacotes e analisar
```

---

### **BLOCO 7: SEGURANÇA (Passo 12)**

#### 1️⃣2️⃣ Criação de Chave SSH
![Passo 12](Docs/imagens/12º%20Dio-Lab-Azure-Create-Key.jpg)

**O que é SSH e por que é importante:**

```
SSH = Secure Shell
  ✓ Criptografia end-to-end
  ✓ Autenticação por chave pública
  ✓ Sem envio de senhas pela rede
  ✓ Padrão de segurança na indústria
```

**Componentes de uma Chave SSH:**

```
┌──────────────────────────────────┐
│   Par de Chaves SSH              │
├──────────────────────────────────┤
│ Chave Pública (Public Key)       │
│ └─ Armazenada na VM              │
│ └─ Pode ser compartilhada        │
│ └─ Arquivo: authorized_keys      │
│                                  │
│ Chave Privada (Private Key)      │
│ └─ Armazenada localmente         │
│ └─ NUNCA compartilhe!            │
│ └─ Arquivo: ~/.ssh/id_rsa.pem    │
└──────────────────────────────────┘
```

**Como Funciona a Autenticação SSH:**

```
Cliente Local          Azure VM
    ↓                      ↓
Tem chave privada → Tem chave pública
    ↓                      ↓
Assina mensagem ← Verifica assinatura
    ↓                      ↓
Acesso Concedido!
```

**Passos para Gerar Chaves (no Passo 12):**

1. **Azure Gera o Par**
   ```bash
   Azure gera:
   - Chave privada (para download)
   - Chave pública (armazenada na VM)
   ```

2. **Você Faz Download**
   ```bash
   Salve em local seguro:
   ~/.ssh/key.pem
   ```

3. **Configure Permissões**
   ```bash
   chmod 600 ~/.ssh/key.pem
   (Apenas você pode ler)
   ```

**Alternativa: Usar PuTTY no Windows**
```
1. Baixe putty.exe e puttygen.exe
2. Converta a chave .pem para formato PuTTY
3. Use PuTTY para conectar (GUI)
```

---

### **BLOCO 8: REVISÃO E CRIAÇÃO (Passos 13-14)**

#### 1️⃣3️⃣ Revisão de Configurações
![Passo 13](Docs/imagens/13º%20Dio-Lab-Azure-Review.jpg)

**Checklist Completo Antes de Criar:**

```
BÁSICO:
☑ Nome da VM definido
☑ Subscription correta
☑ Resource Group criado
☑ Região apropriada
☑ SO selecionado

HARDWARE:
☑ Tamanho da VM adequado
☑ CPU/RAM suficiente
☑ Disco disco grande o suficiente
☑ Tipo de disco selecionado

REDE:
☑ VNet criada ou selecionada
☑ Subnet definida
☑ IP Público alocado
☑ NSG com regras SSH

SEGURANÇA:
☑ SSH habilitado (não senha)
☑ Chaves SSH geradas
☑ Regras NSG apropriadas

GERENCIAMENTO:
☑ Monitoramento ativado
☑ Tags adicionadas
☑ RBAC configurado
☑ Atualizações automáticas ativadas

CUSTOS:
☑ Revisar estimativa mensal
☑ Estar dentro do orçamento
☑ Entender fatores de custo
```

**Estimativa de Custo Típica:**
```
B1s Ubuntu:
  Compute    → $0.01/h = $7.30/mês
  Disco SSD  → ~$2/mês
  IP Público → ~$3/mês (se não for usado)
  ─────────────────────────────────
  Total      → ~$12/mês
```

---

#### 1️⃣4️⃣ Conclusão e Inicialização da VM
![Passo 14](Docs/imagens/14º%20Dio-Lab-Azure-End.jpg)

**O Grande Momento:**

```
1. Clique em "Criar" (Create)
2. Aguarde o Deployment
   └─ Típicamente 2-5 minutos
3. Receba confirmação "Deployment succeeded"
4. Acesse sua VM no Resource Group
```

**O que Acontece nos Bastidores:**

```
Azure está executando:
1. Alocando CPU/RAM para VM
2. Criando disco OS
3. Configurando rede virtual
4. Atribuindo IP público
5. Aplicando regras NSG
6. Instalando SO
7. Configurando SSH
8. Ativando monitoramento
9. Iniciando VM
```

**Se Falhar:**
```
Verifique:
- Quota de vCPU na região
- Permissões da conta
- Assinatura ativa
- Limitações de região
→ Se ainda assim falhar, delete e tente novamente
```

---

### **BLOCO 9: ACESSO E GERENCIAMENTO (Passos 15-16)**

#### 1️⃣5️⃣ Tela Inicial de Gerenciamento da VM
![Passo 15](Docs/imagens/15º%20Dio-Lab-Azure-Initial.jpg)

**O Dashboard Principal:**

```
┌──────────────────────────────────────────────┐
│           PAINEL DA MÁQUINA VIRTUAL          │
├──────────────────────────────────────────────┤
│                                              │
│  Status: ● Running                           │
│  IP Público: 52.170.45.123                   │
│  IP Privado: 10.0.0.4                        │
│  Tamanho: Standard_B1s                       │
│  SO: Ubuntu 20.04 LTS                        │
│                                              │
│  [Iniciar] [Parar] [Reiniciar] [Deletar]   │
│                                              │
├──────────────────────────────────────────────┤
│ Últimas Atividades:                         │
│ ✓ VM criada com sucesso - 14:32              │
│ ✓ Monitoramento iniciado - 14:33             │
│                                              │
└──────────────────────────────────────────────┘
```

**Ações Rápidas Disponíveis:**

| Ação | O que faz | Tempo |
|------|-----------|-------|
| **Start** | Liga a VM | 30-60 seg |
| **Stop** | Desliga mas mantém disco | 30 seg |
| **Restart** | Reinicia o SO | 1-2 min |
| **Delete** | Remove VM (irreversível!) | 1 min |

**⚠️ Importante:**
```
Stop ≠ Delete
- Stop: VM desligada, você ainda paga disco
- Delete: Tudo removido, para cobranças

Para economizar:
- Stop VMs quando não usar
- Delete após experiência completa
```

---

#### 1️⃣6️⃣ Detalhes e Configurações da VM
![Passo 16](Docs/imagens/16º%20Dio-Lab-Azure-Initial01.jpg)

**Seções Exploráveis:**

```
├── Overview (atual)
│   └─ Status, IPs, tamanho, SO
│
├── Activity Log
│   └─ Histórico de mudanças
│
├── Properties
│   └─ ID, zona, subscription
│
├── Compute
│   └─ vCPU, memória, extensions
│
├── Storage
│   └─ Discos, snapshots, imagens
│
├── Networking
│   └─ NICs, IPs, NSG, rotas
│
├── Update Management
│   └─ Updates disponíveis e aplicados
│
├── Backup
│   └─ Política de backup
│
├── Monitoring
│   └─ Alertas, métricas, logs
│
└── Settings
    └─ Gerenciamento, extensões, resgate
```

**Seção de Monitoramento (Importante):**

```
Métricas em Tempo Real:
- CPU Percentage: % uso de CPU
- Network In/Out: bytes entrada/saída
- Disk Read/Write: operações de disco
- Available Memory: RAM disponível

Gráficos:
- Últimas 1 hora, 24 horas, 7 dias
- Média, máximo, mínimo
- Alertas automáticos se exceder limites
```

---

### **BLOCO 10: CONEXÃO REMOTA (Passos 17-18)**

#### 1️⃣7️⃣ Iniciando Conexão SSH
![Passo 17](Docs/imagens/17º%20Dio-Lab-Azure-Conect.jpg)

**Preparação para Conexão:**

**Passo 1: Obter Informações**
```
1. Vá até Dashboard da VM
2. Copie o IP Público (ex: 52.170.45.123)
3. Verifique nome de usuário (ex: azureuser)
4. Localize arquivo de chave privada (ex: key.pem)
```

**Passo 2: Preparar Chave Localmente**
```bash
# Mover chave para ~/.ssh/
mv ~/Downloads/key.pem ~/.ssh/key.pem

# Configurar permissões (IMPORTANTE!)
chmod 600 ~/.ssh/key.pem

# Verificar
ls -la ~/.ssh/key.pem
# Deve mostrar: -rw------- (600)
```

**Passo 3: Testar Conectividade**
```bash
# Verificar que consegue fazer ping
ping 52.170.45.123

# Verificar que porta 22 está aberta
nc -zv 52.170.45.123 22
```

**Passo 4: Comando SSH Final**
```bash
ssh -i ~/.ssh/key.pem azureuser@52.170.45.123
```

**Breakdown do Comando:**
```
ssh              → Protocolo Secure Shell
-i               → Indica arquivo de chave privada
~/.ssh/key.pem   → Caminho da chave privada
azureuser        → Nome do usuário
52.170.45.123    → IP público da VM
```

**Primeira Conexão - Aceitar Fingerprint:**
```
The authenticity of host '52.170.45.123' can't be established.
RSA key fingerprint is SHA256:abc123...
Are you sure you want to continue? (yes/no)

→ Digitar: yes
```

---

#### 1️⃣8️⃣ Máquina Virtual Conectada com Sucesso
![Passo 18](Docs/imagens/18º%20Dio-Lab-Azure-Conected.jpg)

**Confirmação de Sucesso:**

```bash
azureuser@dio-vm-lab:~$
```

Você está agora **logado na VM remota**! 🎉

**Próximas Ações:**

**1. Verificar o Sistema**
```bash
# Informações do SO
uname -a
# Output: Linux dio-vm-lab 5.10.0-8-generic #8-Ubuntu SMP x86_64...

# Distribuição específica
cat /etc/os-release
# Output: PRETTY_NAME="Ubuntu 20.04.5 LTS"

# Usuário e permissões
whoami
# Output: azureuser

id
# Output: uid=1000(azureuser) gid=1000(azureuser) groups=1000...
```

**2. Verificar Conectividade**
```bash
# Teste de internet
ping google.com -c 3

# Requisição HTTP
curl -I https://www.microsoft.com

# Traceroute
traceroute 8.8.8.8
```

**3. Verificar Recursos**
```bash
# Memória
free -h
# Output: Mem:   1.0Gi   128Mi   752Mi   50Mi  ...

# Disco
df -h
# Output: Filesystem      Size  Used Avail Use%  Mounted on
#         /dev/sda1        30G  2.5G   26G   9%  /

# CPU
nproc
# Output: 1

# Uptime
uptime
# Output: up 5 minutes, 0 users, load average: 0.00, 0.00, 0.00
```

**4. Gerenciar Pacotes (Ubuntu/Debian)**
```bash
# Atualizar lista de pacotes
sudo apt-get update

# Atualizar pacotes instalados
sudo apt-get upgrade -y

# Instalar novo pacote
sudo apt-get install -y curl wget git
```

**5. Instalar Aplicações Comuns**
```bash
# Docker
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

# Node.js
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs

# Java
sudo apt-get install -y openjdk-11-jdk

# Python
sudo apt-get install -y python3 python3-pip
```

**6. Criar Diretórios e Arquivos**
```bash
# Criar pasta de projetos
mkdir -p ~/projetos

# Criar arquivo de teste
echo "Hello from Azure VM" > ~/test.txt

# Listar conteúdo
ls -la ~/
```

**7. Configurar Serviços**
```bash
# Verificar serviços em execução
systemctl status

# Iniciar serviço
sudo systemctl start nginx

# Ativar na inicialização
sudo systemctl enable nginx

# Verificar logs
sudo journalctl -u nginx -f
```

**8. Criar Usuários Adicionais**
```bash
# Adicionar novo usuário
sudo useradd -m -s /bin/bash newuser

# Definir senha
sudo passwd newuser

# Adicionar ao grupo sudo
sudo usermod -aG sudo newuser
```

---

## 🐛 Troubleshooting - Problemas Comuns

### ❌ Problema: "Connection refused" ao conectar SSH

**Causas Possíveis:**
1. VM não está rodando
2. NSG não permite porta 22
3. IP público não está atribuído
4. Firewall local bloqueando

**Soluções:**
```bash
# 1. Verificar status da VM
# → Portal Azure → sua VM → Status deve ser "Running"

# 2. Verificar regras NSG
# → Portal Azure → NSG → Inbound rules
# → Deve ter regra para porta 22 TCP

# 3. Verificar IP Público
# → Portal Azure → sua VM → Overview
# → Deve haver IP Público listado

# 4. Testar se consigo alcançar
ping 52.170.45.123

# 5. Testar porta
nc -zv 52.170.45.123 22
# Esperado: Connection successful
```

---

### ❌ Problema: "Permission denied (publickey)"

**Causas:**
1. Chave privada tem permissões erradas
2. Nome de usuário incorreto
3. Chave privada não corresponde à pública

**Soluções:**
```bash
# 1. Verificar permissões da chave
ls -la ~/.ssh/key.pem
# Deve ser: -rw------- (600)

# 2. Corrigir se necessário
chmod 600 ~/.ssh/key.pem

# 3. Verificar SSH com verbose
ssh -v -i ~/.ssh/key.pem azureuser@52.170.45.123

# 4. Se tudo falhar, gere nova chave no Azure
# → Portal Azure → VM → Reset password/SSH
```

---

### ❌ Problema: VM extremamente lenta

**Causas:**
1. CPU está no máximo
2. Memória insuficiente
3. Disco cheio
4. I/O disk muito alto

**Soluções:**
```bash
# Verificar CPU
top
# Procure por processos com alto uso

# Verificar memória
free -h
# Se 100% utilizada, aumentar tamanho da VM

# Verificar disco
df -h
# Se >90% cheio, aumentar disco ou deletar arquivos

# Verificar I/O
iostat -x 1
# Se muito alto, pode ser problema de disco

# Solução: Redimensionar VM
# → Portal Azure → VM → Size → Select new size
```

---

### ❌ Problema: Não conseguir rodar comandos com `sudo`

**Causa:**
Usuário não está no grupo sudoers

**Solução:**
```bash
# Se conseguir conectar como root:
sudo usermod -aG sudo azureuser

# Depois reconectar
logout
ssh -i ~/.ssh/key.pem azureuser@52.170.45.123
```

---

### ❌ Problema: Não consigo ligar/desligar a VM

**Causa:**
Permissões RBAC insuficientes

**Solução:**
```bash
# Verificar permissão
# → Portal Azure → VM → Access control (IAM)
# → Seu email deve ter papel: Owner ou Contributor
```

---

## 📊 Resumo de Configurações Recomendadas

```yaml
DESENVOLVIMENTO:
  Size: B1s (1 vCPU, 1GB RAM)
  Disk: 30GB Standard SSD
  Network: IP Público + SSH aberto
  Cost: ~$10-15/mês

TESTES/STAGING:
  Size: B2s (2 vCPU, 4GB RAM)
  Disk: 64GB Premium SSD
  Network: IP Público + SSH + HTTP/HTTPS
  Monitoring: Ativado
  Cost: ~$30-50/mês

PRODUÇÃO:
  Size: D2s ou maior (2+ vCPU, 8GB+ RAM)
  Disk: 128GB+ Premium SSD
  Network: Load Balancer + NSG restritivo
  Monitoring: Completo + Alertas
  Backup: Diário
  Redundancy: Múltiplas AZs
  Cost: $50-200+/mês
```

---

## 🎯 Próximos Passos Recomendados

Após completar este laboratório:

### 1. **Explorar Serviços Azure**
- [ ] Azure App Service (deploy de aplicações web)
- [ ] Azure Database (PostgreSQL, MySQL, SQL Server)
- [ ] Azure Kubernetes Service (AKS)
- [ ] Azure Functions (serverless)
- [ ] Azure DevOps (CI/CD)

### 2. **Aprofundar em Segurança**
- [ ] Azure Security Center
- [ ] Key Vault (gerenciar secrets)
- [ ] Azure DDoS Protection
- [ ] Network Security Best Practices

### 3. **Automatização e Infraestrutura**
- [ ] Azure Resource Manager (ARM templates)
- [ ] Terraform/Bicep (Infrastructure as Code)
- [ ] Azure Policy (governança)
- [ ] Automation runbooks

### 4. **Monitoramento e Observabilidade**
- [ ] Application Insights
- [ ] Log Analytics queries (KQL)
- [ ] Custom metrics
- [ ] Distributed tracing

### 5. **Custo e Otimização**
- [ ] Azure Cost Management
- [ ] Reserved Instances (RI)
- [ ] Spot VMs (economia)
- [ ] Right-sizing VMs

---

## 📚 Recursos Adicionais

### Documentação Oficial
- [Azure Virtual Machines](https://learn.microsoft.com/en-us/azure/virtual-machines/)
- [Azure CLI Documentation](https://learn.microsoft.com/en-us/cli/azure/)
- [Azure Best Practices](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/)

### Ferramentas Úteis
- [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) - Gerenciar Azure via terminal
- [Azure Storage Explorer](https://azure.microsoft.com/en-us/products/storage/storage-explorer/) - Gerenciar blobs
- [Azure Data Studio](https://learn.microsoft.com/en-us/sql/azure-data-studio/) - Gerenciar bancos

### Comunidades
- [Microsoft Learn](https://learn.microsoft.com/) - Treinamento oficial
- [Azure Tips and Tricks](https://microsoft.github.io/AzureTipsAndTricks/) - Blog comunitário
- [Stack Overflow (tag: azure)](https://stackoverflow.com/questions/tagged/azure)

---

## 🤝 Contribuições

Encontrou um erro ou quer melhorar este guia? 

1. Faça um fork do repositório
2. Crie uma branch para sua feature
3. Commit suas mudanças
4. Abra um Pull Request

---

## 📝 Licença

Este projeto é parte do BootCamp DIO em parceria com Bradesco e é fornecido para fins educacionais.

---

## 👤 Autor

**Gabriel Sales David**  
BootCamp Java & Cloud Azure - Bradesco/DIO  
Data: 23 de maio de 2026

---

## 🎓 Conclusão

Parabéns por completar este laboratório! 🎉

Você aprendeu:
- ✅ Criar máquinas virtuais no Azure
- ✅ Configurar rede e segurança
- ✅ Gerenciar e monitorar recursos
- ✅ Conectar e administrar VMs remotamente

Estas são **habilidades fundamentais** para qualquer pessoa trabalhando com cloud computing.

**Continue aprendendo e explorando o Azure!** 🚀

---

**Última atualização:** 23 de maio de 2026  
**Versão:** 1.0.0  
**Status:** ✅ Completo
