# 07 — Processos
## 06 — nice e renice

### Nice — Process Priority Adjustment (Ajuste de Prioridade do Processo)

O **nice** define o valor de prioridade de CPU de um processo.

O valor **nice** normalmente vai de:

    -20 → maior prioridade
     0 → prioridade padrão
    +19 → menor prioridade

⚠️ **Quanto menor o valor nice, maior a prioridade.**

---

### nice — Start with a Priority (Iniciar com uma Prioridade)

Sintaxe:

    nice -n VALOR comando

Exemplo:

    nice -n 10 comando

- `-n` — nice (definir valor de ajuste)

O comando será iniciado com:

    nice = 10

Ou seja, terá uma prioridade de CPU menor que um processo com `nice = 0`.

---

### Ver o valor nice

Com `ps`:

    ps -o pid,ni,cmd

- `-o` — output (definir campos)
- `ni` — nice (valor de ajuste)
- `cmd` — command (comando)

Exemplo:

    PID  NI CMD
    1250  0 bash
    1387 10 processo

---

### renice — Change Priority (Alterar a Prioridade)

O `renice` altera o valor nice de um processo que já está executando.

Sintaxe:

    renice VALOR -p PID

Exemplo:

    renice 10 -p 1250

- `-p` — PID (selecionar pelo ID do processo)

O processo `1250` passa a ter:

    NI = 10

---

### Aumentando a prioridade

Para aumentar a prioridade, é necessário **diminuir o valor nice**.

Exemplo:

    renice -5 -p 1250

    NI: 0 → -5

⚠️ Usuários comuns normalmente não podem escolher valores nice negativos. Isso geralmente exige privilégios elevados.

Exemplo:

    sudo renice -5 -p 1250

---

### Diminuindo a prioridade

Para dar menos prioridade ao processo:

    renice 10 -p 1250

    NI: 0 → 10

Isso pode ser útil para processos que consomem muita CPU e não precisam ter prioridade sobre outras tarefas.

---

### nice × renice

| Comando | Função |
|---|---|
| `nice` | inicia um processo com determinado valor nice |
| `renice` | altera o valor nice de um processo existente |

Memorize:

    nice   → iniciar
    renice → alterar

---

### ⚠️ Nice não é exatamente "prioridade"

O **nice** é um **ajuste de prioridade** usado pelo escalonador de processos.

O valor `NI` influencia a prioridade, mas não deve ser confundido diretamente com o campo `PR` exibido pelo `top`.

No `top`:

    PR → Priority (Prioridade)
    NI → Nice (Ajuste de prioridade)

---

### Exemplo completo

Iniciar um processo com baixa prioridade:

    nice -n 15 comando

Ver:

    ps -o pid,ni,cmd

Alterar depois:

    renice 5 -p PID

Resultado:

    NI: 15 → 5

A prioridade relativa do processo aumenta, pois o valor nice diminuiu.

---

### ⚠️ Atenção para a prova LPIC-1

Memorize:

    nice -n 10 comando
    renice 10 -p PID

**Nice menor**
→ maior prioridade relativa.

**Nice maior**
→ menor prioridade relativa.

**`nice`**
→ define o ajuste ao iniciar o processo.

**`renice`**
→ altera o ajuste de um processo existente.

Faixa tradicional:

    -20 ← maior prioridade
      0 ← padrão
    +19 ← menor prioridade

> **Conhecimento só tem valor quando é compartilhado** - Laerte Costa
