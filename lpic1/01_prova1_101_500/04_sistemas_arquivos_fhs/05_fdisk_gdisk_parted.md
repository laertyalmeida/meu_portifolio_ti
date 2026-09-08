# 05 — fdisk, gdisk e parted

## fdisk — Partition Table Manipulator (Manipulador de Tabela de Partições)

O `fdisk` é usado para **criar, excluir e alterar partições**.

Também pode ser usado para visualizar informações de particionamento.

### Abrir um disco

    fdisk /dev/sda

### Listar partições

    fdisk -l

`-l` — list (listar)

---

## Comandos interativos do fdisk

Ao executar:

    fdisk /dev/sda

Podemos usar:

| Tecla | Inglês | Português | Função |
|---|---|---|---|
| `p` | print | imprimir/listar | Mostra a tabela de partições |
| `n` | new | nova | Cria uma nova partição |
| `d` | delete | excluir | Exclui uma partição |
| `t` | type | tipo | Altera o tipo da partição |
| `w` | write | gravar | Grava as alterações |
| `q` | quit | sair | Sai sem gravar |

### Atenção

As alterações só são gravadas no disco quando usamos:

    w

`w` — write (gravar)

---

## gdisk — GPT fdisk (fdisk para GPT)

O `gdisk` é uma ferramenta de particionamento voltada principalmente para **GPT — GUID Partition Table (Tabela de Partições GUID)**.

### Abrir um disco

    gdisk /dev/sda

Dentro do `gdisk`, encontramos comandos semelhantes aos do `fdisk`.

| Tecla | Inglês | Português | Função |
|---|---|---|---|
| `p` | print | imprimir/listar | Mostra a tabela |
| `n` | new | nova | Cria partição |
| `d` | delete | excluir | Exclui partição |
| `t` | type | tipo | Altera o tipo |
| `w` | write | gravar | Grava alterações |
| `q` | quit | sair | Sai |

### Memorize

    fdisk  → particionamento geral
    gdisk  → GPT

---

## parted — Partition Editor (Editor de Partições)

O `parted` é outra ferramenta para **criar, excluir e modificar partições**.

Pode trabalhar com diferentes esquemas de particionamento, incluindo:

    MBR
    GPT

### Abrir um disco

    parted /dev/sda

### Listar discos e partições

    parted -l

`-l` — list (listar)

### Dentro do parted

    print

`print` — imprimir/listar

Mostra a tabela de partições do disco.

---

## Criar uma tabela GPT com parted

    parted /dev/sda
    mklabel gpt

`mklabel` — make label (criar rótulo/tabela)

`gpt` — GUID Partition Table (Tabela de Partições GUID)

### Atenção

Criar uma nova tabela de partições pode **destruir as informações de particionamento existentes**.

---

## fdisk × gdisk × parted

| Comando | Principal uso | MBR | GPT |
|---|---|---:|---:|
| `fdisk` | Gerenciar partições | ✓ | ✓ |
| `gdisk` | Gerenciar GPT | — | ✓ |
| `parted` | Gerenciar partições | ✓ | ✓ |

---

## Fluxo básico

    Disco
      ↓
    /dev/sda
      ↓
    fdisk / gdisk / parted
      ↓
    Tabela de partições
      ↓
    Partições
      ↓
    Filesystem
      ↓
    Montagem

---

## Exemplo prático

### Ver discos

    lsblk

### Ver tabela de partições

    fdisk -l

### Abrir o disco

    fdisk /dev/sda

### Criar uma partição

    n

### Verificar

    p

### Gravar

    w

---

## LPIC-1 — O que saber

- `fdisk` — ferramenta de particionamento.
- `gdisk` — ferramenta voltada para GPT.
- `parted` — editor de partições com suporte a MBR e GPT.
- `fdisk -l` — listar informações de particionamento.
- `parted -l` — listar discos e partições.
- Conhecer `p`, `n`, `d`, `t`, `w` e `q` no modo interativo.
- `w` grava as alterações.
- `q` sai sem gravar.
- Saber diferenciar **partição** de **filesystem**.
- Entender que criar uma nova tabela de partições pode causar perda de dados.

---

## Resumo

    fdisk
      ↓
    Particionamento

    gdisk
      ↓
    GPT

    parted
      ↓
    MBR + GPT

    fdisk -l
      ↓
    listar partições

    w
      ↓
    gravar alterações

    q
      ↓
    sair sem gravar

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
