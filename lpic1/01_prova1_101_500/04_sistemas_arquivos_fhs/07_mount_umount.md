# 07 — mount e umount

## mount — Mount a Filesystem (Montar um Sistema de Arquivos)

O comando `mount` conecta um **sistema de arquivos** a um **diretório**, chamado ponto de montagem.

    mount /dev/sda1 /mnt

Nesse exemplo:

- `/dev/sda1` — partição que será montada
- `/mnt` — Mount Point (Ponto de Montagem)

### Montar usando UUID

    mount UUID=a1b2-c3d4 /mnt

O UUID identifica a partição mesmo que o nome do dispositivo mude.

### Ver sistemas montados

    mount

Ou:

    findmnt

`findmnt` — find mounts (encontrar montagens)

---

## umount — Unmount (Desmontar)

Remove a montagem de um sistema de arquivos.

    umount /mnt

Também pode usar o dispositivo:

    umount /dev/sda1

### Atenção

Não confunda:

    umount

com:

    unmount

O comando correto no Linux é **`umount`**.

---

## Ponto de Montagem — Mount Point

O sistema de arquivos precisa ser associado a um diretório.

    /dev/sda1
         │
         ▼
       /mnt
         │
         ▼
    arquivos acessíveis

Depois da montagem, o conteúdo de `/dev/sda1` fica acessível através de `/mnt`.

---

## Opções importantes

### `mount -a`

    mount -a

`-a` — all (todos)

Monta os sistemas de arquivos configurados no `/etc/fstab`, respeitando as regras desse arquivo.

### `mount -t`

    mount -t ext4 /dev/sda1 /mnt

`-t` — type (tipo)

Indica o tipo do sistema de arquivos.

### `mount -o`

    mount -o ro /dev/sda1 /mnt

`-o` — options (opções)

Permite especificar opções de montagem.

`ro` — read-only (somente leitura)

---

## Opções comuns

| Opção | Inglês | Português |
|---|---|---|
| `-a` | all | todos |
| `-t` | type | tipo |
| `-o` | options | opções |
| `ro` | read-only | somente leitura |
| `rw` | read-write | leitura e escrita |

---

## mount × umount

| Comando | Função |
|---|---|
| `mount` | Montar |
| `umount` | Desmontar |
| `findmnt` | Encontrar/ver montagens |
| `mount -a` | Montar entradas do `/etc/fstab` |

### Fluxo básico

    Dispositivo
         ↓
    /dev/sda1
         ↓
    mount
         ↓
    /mnt
         ↓
    Arquivos disponíveis

    /mnt
      ↓
    umount
      ↓
    Sistema de arquivos desmontado

---

## LPIC-1 — O que saber

- **mount** — montar um sistema de arquivos.
- **umount** — desmontar um sistema de arquivos.
- **Mount Point** — ponto de montagem.
- Saber montar uma partição em um diretório.
- Saber desmontar pelo diretório ou dispositivo.
- Conhecer `mount -a`.
- Conhecer `mount -t` e `mount -o`.
- Entender a relação entre `mount`, `/etc/fstab`, UUID e pontos de montagem.
- Antes de desmontar, verificar se o sistema de arquivos não está sendo usado.

---

## Resumo

    mount  → montar
    umount → desmontar

    /dev/sda1
         ↓
       mount
         ↓
       /mnt
         ↓
      arquivos
         ↓
       umount

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
