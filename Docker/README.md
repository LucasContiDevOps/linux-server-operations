# Docker Administration & Troubleshooting

Coleção de comandos, procedimentos e práticas relacionadas à administração e troubleshooting de ambientes Docker.

Este repositório reúne anotações, exemplos e soluções baseadas em experiências práticas do dia a dia em suporte e infraestrutura, servindo como material de consulta rápida para operações recorrentes envolvendo containers e ambientes conteinerizados.

## Objetivos

* Centralizar comandos frequentemente utilizados na administração Docker;
* Documentar procedimentos operacionais recorrentes;
* Registrar cenários de troubleshooting encontrados na prática;
* Compartilhar conhecimento adquirido durante atividades de suporte e infraestrutura;
* Reduzir o tempo de diagnóstico e resolução de incidentes.

---

## Conteúdo

### 🐳 Operações Básicas

* Listagem de containers;
* Acesso ao terminal interno;
* Gerenciamento de imagens;
* Remoção de containers;
* Verificação do ambiente.

### 📋 Logs e Monitoramento

* Consulta de logs;
* Acompanhamento em tempo real;
* Configuração do Docker utilizando Journald;
* Integração com `journalctl`.

### ⚙️ Docker Compose

* Inicialização de ambientes;
* Interrupção e remoção de stacks;
* Compatibilidade entre `docker-compose` e `docker compose`.

### 🌐 Redes Docker

* Listagem de redes;
* Criação de redes;
* Remoção de redes;
* Troubleshooting relacionado à conectividade entre containers.

### 🧹 Limpeza e Manutenção

* Remoção de imagens;
* Exclusão de containers;
* Limpeza de recursos não utilizados;
* Gerenciamento de espaço em disco.

### 🚑 Troubleshooting

Cenários recorrentes documentados durante atividades operacionais, incluindo:

* Containers com nomes duplicados;
* Falhas na remoção de redes;
* Migração de ambientes Docker;
* Remoção de recursos órfãos;
* Recuperação de ambientes.

### 🗄️ PKPLUS-CLI e SQLite

Procedimentos relacionados à ferramenta proprietária utilizada no gerenciamento dos serviços.

Inclui exemplos de:

* Consulta ao banco de estado;
* Remoção de serviços desabilitados;
* Consultas úteis utilizando SQLite.

### 🔍 Verificações e Diagnóstico

Comandos utilizados para validação do ambiente Docker, incluindo:

* Status do daemon;
* Reinicialização do serviço;
* Uso de armazenamento;
* Eventos em tempo real;
* Informações do daemon;
* Consulta de versões.

---

## Estrutura do Repositório

* `docker.md` → documentação principal contendo comandos, exemplos e procedimentos;
* Exemplos de troubleshooting;
* Consultas e verificações operacionais utilizadas como referência rápida.

---

## Principais Aprendizados

A administração de ambientes Docker vai além da execução de comandos básicos. Compreender o comportamento do daemon, interpretar logs, diagnosticar falhas e estruturar procedimentos padronizados são habilidades essenciais para atuação em ambientes produtivos.

A organização deste material reforçou a importância da documentação técnica como mecanismo para compartilhamento de conhecimento, redução de Toil e aumento da eficiência operacional.

---

## Observações

Este repositório não substitui a documentação oficial do Docker, mas atua como um guia prático baseado em estudos e experiências reais vivenciadas durante atividades de suporte e infraestrutura.

Os exemplos aqui apresentados refletem cenários frequentemente encontrados no dia a dia operacional, especialmente em ambientes compostos por múltiplos serviços conteinerizados.
