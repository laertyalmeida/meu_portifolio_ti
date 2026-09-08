# 09 — UUID e Labels

## UUID — Universally Unique Identifier (Identificador Único Universal)

O **UUID** é um identificador único usado para identificar um sistema de arquivos.

Exemplo:

    UUID=a1b2-c3d4-5678

Em vez de depender do nome do dispositivo:

    /dev/sda1

podemos usar:

    UUID=a1b2-c3d4-5678

Isso é muito útil no `/etc/fstab`.

---

## LABEL — Label (Rótulo)

O **LABEL** é um nome definido para identificar um sistema de arquivos.

Exemplo:

    LABEL=Dados

Diferente do UUID, o LABEL pode ser escolhido pelo administrador.

Exemplos:

    LABEL=Sistema
    LABEL=Dados
    LABEL=Backup

---

## UUID × LABEL

| Identificação | Inglês | Português | Exemplo |
|---|---|---|---|
| UUID | Universally Unique Identifier | Identificador Único Universal | `UUID=a1b2-c3d4` |
| LABEL | Label | Rótulo | `LABEL=Dados` |

### Memorize

    UUID  → identificador único
    LABEL → nome/rótulo escolhido

---

## Ver UUID e LABEL

### blkid — Block Device Identification (Identificação de Dispositivos de Bloco)

    blkid

Exemplo:

    /dev/sda1: UUID="a1b2-c3d4" TYPE="ext4" LABEL="Sistema"

---

### lsblk -f — List Block Devices + Filesystem

    lsblk -f

`-f` — filesystem (sistema de arquivos)

Mostra informações como:

    NAME   FSTYPE  LABEL    UUID
    sda1   ext4    Sistema  a1b2-c3d4

---

## Criar ou alterar LABEL

Para sistemas de arquivos **ext2/ext3/ext4**:

    e2label /dev/sda1 Dados

`e2label` — ferramenta para definir o LABEL de sistemas de arquivos ext.

Outra opção:

    tune2fs -L Dados /dev/sda1

`-L` — label (rótulo)

### Atenção

O comando para alterar LABEL depende do tipo de filesystem.

---

## Usando UUID no /etc/fstab

Exemplo:

    UUID=a1b2-c3d4  /dados  ext4  defaults  0  2

Interpretação:

    UUID
      ↓
    identifica a partição
      ↓
    /dados
      ↓
    ponto de montagem
      ↓
    ext4
      ↓
    tipo do filesystem

---

## Usando LABEL no /etc/fstab

Também podemos usar:

    LABEL=Dados  /dados  ext4  defaults  0  2

Assim, o Linux procura o filesystem que possui o LABEL `Dados`.

---

## Por que usar UUID ou LABEL?

O nome `/dev/sda1` pode não ser a melhor forma de identificação em configurações persistentes.

Por isso, no `/etc/fstab`, é comum utilizar:

    UUID=...

ou:

    LABEL=...

### Memorize

    /dev/sda1 → nome do dispositivo

    UUID=... → identificador único

    LABEL=... → nome/rótulo

---

## LPIC-1 — O que saber

- **UUID** — identifica unicamente um filesystem.
- **LABEL** — nome/rótulo atribuído ao filesystem.
- `blkid` — mostra UUID, LABEL e TYPE.
- `lsblk -f` — mostra informações dos filesystems.
- Saber usar UUID no `/etc/fstab`.
- Saber usar LABEL no `/etc/fstab`.
- Conhecer `e2label` para sistemas ext.
- Entender que a ferramenta usada para alterar LABEL depende do filesystem.

---

## Resumo

    /dev/sda1
       ↓
    dispositivo

    UUID=a1b2-c3d4
       ↓
    identificador único

    LABEL=Dados
       ↓
    rótulo/nome

    /etc/fstab
       ↓
    UUID=... ou LABEL=...

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
