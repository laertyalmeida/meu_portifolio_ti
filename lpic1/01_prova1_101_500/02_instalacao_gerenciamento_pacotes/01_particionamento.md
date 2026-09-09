# Instalação e Gerenciamento de Pacotes

## 01 — Particionamento

### Partition — Partição

**Partition — Partição** é uma divisão lógica de um disco.  
Cada partição pode receber um sistema de arquivos diferente.

Exemplo de um disco:

    /dev/sda
    ├── /dev/sda1
    ├── /dev/sda2
    └── /dev/sda3

- `/dev` — devices — dispositivos
- `/dev/sda` — primeiro disco SATA/SCSI
- `/dev/sda1` — primeira partição
- `/dev/sda2` — segunda partição

Em discos NVMe:

    /dev/nvme0n1
    ├── /dev/nvme0n1p1
    └── /dev/nvme0n1p2

- `nvme0n1` — primeiro dispositivo NVMe
- `p1` — partição 1
- `p2` — partição 2

---

## Partition Table — Tabela de Partições

A **Partition Table — Tabela de Partições** registra onde as partições estão localizadas no disco.

Os dois formatos mais importantes são:

| Formato | Nome | Característica |
|---|---|---|
| MBR | Master Boot Record — Registro Mestre de Inicialização | Mais antigo |
| GPT | GUID Partition Table — Tabela de Partições GUID | Mais moderno |

### MBR

Limitações importantes:

- normalmente até 4 partições primárias;
- discos maiores que 2 TiB não são totalmente endereçados;
- utiliza o início do disco para armazenar informações de inicialização e partições.

### GPT

Vantagens:

- suporta discos muito maiores;
- permite muitas partições;
- possui cópia de informações importantes no final do disco;
- trabalha muito bem com UEFI.

---

## Partition Types — Tipos de Partição

No Linux, uma partição pode ser usada para diferentes finalidades.

Exemplo:

    /dev/sda1    → /boot
    /dev/sda2    → /
    /dev/sda3    → /home
    /dev/sda4    → swap

- `/boot` — boot — inicialização
- `/` — root — raiz do sistema
- `/home` — home — diretórios pessoais dos usuários
- `swap` — área de troca de memória

A partição **não é o mesmo que sistema de arquivos**.

Exemplo:

    /dev/sda2
         ↓
    partição
         ↓
    ext4
         ↓
    sistema de arquivos
         ↓
    /


## Filesystem — Sistema de Arquivos

Depois de criar uma partição, podemos criar um sistema de arquivos nela.

Exemplos:

- `ext4` — Fourth Extended Filesystem — Quarto Sistema de Arquivos Estendido
- `xfs` — X File System — Sistema de Arquivos X
- `btrfs` — B-tree File System — Sistema de Arquivos baseado em B-tree
- `vfat` — Virtual File Allocation Table — Tabela Virtual de Alocação de Arquivos
- `swap` — área de troca

Exemplo:

    sudo mkfs.ext4 /dev/sda2

- `mkfs` — Make Filesystem — criar sistema de arquivos
- `ext4` — tipo do sistema de arquivos
- `sudo` — Superuser Do — executar como superusuário

**Atenção:** `mkfs` cria um sistema de arquivos e pode destruir os dados existentes na partição.

---

## Comandos importantes

### lsblk — List Block Devices — Listar Dispositivos de Bloco

    lsblk

Mostra discos, partições e dispositivos de bloco.

Para mostrar sistemas de arquivos:

    lsblk -f

- `-f` — filesystem — sistema de arquivos

---

### fdisk — Fixed Disk — Gerenciador de Partições

    sudo fdisk /dev/sda

Usado principalmente para visualizar e modificar tabelas de partições.

Listar as partições:

    sudo fdisk -l

- `-l` — list — listar

---

### gdisk — GPT fdisk — Gerenciador de Partições GPT

    sudo gdisk /dev/sda

É utilizado principalmente para trabalhar com tabelas **GPT**.

---

### parted — Partition Editor — Editor de Partições

    sudo parted /dev/sda

Também permite criar, remover e modificar partições.

---

## Verificação rápida

Para identificar discos e partições:

    lsblk -f

Para visualizar a tabela de partições:

    sudo fdisk -l

Para verificar UUID e sistema de arquivos:

    blkid

- `blkid` — Block Device Identification — identificação de dispositivos de bloco

---

## Fluxo básico

O processo normalmente segue esta lógica:

    Disco
      ↓
    Tabela de Partições
      ↓
    Partição
      ↓
    Sistema de Arquivos
      ↓
    Mount Point — Ponto de Montagem
      ↓
    Uso pelo sistema

Exemplo:

    /dev/sda
       ↓
    GPT
       ↓
    /dev/sda2
       ↓
    ext4
       ↓
    /
       ↓
    Sistema Linux

---

## Resumo LPIC-1

- **Partition — Partição** = divisão de um disco.
- **Partition Table — Tabela de Partições** = estrutura que organiza as partições.
- **MBR** = formato antigo de tabela de partições.
- **GPT** = formato moderno e mais flexível.
- `/dev/sda` = disco.
- `/dev/sda1` = primeira partição.
- `/dev/nvme0n1p1` = primeira partição de um dispositivo NVMe.
- `lsblk` = visualizar discos e partições.
- `fdisk` = gerenciar partições.
- `gdisk` = gerenciar principalmente GPT.
- `parted` = gerenciar partições.
- `mkfs` = criar sistema de arquivos.
- `blkid` = identificar UUID e sistema de arquivos.
- **Partição ≠ sistema de arquivos**.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
