# Sistemas de Arquivos e FHS

## 01 — Estrutura de Diretórios

**Directory Structure — Estrutura de Diretórios**

No Linux, os arquivos e diretórios formam uma única árvore que começa em:

    /

`/` — **Root Directory — Diretório Raiz**

Diferente do Windows, o Linux não organiza os sistemas de arquivos a partir de letras como `C:` ou `D:`. Tudo fica conectado à árvore a partir de `/`.

---

## 1. `/` — Root — Raiz

É o ponto inicial de toda a estrutura do sistema.

Exemplo:

    /
    ├── boot
    ├── dev
    ├── etc
    ├── home
    ├── lib
    ├── proc
    ├── root
    ├── run
    ├── sys
    ├── tmp
    ├── usr
    └── var

---

## 2. Diretórios principais

| Diretório | English | Português | Função |
|---|---|---|---|
| `/` | Root | Raiz | Início de toda a árvore |
| `/boot` | Boot | Inicialização | Kernel e arquivos usados na inicialização |
| `/dev` | Devices | Dispositivos | Arquivos que representam dispositivos |
| `/etc` | Configuration | Configuração | Configurações do sistema |
| `/home` | Home | Diretórios pessoais | Arquivos dos usuários |
| `/lib` | Libraries | Bibliotecas | Bibliotecas essenciais do sistema |
| `/media` | Media | Mídia | Montagem de mídias removíveis |
| `/mnt` | Mount | Montagem | Ponto tradicional para montagens temporárias |
| `/opt` | Optional | Opcional | Software adicional |
| `/proc` | Processes | Processos | Informações virtuais sobre processos e kernel |
| `/root` | Root Home | Diretório pessoal do root | Home do usuário root |
| `/run` | Runtime | Execução | Dados temporários de execução do sistema |
| `/sbin` | System Binaries | Binários do sistema | Programas administrativos do sistema |
| `/srv` | Service | Serviços | Dados fornecidos por serviços |
| `/sys` | System | Sistema | Informações virtuais sobre kernel e hardware |
| `/tmp` | Temporary | Temporário | Arquivos temporários |
| `/usr` | User System Resources | Recursos do sistema | Programas, bibliotecas e documentação |
| `/var` | Variable | Variável | Dados que mudam durante o funcionamento do sistema |

---

## 3. `/boot` — Boot — Inicialização

Contém arquivos necessários para o processo de inicialização.

Exemplos:

    /boot/vmlinuz
    /boot/initramfs
    /boot/grub/

**Kernel — Núcleo** é o núcleo do sistema operacional.

---

## 4. `/dev` — Devices — Dispositivos

Contém arquivos especiais que representam dispositivos.

Exemplos:

    /dev/sda
    /dev/sda1
    /dev/nvme0n1
    /dev/null

Exemplo:

    /dev/sda

Pode representar um disco.

    /dev/sda1

Pode representar uma partição.

---

## 5. `/etc` — Configuration — Configuração

Armazena arquivos de configuração do sistema e de serviços.

Exemplos:

    /etc/passwd
    /etc/shadow
    /etc/fstab
    /etc/hostname
    /etc/hosts

> No LPIC-1, `/etc` é um diretório fundamental para memorizar.

---

## 6. `/home` — Home — Diretórios pessoais

Contém os diretórios pessoais dos usuários comuns.

Exemplo:

    /home/laerte
    /home/joao
    /home/maria

O usuário normalmente armazena seus arquivos dentro do próprio `/home`.

---

## 7. `/root` — Root Home — Diretório pessoal do root

É o diretório pessoal do usuário administrativo `root`.

    /root

Não confunda:

    /root

com:

    /

`/` é a raiz do sistema.

`/root` é o diretório pessoal do usuário root.

---

## 8. `/lib` — Libraries — Bibliotecas

Contém bibliotecas necessárias para o funcionamento de programas e partes essenciais do sistema.

Exemplos:

    /lib
    /lib64

Em sistemas modernos, esses diretórios podem estar integrados a `/usr/lib` por meio de **symbolic links — links simbólicos**.

---

## 9. `/proc` — Processes — Processos

É um sistema de arquivos **virtual** que fornece informações sobre processos e o kernel.

Exemplos:

    /proc/cpuinfo
    /proc/meminfo
    /proc/mounts
    /proc/1234/

Não é um diretório comum armazenado normalmente no disco.

Consultar informações:

    cat /proc/cpuinfo
    cat /proc/meminfo

---

## 10. `/sys` — System — Sistema

Também é um sistema de arquivos virtual.

Fornece informações sobre:

- kernel;
- hardware;
- dispositivos;
- drivers.

Exemplo:

    /sys/class/
    /sys/devices/
    /sys/block/

---

## 11. `/run` — Runtime — Execução

Armazena dados temporários usados durante a execução do sistema.

Exemplos:

    /run/lock
    /run/user/

Normalmente seu conteúdo é criado durante a inicialização e pode desaparecer após o reboot.

---

## 12. `/tmp` — Temporary — Temporário

Usado para arquivos temporários.

Exemplo:

    /tmp/arquivo.tmp

Arquivos em `/tmp` podem ser removidos automaticamente dependendo da configuração do sistema.

Não use `/tmp` para armazenar dados importantes permanentemente.

---

## 13. `/usr` — User System Resources — Recursos do Sistema

Contém grande parte dos programas e recursos utilizados pelo sistema.

Exemplos:

    /usr/bin
    /usr/sbin
    /usr/lib
    /usr/share

### `/usr/bin`

Programas e comandos utilizados normalmente pelos usuários.

### `/usr/sbin`

Programas administrativos do sistema.

### `/usr/lib`

Bibliotecas.

### `/usr/share`

Arquivos compartilhados, como documentação e dados independentes de arquitetura.

---

## 14. `/var` — Variable — Variável

Contém dados que mudam frequentemente durante o funcionamento do sistema.

Exemplos:

    /var/log
    /var/cache
    /var/lib
    /var/tmp

### `/var/log`

Arquivos de **Log — Registro** do sistema e serviços.

Exemplo:

    /var/log/syslog

ou, dependendo da distribuição:

    /var/log/messages

---

## 15. `/media` e `/mnt`

### `/media`

Usado normalmente para montagem de mídias removíveis.

Exemplo:

    /media/usuario/USB

### `/mnt`

Ponto tradicional para montagens temporárias feitas pelo administrador.

Exemplo:

    mount /dev/sdb1 /mnt

---

## 16. `/opt` — Optional — Opcional

Usado para instalação de determinados softwares adicionais.

Exemplo:

    /opt/programa/

---

## 17. `/srv` — Service — Serviços

Pode armazenar dados fornecidos por serviços do sistema.

Exemplo:

    /srv/www/

---

## 18. Caminho Absoluto × Caminho Relativo

**Absolute Path — Caminho Absoluto**

Começa pela raiz `/`.

Exemplo:

    /home/laerte/documentos/arquivo.txt

**Relative Path — Caminho Relativo**

Depende do diretório atual.

Exemplo:

    documentos/arquivo.txt

Se estamos em:

    /home/laerte

o caminho relativo aponta para:

    /home/laerte/documentos/arquivo.txt

---

## 19. `.` e `..`

`.` — **Current Directory — Diretório Atual**

    ./arquivo.txt

`..` — **Parent Directory — Diretório Pai**

    cd ..

Exemplo:

    /home/laerte/documentos

Executar:

    cd ..

leva para:

    /home/laerte

---

## 20. `~` — Home Directory — Diretório Pessoal

Representa o diretório pessoal do usuário atual.

Exemplo:

    cd ~

ou:

    cd

Se o usuário for `laerte`:

    ~

representa:

    /home/laerte

---

## Resumo LPIC-1

- `/` → **Root — Raiz** de toda a árvore.
- `/boot` → arquivos de inicialização.
- `/dev` → dispositivos.
- `/etc` → configurações.
- `/home` → diretórios dos usuários.
- `/root` → diretório pessoal do `root`.
- `/lib` → bibliotecas essenciais.
- `/media` → mídias removíveis.
- `/mnt` → montagens temporárias.
- `/opt` → software adicional.
- `/proc` → informações virtuais de processos e kernel.
- `/run` → dados temporários de execução.
- `/sbin` → programas administrativos do sistema.
- `/srv` → dados fornecidos por serviços.
- `/sys` → informações virtuais sobre hardware e kernel.
- `/tmp` → arquivos temporários.
- `/usr` → programas e recursos do sistema.
- `/var` → dados variáveis, como logs e caches.
- `/` é diferente de `/root`.
- Caminho absoluto começa com `/`.
- Caminho relativo depende do diretório atual.
- `.` → diretório atual.
- `..` → diretório pai.
- `~` → diretório pessoal do usuário.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
