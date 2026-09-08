# 01 — Sistemas de Arquivos e FHS

## Filesystem — Sistema de Arquivos

O **filesystem** organiza como os dados são armazenados, localizados e acessados no disco.

    Disco
      ↓
    Partição
      ↓
    Filesystem
      ↓
    Diretórios e arquivos

Exemplos de filesystems:

    ext4
    XFS
    Btrfs
    vfat

---

## FHS — Filesystem Hierarchy Standard (Padrão de Hierarquia do Sistema de Arquivos)

O **FHS** define uma organização padrão para os principais diretórios do Linux.

A ideia é saber **onde cada tipo de arquivo deve ficar**.

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

## Diretórios principais

| Diretório | Inglês | Português | Função |
|---|---|---|---|
| `/` | Root | Raiz | Base de todo o sistema |
| `/bin` | Binaries | Binários | Comandos essenciais |
| `/sbin` | System Binaries | Binários do Sistema | Comandos administrativos |
| `/boot` | Boot | Inicialização | Arquivos necessários para iniciar o sistema |
| `/dev` | Devices | Dispositivos | Arquivos que representam dispositivos |
| `/etc` | Et Cetera / Configuration | Configuração | Arquivos de configuração |
| `/home` | Home | Diretórios dos usuários | Dados dos usuários |
| `/root` | Root Home | Diretório do administrador | Home do usuário `root` |
| `/lib` | Libraries | Bibliotecas | Bibliotecas necessárias ao sistema |
| `/media` | Media | Mídias | Montagem automática de mídias removíveis |
| `/mnt` | Mount | Montagem | Montagens temporárias |
| `/opt` | Optional | Opcional | Software adicional |
| `/proc` | Processes | Processos | Informações virtuais do kernel e processos |
| `/run` | Runtime | Execução | Dados temporários da execução do sistema |
| `/srv` | Service | Serviços | Dados fornecidos por serviços |
| `/sys` | System | Sistema | Informações e interface do kernel |
| `/tmp` | Temporary | Temporário | Arquivos temporários |
| `/usr` | Unix System Resources | Recursos do Sistema | Programas, bibliotecas e documentação |
| `/var` | Variable | Variável | Dados que mudam durante a execução |

---

## Os diretórios que mais caem

### `/etc` — Configuration (Configuração)

    /etc
      ↓
    configurações do sistema

Exemplos:

    /etc/fstab
    /etc/hosts
    /etc/passwd

---

### `/home` — User Home (Diretórios dos Usuários)

    /home
      ├── jo
