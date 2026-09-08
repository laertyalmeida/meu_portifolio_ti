# 02 — FHS

## FHS — Filesystem Hierarchy Standard (Padrão de Hierarquia do Sistema de Arquivos)

O **FHS** define uma estrutura organizada para os diretórios usados pelos sistemas Linux.

Seu objetivo é estabelecer **onde os arquivos e recursos do sistema devem ficar**.

    /
    ├── bin
    ├── boot
    ├── dev
    ├── etc
    ├── home
    ├── lib
    ├── media
    ├── mnt
    ├── opt
    ├── proc
    ├── root
    ├── run
    ├── sbin
    ├── srv
    ├── sys
    ├── tmp
    ├── usr
    └── var

---

## `/` — Root Directory (Diretório Raiz)

É o ponto inicial de toda a árvore de diretórios.

Tudo no Linux parte de:

    /

Exemplo:

    /home
    /etc
    /var
    /usr

---

## `/bin` — Binaries (Binários)

Contém comandos essenciais para todos os usuários.

Exemplos:

    ls
    cp
    mv
    rm
    cat

> Em sistemas modernos com **merged-/usr (usr unificado)**, `/bin` pode ser um link simbólico para `/usr/bin`.

---

## `/sbin` — System Binaries (Binários do Sistema)

Contém comandos utilizados principalmente para administração do sistema.

Exemplos:

    ip
    fsck
    mount

> Em sistemas modernos, `/sbin` pode ser um link simbólico para `/usr/sbin`.

---

## `/boot` — Boot (Inicialização)

Contém arquivos necessários para iniciar o sistema.

Exemplos:

    kernel
    initramfs
    arquivos do bootloader

---

## `/dev` — Devices (Dispositivos)

Contém arquivos que representam dispositivos do sistema.

Exemplos:

    /dev/sda
    /dev/sda1
    /dev/null

---

## `/etc` — Configuration (Configuração)

Contém arquivos de configuração do sistema.

Exemplos:

    /etc/fstab
    /etc/hosts
    /etc/passwd

---

## `/home` — Home Directories (Diretórios dos Usuários)

Contém os diretórios pessoais dos usuários comuns.

    /home
    ├── usuario1
    └── usuario2

---

## `/root` — Root Home (Diretório do Administrador)

É o diretório pessoal do usuário `root`.

    /root

Não deve ser confundido com:

    /

`/` = raiz do sistema  
`/root` = diretório pessoal do `root`

---

## `/lib` — Libraries (Bibliotecas)

Contém bibliotecas necessárias para programas e componentes essenciais do sistema.

> Em sistemas modernos com **merged-/usr**, `/lib` também pode ser um link simbólico para `/usr/lib`.

---

## `/media` — Media (Mídias)

Ponto utilizado normalmente para montar mídias removíveis.

Exemplos:

    pendrive
    cartão de memória
    CD/DVD

---

## `/mnt` — Mount (Montagem)

Usado tradicionalmente para montagens temporárias ou administrativas.

    /mnt

---

## `/opt` — Optional (Opcional)

Usado para software adicional que não faz parte da instalação padrão do sistema.

    /opt/programa

---

## `/proc` — Processes (Processos)

Filesystem virtual que fornece informações sobre processos e o kernel.

Exemplos:

    /proc/cpuinfo
    /proc/meminfo
    /proc/uptime

---

## `/run` — Runtime (Execução)

Armazena dados temporários relacionados à execução atual do sistema.

Exemplos:

    PID
    sockets
    arquivos de estado

---

## `/srv` — Service Data (Dados de Serviços)

Contém dados fornecidos por serviços do sistema.

Exemplo:

    /srv/www

---

## `/sys` — System (Sistema)

Filesystem virtual que fornece informações e interfaces relacionadas ao kernel, dispositivos e hardware.

---

## `/tmp` — Temporary (Temporário)

Usado para armazenar arquivos temporários.

    /tmp

Arquivos nesse diretório não devem ser considerados permanentes.

---

## `/usr` — Unix System Resources (Recursos do Sistema)

Contém grande parte dos programas, bibliotecas, documentação e outros recursos do sistema.

Principais subdiretórios:

    /usr/bin
    /usr/sbin
    /usr/lib
    /usr/share

---

## `/var` — Variable Data (Dados Variáveis)

Armazena dados que mudam durante o funcionamento do sistema.

Exemplos:

    /var/log
    /var/cache
    /var/spool

---

## Tabela para memorizar

| Diretório | Tradução | Função |
|---|---|---|
| `/` | Root — Raiz | Base do sistema |
| `/bin` | Binaries — Binários | Comandos essenciais |
| `/sbin` | System Binaries — Binários do Sistema | Administração |
| `/boot` | Boot — Inicialização | Arquivos de inicialização |
| `/dev` | Devices — Dispositivos | Dispositivos |
| `/etc` | Configuration — Configuração | Configurações |
| `/home` | Home — Usuários | Arquivos pessoais |
| `/root` | Root Home — Home do administrador | Arquivos do `root` |
| `/lib` | Libraries — Bibliotecas | Bibliotecas |
| `/media` | Media — Mídias | Mídias removíveis |
| `/mnt` | Mount — Montagem | Montagens temporárias |
| `/opt` | Optional — Opcional | Software adicional |
| `/proc` | Processes — Processos | Informações do kernel/processos |
| `/run` | Runtime — Execução | Dados temporários de execução |
| `/srv` | Service — Serviço | Dados de serviços |
| `/sys` | System — Sistema | Kernel/hardware |
| `/tmp` | Temporary — Temporário | Arquivos temporários |
| `/usr` | Unix System Resources — Recursos do Sistema | Programas e recursos |
| `/var` | Variable Data — Dados Variáveis | Dados que mudam |

---

## LPIC-1 — O que saber

- **FHS** = Filesystem Hierarchy Standard — Padrão de Hierarquia do Sistema de Arquivos.
- `/` = raiz.
- `/etc` = configuração.
- `/home` = usuários.
- `/root` = administrador.
- `/var` = dados variáveis.
- `/tmp` = arquivos temporários.
- `/dev` = dispositivos.
- `/proc` = processos e informações do kernel.
- `/sys` = dispositivos, hardware e kernel.
- `/boot` = inicialização.
- `/usr` = programas e recursos.
- `/opt` = software adicional.
- `/mnt` = montagens temporárias.
- `/media` = mídias removíveis.
- Saber que `/proc` e `/sys` são **virtual filesystems (sistemas de arquivos virtuais)**.

---

## Resumo

    /      → raiz
    /etc   → configuração
    /home  → usuários
    /root  → administrador
    /var   → dados variáveis
    /tmp   → temporários
    /dev   → dispositivos
    /proc  → processos / kernel
    /sys   → hardware / kernel
    /boot  → inicialização
    /usr   → programas / recursos
    /opt   → software adicional
    /mnt   → montagem
    /media  → mídias removíveis

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
