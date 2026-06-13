# Linux Networking Runbook

Coleção de comandos, procedimentos e práticas de troubleshooting relacionados à administração e diagnóstico de redes em ambientes Linux.

Este repositório foi construído a partir de experiências práticas do dia a dia em suporte e infraestrutura, complementadas por estudos e anotações pessoais. O objetivo é servir como um guia rápido de consulta para atividades recorrentes de diagnóstico, configuração e resolução de problemas em ambientes produtivos.

## Objetivos

* Centralizar comandos úteis para troubleshooting de rede;
* Documentar procedimentos frequentemente utilizados em ambientes Linux;
* Reduzir o tempo de diagnóstico e resolução de incidentes;
* Compartilhar conhecimento adquirido na prática;
* Servir como material de consulta rápida para futuras referências.

## Conteúdo

### 🔌 Verificação de Portas

Comandos para identificação de portas abertas, serviços associados e validação de conexões locais.

**Principais ferramentas:**

* `netstat`
* `ss`

Exemplos abordados:

* Listagem de portas abertas;
* Associação entre portas e processos;
* Filtragem de portas específicas.

---

### 🌐 Endereçamento IP

Procedimentos para identificação e validação das configurações de rede.

**Comandos abordados:**

* `hostname -I`
* `ip a`
* `ip addr`
* `ip -br -c a`

Atividades contempladas:

* Identificação de interfaces;
* Validação de endereços IP;
* Visualização simplificada das configurações.

---

### 🛣️ Gerenciamento de Rotas

Procedimentos para consulta e manipulação da tabela de roteamento.

**Comandos abordados:**

* `ip route`
* `route -n`
* `route print`
* `ip route add`
* `ip route del`

Cenários contemplados:

* Consulta de rotas;
* Inclusão de rotas estáticas;
* Remoção de gateway padrão;
* Comparação entre Linux e Windows.

---

### ⚙️ Configuração de Rede

#### CentOS 7

Configuração manual de interfaces através dos arquivos localizados em:

```bash
/etc/sysconfig/network-scripts/
```

Incluindo:

* Configuração de interfaces;
* DNS;
* Reinicialização dos serviços de rede.

---

#### Ubuntu (Netplan)

Procedimentos para configuração utilizando Netplan.

Incluindo:

* Estrutura de arquivos YAML;
* Aplicação segura das alterações;
* Validação das configurações;
* Exemplos completos de configuração.

---

### 🚑 Troubleshooting

Soluções para cenários encontrados durante atividades operacionais.

Exemplos:

* Configuração de rede sem editores de texto instalados;
* Criação automatizada de arquivos Netplan utilizando `echo`;
* Configuração de ambientes sem gateway;
* Aplicação e validação das alterações.

---

### ☁️ Cloud-Init e Persistência de Configurações

Cenário abordado:

Servidores Ubuntu perdendo configurações de IP fixo após reinicializações.

Procedimentos documentados:

* Desabilitação do gerenciamento de rede pelo Cloud-Init;
* Ajustes nos arquivos de configuração;
* Geração e aplicação das configurações;
* Validação final do ambiente.

---

### 🔍 Diagnóstico de Conectividade

Ferramentas utilizadas para investigação de falhas de comunicação.

**Comandos abordados:**

* `ping`
* `nslookup`
* `dig`
* `telnet`
* `nc`
* `traceroute`

Casos de uso:

* Testes de conectividade;
* Validação de DNS;
* Verificação de portas remotas;
* Análise do caminho percorrido pelos pacotes.

---

## Principais Aprendizados

A construção deste material reforçou a importância de procedimentos padronizados e documentação técnica como mecanismos para aumento da eficiência operacional e redução do tempo de resolução de incidentes.

Além do aspecto técnico, a organização destes comandos em formato de runbook evidencia a importância da gestão do conhecimento em equipes de infraestrutura.

## Observações

Este repositório não pretende substituir documentações oficiais, mas sim atuar como um guia prático baseado em experiências reais, estudos e situações recorrentes enfrentadas durante atividades de suporte e administração de ambientes Linux.

Os exemplos aqui apresentados refletem cenários utilizados como consulta rápida no dia a dia operacional.
