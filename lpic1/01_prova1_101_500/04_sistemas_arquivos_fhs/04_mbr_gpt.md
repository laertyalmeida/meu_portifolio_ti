# Sistemas de Arquivos e FHS

## 04 — MBR e GPT

**Partition Table — Tabela de Partições**

A tabela de partições define como um disco é dividido em partições e guarda informações necessárias para que o sistema reconheça essa organização.

Os dois formatos principais são:

- **MBR — Master Boot Record — Registro Mestre de Inicialização**
- **GPT — GUID Partition Table — Tabela de Partições GUID**

---

## 1. MBR — Master Boot Record

O **MBR** é um padrão antigo de particionamento.

Sua estrutura tradicional fica localizada no início do disco.

Características:

- suporta até **4 partições primárias**;
- pode usar uma partição **Extended — Estendida** para criar partições lógicas;
- utiliza endereçamento tradicional com limitações para discos grandes;
- pode ser utilizado com sistemas baseados em **BIOS — Basic Input/Output System — Sistema Básico de Entrada/Saída**.

Exemplo:

    /dev/sda
    ├── /dev/sda1
    ├── /dev/sda2
    ├── /dev/sda3
    └── /dev/sda4

---

## 2. Partições Estendidas e Lógicas no MBR

O MBR permite até quatro entradas de partição primária.

Para criar mais partições, uma delas pode ser uma:

**Extended Partition — Partição Estendida**

Dentro dela podem existir:

**Logical Partitions — Partições Lógicas**

Exemplo:

    /dev/sda
    ├── /dev/sda1 → Primária
    ├── /dev/sda2 → Primária
    ├── /dev/sda3 → Estendida
    │   ├── /dev/sda5 → Lógica
    │   └── /dev/sda6 → Lógica
    └── /dev/sda4 → Primária

> As partições lógicas tradicionalmente começam em números a partir de `5`.

---

## 3. Limitação do MBR

Uma das principais limitações do MBR é o uso tradicional de endereçamento de setores de **32 bits**, que limita o tamanho de um disco endereçável a aproximadamente **2 TiB** quando usados setores de 512 bytes.

Por isso, o MBR não é adequado para discos modernos muito grandes.

---

## 4. GPT — GUID Partition Table

**GPT — GUID Partition Table — Tabela de Partições GUID**

É o padrão moderno de particionamento.

Foi desenvolvido como parte do padrão **UEFI — Unified Extensible Firmware Interface — Interface de Firmware Extensível Unificada**.

Características:

- suporta discos muito maiores que 2 TiB;
- permite muitas partições;
- possui cópia de estruturas importantes no início e no final do disco;
- utiliza **GUID — Globally Unique Identifier — Identificador Globalmente Exclusivo** para identificar partições;
- funciona muito bem com sistemas UEFI.

---

## 5. Estrutura simplificada do GPT

Um disco GPT possui estruturas no início e no final do disco.

Modelo simplificado:

    ┌─────────────────────────────┐
    │ Protective MBR             │
    ├─────────────────────────────┤
    │ GPT Header                 │
    ├─────────────────────────────┤
    │ Partition Entries          │
    ├─────────────────────────────┤
    │                             │
    │ Partições / Dados           │
    │                             │
    ├─────────────────────────────┤
    │ Backup Partition Entries   │
    ├─────────────────────────────┤
    │ Backup GPT Header          │
    └─────────────────────────────┘

A existência de estruturas de backup ajuda na recuperação da tabela caso uma cópia seja danificada.

---

## 6. Protective MBR — MBR de Proteção

Um disco GPT normalmente contém um **Protective MBR — MBR de Proteção** no início.

Sua função principal é ajudar a impedir que ferramentas antigas que entendem apenas MBR tratem o disco GPT como vazio e sobrescrevam suas estruturas.

Ele não transforma o disco GPT em um disco MBR.

---

## 7. GPT e número de partições

O GPT não possui a limitação tradicional de quatro partições primárias do MBR.

O número máximo depende principalmente da implementação e do espaço reservado para as entradas da tabela.

Em muitos sistemas Linux, é comum encontrar:

    /dev/sda1
    /dev/sda2
    /dev/sda3
    ...
    /dev/sda128

Em sistemas UEFI, também é comum existir uma:

**ESP — EFI System Partition — Partição de Sistema EFI**

Normalmente formatada como:

    FAT32

Exemplo:

    /dev/sda1 → EFI System Partition
    /dev/sda2 → Linux filesystem
    /dev/sda3 → Linux filesystem

---

## 8. MBR × GPT

| Característica | MBR | GPT |
|---|---|---|
| Nome | Master Boot Record | GUID Partition Table |
| Português | Registro Mestre de Inicialização | Tabela de Partições GUID |
| Época | Mais antigo | Moderno |
| Partições primárias | Até 4 | Não possui essa limitação tradicional |
| Partições lógicas | Sim | Não utiliza esse modelo |
| Disco > 2 TiB | Limitado | Sim |
| Identificação | Estrutura tradicional | GUID |
| Backup da tabela | Não possui o mesmo mecanismo | Sim |
| UEFI | Pode existir em alguns cenários | Padrão recomendado |
| BIOS | Compatível | Pode funcionar com BIOS, dependendo da configuração |

---

## 9. BIOS × UEFI

Não confunda:

**MBR/GPT** → esquema de particionamento.

**BIOS/UEFI** → firmware responsável pela inicialização do computador.

Uma associação comum é:

    BIOS → MBR

e:

    UEFI → GPT

Mas não são equivalentes.

É possível encontrar configurações diferentes, dependendo do sistema e da forma de inicialização.

---

## 10. EFI System Partition

**ESP — EFI System Partition — Partição de Sistema EFI**

É usada em sistemas que inicializam através de UEFI.

Características:

- normalmente utiliza FAT32;
- contém arquivos `.efi`;
- geralmente é montada em:

    /boot/efi

Exemplo:

    /dev/nvme0n1p1
        ↓
    FAT32
        ↓
    /boot/efi

---

## 11. Identificar MBR ou GPT

### `fdisk`

    sudo fdisk -l

Pode mostrar:

    Disklabel type: gpt

ou:

    Disklabel type: dos

Em `fdisk`, `dos` normalmente indica uma tabela **MBR**.

---

### `parted`

    sudo parted -l

Pode mostrar:

    Partition Table: gpt

ou:

    Partition Table: msdos

`gpt` → GPT.

`msdos` → MBR.

---

## 12. `gdisk` — GPT fdisk

**gdisk — GPT fdisk — Ferramenta de particionamento GPT**

É uma ferramenta voltada para discos GPT.

Exemplo:

    sudo gdisk /dev/sda

Enquanto:

    sudo fdisk /dev/sda

é tradicionalmente associado ao particionamento MBR, embora versões modernas do `fdisk` também trabalhem com GPT.

---

## 13. `parted`

**parted — Partition Editor — Editor de Partições**

Pode trabalhar com diferentes tipos de tabela de partições.

Exemplo:

    sudo parted /dev/sda

Para visualizar:

    sudo parted -l

---

## 14. Como identificar rapidamente

Ver a tabela de partições:

    sudo fdisk -l

Se aparecer:

    Disklabel type: dos

→ **MBR**

Se aparecer:

    Disklabel type: gpt

→ **GPT**

Com `parted`:

    Partition Table: msdos

→ **MBR**

    Partition Table: gpt

→ **GPT**

---

## 15. Exemplo de disco MBR

    /dev/sda
    │
    ├── MBR
    │
    ├── /dev/sda1 → ext4 → /
    ├── /dev/sda2 → swap
    ├── /dev/sda3 → extended
    │       ├── /dev/sda5 → ext4
    │       └── /dev/sda6 → ext4
    │
    └── espaço restante

---

## 16. Exemplo de disco GPT + UEFI

    /dev/nvme0n1
    │
    ├── GPT
    │
    ├── /dev/nvme0n1p1 → FAT32 → /boot/efi
    ├── /dev/nvme0n1p2 → ext4  → /
    └── /dev/nvme0n1p3 → ext4  → /home

---

## Resumo LPIC-1

- **MBR** → Master Boot Record — Registro Mestre de Inicialização.
- **GPT** → GUID Partition Table — Tabela de Partições GUID.
- MBR é um padrão mais antigo.
- GPT é o padrão moderno.
- MBR → tradicionalmente até 4 partições primárias.
- MBR → pode usar partição estendida e partições lógicas.
- MBR → possui limitação tradicional de aproximadamente 2 TiB com setores de 512 bytes.
- GPT → suporta discos muito maiores que 2 TiB.
- GPT → permite muitas partições.
- GPT → possui estruturas de backup.
- GPT → utiliza GUIDs para identificação.
- GPT normalmente é utilizado junto com UEFI.
- **MBR/GPT não são BIOS/UEFI**: são esquemas de particionamento.
- **ESP** → EFI System Partition — Partição de Sistema EFI.
- ESP normalmente usa FAT32 e pode ser montada em `/boot/efi`.
- `fdisk -l` → pode identificar a tabela como `dos` (MBR) ou `gpt`.
- `parted -l` → pode mostrar `msdos` (MBR) ou `gpt`.
- `gdisk` → ferramenta voltada para GPT.
- `parted` → ferramenta que trabalha com diferentes tabelas de partição.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
