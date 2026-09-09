# Sistemas de Arquivos e FHS

## 10 — Sistemas de Arquivos Linux

### 1. O que é um sistema de arquivos?

**Filesystem** — **Sistema de Arquivos**

É a estrutura usada pelo Linux para organizar e armazenar arquivos e diretórios em uma partição ou dispositivo.

Importante:

    Disco → Partição → Sistema de Arquivos → Arquivos

Exemplo:

    /dev/sda1 → ext4 → /home

A partição `/dev/sda1` pode receber um sistema de arquivos `ext4`.

---

### 2. `ext4`

**ext4** — *Fourth Extended Filesystem* — **Quarto Sistema de Arquivos Estendido**

É um dos sistemas de arquivos mais comuns no Linux.

Características:

- Suporta arquivos e sistemas de arquivos grandes.
- Possui **journaling** — **registro de alterações**.
- É muito utilizado em distribuições Linux.
- É uma escolha comum para `/` e `/home`.

Exemplo:

    sudo mkfs.ext4 /dev/sdb1

**mkfs** — *Make Filesystem* — **Criar Sistema de Arquivos**

---

### 3. `ext2` e `ext3`

**ext2** — *Second Extended Filesystem* — **Segundo Sistema de Arquivos Estendido**

- Não possui journaling.
- É mais antigo.

**ext3** — *Third Extended Filesystem* — **Terceiro Sistema de Arquivos Estendido**

- Sucessor do ext2.
- Adicionou journaling.

**ext4** é a evolução do ext3.

    ext2 → ext3 → ext4

---

### 4. `XFS`

**XFS** — *X File System* — **Sistema de Arquivos X**

É um sistema de arquivos de alto desempenho, conhecido por trabalhar bem com arquivos e sistemas de arquivos grandes.

Exemplo:

    sudo mkfs.xfs /dev/sdb1

Comando relacionado:

    xfs_info /dev/sdb1

---

### 5. `Btrfs`

**Btrfs** — *B-tree File System* — **Sistema de Arquivos B-tree**

É um sistema de arquivos moderno com recursos avançados.

Características importantes:

- **Snapshots** — **instantâneos**
- **Subvolumes** — **subvolumes**
- **Compression** — **compressão**
- **Checksums** — **somas de verificação**
- Recursos de gerenciamento avançado

Exemplo:

    sudo mkfs.btrfs /dev/sdb1

---

### 6. `VFAT` / `FAT32`

**FAT32** — *File Allocation Table 32* — **Tabela de Alocação de Arquivos 32**

É muito utilizado em dispositivos removíveis e também pode ser usado na:

**ESP** — *EFI System Partition* — **Partição de Sistema EFI**

Exemplo:

    sudo mkfs.vfat /dev/sdb1

---

### 7. `NTFS`

**NTFS** — *New Technology File System* — **Sistema de Arquivos de Nova Tecnologia**

É o principal sistema de arquivos tradicional do Windows.

O Linux pode trabalhar com NTFS, sendo útil principalmente para acessar partições compartilhadas com Windows.

---

### 8. `swap`

**swap** — **espaço de troca**

Não é utilizado como um sistema de arquivos comum para armazenar arquivos.

É utilizado pelo Linux como espaço de memória virtual.

Criar:

    sudo mkswap /dev/sdb2

Ativar:

    sudo swapon /dev/sdb2

Desativar:

    sudo swapoff /dev/sdb2

---

### 9. Sistemas de arquivos virtuais

Nem tudo em `/proc` e `/sys` está armazenado fisicamente no disco.

**procfs** — *Process Filesystem* — **Sistema de Arquivos de Processos**

Normalmente montado em:

    /proc

Fornece informações sobre:

- Processos
- Kernel
- Memória
- CPU
- Sistema

**sysfs** — *System Filesystem* — **Sistema de Arquivos do Sistema**

Normalmente montado em:

    /sys

Fornece informações sobre:

- Hardware
- Dispositivos
- Kernel
- Drivers

---

### 10. Identificar o sistema de arquivos

Use:

    lsblk -f

ou:

    sudo blkid

Exemplo:

    NAME   FSTYPE LABEL  UUID
    sda1   ext4   ROOT   1234-abcd
    sda2   ext4   HOME   5678-efgh
    sda3   swap          9012-ijkl

---

### 11. Criar um sistema de arquivos

O comando `mkfs` cria um sistema de arquivos em uma partição.

Exemplo:

    sudo mkfs.ext4 /dev/sdb1

Outros exemplos:

    sudo mkfs.xfs /dev/sdb1
    sudo mkfs.btrfs /dev/sdb1
    sudo mkfs.vfat /dev/sdb1

**Atenção:** `mkfs` normalmente apaga os dados existentes na partição. Deve ser usado somente quando a partição puder ser formatada.

---

### 12. Verificar um sistema de arquivos

**fsck** — *Filesystem Check* — **Verificação do Sistema de Arquivos**

É usado para verificar e, dependendo do sistema de arquivos e das opções, reparar problemas.

Exemplo:

    sudo fsck /dev/sdb1

Para ext4:

    sudo e2fsck /dev/sdb1

> Normalmente, o sistema de arquivos deve estar desmontado antes de uma verificação/reparo com `fsck`.

---

### 13. Comparação rápida

| Sistema | Característica principal |
|---|---|
| `ext2` | antigo, sem journaling |
| `ext3` | ext2 + journaling |
| `ext4` | muito comum no Linux |
| `xfs` | desempenho e grandes volumes |
| `btrfs` | snapshots e recursos avançados |
| `vfat/FAT32` | compatibilidade e ESP |
| `ntfs` | comum no Windows |
| `swap` | memória virtual |

---

## Resumo LPIC-1

- **Filesystem** → sistema de arquivos.
- `ext4` → sistema de arquivos Linux muito comum.
- `ext3` → adicionou journaling ao ext2.
- `xfs` → sistema de arquivos de alto desempenho.
- `btrfs` → sistema moderno com snapshots e subvolumes.
- `vfat/FAT32` → comum em mídias removíveis e ESP.
- `ntfs` → sistema de arquivos tradicional do Windows.
- `swap` → espaço usado para memória virtual.
- `mkfs` → cria um sistema de arquivos.
- `mkswap` → prepara uma área para swap.
- `fsck` → verifica sistemas de arquivos.
- `lsblk -f` e `blkid` → identificam sistemas de arquivos.
- `/proc` → informações de processos e sistema.
- `/sys` → informações de hardware, dispositivos e kernel.
- **Partição ≠ sistema de arquivos**.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
