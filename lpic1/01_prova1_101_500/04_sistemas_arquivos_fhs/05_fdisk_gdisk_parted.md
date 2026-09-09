# Sistemas de Arquivos e FHS

## 05 — fdisk, gdisk e parted

**Partitioning Tools — Ferramentas de Particionamento**

`fdisk`, `gdisk` e `parted` são ferramentas usadas para visualizar e gerenciar **Partition Tables — Tabelas de Partições**.

> ⚠️ Operações de particionamento podem causar perda de dados. Sempre confirme o disco correto antes de alterar qualquer coisa.

---

## 1. `fdisk` — Disk Partitioning — Particionamento de Disco

O `fdisk` é uma ferramenta tradicional para criar, excluir e modificar partições.

Pode trabalhar com:

- MBR;
- GPT.

### Listar discos e partições

    sudo fdisk -l

`-l` — list — listar.

Exemplo:

    Disk /dev/sda: 500 GiB
    Disklabel type: gpt

---

## 2. Abrir um disco com `fdisk`

    sudo fdisk /dev/sda

O `fdisk` entra em um modo interativo.

Para mostrar os comandos disponíveis:

    m

---

## 3. Comandos principais do `fdisk`

Dentro do `fdisk`:

| Comando | English | Português |
|---|---|---|
| `m` | menu | mostrar ajuda |
| `p` | print | mostrar tabela |
| `n` | new | criar partição |
| `d` | delete | excluir partição |
| `t` | type | alterar tipo |
| `l` | list | listar tipos de partição |
| `w` | write | gravar alterações |
| `q` | quit | sair sem gravar |

### Visualizar a tabela

    p

### Criar partição

    n

### Excluir partição

    d

### Gravar alterações

    w

### Sair sem gravar

    q

---

## 4. Fluxo básico com `fdisk`

    sudo fdisk /dev/sda

Depois:

    p
    n
    p
    1
    Enter
    Enter
    w

A sequência exata depende do disco e do particionamento existente.

**Nunca execute comandos de alteração sem confirmar primeiro o dispositivo.**

---

# gdisk

## 5. `gdisk` — GPT fdisk — Particionamento GPT

O `gdisk` é uma ferramenta especializada em tabelas **GPT — GUID Partition Table — Tabela de Partições GUID**.

Abrir um disco:

    sudo gdisk /dev/sda

Mostrar ajuda:

    ?

---

## 6. Comandos principais do `gdisk`

Dentro do `gdisk`:

| Comando | English | Português |
|---|---|---|
| `p` | print | mostrar tabela |
| `n` | new | criar partição |
| `d` | delete | excluir partição |
| `t` | type | alterar tipo |
| `l` | list | listar tipos |
| `v` | verify | verificar |
| `w` | write | gravar alterações |
| `q` | quit | sair sem gravar |

O funcionamento é parecido com o `fdisk`, mas o `gdisk` é voltado para GPT.

---

## 7. `fdisk` × `gdisk`

| Ferramenta | Principal uso |
|---|---|
| `fdisk` | MBR e GPT em versões modernas |
| `gdisk` | GPT |
| `parted` | MBR e GPT |

Para LPIC-1, lembre:

    fdisk → particionamento geral
    gdisk → GPT
    parted → diferentes tabelas de partição

---

# parted

## 8. `parted` — Partition Editor — Editor de Partições

O `parted` é outra ferramenta para criar e administrar partições.

Pode trabalhar com:

- MBR;
- GPT;
- outros formatos de tabela de partição.

Listar discos:

    sudo parted -l

`-l` — list — listar.

---

## 9. Abrir um disco com `parted`

    sudo parted /dev/sda

Mostrar a tabela:

    print

Exemplo:

    (parted) print

---

## 10. Criar uma tabela GPT

Dentro do `parted`:

    mklabel gpt

**Atenção:** criar uma nova tabela de partições pode destruir a estrutura de partições existente.

---

## 11. Criar uma tabela MBR

No `parted`:

    mklabel msdos

No `parted`, `msdos` representa o esquema tradicional **MBR**.

---

## 12. Criar uma partição

Exemplo:

    mkpart primary ext4 1MiB 10GiB

Significado:

- `mkpart` → make partition — criar partição;
- `primary` → primária;
- `ext4` → tipo indicado;
- `1MiB` → início;
- `10GiB` → fim.

> `parted` define a partição; a criação real do sistema de arquivos normalmente é feita depois com `mkfs`.

Exemplo:

    sudo mkfs.ext4 /dev/sda1

---

## 13. Verificar alinhamento

O `parted` possui recursos para verificar o alinhamento das partições.

Dentro do `parted`:

    align-check optimal 1

**Alignment — Alinhamento**

Ajuda a garantir que a partição esteja alinhada adequadamente ao dispositivo de armazenamento.

---

## 14. Comandos principais do `parted`

| Comando | English | Português |
|---|---|---|
| `print` | print | mostrar tabela |
| `mklabel` | make label | criar tabela de partições |
| `mkpart` | make partition | criar partição |
| `rm` | remove | remover partição |
| `resizepart` | resize partition | alterar final da partição |
| `name` | name | definir nome |
| `align-check` | alignment check | verificar alinhamento |
| `quit` | quit | sair |

---

## 15. Visualizar informações

### `fdisk`

    sudo fdisk -l

### `gdisk`

    sudo gdisk -l /dev/sda

### `parted`

    sudo parted -l

Todos podem ajudar a identificar a estrutura do disco.

---

## 16. Depois de criar uma partição

Criar a partição **não significa que ela já possui um sistema de arquivos**.

Exemplo:

    sudo fdisk /dev/sda

Depois de criar `/dev/sda1`:

    sudo mkfs.ext4 /dev/sda1

Criar ponto de montagem:

    sudo mkdir /mnt/dados

Montar:

    sudo mount /dev/sda1 /mnt/dados

Fluxo:

    Disco
      ↓
    Tabela de Partições
      ↓
    Partição
      ↓
    Sistema de Arquivos
      ↓
    Mount Point
      ↓
    Arquivos

---

## 17. Comparação rápida

| Recurso | `fdisk` | `gdisk` | `parted` |
|---|---:|---:|---:|
| Visualizar partições | ✓ | ✓ | ✓ |
| Criar partições | ✓ | ✓ | ✓ |
| Excluir partições | ✓ | ✓ | ✓ |
| MBR | ✓ | — | ✓ |
| GPT | ✓ | ✓ | ✓ |
| Interface interativa | ✓ | ✓ | ✓ |
| Ferramenta especializada em GPT | — | ✓ | — |
| Verificar alinhamento | — | — | ✓ |

---

## Resumo LPIC-1

- `fdisk` → ferramenta de particionamento.
- `fdisk -l` → lista discos e partições.
- `fdisk /dev/sda` → abre o disco para gerenciamento.
- `p` → mostra a tabela no `fdisk`.
- `n` → cria partição.
- `d` → exclui partição.
- `t` → altera tipo.
- `w` → grava alterações.
- `q` → sai sem gravar.
- `gdisk` → ferramenta especializada em GPT.
- `gdisk /dev/sda` → abre um disco GPT.
- `parted` → ferramenta de particionamento que suporta diferentes tabelas.
- `parted -l` → lista informações dos discos.
- `mklabel gpt` → cria uma tabela GPT.
- `mklabel msdos` → cria uma tabela MBR.
- `mkpart` → cria uma partição.
- `rm` → remove uma partição no `parted`.
- Criar uma partição **não cria automaticamente um sistema de arquivos**.
- `mkfs.ext4 /dev/sda1` → cria um sistema de arquivos ext4.
- `mount` → disponibiliza o sistema de arquivos em um diretório.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
