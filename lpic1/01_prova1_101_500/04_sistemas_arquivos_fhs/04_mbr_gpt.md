# 04 — MBR e GPT

## MBR — Master Boot Record (Registro Mestre de Inicialização)

O **MBR** é um esquema antigo de particionamento usado para organizar as partições de um disco.

    Disco
    ┌────────┬────────┬────────┬────────┐
    │ MBR    │ Part.1 │ Part.2 │ Part.3 │
    └────────┴────────┴────────┴────────┘

### Características

- **Master Boot Record** — Registro Mestre de Inicialização.
- Suporta até **4 partições primárias**.
- Pode utilizar **Extended Partition (Partição Estendida)**.
- Dentro da partição estendida podem existir **Logical Partitions (Partições Lógicas)**.
- Limite tradicional de aproximadamente **2 TiB** por disco, dependendo do tamanho do setor.
- Mais antigo que o GPT.

### Estrutura MBR

    MBR
     │
     ├── Primária
     ├── Primária
     ├── Primária
     └── Estendida
             │
             ├── Lógica
             ├── Lógica
             └── Lógica

---

## GPT — GUID Partition Table (Tabela de Partições GUID)

O **GPT** é um esquema moderno de particionamento criado para substituir as limitações do MBR.

    Disco
    ┌────────┬────────┬────────┬────────┐
    │ GPT    │ Part.1 │ Part.2 │ Part.3 │
    └────────┴────────┴────────┴────────┘
                                     
                    GPT de backup
                         ↓
    ┌──────────────────────────────────┐
    │ cópia da tabela no final do disco│
    └──────────────────────────────────┘

### Características

- **GUID Partition Table** — Tabela de Partições GUID.
- Suporta discos muito maiores que 2 TiB.
- Permite muitas partições.
- Não utiliza o conceito de partição estendida/lógica.
- Mantém uma cópia de proteção da estrutura de particionamento.
- É normalmente utilizado em sistemas modernos com **UEFI — Unified Extensible Firmware Interface (Interface de Firmware Extensível Unificada)**.

---

## Protective MBR — MBR de Proteção

Discos GPT normalmente possuem um **Protective MBR (MBR de Proteção)**.

Sua função é evitar que ferramentas antigas que entendem apenas MBR interpretem o disco GPT como vazio e tentem sobrescrevê-lo.

    GPT
     ↓
    Protective MBR
     ↓
    Proteção contra ferramentas antigas

---

## MBR × GPT

| Característica | MBR | GPT |
|---|---|---|
| Nome | Master Boot Record | GUID Partition Table |
| Tradução | Registro Mestre de Inicialização | Tabela de Partições GUID |
| Época | Antigo | Moderno |
| Disco grande | Limitação tradicional ~2 TiB | Suporta discos muito maiores |
| Partições primárias | Até 4 | Muitas |
| Estendida/Lógica | Sim | Não |
| Backup da tabela | Não da mesma forma | Sim |
| UEFI | Pode funcionar | Comum |

---

## BIOS × UEFI

### BIOS — Basic Input/Output System (Sistema Básico de Entrada/Saída)

Firmware tradicional usado em computadores mais antigos.

### UEFI — Unified Extensible Firmware Interface (Interface de Firmware Extensível Unificada)

Firmware moderno que substitui o BIOS em muitos computadores atuais.

### Relação comum

    BIOS → MBR
    UEFI → GPT

**Atenção:** essa relação não é absoluta. Existem combinações diferentes dependendo do sistema e da configuração.

---

## Comandos relacionados

### fdisk — Partition Table Manipulator (Manipulador de Tabela de Partições)

    fdisk -l

`-l` — list (listar)

Pode ser usado para visualizar e gerenciar tabelas de partição.

### gdisk — GPT fdisk (fdisk para GPT)

    gdisk /dev/sda

Voltado principalmente para discos com **GPT**.

---

## LPIC-1 — O que saber

- **MBR** = Master Boot Record.
- **GPT** = GUID Partition Table.
- MBR suporta até **4 partições primárias**.
- MBR pode usar **partição estendida e lógica**.
- MBR possui limite tradicional de aproximadamente **2 TiB**.
- GPT suporta discos muito maiores.
- GPT permite muitas partições.
- GPT não utiliza partições estendidas/lógicas.
- Conhecer **Protective MBR — MBR de Proteção**.
- Saber a relação comum entre **BIOS/MBR** e **UEFI/GPT**.
- `fdisk` e `gdisk` são ferramentas importantes para particionamento.

---

## Resumo

    MBR
     ↓
    antigo
     ↓
    até 4 primárias
     ↓
    estendida + lógicas
     ↓
    ~2 TiB tradicionalmente

    GPT
     ↓
    moderno
     ↓
    muitas partições
     ↓
    discos muito grandes
     ↓
    comum com UEFI

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
