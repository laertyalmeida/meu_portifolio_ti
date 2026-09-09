# Memória

## 05 — OOM Killer

### 1. O que é OOM Killer

**OOM — Out Of Memory — Sem Memória**

O **OOM Killer** é um mecanismo do **kernel Linux** usado quando o sistema fica sem memória suficiente para continuar funcionando normalmente.

Quando a memória disponível se esgota e o kernel não consegue atender novas solicitações, ele pode escolher um processo e encerrá-lo para liberar memória.

    RAM + Swap
          ↓
    Memória insuficiente
          ↓
    Kernel
          ↓
    OOM Killer
          ↓
    Processo escolhido é encerrado
          ↓
    Memória liberada

---

### 2. Por que ele existe?

Sem o OOM Killer, uma situação extrema de falta de memória poderia deixar o sistema gravemente comprometido.

O objetivo é:

> **Liberar memória para permitir que o sistema continue funcionando.**

O processo encerrado pode ser um dos maiores consumidores de memória, mas a escolha é feita pelo kernel com base em vários fatores.

---

### 3. Quando pode acontecer?

Exemplo:

    Programa A → 2 GB
    Programa B → 4 GB
    Programa C → 8 GB

Se a RAM estiver praticamente cheia e a Swap não conseguir resolver a situação, uma nova solicitação de memória pode provocar uma condição de **OOM**.

O kernel pode então acionar o OOM Killer.

---

### 4. O processo escolhido

O kernel calcula uma pontuação relacionada à possibilidade de um processo ser terminado.

Um conceito importante é:

**OOM Score — Pontuação OOM**

Pode ser consultado em:

    /proc/PID/oom_score

Exemplo:

    cat /proc/1234/oom_score

Quanto maior a pontuação, maior tende a ser a possibilidade de o processo ser escolhido.

> A decisão real do kernel é mais complexa do que simplesmente escolher o processo que usa mais RAM.

---

### 5. Ajustando a prioridade OOM

Existe também:

    /proc/PID/oom_score_adj

Exemplo:

    cat /proc/1234/oom_score_adj

O valor pode influenciar a preferência do kernel ao escolher processos durante uma situação de OOM.

Valores:

    -1000 → proteção máxima contra OOM Killer
     0    → valor padrão
    1000  → maior preferência para ser escolhido

Exemplo:

    sudo sh -c 'echo -500 > /proc/1234/oom_score_adj'

> Alterar esse valor exige cuidado. Proteger muitos processos contra o OOM Killer pode deixar menos opções para o kernel liberar memória.

---

### 6. Como identificar um OOM Killer

As mensagens do kernel podem ser consultadas com:

    dmesg

Ou:

    dmesg | grep -i 'out of memory\|killed process'

`-i` — **Ignore Case — Ignorar Maiúsculas/Minúsculas**

Também é comum consultar o journal:

    journalctl -k

`-k` — **Kernel — Mensagens do Kernel**

Procurando mensagens relacionadas:

    journalctl -k | grep -i 'oom\|out of memory\|killed process'

---

### 7. OOM Killer × Swap

A existência de Swap **não impede necessariamente** o OOM Killer.

O fluxo pode ser:

    RAM começa a ficar cheia
            ↓
    Kernel pode utilizar Swap
            ↓
    Memória continua insuficiente
            ↓
    Não é possível atender novas alocações
            ↓
    OOM Killer pode ser acionado

Por isso, **ter Swap não significa que o sistema nunca terá OOM**.

---

### 8. OOM não significa "Swap cheia"

OOM significa **falta de memória para atender às necessidades do sistema**.

A situação pode envolver:

- RAM muito ocupada;
- Swap insuficiente ou indisponível;
- grande pressão de memória;
- limites de memória;
- impossibilidade de atender novas alocações.

Portanto:

    Swap cheia ≠ necessariamente OOM

e:

    OOM ≠ simplesmente "Swap cheia"

---

### 9. Verificar memória antes de investigar OOM

Comandos úteis:

    free -h

    swapon --show

    cat /proc/meminfo

    ps aux --sort=-%mem

O último comando ajuda a identificar processos que estão usando muita memória.

---

## Resumo LPIC-1

- **OOM** = **Out Of Memory — Sem Memória**.
- **OOM Killer** é um mecanismo do kernel Linux.
- É acionado em situações graves de falta de memória.
- Pode encerrar processos para liberar memória.
- `/proc/PID/oom_score` → mostra a pontuação OOM do processo.
- `/proc/PID/oom_score_adj` → permite influenciar essa pontuação.
- `dmesg` → mostra mensagens do kernel.
- `journalctl -k` → mostra mensagens do kernel no journal.
- Swap pode ajudar, mas **não elimina a possibilidade de OOM**.
- OOM não significa simplesmente que a Swap ficou cheia.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
