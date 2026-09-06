Particionamento

Partition — Partição

Uma Partition (Partição) é uma divisão de um disco.

Um único disco pode ser dividido em várias partes:

SSD 500 GB
│
├── Partição 1 → 100 GB
├── Partição 2 → 300 GB
└── Partição 3 → 100 GB

Cada partição pode ter um sistema de arquivos diferente.

---

Por que usar partições?

Podemos separar diferentes partes do sistema.

Exemplo:

/dev/sda1 → /
/dev/sda2 → /home
/dev/sda3 → swap

Assim, os arquivos pessoais em "/home" podem ficar separados dos arquivos do sistema.

---

Partition Table — Tabela de Partições

O computador precisa saber como o disco está dividido.

Essa informação fica em uma Partition Table (Tabela de Partições).

Os dois formatos mais importantes são:

- MBR
- GPT

---

MBR — Master Boot Record

É um formato mais antigo de tabela de partições.

Características importantes:

- Mais antigo
- Limite de aproximadamente 2 TB por disco
- Até 4 partições primárias

---

GPT — GUID Partition Table

É o formato mais moderno.

Características:

- Suporta discos muito maiores
- Permite muitas partições
- Trabalha muito bem com UEFI
- Possui mecanismos melhores de proteção da tabela

---

MBR x GPT

MBR| GPT
Mais antigo| Mais moderno
Até ~2 TB| Suporta discos muito maiores
4 partições primárias| Muitas partições
Comum em BIOS| Comum em UEFI

---

Comando

"lsblk" — List Block Devices (Listar Dispositivos de Bloco)

Mostra discos e suas partições.

lsblk

Exemplo:

NAME   SIZE TYPE
sda    500G disk
├─sda1 100G part
├─sda2 300G part
└─sda3 100G part

---

LPIC-1 — O que saber

- Partição é uma divisão do disco.
- Um disco pode possuir várias partições.
- MBR é mais antigo.
- GPT é mais moderno.
- MBR possui limite tradicional de aproximadamente 2 TB.
- MBR permite até 4 partições primárias.
- GPT permite muito mais partições.
- UEFI normalmente trabalha com GPT.
- "lsblk" mostra discos e partições.

---

Resumo

Disco
  ↓
Tabela de Partições
  ↓
Partições
  ↓
Sistema de Arquivos
  ↓
Arquivos

Principais formatos:

MBR → antigo
GPT → moderno
