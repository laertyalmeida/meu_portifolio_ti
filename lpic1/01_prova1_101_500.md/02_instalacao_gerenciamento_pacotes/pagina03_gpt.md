# 📖 HQ 2 — INSTALAÇÃO DO LINUX E GERENCIAMENTO DE PACOTES

# 📖 PÁGINA 3 — GPT

# 🧠 1. O QUE É GPT?

**GPT = GUID Partition Table**

Tradução:

**Tabela de Partições de GUID**

GPT é um padrão moderno utilizado para organizar as partições de um disco.

É normalmente utilizado em computadores modernos com **UEFI**.

---

# 💽 2. GPT x MBR

A diferença principal:

```text
MBR
→ padrão antigo
→ tradicionalmente associado ao BIOS
→ limitações de tamanho e quantidade de partições

GPT
→ padrão moderno
→ normalmente utilizado com UEFI
→ suporta discos muito maiores
→ suporta muitas mais partições
```

---

# 🔢 3. GPT E QUANTIDADE DE PARTIÇÕES

Ao contrário do MBR, o GPT não possui a limitação de apenas 4 partições primárias.

A quantidade máxima depende principalmente da implementação e do sistema operacional.

No Linux, é comum utilizar:

```text
/boot
/
/home
swap
...
```

sem precisar utilizar o conceito de partição estendida/lógica do MBR.

---

# 💾 4. GPT E DISCOS GRANDES

Uma das principais vantagens do GPT é permitir o uso de discos muito maiores que o limite tradicional do MBR.

```text
MBR
→ aproximadamente 2 TiB
```

```text
GPT
→ suporta discos muito maiores
```

Para a prova, memorize essa diferença.

---

# 🛡️ 5. CÓPIAS DA TABELA GPT

O GPT mantém informações da tabela de partições:

- No início do disco.
- Uma cópia de backup no final do disco.

Isso aumenta a capacidade de recuperação caso a estrutura principal seja danificada.

Representação:

```text
INÍCIO DO DISCO
┌──────────────────────────────┐
│ GPT / informações principais │
├──────────────────────────────┤
│                              │
│          PARTIÇÕES           │
│                              │
├──────────────────────────────┤
│ GPT / backup                 │
└──────────────────────────────┘
FINAL DO DISCO
```

---

# 🔑 6. O QUE É GUID?

**GUID = Globally Unique Identifier**

Tradução:

**Identificador Globalmente Único**

Cada partição GPT possui um identificador próprio.

Isso ajuda a identificar as partições de maneira única.

---

# 🥾 7. GPT E UEFI

Em sistemas inicializados utilizando UEFI, normalmente existe uma:

**ESP = EFI System Partition**

Tradução:

**Partição de Sistema EFI**

Ela é utilizada para armazenar arquivos necessários para a inicialização.

Exemplo:

```text
DISCO GPT
│
├── ESP
├── /
├── /home
└── swap
```

A ESP será estudada com mais detalhes na parte de **UEFI/boot**.

---

# 🔍 8. IDENTIFICANDO GPT COM `fdisk`

Podemos verificar a tabela de partições:

```bash
sudo fdisk -l
```

Na saída podemos encontrar:

```text
Disklabel type: gpt
```

Isso indica que o disco utiliza uma tabela de partições GPT.

---

# 🛠️ 9. `fdisk`

O comando:

```bash
sudo fdisk /dev/sda
```

abre o disco para gerenciamento de partições.

Dentro do `fdisk`, o comando:

```text
p
```

mostra a tabela de partições.

### Tradução

**p = print → mostrar/imprimir**

---

# 🔎 10. `parted`

Outro comando importante para trabalhar com partições é:

```bash
sudo parted -l
```

### Tradução

`parted`

→ **partition editor → editor de partições**

`-l`

→ **list → listar**

Portanto:

```bash
parted -l
```

→ lista informações sobre os discos e suas partições.

O `parted` suporta tabelas de partições como:

- MBR
- GPT

---

# 🧠 11. `lsblk`

Também podemos visualizar a estrutura dos discos e partições usando:

```bash
lsblk
```

### Tradução

`ls`

→ **list → listar**

`blk`

→ **block → bloco**

Portanto:

**lsblk → listar dispositivos de bloco**

---

# 📝 12. COMANDOS NECESSÁRIOS

### Ver a tabela de partições

```bash
sudo fdisk -l
```

**-l = list → listar**

Procure por:

```text
Disklabel type: gpt
```

---

### Listar discos e partições

```bash
lsblk
```

**ls = list → listar**

**blk = block → bloco**

---

### Listar partições com `parted`

```bash
sudo parted -l
```

**parted → partition editor → editor de partições**

**-l = list → listar**

---

### Abrir um disco no `fdisk`

```bash
sudo fdisk /dev/sda
```

Dentro dele:

```text
p
```

**print → mostrar**

---

# 🎯 13. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O significado de GPT.
- Que GPT significa **GUID Partition Table**.
- O significado de GUID.
- Que GPT é uma tabela de partições moderna.
- A relação entre GPT e UEFI.
- Que GPT não possui a limitação de 4 partições primárias do MBR.
- Que GPT suporta discos muito maiores que o limite tradicional do MBR.
- Que GPT mantém informações principais e uma cópia de backup da tabela.
- O que é uma ESP.
- O significado de EFI System Partition.
- Usar `fdisk -l`.
- Reconhecer `Disklabel type: gpt`.
- Conhecer `parted`.
- Usar `parted -l`.
- Usar `lsblk`.
- Saber diferenciar GPT de MBR.

---

# 🧠 RESUMO

```text
GPT
│
├── GUID Partition Table
│
├── padrão moderno
│
├── normalmente usado com UEFI
│
├── suporta discos muito grandes
│
├── suporta muitas partições
│
├── não precisa de partições estendidas/lógicas
│
└── possui informações de backup da tabela
```

# ⚖️ MBR x GPT

```text
MBR
├── antigo
├── BIOS
├── até 4 primárias
└── ≈ 2 TiB no esquema tradicional

GPT
├── moderno
├── UEFI
├── muitas partições
├── discos muito maiores
└── tabela com backup
```

# 🔑 PALAVRAS-CHAVE

```text
GPT
→ GUID Partition Table
→ Tabela de Partições de GUID

GUID
→ Globally Unique Identifier
→ Identificador Globalmente Único

UEFI
→ firmware moderno

ESP
→ EFI System Partition
→ Partição de Sistema EFI

fdisk
→ gerenciamento de partições

parted
→ editor de partições

lsblk
→ listar dispositivos de bloco
```

# 🎯 PARA MEMORIZAR

```text
BIOS → tradicionalmente MBR

UEFI → normalmente GPT

MBR → limitações maiores

GPT → discos grandes + muitas partições
```

# ✅ FIM DA PÁGINA 3
