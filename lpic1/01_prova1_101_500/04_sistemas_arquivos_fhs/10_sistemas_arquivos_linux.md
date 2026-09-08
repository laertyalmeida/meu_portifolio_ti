# 10 — Sistemas de Arquivos Linux

## Filesystem — Sistema de Arquivos

O **filesystem** é responsável por organizar e armazenar arquivos e diretórios em uma partição ou dispositivo.

    Disco
      ↓
    Partição
      ↓
    Filesystem
      ↓
    Arquivos e diretórios

---

## ext2 — Second Extended Filesystem (Segundo Sistema de Arquivos Estendido)

Filesystem antigo da família `ext`.

- Não possui **journaling** (registro de alterações).
- Hoje é pouco utilizado.
- Importante conhecer para a prova.

---

## ext3 — Third Extended Filesystem (Terceiro Sistema de Arquivos Estendido)

Evolução do `ext2`.

- Possui **journaling**.
- Maior segurança contra corrupção após desligamentos inesperados.
- Foi muito utilizado em sistemas Linux.

---

## ext4 — Fourth Extended Filesystem (Quarto Sistema de Arquivos Estendido)

Evolução do `ext3` e um dos filesystems Linux mais conhecidos.

- Possui **journaling**.
- Suporta arquivos e sistemas de arquivos grandes.
- É uma opção comum em distribuições Linux.

    /dev/sda1 → ext4 → /home

---

## XFS — X File System (Sistema de Arquivos X)

Filesystem desenvolvido originalmente pela Silicon Graphics e muito utilizado em ambientes Linux.

- Possui **journaling**.
- Bom desempenho com arquivos e sistemas de arquivos grandes.
- Muito usado em servidores.

---

## Btrfs — B-tree File System (Sistema de Arquivos B-tree)

Filesystem moderno com recursos avançados.

- **Snapshots** — instantâneos.
- **Subvolumes** — subvolumes.
- **Checksums** — verificações de integridade.
- Suporte a recursos avançados de gerenciamento.

---

## swap — Swap Space (Espaço de Troca)

Não é um filesystem tradicional para armazenar arquivos.

É utilizado como **espaço de memória virtual**.

    RAM
     ↓
    pouca memória disponível
     ↓
    swap

Pode ser uma partição ou um arquivo.

Exemplo:

    /dev/sda2 → swap

---

## vfat — Virtual FAT (FAT Virtual)

Filesystem baseado na família FAT, muito utilizado em dispositivos compatíveis com vários sistemas.

É comum encontrar `vfat` em:

- Partições EFI.
- Pendrives.
- Cartões de memória.

---

## Filesystem × Journaling

**Journaling — Registro de alterações**

O journaling mantém um registro de operações para ajudar na recuperação do filesystem após uma falha.

    ext3 → journaling
    ext4 → journaling
    XFS  → journaling

---

## Identificar o Filesystem

### lsblk -f — List Block Devices (Listar Dispositivos de Bloco)

    lsblk -f

`-f` — filesystem (sistema de arquivos)

Mostra o tipo do filesystem, LABEL, UUID e ponto de montagem.

---

### blkid — Block Device Identification (Identificação de Dispositivos de Bloco)

    blkid /dev/sda1

Mostra informações como:

    TYPE="ext4"
    UUID="a1b2-c3d4"

---

## Criar um Filesystem

### mkfs — Make Filesystem (Criar Sistema de Arquivos)

    mkfs.ext4 /dev/sda1

`mkfs` — make filesystem (criar sistema de arquivos)

Nesse exemplo, cria um filesystem `ext4` na partição `/dev/sda1`.

### Atenção

Criar um filesystem normalmente **apaga os dados existentes** na partição.

---

## Principais Filesystems

| Filesystem | Característica principal |
|---|---|
| `ext2` | Sem journaling |
| `ext3` | Journaling |
| `ext4` | Evolução do ext3 |
| `XFS` | Bom para grandes volumes |
| `Btrfs` | Recursos avançados |
| `swap` | Memória virtual |
| `vfat` | Compatibilidade e partição EFI |

---

## LPIC-1 — O que saber

- O que é **filesystem**.
- Diferença básica entre `ext2`, `ext3` e `ext4`.
- O que é **journaling**.
- Reconhecer `ext4`, `XFS`, `Btrfs`, `vfat` e `swap`.
- Saber identificar o filesystem com `lsblk -f` e `blkid`.
- Conhecer `mkfs` — Make Filesystem (Criar Sistema de Arquivos).
- Entender que criar um filesystem pode destruir os dados existentes.
- Saber relacionar **partição → filesystem → ponto de montagem**.

---

## Resumo

    Disco
      ↓
    Partição
      ↓
    Filesystem
      ↓
    Montagem
      ↓
    Arquivos

    ext2  → sem journaling
    ext3  → journaling
    ext4  → evolução do ext3
    XFS   → grandes volumes
    Btrfs → recursos avançados
    vfat  → compatibilidade / EFI
    swap  → memória virtual

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
