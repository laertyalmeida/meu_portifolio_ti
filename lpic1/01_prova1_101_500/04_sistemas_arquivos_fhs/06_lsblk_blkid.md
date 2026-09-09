# Sistemas de Arquivos e FHS

## 06 — lsblk e blkid

### 1. `lsblk`

**lsblk** — *List Block Devices* — **Listar Dispositivos de Bloco**

Mostra discos, partições e outros dispositivos de bloco em forma de árvore.

    lsblk

Exemplo:

    NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
    sda           8:0    0   500G  0 disk
    ├─sda1        8:1    0   100G  0 part /
    └─sda2        8:2    0   400G  0 part /home

### Opções importantes

| Opção | English | Português |
|---|---|---|
| `-f` | filesystem | mostrar sistema de arquivos |
| `-o` | output | escolher colunas |
| `-l` | list | formato em lista |
| `-p` | paths | mostrar caminho completo do dispositivo |
| `-a` | all | mostrar também dispositivos vazios |

Exemplos:

    lsblk -f
    lsblk -o NAME,SIZE,FSTYPE,MOUNTPOINTS
    lsblk -p

`lsblk -f` é especialmente útil para identificar:

- Partição
- Sistema de arquivos
- UUID
- Label
- Ponto de montagem

---

### 2. `blkid`

**blkid** — *Block Device Identification* — **Identificação de Dispositivos de Bloco**

Mostra informações de identificação das partições, principalmente:

- `UUID`
- `LABEL`
- `TYPE` — tipo de sistema de arquivos

Exemplo:

    sudo blkid

Saída:

    /dev/sda1: UUID="a1b2-c3d4" TYPE="ext4"
    /dev/sda2: UUID="1234-5678" TYPE="swap"

### Opções importantes

| Opção | English | Português |
|---|---|---|
| `-s` | show specific tag | mostrar uma informação específica |
| `-o` | output | definir formato da saída |
| `-L` | lookup by label | localizar pelo Label |
| `-U` | lookup by UUID | localizar pelo UUID |

Exemplos:

    sudo blkid /dev/sda1
    sudo blkid -s UUID /dev/sda1
    sudo blkid -s TYPE /dev/sda1

---

### 3. Diferença entre `lsblk` e `blkid`

| Comando | Principal finalidade |
|---|---|
| `lsblk` | visualizar discos e partições |
| `lsblk -f` | visualizar discos, partições e sistemas de arquivos |
| `blkid` | identificar UUID, Label e tipo de sistema de arquivos |

Uma forma simples de lembrar:

    lsblk  → "O que existe e como está organizado?"
    blkid  → "Qual é a identificação dessa partição?"

---

### 4. `UUID` e `LABEL`

**UUID** — *Universally Unique Identifier* — **Identificador Universalmente Único**

Identifica uma partição por um valor único.

**LABEL** — *Label* — **Rótulo/Nome**

É um nome definido para facilitar a identificação do sistema de arquivos.

Exemplo:

    /dev/sda1
    UUID="7c8a..."
    LABEL="SISTEMA"
    TYPE="ext4"

O `UUID` é muito utilizado no `/etc/fstab`, porque o nome `/dev/sda1` pode mudar dependendo da detecção dos discos.

---

### 5. Comandos úteis juntos

Para uma visão rápida:

    lsblk

Para ver sistemas de arquivos:

    lsblk -f

Para consultar identificação:

    sudo blkid

Para consultar uma partição específica:

    sudo blkid /dev/sda1

---

## Resumo LPIC-1

- `lsblk` → lista discos e partições.
- `lsblk -f` → mostra sistemas de arquivos, UUID e pontos de montagem.
- `blkid` → mostra identificação das partições.
- `UUID` → identificador único.
- `LABEL` → nome/rótulo do sistema de arquivos.
- `TYPE` → tipo do sistema de arquivos, como `ext4`, `xfs` ou `swap`.
- `lsblk` ajuda a entender a **estrutura** dos dispositivos.
- `blkid` ajuda a identificar as **características** das partições.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
