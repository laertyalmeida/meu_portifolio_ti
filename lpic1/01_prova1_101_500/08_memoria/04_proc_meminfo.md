# Memória

## 04 — /proc/meminfo

### 1. O que é /proc/meminfo

`/proc/meminfo` — **Memory Information — Informações da Memória**

É um arquivo virtual do **procfs** que apresenta informações detalhadas sobre o uso e o estado da memória do sistema.

    /proc/meminfo

Ele não é um arquivo comum armazenado no disco. O **kernel** fornece essas informações dinamicamente.

---

### 2. Visualizar o conteúdo

    cat /proc/meminfo

Para visualizar apenas informações relacionadas à Swap:

    grep -i swap /proc/meminfo

`-i` — **Ignore Case — Ignorar Maiúsculas/Minúsculas**

---

### 3. Principais campos

| Campo | Significado |
|---|---|
| `MemTotal` | Quantidade total de RAM |
| `MemFree` | RAM completamente livre |
| `MemAvailable` | RAM estimada disponível para novos programas |
| `Buffers` | Memória usada por buffers |
| `Cached` | Memória usada por cache de arquivos |
| `SwapCached` | Memória que também possui cópia na Swap |
| `SwapTotal` | Quantidade total de Swap |
| `SwapFree` | Quantidade de Swap livre |
| `Active` | Memória ativa, usada recentemente |
| `Inactive` | Memória menos recentemente usada |
| `SReclaimable` | Memória recuperável pelo kernel |
| `Shmem` | Memória compartilhada |

Os valores normalmente aparecem em **KiB (Kibibytes)**.

Exemplo:

    MemTotal:       16384000 kB
    MemFree:         2048000 kB
    MemAvailable:    9430000 kB
    SwapTotal:       2097148 kB
    SwapFree:        2097148 kB

---

### 4. MemTotal

    MemTotal

Representa a quantidade total de memória RAM que o kernel considera disponível para uso.

Não deve ser confundido diretamente com a capacidade anunciada fisicamente pelo fabricante, pois parte da memória pode ser reservada para hardware ou outros usos.

---

### 5. MemFree × MemAvailable

Essa diferença é importante.

**`MemFree`**

→ memória que está completamente livre neste momento.

**`MemAvailable`**

→ estimativa de quanto de memória pode ser disponibilizado para novos programas sem recorrer significativamente à Swap.

Exemplo:

    MemFree:        2 GB
    MemAvailable:   9 GB

Isso **não significa** que apenas 2 GB de RAM estão disponíveis.

O Linux utiliza RAM livre como **cache**, podendo liberar parte dela quando necessário.

---

### 6. Informações sobre Swap

Procure:

    grep -i swap /proc/meminfo

Exemplo:

    SwapCached:          0 kB
    SwapTotal:     2097148 kB
    SwapFree:      2097148 kB

Interpretação:

    SwapTotal → tamanho total da Swap
    SwapFree  → espaço de Swap ainda livre
    SwapCached → páginas que possuem cópia na Swap e também podem estar na RAM

---

### 7. Ver apenas informações de memória

    grep -E 'MemTotal|MemFree|MemAvailable|Buffers|Cached' /proc/meminfo

`-E` — **Extended Regular Expressions — Expressões Regulares Estendidas**

---

### 8. Relação com outros comandos

    /proc/meminfo
          ↓
       informações
          ↓
    ┌───────────────┐
    │     free      │
    │    vmstat     │
    └───────────────┘

O `free` utiliza informações fornecidas pelo kernel para apresentar um resumo da memória.

O `vmstat` apresenta informações de memória virtual junto com processos, I/O e CPU.

---

### 9. /proc é um sistema de arquivos virtual

O diretório:

    /proc

é o **procfs — Process Filesystem — Sistema de Arquivos de Processos**.

Ele fornece informações sobre:

- processos;
- memória;
- CPU;
- kernel;
- dispositivos;
- parâmetros do sistema.

Exemplos:

    /proc/cpuinfo
    /proc/meminfo
    /proc/loadavg
    /proc/uptime

---

## Resumo LPIC-1

- `/proc/meminfo` → informações detalhadas sobre a memória.
- É fornecido dinamicamente pelo **kernel**.
- Faz parte do **procfs**.
- `MemTotal` → RAM total reconhecida pelo kernel.
- `MemFree` → RAM completamente livre.
- `MemAvailable` → estimativa de RAM disponível para novos programas.
- `SwapTotal` → Swap total.
- `SwapFree` → Swap livre.
- `Buffers` → memória usada por buffers.
- `Cached` → memória usada como cache.
- `cat /proc/meminfo` → visualizar todas as informações.
- `grep /proc/meminfo` → filtrar informações específicas.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
