# Sistemas de Arquivos e FHS

## 09 — UUID e Labels

### 1. UUID

**UUID** — *Universally Unique Identifier* — **Identificador Universalmente Único**

É um identificador usado para identificar um sistema de arquivos de forma única.

Exemplo:

    UUID="7c8a1234-5678-90ab-cdef-1234567890ab"

Uma partição pode ser acessada pelo dispositivo:

    /dev/sda1

ou pelo seu UUID:

    UUID=7c8a1234-5678-90ab-cdef-1234567890ab

O UUID é muito utilizado no `/etc/fstab`.

---

### 2. LABEL

**LABEL** — *Label* — **Rótulo**

É um nome atribuído ao sistema de arquivos para facilitar sua identificação.

Exemplo:

    LABEL=DADOS

Uma partição pode ter:

    UUID="7c8a..."
    LABEL="DADOS"
    TYPE="ext4"

---

### 3. Consultar UUID e LABEL

O comando principal é:

    sudo blkid

Exemplo:

    /dev/sda1: UUID="7c8a..." TYPE="ext4"
    /dev/sdb1: UUID="1234..." LABEL="DADOS" TYPE="ext4"

Também podemos usar:

    lsblk -f

O `lsblk -f` apresenta informações de sistemas de arquivos em uma visão mais organizada.

---

### 4. UUID × LABEL × dispositivo

| Identificação | Exemplo | Característica |
|---|---|---|
| Device — Dispositivo | `/dev/sda1` | nome do dispositivo |
| UUID | `UUID=7c8a...` | identificador único |
| LABEL | `LABEL=DADOS` | nome/rótulo definido pelo usuário |

Exemplo:

    /dev/sdb1
    UUID="1234-abcd"
    LABEL="BACKUP"
    TYPE="ext4"

---

### 5. Usando UUID no `mount`

Montagem usando o dispositivo:

    sudo mount /dev/sdb1 /mnt/dados

Usando UUID:

    sudo mount UUID=1234-abcd /mnt/dados

O UUID permite identificar o sistema de arquivos sem depender do nome `/dev/sdb1`.

---

### 6. Usando LABEL no `mount`

Também podemos montar usando o rótulo:

    sudo mount LABEL=BACKUP /mnt/dados

O Linux procura o sistema de arquivos que possui esse LABEL.

---

### 7. Criar um LABEL

Para sistemas de arquivos **ext2/ext3/ext4**, podemos usar:

    sudo e2label /dev/sdb1 BACKUP

Ou:

    sudo tune2fs -L BACKUP /dev/sdb1

**e2label** — **definir/consultar rótulo de sistemas ext**

**tune2fs** — *Tune2FS* — **ajustar parâmetros do sistema de arquivos ext**

Depois:

    sudo blkid /dev/sdb1

---

### 8. Alterar LABEL de XFS

Para **XFS**, utiliza-se:

    sudo xfs_admin -L BACKUP /dev/sdb1

**xfs_admin** — **administrar parâmetros de sistemas de arquivos XFS**

> O sistema de arquivos deve ser tratado de acordo com suas próprias ferramentas.

---

### 9. LABEL e `/etc/fstab`

O LABEL também pode ser usado no `/etc/fstab`.

Exemplo:

    LABEL=BACKUP  /backup  ext4  defaults  0  2

Isso significa:

    LABEL=BACKUP → sistema de arquivos
    /backup      → ponto de montagem
    ext4         → tipo
    defaults     → opções
    0            → dump
    2            → ordem do fsck

---

### 10. UUID e LABEL no dia a dia

Para descobrir:

    sudo blkid

Para visualizar de forma organizada:

    lsblk -f

Para montar por UUID:

    sudo mount UUID=xxxx-xxxx /mnt/dados

Para montar por LABEL:

    sudo mount LABEL=DADOS /mnt/dados

Para usar automaticamente:

    /etc/fstab

---

## Resumo LPIC-1

- **UUID** → identificador único do sistema de arquivos.
- **LABEL** → nome/rótulo dado ao sistema de arquivos.
- `/dev/sda1` → identificação pelo dispositivo.
- `blkid` → mostra UUID, LABEL e TYPE.
- `lsblk -f` → mostra informações dos sistemas de arquivos.
- `mount UUID=...` → monta usando UUID.
- `mount LABEL=...` → monta usando LABEL.
- UUID e LABEL podem ser usados no `/etc/fstab`.
- `e2label` e `tune2fs -L` → trabalham com LABEL de ext2/ext3/ext4.
- `xfs_admin -L` → altera LABEL de XFS.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
