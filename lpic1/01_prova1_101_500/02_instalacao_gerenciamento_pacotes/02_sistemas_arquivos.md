# Instalação e Gerenciamento de Pacotes

## 02 — Sistemas de Arquivos

### Filesystem — Sistema de Arquivos

**Filesystem — Sistema de Arquivos** é a estrutura usada pelo Linux para organizar e armazenar arquivos e diretórios dentro de uma partição ou dispositivo.

Exemplo:

    /dev/sda2
        ↓
      ext4
        ↓
    /
    ├── etc
    ├── home
    ├── var
    └── usr

---

## Principais sistemas de arquivos

| Filesystem | Tradução | Uso comum |
|---|---|---|
| `ext4` | Fourth Extended Filesystem — Quarto Sistema de Arquivos Estendido | Linux |
| `xfs` | X File System — Sistema de Arquivos X | Servidores/Linux |
| `btrfs` | B-tree File System — Sistema de Arquivos B-tree | Linux |
| `vfat` | Virtual File Allocation Table — Tabela Virtual de Alocação de Arquivos | Compatibilidade/EFI |
| `exfat` | Extended File Allocation Table — Tabela Estendida de Alocação de Arquivos | Pendrives e cartões |
| `ntfs` | New Technology File System — Sistema de Arquivos de Nova Tecnologia | Windows |
| `swap` | Swap — Área de Troca | Memória virtual |

---

## ext4

**ext4 — Fourth Extended Filesystem — Quarto Sistema de Arquivos Estendido**

É um dos sistemas de arquivos Linux mais utilizados.

Características:

- suporta arquivos e partições grandes;
- possui **journaling — registro de alterações**;
- permite verificar e reparar o sistema de arquivos;
- é uma escolha comum para instalações Linux.

Criar:

    sudo mkfs.ext4 /dev/sda2

- `mkfs` — Make Filesystem — criar sistema de arquivos
- `.ext4` — sistema de arquivos escolhido

---

## XFS

**XFS — X File System — Sistema de Arquivos X**

É muito utilizado em servidores e ambientes que trabalham com grandes volumes de dados.

Criar:

    sudo mkfs.xfs /dev/sda2

---

## Btrfs

**Btrfs — B-tree File System — Sistema de Arquivos B-tree**

Possui recursos avançados, como:

- snapshots — instantâneos;
- subvolumes — subvolumes;
- compressão;
- checksums — somas de verificação.

Criar:

    sudo mkfs.btrfs /dev/sda2

---

## VFS

**VFS — Virtual File System — Sistema de Arquivos Virtual**

É uma camada do kernel que permite ao Linux trabalhar com diferentes sistemas de arquivos usando uma interface comum.

Exemplo:

    ext4
      ↓
     VFS
      ↓
    Kernel
      ↓
    Disco

Assim, comandos como:

    ls
    cd
    cp
    mv

podem trabalhar com diferentes sistemas de arquivos sem precisar conhecer todos os detalhes internos de cada um.

---

## Criar um sistema de arquivos

O comando `mkfs` é usado para criar um sistema de arquivos.

Exemplo:

    sudo mkfs.ext4 /dev/sdb1

Fluxo:

    Disco
      ↓
    Partição
      ↓
    mkfs.ext4
      ↓
    Sistema de arquivos ext4
      ↓
    mount
      ↓
    Diretório disponível

**Cuidado:** criar um sistema de arquivos normalmente apaga ou torna inacessíveis os dados existentes naquela partição.

---

## Identificar o sistema de arquivos

### lsblk — List Block Devices — Listar Dispositivos de Bloco

    lsblk -f

- `-f` — filesystem — sistema de arquivos

Exemplo de informação:

    NAME   FSTYPE   UUID
    sda
    ├─sda1 vfat     XXXX-XXXX
    └─sda2 ext4     xxxxxxxx-xxxx

---

### blkid — Block Device Identification — Identificação de Dispositivo de Bloco

    sudo blkid

Mostra informações como:

- dispositivo;
- tipo de sistema de arquivos;
- UUID;
- LABEL — rótulo.

---

## Verificar um sistema de arquivos

### fsck — Filesystem Check — Verificação do Sistema de Arquivos

    sudo fsck /dev/sda2

É usado para verificar e, quando possível, corrigir problemas no sistema de arquivos.

**Importante:** normalmente o sistema de arquivos deve estar desmontado antes de executar uma verificação/reparo.

---

## Mount — Montagem

Um sistema de arquivos precisa ser **montado** para ficar disponível em um diretório.

Exemplo:

    sudo mount /dev/sda2 /mnt

- `mount` — montar
- `/mnt` — mount — ponto de montagem temporário

Depois:

    ls /mnt

---

## Umount — Desmontagem

Para remover o sistema de arquivos do ponto de montagem:

    sudo umount /mnt

- `umount` — unmount — desmontar

---

## Formatação × Particionamento

São operações diferentes:

**Partitioning — Particionamento**

    Disco
      ↓
    /dev/sda1
    /dev/sda2
    /dev/sda3

**Formatting — Formatação**

    /dev/sda2
        ↓
      ext4

Ou seja:

**Particionar** divide o disco.

**Formatar** cria um sistema de arquivos na partição.

---

## Resumo LPIC-1

- **Filesystem — Sistema de Arquivos** = organiza os dados em uma partição/dispositivo.
- `ext4` = sistema de arquivos Linux muito comum.
- `xfs` = bastante usado em servidores.
- `btrfs` = possui recursos avançados, como snapshots.
- `vfat` = comum em partições EFI.
- `exfat` = comum em mídias removíveis.
- `ntfs` = sistema de arquivos associado ao Windows.
- **VFS** = Virtual File System — camada que permite ao Linux trabalhar com diferentes sistemas de arquivos.
- `mkfs` = criar sistema de arquivos.
- `lsblk -f` = visualizar sistemas de arquivos.
- `blkid` = identificar UUID e sistemas de arquivos.
- `fsck` = verificar/reparar sistemas de arquivos.
- `mount` = montar.
- `umount` = desmontar.
- **Particionar ≠ formatar**.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
