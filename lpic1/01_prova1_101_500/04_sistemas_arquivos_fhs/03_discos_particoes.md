# 03 — Discos e Partições

## Disk — Disco

Um **disk (disco)** é o dispositivo físico usado para armazenar dados.

Exemplos:

    /dev/sda
    /dev/sdb
    /dev/nvme0n1

### Nomes comuns

| Dispositivo | Significado |
|---|---|
| `/dev/sda` | Primeiro disco SATA/SCSI |
| `/dev/sdb` | Segundo disco SATA/SCSI |
| `/dev/nvme0n1` | Primeiro disco NVMe |
| `/dev/sr0` | Unidade óptica |

---

## Partition — Partição

Uma **partition (partição)** é uma divisão lógica de um disco.

    Disco
    /dev/sda
       │
       ├── /dev/sda1
       ├── /dev/sda2
       └── /dev/sda3

Cada partição pode receber um **filesystem (sistema de arquivos)** diferente.

Exemplo:

    /dev/sda1 → ext4
    /dev/sda2 → swap
    /dev/sda3 → XFS

---

## Disk × Partition

| Termo | Tradução | Exemplo |
|---|---|---|
| Disk | Disco | `/dev/sda` |
| Partition | Partição | `/dev/sda1` |
| Filesystem | Sistema de arquivos | `ext4` |
| Mount Point | Ponto de montagem | `/home` |

### Memorize

    /dev/sda
       ↓
      disco

    /dev/sda1
       ↓
     partição

    ext4
       ↓
    filesystem

    /home
       ↓
    ponto de montagem

---

## SATA/SCSI — Nomenclatura

Discos tradicionais costumam aparecer como:

    /dev/sda
    /dev/sdb
    /dev/sdc

As partições recebem números:

    /dev/sda1
    /dev/sda2
    /dev/sda3

---

## NVMe — Nomenclatura

Discos NVMe usam outro padrão:

    /dev/nvme0n1

As partições recebem `p` antes do número:

    /dev/nvme0n1p1
    /dev/nvme0n1p2
    /dev/nvme0n1p3

### Atenção para a prova

    /dev/sda1
          ↑
       partição

    /dev/nvme0n1p1
              ↑
           partição

---

## Partition Table — Tabela de Partições

A **partition table (tabela de partições)** informa ao sistema como o disco está dividido.

Os dois formatos mais importantes são:

    MBR
    GPT

### MBR — Master Boot Record

Formato mais antigo.

- Até 4 partições primárias.
- Pode utilizar partição estendida e lógica.
- Limitação tradicional de aproximadamente 2 TiB.

### GPT — GUID Partition Table

Formato moderno.

- Suporta discos grandes.
- Permite muitas partições.
- Possui mecanismos de proteção e cópia da tabela.
- É comum em sistemas UEFI.

---

## Primary Partition — Partição Primária

No esquema MBR, uma **primary partition (partição primária)** é uma entrada principal da tabela de partições.

    MBR
     ↓
    ├── Primária
    ├── Primária
    ├── Primária
    └── Primária

São possíveis até **4 partições primárias**.

---

## Extended Partition — Partição Estendida

No MBR, uma **extended partition (partição estendida)** permite criar partições lógicas dentro dela.

    Partição estendida
          │
          ├── lógica
          ├── lógica
          └── lógica

Esse conceito é principalmente relacionado ao **MBR**.

---

## Logical Partition — Partição Lógica

Uma **logical partition (partição lógica)** fica dentro de uma partição estendida.

É uma forma de superar a limitação das quatro entradas primárias do MBR.

---

## Block Device — Dispositivo de Bloco

Discos e partições são exemplos de **block devices (dispositivos de bloco)**.

Podemos visualizar com:

    lsblk

Exemplo:

    NAME
    sda
    ├─sda1
    └─sda2

---

## Comandos importantes

### lsblk — List Block Devices (Listar Dispositivos de Bloco)

    lsblk

Lista discos, partições e pontos de montagem.

### fdisk — Partition Table Manipulator (Manipulador de Tabela de Partições)

    fdisk -l

`-l` — list (listar)

Lista os discos e suas partições.

### blkid — Block Device Identification (Identificação de Dispositivos de Bloco)

    blkid

Mostra UUID, LABEL e tipo do filesystem.

---

## Fluxo completo

    Disco
      ↓
    Partição
      ↓
    Filesystem
      ↓
    Mount Point
      ↓
    Arquivos

Exemplo:

    /dev/sda
       ↓
    /dev/sda1
       ↓
    ext4
       ↓
    /home
       ↓
    arquivos do usuário

---

## LPIC-1 — O que saber

- Diferença entre **disco** e **partição**.
- Reconhecer `/dev/sda`, `/dev/sda1` e `/dev/nvme0n1p1`.
- Entender **partition table (tabela de partições)**.
- Conhecer MBR e GPT.
- Saber o conceito de partição primária, estendida e lógica.
- Saber que `/dev/sda1` é uma partição.
- Saber que `lsblk` lista discos e partições.
- Saber que `fdisk -l` lista informações de particionamento.
- Entender a sequência:

    Disco → Partição → Filesystem → Montagem

---

## Resumo

    /dev/sda
       ↓
    Disco

    /dev/sda1
       ↓
    Partição

    ext4
       ↓
    Filesystem

    /home
       ↓
    Mount Point

    Arquivos
       ↓
    Dados

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
