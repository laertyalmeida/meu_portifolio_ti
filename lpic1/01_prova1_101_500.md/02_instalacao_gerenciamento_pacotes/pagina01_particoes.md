# 📖 HQ 2 — INSTALAÇÃO DO LINUX E GERENCIAMENTO DE PACOTES

# 📖 PÁGINA 1 — PARTIÇÕES

# 🧠 1. O QUE É UMA PARTIÇÃO?

Uma **partição** é uma divisão lógica de um dispositivo de armazenamento.

Imagine um disco de:

**500 GB**

Podemos dividi-lo, por exemplo, em:

```text
DISCO — 500 GB
│
├── Partição 1 — 100 GB
├── Partição 2 — 300 GB
└── Partição 3 — 100 GB
```

Cada partição pode ser utilizada para uma finalidade diferente.

---

# 💽 2. PARTIÇÃO NÃO É SISTEMA DE ARQUIVOS

É importante não confundir:

**Partição**

→ divisão do disco.

**Sistema de arquivos**

→ estrutura utilizada para organizar arquivos dentro de uma partição.

Exemplo:

```text
DISCO
   ↓
PARTIÇÃO
   ↓
SISTEMA DE ARQUIVOS
   ↓
ARQUIVOS E DIRETÓRIOS
```

Uma partição pode receber um sistema de arquivos como:

```text
ext4
xfs
btrfs
```

---

# 🧩 3. POR QUE CRIAR PARTIÇÕES?

As partições permitem separar diferentes áreas do armazenamento.

Um sistema Linux pode, por exemplo, utilizar:

```text
/dev/sda1 → /
/dev/sda2 → /home
/dev/sda3 → swap
```

Isso separa:

- Sistema
- Arquivos dos usuários
- Memória virtual

---

# 🐧 4. PARTIÇÃO `/`

A partição montada em:

```text
/
```

é chamada de:

**root filesystem**

Tradução:

**sistema de arquivos raiz**

Ela é a base da árvore de diretórios do Linux.

Exemplo:

```text
/
├── etc
├── home
├── var
├── usr
├── boot
└── ...
```

---

# 👤 5. PARTIÇÃO `/home`

A partição `/home` pode ser separada da partição raiz.

Ela contém os diretórios pessoais dos usuários.

Exemplo:

```text
/home
├── joao
├── maria
└── usuario
```

Uma vantagem de separar `/home` é facilitar a preservação dos dados dos usuários quando o sistema é reinstalado.

---

# 💾 6. DISPOSITIVOS E PARTIÇÕES

No Linux, discos e partições aparecem como dispositivos.

Exemplo:

```text
/dev/sda
```

→ disco inteiro.

```text
/dev/sda1
```

→ primeira partição.

```text
/dev/sda2
```

→ segunda partição.

Outro exemplo:

```text
/dev/nvme0n1
```

→ dispositivo NVMe.

```text
/dev/nvme0n1p1
```

→ primeira partição desse dispositivo.

---

# 🔍 7. `lsblk`

O comando:

```bash
lsblk
```

é utilizado para listar dispositivos de bloco e suas partições.

### Tradução

`ls`

→ **list → listar**

`blk`

→ **block → bloco**

Portanto:

**lsblk → list block devices → listar dispositivos de bloco**

Exemplo:

```text
NAME        SIZE TYPE
sda         500G disk
├─sda1      100G part
├─sda2      300G part
└─sda3      100G part
```

---

# 🧠 8. INTERPRETANDO `lsblk`

```text
sda
```

→ disco.

```text
sda1
```

→ primeira partição.

```text
sda2
```

→ segunda partição.

```text
TYPE
```

→ tipo do dispositivo.

```text
disk
```

→ disco.

```text
part
```

→ partição.

---

# 🔎 9. `fdisk -l`

O comando:

```bash
sudo fdisk -l
```

lista informações sobre os discos e suas partições.

### Tradução

`fdisk`

→ ferramenta de gerenciamento de discos/partições.

`-l`

→ **list → listar**

Portanto:

**fdisk -l → listar discos e partições**

Ele pode mostrar informações como:

- Tamanho do disco
- Número das partições
- Setores
- Tipo de partição
- Tabela de partições

---

# 🛠️ 10. `fdisk`

O `fdisk` também pode ser utilizado para criar, excluir e modificar partições.

Exemplo:

```bash
sudo fdisk /dev/sda
```

⚠️ É uma ferramenta de administração de discos.

Alterar partições incorretamente pode causar perda de dados.

Para a prova, o mais importante é saber:

**fdisk → ferramenta para gerenciamento de partições.**

---

# 🧩 11. TABELA DE PARTIÇÕES

O disco precisa de uma estrutura que informe ao sistema como suas partições estão organizadas.

As duas estruturas que você precisa conhecer são:

**MBR**

e

**GPT**

Nesta página, basta reconhecer que:

```text
DISCO
   ↓
TABELA DE PARTIÇÕES
   ↓
PARTIÇÕES
```

MBR e GPT serão estudados em detalhes na próxima página.

---

# 📝 12. COMANDOS NECESSÁRIOS

### Listar discos e partições

```bash
lsblk
```

**ls → list → listar**

**blk → block → bloco**

→ lista dispositivos de bloco e partições.

---

### Listar informações das partições

```bash
sudo fdisk -l
```

**fdisk → ferramenta de gerenciamento de discos/partições**

**-l → list → listar**

→ lista informações sobre discos e partições.

---

### Abrir um disco para gerenciamento

```bash
sudo fdisk /dev/sda
```

→ permite trabalhar com as partições do disco `/dev/sda`.

---

# 🎯 13. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que é uma partição.
- Que partição é uma divisão lógica de um dispositivo de armazenamento.
- A diferença entre disco e partição.
- A diferença entre partição e sistema de arquivos.
- O que é a partição `/`.
- O que é `/home`.
- Reconhecer `/dev/sda`.
- Reconhecer `/dev/sda1`.
- Reconhecer `/dev/sda2`.
- Reconhecer dispositivos NVMe, como `/dev/nvme0n1`.
- Reconhecer uma partição NVMe, como `/dev/nvme0n1p1`.
- Usar `lsblk`.
- Entender `disk` e `part` na saída do `lsblk`.
- Usar `fdisk -l`.
- Saber que `-l` significa **list**.
- Saber que `fdisk` é utilizado para gerenciamento de partições.
- Reconhecer MBR e GPT como tabelas de partição.

---

# 🧠 RESUMO

```text
DISCO
   ↓
DIVIDIDO EM
   ↓
PARTIÇÕES
   ↓
RECEBEM
   ↓
SISTEMAS DE ARQUIVOS
   ↓
ARQUIVOS
```

### Exemplos:

```text
/dev/sda
→ disco

/dev/sda1
→ primeira partição

/dev/sda2
→ segunda partição

/dev/nvme0n1
→ disco NVMe

/dev/nvme0n1p1
→ primeira partição NVMe
```

### Comandos:

```text
lsblk
→ list block devices
→ listar dispositivos de bloco

fdisk -l
→ list
→ listar discos/partições
```

# 🎯 PARA MEMORIZAR

```text
PARTIÇÃO
    ↓
DIVISÃO DO DISCO

SISTEMA DE ARQUIVOS
    ↓
ORGANIZA OS DADOS

MONTAGEM
    ↓
DISPONIBILIZA A PARTIÇÃO NA ÁRVORE DO LINUX
```

# ✅ FIM DA PÁGINA 1
