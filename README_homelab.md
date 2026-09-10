# Homelab de Infraestrutura, Segurança e Cloud

Projeto de laboratório pessoal voltado para **redes, administração de infraestrutura, segurança, observabilidade, automação e cloud**.

A estrutura foi planejada para permitir a evolução do ambiente por etapas, começando pela rede local e administração centralizada e avançando para monitoramento, Infrastructure as Code e workloads em nuvem.

> Este README será atualizado conforme cada etapa da topologia for implementada, testada e documentada.

---

## Visão geral

A arquitetura do laboratório é dividida em quatro áreas principais:

- **Edge / Rede local:** MikroTik responsável pelo controle da rede.
- **Administração:** PC principal utilizado para gerenciamento e automação da infraestrutura.
- **Servidor local:** Notebook com Ubuntu Server utilizado para serviços internos e segurança.
- **Cloud:** Ambiente AWS para Kubernetes, aplicações e recursos provisionados via Terraform.

---

## Topologia

```text
                         INTERNET
                            │
                            ▼
                      ┌───────────┐
                      │ MikroTik  │
                      │ DNS       │
                      │ Firewall  │
                      │ LAN       │
                      └─────┬─────┘
                            │
              ┌─────────────┴─────────────┐
              │                           │
              ▼                           ▼
       ┌──────────────┐            ┌──────────────┐
       │   PC Admin   │            │ Ubuntu Server│
       │   Zorin OS   │            │   Notebook   │
       │  Terraform   │            │    Wazuh     │
       └──────┬───────┘            └──────────────┘
              │
              │ Gerenciamento / IaC
              │
              ▼
       ┌──────────────┐
       │     AWS      │
       │  Kubernetes  │
       │ Aplicações   │
       └──────────────┘
```

A versão gráfica da topologia pode ser adicionada em:

```text
docs/topologia.png
```

E referenciada no README com:

```md
![Topologia do laboratório](docs/topologia.png)
```

---

# Componentes

## 1. MikroTik — Edge e rede local

O MikroTik atua como ponto central da infraestrutura de rede do laboratório.

### Responsabilidades

- Roteamento da rede local
- DHCP
- DNS
- Firewall
- NAT
- Segmentação de rede
- Controle de acesso
- Comunicação entre os equipamentos do laboratório
- Futuramente, conexão segura com a infraestrutura AWS

### Equipamento

```text
Modelo:
RouterOS:
IP de gerenciamento:
Rede LAN:
Gateway:
DNS:
```

### Implementação

- [ ] Configuração inicial
- [ ] Atualização do RouterOS
- [ ] Configuração da interface WAN
- [ ] Configuração da LAN
- [ ] Configuração do DHCP
- [ ] Configuração do DNS
- [ ] Configuração de endereçamento estático
- [ ] Criação das regras de firewall
- [ ] Configuração de NAT
- [ ] Separação das redes/VLANs
- [ ] Testes de conectividade
- [ ] Backup da configuração

### Configurações realizadas

```text
Adicionar aqui as configurações implementadas.
```

### Testes

```text
Adicionar comandos, prints, testes de ping, traceroute,
DNS, regras de firewall e validações realizadas.
```

---

# 2. PC Admin

Máquina principal utilizada para administração do laboratório.

## Sistema operacional

**Zorin OS / Linux**

### Responsabilidades

- Administração do MikroTik
- Administração dos servidores
- Acesso à AWS
- Execução do Terraform
- SSH
- Testes de rede
- Troubleshooting
- Gerenciamento da infraestrutura

### Ferramentas

- Terraform
- SSH
- Nmap
- Wireshark
- AWS CLI
- kubectl
- Terminal Linux
- WinBox, quando necessário

### Implementação

- [ ] Configuração do sistema operacional
- [ ] Configuração de IP administrativo
- [ ] Configuração de SSH
- [ ] Instalação do Terraform
- [ ] Instalação da AWS CLI
- [ ] Configuração do acesso à AWS
- [ ] Instalação do kubectl
- [ ] Configuração de acesso ao MikroTik
- [ ] Configuração de acesso ao Ubuntu Server
- [ ] Configuração do Wazuh Agent
- [ ] Testes de administração remota

### Configurações realizadas

```text
Adicionar aqui comandos, configurações e decisões realizadas.
```

---

# 3. Servidor Local

Notebook utilizado como servidor físico do laboratório.

## Sistema operacional

**Ubuntu Server**

### Objetivo

Hospedar serviços locais que façam parte da infraestrutura e do ambiente de segurança.

### Hardware

```text
Equipamento:
CPU:
RAM:
Armazenamento:
Interface de rede:
IP:
```

### Serviços

Atualmente planejados:

- Wazuh Server
- Wazuh Indexer
- Wazuh Dashboard

Possíveis serviços futuros:

- Docker
- Reverse Proxy
- Servidor de logs
- DNS secundário
- Monitoramento
- Serviços internos do laboratório

### Implementação

- [ ] Instalação do Ubuntu Server
- [ ] Configuração de IP estático
- [ ] Configuração de hostname
- [ ] Atualização do sistema
- [ ] Configuração de SSH
- [ ] Hardening básico
- [ ] Configuração de firewall local
- [ ] Instalação do Wazuh
- [ ] Configuração dos agentes
- [ ] Testes de comunicação
- [ ] Backup das configurações

---

# 4. Wazuh

O Wazuh é utilizado como plataforma de segurança e monitoramento dos endpoints do laboratório.

## Objetivos

- Centralização de eventos
- Monitoramento dos endpoints
- Detecção de eventos de segurança
- File Integrity Monitoring
- Vulnerability Detection
- Coleta de logs
- Visualização de alertas
- Experimentos de SIEM/XDR

## Arquitetura

```text
PC Admin
   │
   │ Wazuh Agent
   ▼
Ubuntu Server
   │
   ├── Wazuh Server
   ├── Wazuh Indexer
   └── Wazuh Dashboard
```

## Implementação

- [ ] Instalação do Wazuh Server
- [ ] Instalação do Wazuh Indexer
- [ ] Instalação do Wazuh Dashboard
- [ ] Cadastro do PC Admin
- [ ] Instalação do Wazuh Agent
- [ ] Teste de comunicação
- [ ] Configuração de FIM
- [ ] Configuração de vulnerabilidades
- [ ] Criação de regras personalizadas
- [ ] Testes de eventos
- [ ] Documentação dos alertas

## Testes realizados

```text
Exemplo:

Teste:
Resultado esperado:
Resultado obtido:
Conclusão:
```

---

# 5. AWS

A AWS representa a camada de infraestrutura em nuvem do laboratório.

O ambiente será utilizado progressivamente, evitando a criação de serviços sem necessidade prática.

## Objetivos

- Aprender administração de infraestrutura cloud
- Provisionar recursos utilizando Terraform
- Executar aplicações pessoais
- Criar workloads em Kubernetes
- Trabalhar com redes cloud
- Integrar infraestrutura local e cloud

## Arquitetura prevista

```text
AWS
│
├── VPC
│
├── Subnets
│
├── Security Groups
│
├── Compute
│
├── Kubernetes
│
└── Aplicações
```

Os serviços serão definidos conforme a necessidade do laboratório.

## Possíveis serviços

- EC2
- VPC
- IAM
- S3
- Route 53
- CloudWatch
- EKS

> A inclusão de cada serviço deverá estar relacionada a uma necessidade real do projeto.

## Implementação

- [ ] Criação da conta/ambiente
- [ ] Configuração de IAM
- [ ] Configuração da AWS CLI
- [ ] Criação da VPC
- [ ] Criação das subnets
- [ ] Configuração de Security Groups
- [ ] Provisionamento via Terraform
- [ ] Definição da solução Kubernetes
- [ ] Deploy da primeira aplicação
- [ ] Configuração de observabilidade
- [ ] Testes de conectividade
- [ ] Avaliação de integração VPN com o laboratório local

---

# 6. Kubernetes

O Kubernetes será utilizado na camada AWS para estudar orquestração de containers e execução de aplicações.

## Objetivos

- Deploy de aplicações
- Gerenciamento de containers
- Services
- Deployments
- ConfigMaps
- Secrets
- Volumes
- Escalabilidade
- Atualizações controladas

## Implementação

- [ ] Definir arquitetura Kubernetes
- [ ] Criar cluster
- [ ] Configurar kubectl
- [ ] Criar namespace do laboratório
- [ ] Fazer deploy da primeira aplicação
- [ ] Criar Service
- [ ] Configurar Ingress
- [ ] Configurar armazenamento
- [ ] Configurar Secrets
- [ ] Testar atualização de aplicação
- [ ] Testar rollback
- [ ] Documentar arquitetura final

---

# 7. Terraform

Terraform será utilizado como ferramenta de **Infrastructure as Code (IaC)** para administrar principalmente os recursos em cloud.

A execução será feita através do **PC Admin**.

## Objetivos

- Padronizar a criação da infraestrutura
- Manter a configuração da AWS reproduzível
- Automatizar provisionamento
- Controlar mudanças de infraestrutura
- Reduzir configurações manuais

## Estrutura prevista

```text
terraform/
├── providers.tf
├── variables.tf
├── outputs.tf
├── network.tf
├── compute.tf
├── kubernetes.tf
└── terraform.tfvars.example
```

## Fluxo

```bash
terraform init
terraform fmt
terraform validate
terraform plan
terraform apply
```

Por segurança, alterações destrutivas ou de produção devem sempre passar por revisão antes da execução.

## Implementação

- [ ] Configurar provider AWS
- [ ] Configurar variáveis
- [ ] Criar VPC via Terraform
- [ ] Criar subnets
- [ ] Criar Security Groups
- [ ] Criar recursos de compute
- [ ] Provisionar recursos Kubernetes
- [ ] Criar outputs
- [ ] Validar plano
- [ ] Documentar mudanças

---

# 8. VMware

O VMware só será incluído na arquitetura caso exista uma função prática para virtualização local.

Possíveis usos:

- Testes com máquinas virtuais
- Laboratórios temporários
- Testes de sistemas operacionais
- Simulação de servidores
- Ambientes isolados

Caso nenhuma VM seja utilizada de forma permanente no projeto, o VMware não precisa fazer parte da topologia principal.

### Status

```text
[ ] Não utilizado
[ ] Em avaliação
[ ] Utilizado no laboratório
```

---

# Comunicação entre os componentes

| Origem | Destino | Função |
|---|---|---|
| Internet | MikroTik | Acesso externo |
| MikroTik | PC Admin | Rede administrativa |
| MikroTik | Ubuntu Server | Rede de servidores |
| PC Admin | MikroTik | Administração |
| PC Admin | Ubuntu Server | SSH / administração |
| PC Admin | AWS | Terraform / AWS CLI / kubectl |
| PC Admin | Wazuh | Envio de eventos |
| Ubuntu Server | PC Admin | Monitoramento |
| AWS | Kubernetes | Execução de workloads |
| MikroTik | AWS | VPN / integração futura |

---

# Endereçamento de rede

Esta seção deve refletir a configuração real do laboratório.

| Equipamento | Interface | Rede | IP | Função |
|---|---|---|---|---|
| MikroTik | LAN | `A definir` | `A definir` | Gateway |
| PC Admin | Ethernet | `A definir` | `A definir` | Administração |
| Ubuntu Server | Ethernet | `A definir` | `A definir` | Servidor |
| AWS | VPC | `A definir` | `A definir` | Cloud |

---

# Segurança

Princípios utilizados no projeto:

- Segmentação de rede
- Menor privilégio
- Firewall no edge
- Firewall nos servidores
- Administração autenticada
- Monitoramento com Wazuh
- Infraestrutura versionada
- Secrets fora do código
- Acesso SSH utilizando chaves
- Controle de acesso aos recursos AWS

---

# Estrutura do repositório

```text
homelab/
├── README.md
│
├── docs/
│   ├── topologia.png
│   ├── rede.md
│   ├── mikrotik.md
│   ├── wazuh.md
│   ├── aws.md
│   └── kubernetes.md
│
├── terraform/
│   ├── providers.tf
│   ├── variables.tf
│   ├── outputs.tf
│   └── modules/
│
├── scripts/
│
├── configs/
│   ├── mikrotik/
│   └── wazuh/
│
└── tests/
```

---

# Roadmap

## Fase 1 — Rede

- [ ] MikroTik instalado
- [ ] LAN configurada
- [ ] DHCP configurado
- [ ] DNS configurado
- [ ] Firewall configurado
- [ ] Endereçamento definido

## Fase 2 — Administração

- [ ] PC Admin configurado
- [ ] SSH configurado
- [ ] Terraform instalado
- [ ] AWS CLI instalada
- [ ] kubectl instalado

## Fase 3 — Servidor

- [ ] Ubuntu Server instalado
- [ ] Rede configurada
- [ ] SSH configurado
- [ ] Hardening realizado

## Fase 4 — Segurança

- [ ] Wazuh instalado
- [ ] PC Admin registrado
- [ ] Logs sendo enviados
- [ ] Alertas validados
- [ ] Regras testadas

## Fase 5 — Cloud

- [ ] AWS configurada
- [ ] IAM configurado
- [ ] VPC criada
- [ ] Recursos provisionados com Terraform

## Fase 6 — Kubernetes

- [ ] Cluster criado
- [ ] kubectl configurado
- [ ] Aplicação publicada
- [ ] Services configurados
- [ ] Observabilidade configurada

## Fase 7 — Integração

- [ ] Integração local/cloud
- [ ] VPN, caso necessária
- [ ] Monitoramento centralizado
- [ ] Documentação final

---

# Registro de evolução

## Etapa 01 — Estrutura inicial

**Objetivo:**

```text
Descrever o objetivo da etapa.
```

**Alterações realizadas:**

```text
Descrever o que foi configurado.
```

**Problemas encontrados:**

```text
Descrever erros, limitações ou dificuldades.
```

**Solução aplicada:**

```text
Descrever como o problema foi resolvido.
```

**Resultado:**

```text
Descrever o estado final da etapa.
```

---

## Etapa 02

```text
Adicionar próxima etapa.
```

---

# Decisões técnicas

Esta seção registra decisões importantes para evitar que alterações futuras percam o contexto original.

| Decisão | Motivo |
|---|---|
| MikroTik como gateway principal | Centralizar roteamento, firewall, DNS e LAN |
| Zorin OS no PC Admin | Sistema principal de administração |
| Ubuntu Server no servidor físico | Ambiente estável para serviços Linux |
| Wazuh no servidor local | Monitoramento e laboratório de segurança |
| Terraform no PC Admin | Centralizar o gerenciamento IaC |
| Kubernetes na AWS | Laboratório de containers e cloud |
| VMware opcional | Só será mantido se houver uso real |

---

# Tecnologias

![Linux](https://img.shields.io/badge/Linux-Zorin%20OS%20%7C%20Ubuntu-informational)
![MikroTik](https://img.shields.io/badge/MikroTik-RouterOS-informational)
![Wazuh](https://img.shields.io/badge/Wazuh-SIEM%20%2F%20XDR-informational)
![AWS](https://img.shields.io/badge/AWS-Cloud-informational)
![Terraform](https://img.shields.io/badge/Terraform-IaC-informational)
![Kubernetes](https://img.shields.io/badge/Kubernetes-Orchestration-informational)

---

# Objetivo do projeto

O objetivo deste laboratório não é apenas instalar tecnologias individualmente, mas entender como diferentes componentes de infraestrutura trabalham juntos.

O projeto busca desenvolver experiência prática em:

- Redes
- Linux
- Segurança
- Administração de servidores
- Cloud
- Infrastructure as Code
- Kubernetes
- Troubleshooting
- Observabilidade
- Documentação técnica

Cada componente deverá possuir uma função clara dentro da arquitetura, evitando adicionar tecnologias apenas para aumentar artificialmente a stack utilizada.

---

## Status

**Em desenvolvimento.**
