# Memória

## 01 — RAM e Memória Virtual

### RAM — Random Access Memory — Memória de Acesso Aleatório

A **RAM** é a memória física usada pelo sistema para manter dados e programas que estão sendo utilizados.

Exemplo:

    Programa no disco
          ↓
        RAM
          ↓
        CPU

A RAM é muito mais rápida que o armazenamento em disco, mas possui capacidade limitada.

---

## Memory — Memória

Quando um programa é executado, o Linux precisa fornecer memória para ele.

Essa memória pode conter:

- código do programa;
- dados;
- bibliotecas;
- informações temporárias;
- estruturas usadas pelo processo.

Cada processo possui seu próprio **Virtual Address Space — Espaço de Endereçamento Virtual**.

---

# Virtual Memory — Memória Virtual

A **Memória Virtual** permite que o Linux utilize uma combinação de:

    RAM + Swap

para gerenciar a memória disponível.

A memória virtual cria para os processos a impressão de que existe um espaço de memória grande e contínuo, mesmo que fisicamente a memória esteja distribuída entre RAM e armazenamento.

---

## Swap — Área de Troca

**Swap — Área de Troca** é uma área do armazenamento usada pelo Linux para auxiliar no gerenciamento da memória.

Pode ser:

- uma partição;
- um arquivo.

Exemplo:

    RAM
     │
     ├── páginas usadas
     │
     └── páginas menos utilizadas
                ↓
             Swap

Quando necessário, o kernel pode mover páginas de memória entre RAM e Swap.

---

## RAM × Swap

| RAM | Swap |
|---|---|
| Memória física | Área no armazenamento |
| Muito mais rápida | Muito mais lenta |
| Capacidade física limitada | Pode ampliar o espaço disponível para memória |
| Acesso direto pela memória do sistema | Depende do armazenamento |

> **Swap não substitui RAM.** Ela é muito mais lenta e seu uso intenso pode reduzir bastante o desempenho.

---

## Pages — Páginas

O Linux divide a memória em blocos chamados:

**Page — Página**

O gerenciamento da memória trabalha com essas páginas.

Uma página pode estar:

    RAM

ou, em determinadas situações:

    Swap

Esse mecanismo permite ao kernel controlar melhor o uso da memória.

---

## Virtual Address — Endereço Virtual

Os processos trabalham com **endereços virtuais**, e não diretamente com endereços físicos da RAM.

Simplificando:

    Processo
       ↓
    Endereço Virtual
       ↓
    Kernel / MMU
       ↓
    Endereço Físico
       ↓
    RAM

**MMU — Memory Management Unit — Unidade de Gerenciamento de Memória**

A MMU ajuda a traduzir endereços virtuais para endereços físicos.

---

## Por que usar memória virtual?

A memória virtual permite:

- isolamento entre processos;
- melhor gerenciamento da RAM;
- uso de Swap;
- execução de programas que precisam de mais memória virtual;
- proteção entre processos.

Um processo normalmente não pode simplesmente acessar a memória de outro processo.

---

## Verificar a memória

O comando:

    free

mostra informações sobre RAM e Swap.

Exemplo:

    free -h

**`-h` — Human Readable — Formato Legível por Humanos**

Também podemos consultar:

    /proc/meminfo

Exemplo:

    cat /proc/meminfo

---

## Exemplo simplificado

Imagine:

    RAM: 8 GB
    Swap: 2 GB

O sistema possui:

    8 GB → memória física
    2 GB → área de Swap

A Swap não significa que o computador possui 10 GB de RAM.

Ela é um recurso adicional para o gerenciamento da memória.

---

## Resumo LPIC-1

- **RAM** → *Random Access Memory* — Memória de Acesso Aleatório.
- RAM é a memória física principal do sistema.
- **Virtual Memory** → Memória Virtual.
- Memória virtual utiliza mecanismos que permitem ao sistema gerenciar RAM e Swap.
- **Swap** → Área de Troca.
- Swap pode ser uma partição ou um arquivo.
- Swap é muito mais lenta que RAM.
- **Page** → Página de memória.
- **Virtual Address** → Endereço Virtual.
- **MMU** → *Memory Management Unit* — Unidade de Gerenciamento de Memória.
- `free` → consultar uso de memória.
- `free -h` → mostrar memória em formato legível.
- `/proc/meminfo` → informações detalhadas sobre a memória.
- **Swap não é RAM** e não substitui a memória física.

**Conhecimento só tem valor quando é compartilhado** - Laerte Costa
