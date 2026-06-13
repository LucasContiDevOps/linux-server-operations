# Linux Commands and Permissions

## Navegação e Diretórios

| Comando | Descrição                      |
| ------- | ------------------------------ |
| `pwd`   | Exibe o diretório atual        |
| `ls`    | Lista arquivos e diretórios    |
| `cd`    | Navega entre diretórios        |
| `cd ..` | Retorna ao diretório anterior  |
| `cd ~`  | Retorna para a home            |
| `mkdir` | Cria diretórios                |
| `touch` | Cria arquivos                  |
| `find`  | Pesquisa arquivos e diretórios |

---

## Manipulação de Arquivos

| Comando  | Descrição                        |
| -------- | -------------------------------- |
| `cp`     | Copia arquivos                   |
| `mv`     | Move ou renomeia arquivos        |
| `rm`     | Remove arquivos                  |
| `rm -i`  | Remove solicitando confirmação   |
| `rm -rf` | Remove diretórios recursivamente |
| `rmdir`  | Remove diretórios vazios         |
| `cat`    | Exibe conteúdo                   |
| `head`   | Primeiras linhas                 |
| `tail`   | Últimas linhas                   |
| `less`   | Leitura paginada                 |

---

## Edição de Arquivos

| Comando | Descrição          |
| ------- | ------------------ |
| `nano`  | Editor simples     |
| `vim`   | Editor avançado    |
| `vi`    | Editor tradicional |

### Atalhos do Nano

* `Ctrl + X` → sair;
* `Ctrl + O` → salvar;
* `Ctrl + K` → recortar linha;
* `Ctrl + U` → colar linha.

---

## Usuários e Privilégios

| Comando   | Descrição                                     |
| --------- | --------------------------------------------- |
| `whoami`  | Exibe o usuário atual                         |
| `sudo`    | Executa comando com privilégios elevados      |
| `sudo su` | Alterna para root                             |
| `exit`    | Encerra sessão ou retorna ao usuário anterior |
| `useradd` | Cria usuários                                 |
| `passwd`  | Define ou altera senhas                       |

### Convenções

| Símbolo | Significado    |
| ------- | -------------- |
| `$`     | Usuário comum  |
| `#`     | Usuário root   |
| `~`     | Diretório home |

---

## Utilitários

| Comando        | Descrição                   |
| -------------- | --------------------------- |
| `man`          | Manual completo             |
| `--help`       | Ajuda resumida              |
| `clear`        | Limpa o terminal            |
| `echo`         | Exibe texto na saída padrão |
| `hostname`     | Nome da máquina             |
| `hostname -I`  | Endereços IP                |
| `unzip`        | Descompacta arquivos        |
| `bash`         | Shell padrão                |
| `shutdown now` | Desliga a máquina           |

---

## Informações do Sistema

| Comando                   | Descrição                          |
| ------------------------- | ---------------------------------- |
| `cat /etc/os-release`     | Informações do sistema operacional |
| `cat /etc/redhat-release` | Versão do CentOS/RHEL              |
| `cat /proc/cpuinfo`       | Informações do processador         |
| `lscpu`                   | Dados detalhados da CPU            |
| `lspci`                   | Dispositivos PCI                   |
| `uptime`                  | Tempo ligado                       |
| `df -h`                   | Uso do armazenamento               |
| `du -hs *`                | Tamanho dos arquivos e diretórios  |

---

# Permissões Linux

## Tipos de Arquivos

| Símbolo | Tipo                     |
| ------- | ------------------------ |
| `d`     | Diretório                |
| `-`     | Arquivo comum            |
| `b`     | Dispositivo de bloco     |
| `c`     | Dispositivo de caractere |
| `p`     | Pipe                     |
| `s`     | Socket                   |

---

## Permissões

| Permissão | Significado   |
| --------- | ------------- |
| `r`       | Leitura       |
| `w`       | Escrita       |
| `x`       | Execução      |
| `-`       | Sem permissão |

### Exemplos

| Notação | Significado        |
| ------- | ------------------ |
| `---`   | Nenhuma permissão  |
| `r--`   | Leitura            |
| `rw-`   | Leitura e escrita  |
| `r-x`   | Leitura e execução |
| `rwx`   | Controle total     |

---

## chmod

### Classes

| Símbolo | Significado |
| ------- | ----------- |
| `u`     | Usuário     |
| `g`     | Grupo       |
| `o`     | Outros      |
| `a`     | Todos       |

### Operadores

| Operador | Ação               |
| -------- | ------------------ |
| `+`      | Adiciona permissão |
| `-`      | Remove permissão   |
| `=`      | Define permissão   |

### Exemplos

```bash
chmod u+x script.sh
chmod g-w arquivo.txt
chmod o+r documento.txt

chmod 755 script.sh
chmod 644 documento.txt
chmod 700 ~/.ssh
```

### Permissões Numéricas

| Valor | Permissão |
| ----- | --------- |
| 4     | Leitura   |
| 2     | Escrita   |
| 1     | Execução  |

Exemplos:

* `755` → rwx r-x r-x
* `644` → rw- r-- r--
* `700` → rwx --- ---
