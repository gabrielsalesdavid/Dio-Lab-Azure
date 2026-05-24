# 🚀 Passo a Passo Completo - Criação de Máquina Virtual no Azure

## Resumo do Laboratório

Este documento descreve todas as etapas realizadas para criar e configurar uma máquina virtual no Microsoft Azure, desde a inicialização até a conexão bem-sucedida.

---

## 📋 Índice de Passos

1. [Iniciando a Criação](#passo-1)
2. [Seleção de Máquina Virtual](#passo-2)
3. [Configuração Básica - Parte 1](#passo-3)
4. [Configuração Básica - Parte 2](#passo-4)
5. [Configuração de Disco](#passo-5)
6. [Configuração de Rede - Parte 1](#passo-6)
7. [Configuração de Rede - Parte 2](#passo-7)
8. [Configuração de Gerenciamento - Parte 1](#passo-8)
9. [Configuração de Gerenciamento - Parte 2](#passo-9)
10. [Configuração de NOC - Parte 1](#passo-10)
11. [Configuração de NOC - Parte 2](#passo-11)
12. [Criação de Chave SSH](#passo-12)
13. [Revisão de Configurações](#passo-13)
14. [Conclusão e Inicialização](#passo-14)
15. [Tela Inicial de Gerenciamento](#passo-15)
16. [Detalhes e Configurações](#passo-16)
17. [Iniciando Conexão SSH](#passo-17)
18. [Máquina Conectada com Sucesso](#passo-18)

---

## <a name="passo-1"></a>✅ PASSO 1: Iniciando a Criação de Recurso no Azure

**O que foi feito:**
- Acesso ao portal Azure
- Clique no botão **"Criar um recurso"** ou **"Create"**
- Redirecionamento para o marketplace de recursos do Azure

**Detalhes técnicos:**
- Portal: https://portal.azure.com
- Local: Seção principal de gerenciamento de assinatura
- Propósito: Iniciar o processo de provisionamento de novos recursos

---

## <a name="passo-2"></a>✅ PASSO 2: Seleção de Máquina Virtual

**O que foi feito:**
- Busca pelo termo **"Máquina Virtual"** ou **"Virtual Machine"**
- Seleção da opção oficial do Azure (Microsoft)
- Confirmação da escolha para prosseguir

**Detalhes técnicos:**
- Tipo de recurso: Compute (Máquinas Virtuais)
- Provedor: Microsoft Azure
- SKU: Virtual Machines (padrão)

---

## <a name="passo-3"></a>✅ PASSO 3: Configuração Básica - Parte 1

**O que foi feito:**
Preenchimento das informações fundamentais da máquina virtual:

| Campo | Descrição |
|-------|-----------|
| **Assinatura** | Seleção da subscription Azure ativa |
| **Grupo de Recursos** | Criação ou seleção de Resource Group |
| **Nome da VM** | Definição de um nome identificador único |
| **Região** | Seleção da localização geográfica (ex: East US, West Europe) |
| **Imagem do SO** | Escolha do sistema operacional (Linux, Windows, etc) |

**Detalhes técnicos:**
- Formato de nome: sem espaços, caracteres especiais limitados
- Região: afeta latência, conformidade regulatória e custos
- Imagem: define o SO base e software pré-instalado

---

## <a name="passo-4"></a>✅ PASSO 4: Configuração Básica - Parte 2

**O que foi feito:**
Continuação da configuração inicial com parâmetros de desempenho e autenticação:

| Campo | Descrição |
|-------|-----------|
| **Tamanho da VM** | Seleção de CPU, memória RAM e recursos (B1s, D2s_v3, etc) |
| **Tipo de Autenticação** | Escolha entre SSH (chave pública) ou Senha |
| **Nome de usuário** | Definição do usuário administrativo |
| **Inicialização rápida** | Opções para configuração automática |

**Detalhes técnicos:**
- Tamanho afeta custo e performance
- SSH é mais seguro que senha
- Usuário padrão varia conforme o SO

---

## <a name="passo-5"></a>✅ PASSO 5: Configuração de Disco

**O que foi feito:**
Configuração de armazenamento e persistência de dados:

| Campo | Descrição |
|-------|-----------|
| **Tipo de Disco** | Premium SSD, Standard SSD, Standard HDD |
| **Tamanho do Disco** | Tamanho em GB (ex: 30GB, 128GB) |
| **Criptografia** | Habilitação de criptografia em repouso |
| **Backup/Snapshot** | Configuração de políticas de backup |

**Detalhes técnicos:**
- Premium SSD: melhor performance, custo maior
- Standard HDD: custo menor, performance menor
- Disco SO mínimo: ~30GB
- Criptografia: padrão com Azure-Managed Keys

---

## <a name="passo-6"></a>✅ PASSO 6: Configuração de Rede - Parte 1

**O que foi feito:**
Configuração de conectividade de rede e isolamento:

| Campo | Descrição |
|-------|-----------|
| **Virtual Network** | Criação ou seleção de VNet (rede virtual) |
| **Subnet** | Seleção de sub-rede para a VM |
| **IP Público** | Alocação de endereço IP público (necessário para acesso remoto) |
| **Grupo de Segurança** | Seleção ou criação de NSG (Firewall) |

**Detalhes técnicos:**
- VNet: rede privada virtual customizável
- Subnet: segmentação da VNet em blocos de IP
- IP Público: necessário para acesso via SSH da internet
- NSG: controla tráfego de entrada e saída

---

## <a name="passo-7"></a>✅ PASSO 7: Configuração de Rede - Parte 2

**O que foi feito:**
Configuração de regras de firewall e conectividade:

| Campo | Descrição |
|-------|-----------|
| **Portas Abertas** | Definição de portas permitidas (22 para SSH, 80 para HTTP, 443 para HTTPS) |
| **Regras de Entrada** | Configuração de Inbound Rules (quem pode acessar) |
| **Conectividade** | Verificação de roteamento e conectividade |
| **Load Balancer** | Configuração de balanceamento de carga (se necessário) |

**Detalhes técnicos:**
- Porta 22: SSH (acesso remoto)
- Porta 80: HTTP (web não criptografado)
- Porta 443: HTTPS (web criptografado)
- NSG rules: especificar origem (source IP/range)

---

## <a name="passo-8"></a>✅ PASSO 8: Configuração de Gerenciamento - Parte 1

**O que foi feito:**
Ativação de ferramentas de monitoramento e gerenciamento:

| Campo | Descrição |
|-------|-----------|
| **Azure Monitor** | Habilitação de monitoramento de performance |
| **Log Analytics Workspace** | Seleção de workspace para armazenar logs |
| **Azure Update Manager** | Habilitação de atualizações automáticas |
| **Diagnóstico** | Configuração de boot diagnostics |

**Detalhes técnicos:**
- Azure Monitor: coleta métricas de CPU, memória, disco
- Log Analytics: análise centralizada de logs
- Update Manager: patches de segurança automáticos
- Boot Diagnostics: solução de problemas de inicialização

---

## <a name="passo-9"></a>✅ PASSO 9: Configuração de Gerenciamento - Parte 2

**O que foi feito:**
Continuação de gerenciamento com organização e compliance:

| Campo | Descrição |
|-------|-----------|
| **Tags** | Adição de metadados para organização (ex: environment: production) |
| **Políticas de Conformidade** | Aplicação de Azure Policy |
| **Alertas e Notificações** | Configuração de alertas automáticos |
| **Controle de Acesso (RBAC)** | Definição de quem pode gerenciar a VM |

**Detalhes técnicos:**
- Tags: facilitam billing, reporting e filtragem
- Azure Policy: enforce padrões corporativos
- RBAC: controle granular de permissões (Owner, Contributor, Reader)
- Alertas: notificações por email/SMS

---

## <a name="passo-10"></a>✅ PASSO 10: Configuração de NOC - Parte 1

**O que foi feito:**
Configuração do Network Operations Center para monitoramento de rede:

| Campo | Descrição |
|-------|-----------|
| **Análise de Tráfego** | Visualização de padrões de comunicação |
| **Monitoramento de Performance** | Acompanhamento de latência e throughput |
| **Topologia de Rede** | Visualização de diagrama de conexões |
| **Troubleshooting** | Ferramentas para diagnosis de problemas |

**Detalhes técnicos:**
- NOC: seção especializada em operações de rede
- Network Watcher: ferramenta Azure para análise
- Métricas: bytes entrada/saída, pacotes, conexões ativas

---

## <a name="passo-11"></a>✅ PASSO 11: Configuração de NOC - Parte 2

**O que foi feito:**
Ferramentas avançadas de diagnóstico de rede:

| Campo | Descrição |
|-------|-----------|
| **Packet Capture** | Captura de pacotes para análise detalhada |
| **Fluxo de Tráfego** | Visualização de NSG Flow Logs |
| **Connection Troubleshoot** | Teste de conectividade ponto-a-ponto |
| **Métricas em Tempo Real** | Dashboard com métricas atualizadas |

**Detalhes técnicos:**
- Packet Capture: análise profunda com Wireshark
- NSG Flow Logs: registro de tráfego permitido/bloqueado
- Connection Troubleshoot: diagnóstico de conectividade TCP/UDP
- Latência: medida em milissegundos (ms)

---

## <a name="passo-12"></a>✅ PASSO 12: Criação de Chave SSH

**O que foi feito:**
Geração e configuração de autenticação segura por SSH:

### Processo:
1. **Geração de Par de Chaves**
   - Chave pública: enviada para a VM (arquivo authorized_keys)
   - Chave privada: mantida segura no cliente local

2. **Download da Chave Privada**
   - Arquivo: formato .pem
   - Armazenamento: local seguro (ex: ~/.ssh/)
   - Backup: realizar cópia de segurança

3. **Configuração de Permissões**
   ```bash
   chmod 600 /path/to/private/key.pem
   ```

4. **Armazenamento Seguro**
   - Não compartilhar ou versionar em git
   - Proteger com password (opcional)

**Detalhes técnicos:**
- Algoritmo: RSA 2048 bits (padrão Azure)
- SSH: protocolo seguro para acesso remoto
- Autenticação por chave: mais segura que senha

---

## <a name="passo-13"></a>✅ PASSO 13: Revisão de Configurações

**O que foi feito:**
Verificação completa de todos os parâmetros antes da implantação:

### Checklist de Revisão:
- ✓ Configurações básicas (nome, região, tamanho)
- ✓ Disco (tipo, tamanho, criptografia)
- ✓ Rede (VNet, Subnet, IP público, NSG)
- ✓ Gerenciamento (monitor, logs, RBAC)
- ✓ NOC e ferramentas de diagnóstico
- ✓ Autenticação SSH
- ✓ Tags e políticas
- ✓ Custos estimados

**Detalhes técnicos:**
- Review automático: validação de configurações
- Custos: Azure mostra estimativa mensal
- Conformidade: verificação de políticas corporativas

---

## <a name="passo-14"></a>✅ PASSO 14: Conclusão e Inicialização da VM

**O que foi feito:**
Finalização do processo de criação e provisionamento:

### Etapas:
1. **Clique em "Criar" (Create)**
   - Confirmação final de todas as configurações

2. **Deployment/Implantação**
   - Azure provisiona os recursos
   - Tempo típico: 2-5 minutos
   - Status: "Deployment in progress"

3. **Notificação de Sucesso**
   - "Deployment succeeded"
   - Acesso ao Resource Group

**Detalhes técnicos:**
- Deployment: orquestração de recursos (VM, disco, NIC, IP)
- Rollback: se houver erro, recursos são removidos automaticamente

---

## <a name="passo-15"></a>✅ PASSO 15: Tela Inicial de Gerenciamento da VM

**O que foi feito:**
Acesso ao dashboard principal de gerenciamento:

### Informações Disponíveis:
| Campo | Descrição |
|-------|-----------|
| **Status** | Running, Stopped, Deallocated |
| **IP Público** | Endereço para acesso SSH |
| **IP Privado** | Endereço interno da VNet |
| **Tamanho** | Configuração de CPU/RAM |
| **SO** | Sistema Operacional e versão |
| **Última atividade** | Histórico de mudanças |

**Detalhes técnicos:**
- Painel principal: Overview da VM
- Ações rápidas: Start, Stop, Restart, Delete
- Métricas: gráficos de performance

---

## <a name="passo-16"></a>✅ PASSO 16: Detalhes e Configurações da VM

**O que foi feito:**
Exploração dos detalhes técnicos avançados:

### Seções Exploradas:
- **Hardware**: CPU, memória, disk I/O
- **Armazenamento**: Discos, snapshots, imagens
- **Rede**: NICs, IP configurations, NSG rules
- **Gerenciamento**: Updates, backups, extensions
- **Monitoramento**: Alertas, logs, performance

**Detalhes técnicos:**
- Extensions: software adicional instalável (Agent)
- Performance Diagnostics: análise de gargalos
- System updates: patches de segurança do SO

---

## <a name="passo-17"></a>✅ PASSO 17: Iniciando Conexão SSH

**O que foi feito:**
Preparação e configuração para conexão remota:

### Obtenção de Informações:
1. **IP Público da VM**
   - Obtido no Overview
   - Exemplo: 52.170.45.123

2. **Chave SSH Privada**
   - Arquivo baixado no Passo 12
   - Caminho local: ~/.ssh/key.pem

### Comando SSH:
```bash
ssh -i ~/.ssh/key.pem azureuser@52.170.45.123
```

### Parâmetros:
- `-i`: indica arquivo de chave privada
- `azureuser`: nome de usuário (configurado no Passo 4)
- `52.170.45.123`: IP público da VM

**Detalhes técnicos:**
- Porta padrão: 22 (SSH)
- First connection: aceitar fingerprint da chave do servidor
- Timeout padrão: 10 segundos

---

## <a name="passo-18"></a>✅ PASSO 18: Máquina Virtual Conectada com Sucesso

**O que foi feito:**
Conexão SSH estabelecida e máquina pronta para uso:

### Confirmação de Sucesso:
- ✓ Prompt do shell remoto visível
- ✓ Comando `whoami` retorna o usuário
- ✓ Acesso ao terminal da VM

### Próximos Passos Possíveis:
1. **Verificar o Sistema**
   ```bash
   uname -a
   lsb_release -a
   ```

2. **Verificar Conectividade**
   ```bash
   ping google.com
   curl -I https://www.microsoft.com
   ```

3. **Instalar Aplicações**
   ```bash
   sudo apt-get update && sudo apt-get install -y [pacote]
   ```

4. **Monitorar Recursos**
   ```bash
   htop
   df -h
   ```

**Detalhes técnicos:**
- Acesso root: usar `sudo` ou `sudo su -`
- Gerenciador de pacotes: apt (Ubuntu/Debian), yum (CentOS/RHEL)
- Permissões: verificar com `whoami` e `id`

---

## 📊 Resumo Geral do Processo

```
┌─────────────────────────────────────────────────┐
│ CRIAÇÃO DE VM NO AZURE - FLUXO COMPLETO         │
├─────────────────────────────────────────────────┤
│ 1. Criar Recurso                                │
│ 2. Selecionar VM                                │
│ 3. Configurar Básico (Parte 1)                  │
│ 4. Configurar Básico (Parte 2)                  │
│ 5. Configurar Disco                             │
│ 6. Configurar Rede (Parte 1)                    │
│ 7. Configurar Rede (Parte 2)                    │
│ 8. Configurar Gerenciamento (Parte 1)           │
│ 9. Configurar Gerenciamento (Parte 2)           │
│ 10. Configurar NOC (Parte 1)                    │
│ 11. Configurar NOC (Parte 2)                    │
│ 12. Criar Chave SSH                             │
│ 13. Revisar Configurações                       │
│ 14. Finalizar e Criar                           │
│ 15. Acessar Painel de Gerenciamento             │
│ 16. Explorar Detalhes da VM                     │
│ 17. Preparar Conexão SSH                        │
│ 18. Conectar à VM com Sucesso ✓                │
└─────────────────────────────────────────────────┘
```

---

## 🎯 Conclusão

Você completou com sucesso o laboratório de criação e configuração de uma Máquina Virtual no Microsoft Azure! A VM está:

- ✅ Criada e em execução
- ✅ Configurada com segurança (SSH)
- ✅ Monitorada e gerenciada
- ✅ Conectada e acessível
- ✅ Pronta para receber aplicações

---

**Data:** 23 de maio de 2026  
**Laboratório:** Dio-Lab-Azure  
**Bootcamp:** Java & Cloud Azure - Bradesco