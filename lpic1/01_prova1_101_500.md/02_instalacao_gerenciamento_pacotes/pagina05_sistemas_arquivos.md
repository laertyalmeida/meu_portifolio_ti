# 📖 HQ 2 — INSTALAÇÃO DO LINUX E GERENCIAMENTO DE PACOTES

# 📖 PÁGINA 5 — SISTEMAS DE ARQUIVOS

# 🧠 1. O QUE É UM SISTEMA DE ARQUIVOS?

Um **sistema de arquivos (filesystem)** é a estrutura utilizada pelo sistema operacional para **organizar e controlar os dados armazenados** em um dispositivo.

Ele define como arquivos e diretórios são armazenados e encontrados.

Exemplo:

```text
PARTIÇÃO
    ↓
SISTEMA DE ARQUIVOS
    ↓
DIRETÓRIOS
    ↓
ARQUIVOS
```

Sem um sistema de arquivos, uma partição não possui a estrutura normal necessária para armazenar arquivos e diretórios de forma organizada.

---

# 💾 2. SISTEMAS DE ARQUIVOS NO LINUX

Existem vários sistemas de arquivos que podem ser utilizados no Linux.

Os principais que você deve reconhecer para a prova são:

```text
ext2
ext3
ext4
XFS
Btrfs
```

---

# 🐧 3. EXT2

**ext2 = Second Extended Filesystem**

Tradução:

**Segundo Sistema de Arquivos Estendido**

É uma versão antiga da família ext.

Uma característica importante:

**ext2 não possui journaling.**

---

# 📓 4. EXT3

**ext3 = Third Extended Filesystem**

Tradução:

**Terceiro Sistema de Arquivos Estendido**

É baseado no ext2 e adicionou:

**journaling**

### Journaling

→ registro de operações do sistema de arquivos.

O journaling ajuda na recuperação do sistema de arquivos após determinadas interrupções inesperadas, como uma queda de energia.

---

# 🚀 5. EXT4

**ext4 = Fourth Extended Filesystem**

Tradução:

**Quarto Sistema de Arquivos Estendido**

É uma evolução do ext3.

Características importantes:

- Journaling
- Suporte a arquivos grandes
- Suporte a sistemas de arquivos grandes
- Muito utilizado em sistemas Linux

Para a prova:

```text
ext2
→ sem journaling

ext3
→ journaling

ext4
→ evolução do ext3 + journaling
```

---

# 🗂️ 6. XFS

**XFS** é um sistema de arquivos de alto desempenho.

É conhecido por funcionar bem com:

- Arquivos grandes
- Sistemas de arquivos grandes
- Grandes volumes de dados

Para a LPIC-1, reconheça:

**XFS → sistema de arquivos Linux com journaling e foco em escalabilidade/desempenho.**

---

# 🌳 7. BTRFS

**Btrfs = B-tree File System**

Tradução aproximada:

**Sistema de Arquivos baseado em B-tree**

É um sistema de arquivos moderno do Linux.

Possui recursos como:

- Snapshots
- Subvolumes
- Copy-on-write
- Checksums

Para a prova, o mais importante é reconhecer:

**Btrfs → sistema de arquivos moderno com recursos avançados, como snapshots e subvolumes.**

---

# 📓 8. O QUE É JOURNALING?

Journaling é uma técnica utilizada por determinados sistemas de arquivos para registrar operações antes de efetivá-las completamente.

Imagine:

```text
OPERAÇÃO
   ↓
REGISTRO NO JOURNAL
   ↓
ALTERAÇÃO DO SISTEMA DE ARQUIVOS
```

Se ocorrer uma interrupção inesperada, o journal pode ajudar o sistema de arquivos a recuperar operações pendentes.

### Tradução

**journal**

→ diário / registro.

**journaling**

→ registro de operações.

---

# 🔍 9. IDENTIFICANDO O SISTEMA DE ARQUIVOS

O comando:

```bash
lsblk -f
```

mostra informações sobre sistemas de arquivos associados aos dispositivos.

### Tradução

`ls`

→ **list → listar**

`blk`

→ **block → bloco**

`-f`

→ **filesystem → sistema de arquivos**

Exemplo:

```text
NAME   FSTYPE  UUID
sda1   ext4    xxxx-xxxx
sda2   swap    xxxx-xxxx
```

---

# 🧠 10. `blkid`

O comando:

```bash
sudo blkid
```

mostra informações sobre dispositivos, incluindo:

- Tipo do sistema de arquivos
- UUID
- PARTUUID
- Dispositivo

Exemplo:

```text
/dev/sda1: UUID="..." TYPE="ext4"
```

### Tradução

**blkid**

→ **block device identification**

→ identificação de dispositivos de bloco.

---

# 📋 11. `file -s`

Também podemos obter informações sobre o conteúdo de um dispositivo usando:

```bash
sudo file -s /dev/sda1
```

### Tradução

**file**

→ arquivo.

**-s**

→ **special files → arquivos especiais/dispositivos**

O comando pode identificar o tipo de sistema de arquivos encontrado.

Para a prova, o mais importante é conhecer:

```text
lsblk -f
blkid
```

---

# 🧩 12. FORMATAR UM SISTEMA DE ARQUIVOS

O comando `mkfs` é utilizado para criar um sistema de arquivos.

Exemplo:

```bash
sudo mkfs.ext4 /dev/sda1
```

### Tradução

**mkfs = make filesystem**

→ criar sistema de arquivos.

**ext4**

→ tipo de sistema de arquivos.

⚠️ Formatar uma partição destrói os dados existentes nela.

---

# 🛠️ 13. COMANDOS `mkfs`

Exemplos:

```bash
sudo mkfs.ext4 /dev/sda1
```

→ cria um sistema de arquivos ext4.

```bash
sudo mkfs.xfs /dev/sda1
```

→ cria um sistema de arquivos XFS.

O comando:

```bash
mkfs
```

significa:

**make filesystem → criar sistema de arquivos.**

---

# 📝 14. COMANDOS NECESSÁRIOS

### Mostrar sistemas de arquivos

```bash
lsblk -f
```

→ lista dispositivos de bloco e seus sistemas de arquivos.

### Identificar sistemas de arquivos

```bash
sudo blkid
```

→ identifica dispositivos e seus sistemas de arquivos.

### Criar ext4

```bash
sudo mkfs.ext4 /dev/sda1
```

→ cria um sistema de arquivos ext4.

### Criar XFS

```bash
sudo mkfs.xfs /dev/sda1
```

→ cria um sistema de arquivos XFS.

### Identificar o tipo de dispositivo/arquivo

```bash
sudo file -s /dev/sda1
```

→ tenta identificar o conteúdo do dispositivo.

---

# 🎯 15. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que é um sistema de arquivos.
- A diferença entre partição e sistema de arquivos.
- Reconhecer ext2.
- Reconhecer ext3.
- Reconhecer ext4.
- Reconhecer XFS.
- Reconhecer Btrfs.
- Saber o que é journaling.
- Saber que ext2 não possui journaling.
- Saber que ext3 possui journaling.
- Saber que ext4 possui journaling.
- Reconhecer recursos básicos do Btrfs.
- Usar `lsblk -f`.
- Usar `blkid`.
- Conhecer `mkfs`.
- Saber que `mkfs` significa **make filesystem**.
- Saber que `mkfs.ext4` cria um sistema de arquivos ext4.
- Saber que formatar uma partição pode destruir seus dados.

---

# 🧠 RESUMO

```text
PARTIÇÃO
   ↓
RECEBE UM
   ↓
SISTEMA DE ARQUIVOS
   ↓
ORGANIZA
   ↓
ARQUIVOS E DIRETÓRIOS
```

### Principais sistemas:

```text
ext2
→ antigo
→ sem journaling

ext3
→ journaling

ext4
→ evolução do ext3
→ journaling

XFS
→ desempenho
→ grandes volumes

Btrfs
→ moderno
→ snapshots
→ subvolumes
→ copy-on-write
```

---

# 🔑 PALAVRAS-CHAVE

```text
filesystem
→ sistema de arquivos

journal
→ registro

journaling
→ registro de operações

mkfs
→ make filesystem
→ criar sistema de arquivos

lsblk
→ listar dispositivos de bloco

blkid
→ identificar dispositivos de bloco

UUID
→ identificador único do sistema de arquivos
```

# 🎯 PARA MEMORIZAR

```text
ext2 → sem journaling

ext3 → journaling

ext4 → journaling + evolução do ext3

XFS → grandes volumes/desempenho

Btrfs → snapshots/subvolumes
```

# 🧠 COMANDOS PRINCIPAIS

```bash
lsblk -f
```

→ **listar dispositivos de bloco + sistemas de arquivos**

```bash
blkid
```

→ **identificar sistemas de arquivos e UUIDs**

```bash
mkfs.ext4 /dev/sda1
```

→ **criar sistema de arquivos ext4**

# ✅ FIM DA PÁGINA 5
