# 06 — lsblk e blkid

## lsblk — List Block Devices (Listar Dispositivos de Bloco)

Mostra discos, partições e pontos de montagem em formato de árvore.

    lsblk

Exemplo:

    sda
    ├─sda1
    ├─sda2
    └─sda3

### Opção importante

    lsblk -f

`-f` — filesystem (sistema de arquivos)

Mostra:

- **NAME** — name (nome)
- **FSTYPE** — filesystem type (tipo de sistema de arquivos)
- **LABEL** — label (rótulo)
- **UUID** — universally unique identifier (identificador único universal)
- **MOUNTPOINTS** — mount points (pontos de montagem)

---

## blkid — Block Device Identification (Identificação de Dispositivos de Bloco)

Mostra informações usadas para identificar os sistemas de arquivos.

    blkid

Exemplo:

    /dev/sda1: UUID="a1b2-c3d4" TYPE="ext4"
    /dev/sda2: UUID="x9y8-z7w6" TYPE="xfs"

Consultar uma partição específica:

    blkid /dev/sda1

### Informações principais

- **UUID** — Universally Unique Identifier (Identificador Único Universal)
- **LABEL** — label (rótulo)
- **TYPE** — type (tipo do sistema de arquivos)

---

## lsblk × blkid

| Comando | Tradução | Função |
|---|---|---|
| `lsblk` | List Block Devices — Listar Dispositivos de Bloco | Mostra discos e partições |
| `lsblk -f` | filesystem — sistema de arquivos | Mostra filesystem, UUID e LABEL |
| `blkid` | Block Device Identification — Identificação de Dispositivos de Bloco | Mostra UUID, LABEL e TYPE |
| `blkid /dev/sda1` | identificar `/dev/sda1` | Mostra os dados da partição |

### Memorize

    lsblk → estrutura dos discos e partições
    blkid → identificação do sistema de arquivos

---

## LPIC-1 — O que saber

- `lsblk` — listar dispositivos de bloco.
- `lsblk -f` — mostrar informações do sistema de arquivos.
- `blkid` — identificar sistemas de arquivos.
- **UUID** — identificador único.
- **LABEL** — rótulo do filesystem.
- **TYPE** — tipo do filesystem.
- Saber diferenciar `lsblk` de `blkid`.
- Entender o uso do UUID no `/etc/fstab`.

---

## Resumo

    lsblk
      ↓
    Discos → Partições → Pontos de montagem

    lsblk -f
      ↓
    Filesystem → UUID → LABEL → Montagem

    blkid
      ↓
    UUID → LABEL → TYPE

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
