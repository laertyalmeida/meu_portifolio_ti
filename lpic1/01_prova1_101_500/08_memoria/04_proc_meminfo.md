# 08 — Memória
## 04 — /proc/meminfo

### /proc/meminfo — Memory Information (Informações de Memória)

O arquivo:

    /proc/meminfo

fornece informações detalhadas sobre a memória gerenciada pelo **kernel Linux**.

Ele faz parte do:

    /proc

O `/proc` é um **Virtual Filesystem — Sistema de Arquivos Virtual** que fornece informações sobre o sistema e os processos.

---

### Visualizar o conteúdo

Use:

    cat /proc/meminfo

Exemplo simplificado:

    MemTotal:        8023456 kB
    MemFree:          512000 kB
    MemAvailable:    4200000 kB
    Buffers:           120000 kB
    Cached:           2800000 kB
    SwapCached:             0 kB
    SwapTotal:       2097148 kB
    SwapFree:        2097148 kB

Os valores podem variar conforme o sistema.

---

### Principais informações

| Campo | Inglês | Português |
|---|---|---|
| `MemTotal` | Total Memory | Memória total |
| `MemFree` | Free Memory | Memória completamente livre |
| `MemAvailable` | Available Memory | Memória estimada disponível |
| `Buffers` | Buffers | Memória usada para buffers |
| `Cached` | Cache | Memória usada para cache |
| `SwapCached` | Swap Cache | Memória da Swap também mantida em cache |
| `SwapTotal` | Total Swap | Swap total |
| `SwapFree` | Free Swap | Swap livre |

---

### MemTotal — Total Memory (Memória Total)

    grep MemTotal /proc/meminfo

Mostra a quantidade total de memória RAM reconhecida pelo sistema.

Exemplo:

    MemTotal:        8023456 kB

---

### MemFree — Free Memory (Memória Livre)

    grep MemFree /proc/meminfo

Representa a memória que está completamente livre.

⚠️ **Não confunda `MemFree` com `MemAvailable`.**

---

### MemAvailable — Available Memory (Memória Disponível)

    grep MemAvailable /proc/meminfo

Indica uma estimativa de memória que pode ser disponibilizada para novos processos sem recorrer significativamente à Swap.

Por isso, geralmente é mais útil para avaliar a memória disponível do que observar apenas `MemFree`.

---

### Informações sobre Swap

Consultar:

    grep Swap /proc/meminfo

Exemplo:

    SwapCached:       0 kB
    SwapTotal:  2097148 kB
    SwapFree:   2097148 kB

Temos:

**SwapTotal**
→ quantidade total de Swap.

**SwapFree**
→ quantidade de Swap ainda disponível.

**SwapCached**
→ páginas que foram enviadas para Swap, mas que também permanecem em memória RAM.

---

### Buffers e Cached

O Linux utiliza parte da RAM para **buffers e cache**, melhorando o desempenho de operações de I/O.

Consultar:

    grep -E 'Buffers|Cached' /proc/meminfo

- `-E` — extended regular expression (expressão regular estendida)

⚠️ Memória usada como cache não significa necessariamente memória "perdida". O kernel pode liberar parte dela quando necessário.

---

### /proc/meminfo × free

O comando:

    free -h

apresenta uma visão resumida e mais amigável.

Já:

    cat /proc/meminfo

fornece uma quantidade muito maior de informações.

Podemos pensar assim:

    /proc/meminfo
          ↓
    informações detalhadas
          ↓
        free
          ↓
    visão resumida

---

### Filtrando informações

Para consultar somente a memória total:

    grep MemTotal /proc/meminfo

Para consultar memória disponível:

    grep MemAvailable /proc/meminfo

Para consultar Swap:

    grep Swap /proc/meminfo

Para consultar várias informações:

    grep -E 'MemTotal|MemFree|MemAvailable|SwapTotal|SwapFree' /proc/meminfo

---

### ⚠️ Atenção para a prova LPIC-1

Memorize:

**`/proc/meminfo`**
→ fornece informações detalhadas sobre a memória do sistema.

**`MemTotal`**
→ memória total reconhecida.

**`MemFree`**
→ memória completamente livre.

**`MemAvailable`**
→ estimativa de memória disponível para novos usos.

**`SwapTotal`**
→ tamanho total da Swap.

**`SwapFree`**
→ Swap disponível.

**`free -h`**
→ apresenta uma visão resumida dessas informações.

> **Conhecimento só tem valor quando é compartilhado** - Laerte Costa
