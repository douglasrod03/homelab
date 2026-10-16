# Projeto de Infraestrutura de Rede Corporativa — Cisco Packet Tracer

## 1. Objetivo

Projetar e implementar uma infraestrutura de rede corporativa no Cisco Packet Tracer, composta por uma matriz e duas filiais localizadas em cidades diferentes.

O projeto deverá contemplar a topologia física e lógica, segmentação de rede, endereçamento IP, serviços corporativos, roteamento entre unidades e políticas de segurança.

A implementação será realizada do zero, utilizando os equipamentos e recursos disponíveis no Cisco Packet Tracer.

## 2. Escopo da infraestrutura

### 2.1. Matriz

**Capacidade:** 100 notebooks corporativos.

#### Equipamentos de rede
- 1 roteador de borda para conexão com o provedor de internet.
- 1 firewall corporativo.
- 1 switch de distribuição (Core).
- 3 switches gerenciáveis de acesso, com 48 portas.
- 4 pontos de acesso Wi-Fi corporativo.

#### Servidores e armazenamento
- 1 servidor de Active Directory (AD) para autenticação centralizada.
- 1 servidor DNS para resolução de nomes.
- 1 servidor DHCP para distribuição automática de endereços IP.
- 1 servidor de arquivos para compartilhamento de documentos.
- 1 servidor de monitoramento da infraestrutura.
- 1 dispositivo NAS para armazenamento e backup.

#### Dispositivos adicionais
- 100 notebooks corporativos.
- 8 impressoras de rede.
- 2 computadores para administração da infraestrutura.
- 2 equipamentos de videoconferência.

#### Distribuição dos departamentos

| Departamento | Notebooks |
|---|---:|
| Administrativo / Financeiro | 20 |
| Recursos Humanos | 10 |
| Comercial | 25 |
| Tecnologia da Informação | 15 |
| Operações | 20 |
| Diretoria | 10 |
| **Total** | **100** |

### 2.2. Filial 1

**Capacidade:** 70 notebooks corporativos.

#### Equipamentos de rede
- 1 roteador WAN para comunicação com a matriz.
- 1 firewall para controle de tráfego.
- 2 switches gerenciáveis de 48 portas.
- 2 pontos de acesso Wi-Fi corporativo.

#### Dispositivos adicionais
- 70 notebooks corporativos.
- 4 impressoras de rede.
- 1 computador para administração local.
- 1 equipamento de videoconferência.

#### Serviços de rede
- DHCP centralizado na matriz ou serviço local.
- DNS centralizado na matriz.
- Autenticação por meio do domínio corporativo.
- Acesso autorizado aos servidores e recursos compartilhados da matriz.

#### Distribuição dos departamentos

| Departamento | Notebooks |
|---|---:|
| Atendimento | 25 |
| Comercial | 20 |
| Operações | 15 |
| Administrativo | 10 |
| **Total** | **70** |

### 2.3. Filial 2

**Capacidade:** 50 notebooks corporativos.

#### Equipamentos de rede
- 1 roteador WAN para comunicação com a matriz.
- 1 firewall para controle de tráfego.
- 2 switches gerenciáveis de 24 ou 48 portas.
- 2 pontos de acesso Wi-Fi corporativo.

#### Dispositivos adicionais
- 50 notebooks corporativos.
- 3 impressoras de rede.
- 1 computador para administração local.
- 1 equipamento de videoconferência.

#### Serviços de rede
- DHCP centralizado na matriz ou serviço local.
- DNS centralizado na matriz.
- Autenticação por meio do domínio corporativo.
- Acesso autorizado aos sistemas internos e recursos compartilhados.

#### Distribuição dos departamentos

| Departamento | Notebooks |
|---|---:|
| Comercial | 20 |
| Atendimento | 15 |
| Administrativo | 10 |
| Gerência | 5 |
| **Total** | **50** |

## 3. Conectividade entre unidades

A matriz será responsável pela infraestrutura central e pelos serviços corporativos compartilhados.

As duas filiais deverão possuir conectividade WAN com a matriz, permitindo a comunicação entre as redes autorizadas.

Requisitos:
- Conexão com a internet nas três unidades.
- Roteamento entre matriz e filiais.
- Comunicação bidirecional entre as redes autorizadas.
- Acesso remoto aos serviços corporativos da matriz.
- Implementação de VPN site-to-site, caso suportada pelos equipamentos escolhidos.
- Configuração de rotas de retorno.
- Controle do tráfego entre as unidades.

## 4. Segmentação lógica da rede

A infraestrutura deverá ser segmentada por VLAN, separando os dispositivos de acordo com sua função.

| VLAN | Nome | Finalidade |
|---:|---|---|
| 10 | ADMIN | Administração da infraestrutura de TI |
| 20 | SERVIDORES | Servidores e serviços corporativos |
| 30 | FINANCEIRO | Dispositivos do departamento financeiro |
| 40 | COMERCIAL | Dispositivos do departamento comercial |
| 50 | OPERACOES | Operações e atendimento |
| 60 | DIRETORIA | Dispositivos da diretoria |
| 70 | WIFI-CORP | Acesso Wi-Fi corporativo |
| 80 | IMPRESSORAS | Impressoras de rede |
| 90 | VISITANTES | Acesso de visitantes isolado da rede interna |
| 99 | GERENCIAMENTO | Gerenciamento de equipamentos de rede |

As VLANs poderão utilizar identificadores iguais nas diferentes unidades, desde que sejam configuradas em redes IP distintas e corretamente roteadas.

## 5. Plano de endereçamento IP

Será utilizado o bloco privado `10.0.0.0/8`, com uma faixa reservada para cada unidade.

| Unidade | Bloco reservado |
|---|---|
| Matriz | `10.10.0.0/16` |
| Filial 1 | `10.20.0.0/16` |
| Filial 2 | `10.30.0.0/16` |
| Links WAN | `10.255.0.0/24` |

### 5.1. Sub-redes da matriz

| VLAN | Sub-rede |
|---:|---|
| 10 | `10.10.10.0/24` |
| 20 | `10.10.20.0/24` |
| 30 | `10.10.30.0/24` |
| 40 | `10.10.40.0/24` |
| 50 | `10.10.50.0/24` |
| 60 | `10.10.60.0/24` |
| 70 | `10.10.70.0/24` |
| 80 | `10.10.80.0/24` |
| 90 | `10.10.90.0/24` |
| 99 | `10.10.99.0/24` |

As filiais deverão seguir o mesmo padrão, utilizando `10.20.x.0/24` na Filial 1 e `10.30.x.0/24` na Filial 2.

O dimensionamento definitivo das sub-redes, gateways, endereços estáticos e intervalos DHCP deverá ser documentado durante a implementação.

## 6. Requisitos técnicos

O projeto deverá contemplar:

- Topologia física das três unidades.
- Topologia lógica e identificação dos equipamentos.
- Configuração de VLANs.
- Configuração de portas de acesso e trunks 802.1Q.
- Roteamento entre VLANs.
- Roteamento WAN entre matriz e filiais.
- Endereçamento IPv4 e definição de gateways.
- Configuração de DHCP e DNS.
- Representação dos serviços corporativos.
- Configuração de ACLs para controle de acesso.
- Políticas de isolamento da rede de visitantes.
- Controle de acesso aos servidores.
- Documentação das interfaces, conexões, VLANs e sub-redes.

## 7. Critérios de conclusão

O projeto será considerado concluído quando:

1. Os dispositivos obtiverem endereços IP válidos conforme suas respectivas redes.
2. A comunicação entre VLANs funcionar de acordo com as políticas estabelecidas.
3. A matriz e as duas filiais possuírem conectividade WAN funcional.
4. Os dispositivos autorizados das filiais conseguirem acessar os serviços corporativos da matriz.
5. A resolução DNS e a distribuição DHCP funcionarem conforme o desenho implementado.
6. As ACLs impedirem os acessos não autorizados definidos no escopo.
7. A rede de visitantes permanecer isolada dos recursos internos.
8. Os testes de conectividade, roteamento e acesso aos serviços forem realizados e documentados.
9. A topologia física e lógica estiver documentada e o arquivo do Packet Tracer estiver organizado.

## 8. Restrições do ambiente

A implementação será realizada utilizando os equipamentos, serviços e recursos disponíveis no Cisco Packet Tracer.

Equipamentos e serviços reais que não possuam representação integral no simulador deverão ser substituídos por equivalentes funcionais para fins de estudo.

O Active Directory, o firewall dedicado, o NAS, o monitoramento e a VPN deverão ser representados conforme as capacidades efetivamente disponíveis no ambiente de simulação.

O foco do projeto é o planejamento e a implementação de uma infraestrutura corporativa, abrangendo switching, routing, serviços de rede, segmentação e segurança.
