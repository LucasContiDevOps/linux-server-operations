# Comandos Úteis de Rede e Troubleshooting Linux

## Verificação de Portas

### Listar portas abertas e processos associados

```bash
netstat -tunlp
```

### Filtrar uma porta específica

```bash
netstat -an | grep 8080
```

### Alternativas modernas (Ubuntu/CentOS)

```bash
ss -tunlp
```

```bash
ss -an | grep 8080
```

---

# Verificação de Endereçamento IP

## Exibir IP principal

```bash
hostname -I
```

## Exibir todas as interfaces

```bash
ip a
```

ou

```bash
ip addr
```

## Filtrar apenas endereços IP

```bash
ip a | grep inet
```

## Exibição resumida e organizada

```bash
ip -br -c a
```

---

# Gerenciamento de Rotas

## Exibir tabela de rotas

```bash
ip route
```

ou

```bash
route -n
```

## Remover rota padrão

```bash
ip route del default
```

## Adicionar rota estática (Windows)

```cmd
route -p add 10.61.1.182 mask 255.255.255.255 192.168.77.1
```

## Exibir rotas configuradas (Windows)

```cmd
route print
```

## Adicionar rota estática (Linux)

```bash
ip route add 10.61.1.182 via 192.168.77.1
```

---

# Configuração de Rede - CentOS 7

## Arquivos de configuração

### Interface de rede

```bash
/etc/sysconfig/network-scripts/ifcfg-<interface>
```

Exemplo:

```bash
vi /etc/sysconfig/network-scripts/ifcfg-ens192
```

### DNS

```bash
vi /etc/resolv.conf
```

## Aplicar alterações

```bash
ifdown ens192 && ifup ens192
```

ou

```bash
systemctl restart network
```

---

# Configuração de Rede - Ubuntu (Netplan)

## Arquivos de configuração

```bash
/etc/netplan/
```

Exemplo:

```bash
vi /etc/netplan/00-installer-config.yaml
```

## Aplicar alterações

Testar configuração:

```bash
sudo netplan try
```

Aplicar definitivamente:

```bash
sudo netplan apply
```

---

# Modelo de Configuração Netplan

```yaml
network:
  version: 2
  renderer: networkd

  ethernets:
    enp3s0:
      addresses:
        - 125.125.10.101/24

      routes:
        - to: default
          via: 125.125.10.1

      nameservers:
        addresses:
          - 8.8.8.8
          - 8.8.4.4

    enp2s0:
      dhcp4: true
```

### Campos importantes

| Campo       | Descrição                     |
| ----------- | ----------------------------- |
| addresses   | IP e máscara                  |
| via         | Gateway                       |
| nameservers | DNS                           |
| dhcp4       | DHCP habilitado               |
| renderer    | Gerenciador de rede utilizado |

---

# Troubleshooting

## Configurar Rede Sem Editor de Texto

Situação comum quando o servidor está sem `vim`, `nano` ou acesso interativo.

### Exemplo 1

```bash
echo -e "network:\n  ethernets:\n    enp44s0:\n      addresses:\n      - 172.22.11.160/24\n      nameservers:\n        addresses:\n        - 8.8.8.8\n        search:\n        - 8.8.4.4\n      routes:\n       - to: default\n         via: 172.22.11.254\n  version: 2" > /etc/netplan/00-installer-config.yaml
```

### Exemplo 2

```bash
echo -e "network:\n  ethernets:\n    enp0s31f6:\n      addresses:\n      - 10.48.1.105/24\n      nameservers:\n        addresses: [8.8.8.8, 8.8.4.4]\n        search: []\n      routes:\n       - to: default\n         via: 125.125.10.2\n  version: 2" > /etc/netplan/00-installer-config.yaml
```

### Exemplo 3 (Sem Gateway)

```bash
echo -e "network:\n  ethernets:\n    enp0s31f6:\n      addresses:\n      - 125.125.10.101/24\n      nameservers:\n        addresses:\n        - 4.2.2.2\n        search:\n        - 8.8.8.8\n  version: 2" > /etc/netplan/00-installer-config.yaml
```

Após criar o arquivo:

```bash
sudo netplan try
sudo netplan apply
```

---

## Ubuntu Perdendo IP Fixo Após Reinicialização

Algumas instalações utilizam o Cloud-Init para recriar a configuração de rede durante o boot.

### Desabilitar gerenciamento de rede pelo Cloud-Init

Editar:

```bash
/etc/cloud/cloud.cfg.d/99-installer.cfg
```

Adicionar:

```yaml
network: {config: disabled}
```

### Renomear arquivo do Netplan

Manter o padrão:

```bash
/etc/netplan/00-installer-config.yaml
```

### Aplicar alterações

```bash
sudo netplan generate
sudo netplan apply
```

### Validar

```bash
ip a
ip route
```

---

# Comandos Úteis para Diagnóstico de Rede

## Testar conectividade

```bash
ping 8.8.8.8
```

```bash
ping google.com
```

## Verificar DNS

```bash
nslookup google.com
```

ou

```bash
dig google.com
```

## Verificar gateway

```bash
ip route
```

## Verificar portas remotas

```bash
telnet IP PORTA
```

ou

```bash
nc -zv IP PORTA
```

Exemplo:

```bash
nc -zv 125.125.10.100 5432
```

## Verificar caminho da rota

```bash
traceroute 8.8.8.8
```

Caso não esteja instalado:

```bash
apt install traceroute
```

ou

```bash
yum install traceroute
```
