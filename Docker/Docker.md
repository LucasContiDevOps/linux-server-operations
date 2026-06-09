# Docker - Administração e Troubleshooting

# Comandos Básicos

## Listar Containers

### Containers em execução

```bash
docker ps
```

### Todos os containers

```bash
docker ps -a
```

---

# Acessar um Container

## Identificar o container

```bash
docker ps
```

## Acessar terminal interno

```bash
docker exec -it <container_id> bash
```

Caso a imagem não possua Bash:

```bash
docker exec -it <container_id> sh
```

---

# Logs

## Exibir logs

```bash
docker logs <container_id>
```

## Acompanhar logs em tempo real

```bash
docker logs -f <container_id>
```

## Utilizando Journald (CONTAINER_TAG)

Configurar o Docker para enviar logs ao Journal.

Arquivo:

```bash
/etc/docker/daemon.json
```

Conteúdo:

```json
{
    "log-driver": "journald"
}
```

Reiniciar Docker:

```bash
systemctl restart docker
```

Consultar logs:

```bash
journalctl -f CONTAINER_TAG=<nome_container> --output cat
```

Exemplo:

```bash
journalctl -f CONTAINER_TAG=ParkingPlus:servicoregistrasetor --output cat
```

---

# Docker Compose

## Subir containers

```bash
docker-compose up -d
```

ou versões mais recentes:

```bash
docker compose up -d
```

## Parar e remover ambiente

```bash
docker-compose down
```

ou

```bash
docker compose down
```

---

# Importação de Imagens

## Carregar imagem exportada

```bash
docker load -i arquivo.tar
```

---

# Redes Docker

## Listar redes

```bash
docker network ls
```

## Remover rede

```bash
docker network rm <network_name>
```

## Criar rede

```bash
docker network create <network_name>
```

Exemplo:

```bash
docker network create parkingplus_network
```

---

# Limpeza de Ambiente

## Remover container

```bash
docker rm <container_id>
```

## Remover container forçadamente

```bash
docker rm -f <container_id>
```

## Remover imagem

```bash
docker images
```

```bash
docker rmi <image_id>
```

## Limpeza geral

Remove:

* Containers parados
* Redes não utilizadas
* Imagens órfãs
* Cache de build

```bash
docker system prune
```

Limpeza completa:

```bash
docker system prune -a
```

---

# Troubleshooting

# Container Já Existe

## Erro

```text
Error response from daemon:
Conflict.
The container name "/parkingplus_wps_lpr"
is already in use by container "xxxx"
```

## Diagnóstico

Existe um container antigo utilizando o mesmo nome.

Verificar:

```bash
docker ps -a
```

## Solução

Parar o container antigo:

```bash
docker stop <container_id>
```

Remover:

```bash
docker rm <container_id>
```

Subir novamente:

```bash
docker-compose up -d
```

---

# Falha ao Remover Rede

## Erro

```text
failed to remove network docker_old_default:
Error: No such network
```

## Diagnóstico

A rede já foi removida ou não existe mais.

Verificar:

```bash
docker network ls
```

Se não estiver listada, o erro pode ser ignorado.

---

# Migração de Ambiente Docker

Quando houver substituição de ambiente:

## Passo 1

Copiar ou mover o arquivo:

```bash
docker-compose.yml
```

para o diretório do novo ambiente.

## Passo 2

Parar ambiente antigo:

```bash
docker-compose down
```

ou

```bash
docker stop <container_id>
```

## Passo 3

Remover containers antigos:

```bash
docker rm <container_id>
```

## Passo 4

Subir novo ambiente:

```bash
docker-compose up -d
```

---

# Remoção de Containers Indesejados

Listar:

```bash
docker ps -a
```

Remover:

```bash
docker rm <container_id>
```

Forçar remoção:

```bash
docker rm -f <container_id>
```

---

# Remoção de Imagens Não Utilizadas

Listar:

```bash
docker images
```

Remover:

```bash
docker rmi <image_id>
```

---

# PKPLUS-CLI

Ferramenta proprietária utilizada para gerenciamento dos serviços.

## Banco de Estado

```bash
sqlite3 /var/lib/pkplus-svc/state.sqlite
```

## Remover serviços desabilitados

```sql
DELETE FROM service
WHERE enabled = 0;
```

Sair:

```sql
.quit
```

---

# SQLite - Consultas Úteis

## Listar estrutura de uma tabela

```sql
PRAGMA table_info(nome_da_tabela);
```

## Listar tabelas

```sql
.tables
```

## Visualizar registros

```sql
SELECT * FROM nome_da_tabela;
```

## Contar registros

```sql
SELECT COUNT(*) FROM nome_da_tabela;
```

---

# Verificações Úteis

## Status do Docker

```bash
systemctl status docker
```

## Reiniciar Docker

```bash
systemctl restart docker
```

## Verificar uso de espaço

```bash
docker system df
```

## Verificar eventos em tempo real

```bash
docker events
```

## Verificar informações do daemon

```bash
docker info
```

## Verificar versão

```bash
docker version
```
