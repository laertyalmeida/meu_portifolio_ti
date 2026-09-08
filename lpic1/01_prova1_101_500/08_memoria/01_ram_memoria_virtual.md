# 08 — Memória
## 01 — RAM e Memória Virtual

### RAM — Random Access Memory (Memória de Acesso Aleatório)

A **RAM** é a memória física usada pelo Linux para armazenar temporariamente dados e programas que estão sendo utilizados.

A RAM é **volátil**: seu conteúdo é perdido quando o computador é desligado.

Exemplo:

    Aplicação
       ↓
    RAM
       ↓
    CPU

Quanto mais RAM disponível, mais dados e programas podem permanecer na memória sem precisar acessar o armazenamento.

---

### Memória Virtual — Virtual Memory (Memória Virtual)

A **memória virtual** permite que o sistema utilize uma combinação de:

    RAM + Swap

Ela cria uma camada de memória que dá aos processos a impressão de possuir mais memória disponível do que apenas a RAM física.

---

### Swap — Área de Troca

A **Swap** é uma área do armazenamento usada como extensão da memória quando necessário.

Pode ser:

- **Swap Partition** — Partição Swap
- **Swap File** — Arquivo Swap

Exemplo:

    RAM
    ┌─────────────────┐
    │ Processos ativos │
    └─────────────────┘
             ↕
    ┌─────────────────┐
    │      Swap       │
    │ armazenamento   │
    └─────────────────┘

⚠️ A Swap é muito mais lenta que a RAM.

---

### Quando a Swap é utilizada?

Quando existe pressão de memória, o Linux pode mover páginas de memória menos utilizadas da RAM para a Swap.

Esse processo libera espaço na RAM para dados mais necessários.

Exemplo:

    RAM cheia
       ↓
    páginas menos usadas
       ↓
    Swap
       ↓
    espaço liberado na RAM

Isso **não significa** que a Swap substitui a RAM em desempenho.

---

### RAM × Memória Virtual

| RAM | Memória Virtual |
|---|---|
| Memória física | Abstração de memória |
| Está no hardware | Usa mecanismos do sistema |
| Muito rápida | Pode envolver RAM e Swap |
| Volátil | Permite gerenciar melhor a memória |

---

### Ver memória com free

O comando mais importante para a prova:

    free

Para mostrar valores mais fáceis de ler:

    free -h

- `-h` — human-readable (legível por humanos)

Exemplo:

    free -h

Saída simplificada:

                  total   used   free   shared  buff/cache  available
    Mem:            8Gi    3Gi    1Gi      ...       4Gi        5Gi
    Swap:           2Gi    0Gi    2Gi

---

### Campos importantes

**total**
→ quantidade total disponível.

**used**
→ memória atualmente utilizada.

**free**
→ memória completamente livre.

**buff/cache**
→ memória usada para buffers e cache.

**available**
→ estimativa de memória disponível para novos processos sem recorrer à Swap de forma significativa.

**Swap**
→ informações sobre a área de troca.

---

### /proc/meminfo

O Linux também disponibiliza informações detalhadas sobre memória em:

    /proc/meminfo

Consultar:

    cat /proc/meminfo

Exemplo de informações:

    MemTotal
    MemFree
    MemAvailable
    Buffers
    Cached
    SwapTotal
    SwapFree

O `/proc` é um **Virtual Filesystem — Sistema de Arquivos Virtual** que fornece informações sobre o kernel e os processos.

---

### vmstat — Virtual Memory Statistics (Estatísticas da Memória Virtual)

O `vmstat` mostra informações sobre memória, processos, CPU e I/O.

    vmstat

Para atualizar continuamente:

    vmstat 2

O `2` significa atualizar a cada **2 segundos**.

---

### ⚠️ Atenção para a prova LPIC-1

Memorize:

**RAM**
→ memória física e rápida.

**Virtual Memory**
→ mecanismo que permite ao sistema gerenciar memória usando RAM e, quando necessário, Swap.

**Swap**
→ área em armazenamento usada para páginas de memória.

**`free -h`**
→ mostra RAM e Swap de forma legível.

**`/proc/meminfo`**
→ informações detalhadas sobre memória.

**`vmstat`**
→ estatísticas de memória virtual, processos, CPU e I/O.

### Resumo

    RAM
     ↓
    memória física

    Memória Virtual
     ↓
    gerenciamento da memória pelos processos

    Swap
     ↓
    área de armazenamento usada quando necessário

    free -h
     ↓
    visualizar RAM e Swap

> **Conhecimento só tem valor quando é compartilhado** - Laerte Costa
