# Sistemas de Arquivos e FHS

## 03 — Discos e Partições

**Disk — Disco**

É o dispositivo físico usado para armazenar dados.

Exemplos:

    /dev/sda
    /dev/sdb
    /dev/nvme0n1

**Partition — Partição**

É uma divisão lógica de um disco.

Exemplo:

    /dev/sda1
    /dev/sda2
    /dev/sda3

---

## 1. Disco × Partição × Sistema de Arquivos

São coisas diferentes:

    Disco
       ↓
    Partição
       ↓
    Sistema de Arquivos
       ↓
    Arquivos

Exemplo:

    /dev/sda
       ├── /dev/sda1 → ext4 → /
       ├── /dev/sda2 → swap
       └── /dev/sda3 → ext4 → /home

**Importante:**

- Disco = dispositivo de armazenamento.
- Partição = divisão do disco.
- Sistema de arquivos = estrutura usada para armazenar arquivos.

---

## 2. `/dev/sda` — Primeiro disco SATA/SCSI

Em sistemas Linux, discos podem receber nomes como:

    /dev/sda
    /dev/sdb
    /dev/sdc

Normalmente:

- `sd` → tipo de nomenclatura do dispositivo.
- `a` → primeiro disco.
- `b` → segundo disco.
- `c` → terceiro disco.

Exemplo:

    /dev/sda → primeiro disco
    /dev/sdb → segundo disco

---

## 3. Partições em `/dev/sda`

As partições recebem números:

    /dev/sda1
    /dev/sda2
    /dev/sda3

Exemplo:

    /dev/sda
    ├── /dev/sda1
    ├── /dev/sda2
    └── /dev/sda3

`/dev/sda1` significa:

**primeira partição do disco `/dev/sda`.**

---

## 4. NVMe — Non-Volatile Memory Express

Discos NVMe usam outra nomenclatura.

Exemplo:

    /dev/nvme0n1

Uma partição:

    /dev/nvme0n1p1

Observe o `p` antes do número.

    /dev/nvme0n1p1
                    ↑
              primeira partição

Outro exemplo:

    /dev/nvme0n1p2
    /dev/nvme0n1p3

---

## 5. HDD × SSD

**HDD — Hard Disk Drive — Unidade de Disco Rígido**

Utiliza discos magnéticos e partes mecânicas.

**SSD — Solid State Drive — Unidade de Estado Sólido**

Utiliza memória flash e não possui partes mecânicas móveis.

**NVMe — Non-Volatile Memory Express**

É um protocolo de armazenamento utilizado normalmente em SSDs conectados por PCIe.

---

## 6. Tabela de Partições

**Partition Table — Tabela de Partições**

Armazena informações sobre as partições existentes no disco.

Os dois formatos principais são:

- **MBR — Master Boot Record — Registro Mestre de Inicialização**
- **GPT — GUID Partition Table — Tabela de Partições GUID**

Exemplo:

    /dev/sda
       ↓
    GPT
       ↓
    /dev/sda1
    /dev/sda2
    /dev/sda3

A tabela de partições não é o mesmo que o sistema de arquivos.

---

## 7. MBR

**MBR — Master Boot Record — Registro Mestre de Inicialização**

É um esquema de particionamento mais antigo.

Características importantes:

- tradicionalmente até 4 partições primárias;
- permite partições estendidas e lógicas;
- limitações para discos grandes;
- associado historicamente ao BIOS.

Exemplo:

    /dev/sda1
    /dev/sda2
    /dev/sda3
    /dev/sda4

---

## 8. GPT

**GPT — GUID Partition Table — Tabela de Partições GUID**

É o esquema moderno de particionamento.

Características:

- suporta discos muito grandes;
- permite muitas partições;
- possui mecanismos de proteção da tabela;
- é normalmente utilizado com sistemas **UEFI — Unified Extensible Firmware Interface — Interface de Firmware Extensível Unificada**.

Exemplo:

    /dev/nvme0n1p1
    /dev/nvme0n1p2
    /dev/nvme0n1p3

---

## 9. Partição Primária, Estendida e Lógica

Esses conceitos são principalmente relacionados ao **MBR**.

**Primary Partition — Partição Primária**

Pode ser usada diretamente para armazenar um sistema de arquivos.

**Extended Partition — Partição Estendida**

Funciona como um contêiner para partições lógicas.

**Logical Partition — Partição Lógica**

Fica dentro de uma partição estendida.

Modelo:

    Disco
    ├── Primária
    ├── Primária
    ├── Estendida
    │   ├── Lógica
    │   └── Lógica
    └── Primária

No GPT, essa divisão entre primária, estendida e lógica não é utilizada da mesma forma.

---

## 10. Ver os discos e partições

### `lsblk` — List Block Devices — Listar Dispositivos de Bloco

    lsblk

Exemplo:

    NAME        SIZE TYPE
    sda         500G disk
    ├─sda1      100G part
    └─sda2      400G part

Com sistemas de arquivos:

    lsblk -f

`-f` — filesystem — sistema de arquivos.

---

## 11. `fdisk` — Partition Table Manipulation — Manipulação da Tabela de Partições

Listar discos e partições:

    sudo fdisk -l

`-l` — list — listar.

O `fdisk` também pode ser utilizado para criar, alterar e remover partições.

Exemplo:

    sudo fdisk /dev/sda

> Alterar partições pode causar perda de dados. Sempre confirme o disco correto antes de modificar.

---

## 12. `blkid` — Block Device Identification — Identificação de Dispositivos de Bloco

Mostra informações como:

- UUID;
- LABEL;
- TYPE;
- dispositivo.

Exemplo:

    sudo blkid

Resultado:

    /dev/sda1: UUID="..." TYPE="ext4"

---

## 13. Montar uma partição

Uma partição precisa estar associada a um **Mount Point — Ponto de Montagem** para que seus arquivos sejam acessados pelo sistema.

Exemplo:

    sudo mount /dev/sda1 /mnt

Agora o conteúdo da partição pode ser acessado através de:

    /mnt

O comando `mount` não cria a partição. Ele apenas monta um sistema de arquivos existente.

---

## 14. Partição sem sistema de arquivos

Uma partição pode existir sem um sistema de arquivos utilizável.

Exemplo:

    /dev/sda1

Para criar um sistema de arquivos ext4:

    sudo mkfs.ext4 /dev/sda1

Depois:

    sudo mount /dev/sda1 /mnt

Fluxo:

    Disco
      ↓
    Partição
      ↓
    Sistema de Arquivos
      ↓
    Mount Point
      ↓
    Arquivos

---

## 15. Swap

**Swap — Área de Troca**

É uma área usada pelo sistema para gerenciamento de memória.

Pode ser:

- uma partição dedicada;
- um arquivo de swap.

Exemplo:

    /dev/sda2

Pode ser configurada como swap com:

    sudo mkswap /dev/sda2

Ativar:

    sudo swapon /dev/sda2

---

## 16. Comandos principais

| Comando | English | Português | Função |
|---|---|---|---|
| `lsblk` | List Block Devices | Listar dispositivos de bloco | Ver discos e partições |
| `fdisk` | Disk Partitioning | Particionamento de disco | Gerenciar partições |
| `gdisk` | GPT Disk | Disco GPT | Gerenciar GPT |
| `parted` | Partition Editor | Editor de partições | Gerenciar partições |
| `blkid` | Block Device Identification | Identificação de dispositivos | Ver UUID, LABEL e tipo |
| `mount` | Mount | Montar | Montar sistema de arquivos |
| `umount` | Unmount | Desmontar | Desmontar sistema de arquivos |
| `mkfs` | Make Filesystem | Criar sistema de arquivos | Formatar uma partição |
| `mkswap` | Make Swap | Criar swap | Preparar área de swap |
| `swapon` | Swap On | Ativar swap | Ativar swap |
| `swapoff` | Swap Off | Desativar swap | Desativar swap |

---

## Resumo LPIC-1

- **Disk — Disco** → dispositivo físico de armazenamento.
- **Partition — Partição** → divisão lógica de um disco.
- `/dev/sda` → disco tradicionalmente identificado como primeiro `sd`.
- `/dev/sda1` → primeira partição de `/dev/sda`.
- `/dev/nvme0n1` → dispositivo NVMe.
- `/dev/nvme0n1p1` → primeira partição do NVMe.
- **MBR** → esquema de particionamento mais antigo.
- **GPT** → esquema moderno de particionamento.
- **Primary — Primária**, **Extended — Estendida** e **Logical — Lógica** são conceitos principalmente relacionados ao MBR.
- `lsblk` → visualizar discos e partições.
- `fdisk -l` → listar informações de particionamento.
- `blkid` → visualizar UUID, LABEL e tipo do sistema de arquivos.
- `mkfs` → criar sistema de arquivos.
- `mount` → montar um sistema de arquivos.
- `umount` → desmontar.
- **Partição ≠ Sistema de Arquivos**.
- **Mount Point — Ponto de Montagem** → diretório onde o sistema de arquivos é disponibilizado.
- **Swap** → área usada para gerenciamento de memória.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
