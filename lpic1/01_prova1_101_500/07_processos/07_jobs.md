# 07 — Processos
## 07 — Jobs

### Job — Tarefa (Processo controlado pelo Shell)

Um **job** é um processo que o **shell** está controlando, principalmente quando executamos comandos em primeiro ou segundo plano.

Exemplo:

    comando &

O `&` inicia o comando em **Background — Segundo Plano**.

---

### Foreground — Primeiro Plano

Quando executamos normalmente:

    comando

O processo ocupa o terminal e permanece em primeiro plano.

Enquanto ele estiver executando, normalmente não podemos usar aquele terminal para executar outro comando.

---

### Background — Segundo Plano

Para executar um comando em segundo plano:

    comando &

Exemplo:

    sleep 60 &

O shell pode mostrar:

    [1] 1250

- `[1]` → **Job ID (ID do Job)**
- `1250` → **PID (ID do Processo)**

⚠️ **Job ID e PID são diferentes.**

---

### jobs — List Jobs (Listar Jobs)

O comando `jobs` mostra os jobs controlados pelo shell atual.

    jobs

Exemplo:

    [1]+  Running    sleep 60 &
    [2]-  Stopped    vim

Informações:

- `[1]` → Job ID
- `Running` → Executando
- `Stopped` → Parado
- `+` → job atual/padrão para operações de job
- `-` → job anterior

---

### Ctrl + Z — Suspender um Job

Pressionar:

    Ctrl + Z

Normalmente envia `SIGTSTP` para o processo em primeiro plano e o suspende.

Exemplo:

    comando

Pressione:

    Ctrl + Z

O shell pode mostrar:

    [1]+  Stopped    comando

O processo não foi encerrado. Ele está **parado**.

---

### bg — Background (Segundo Plano)

O comando `bg` continua um job parado em segundo plano.

    bg

Por padrão, atua sobre o job atual (`%+`).

Também podemos indicar o Job ID:

    bg %1

- `%1` → Job ID 1

Exemplo:

    [1]+  Stopped    comando

Depois:

    bg %1

Resultado:

    [1]+  Running    comando &

---

### fg — Foreground (Primeiro Plano)

O comando `fg` traz um job para o primeiro plano.

    fg

Ou:

    fg %1

Exemplo:

    [1]+  Running    comando

Depois:

    fg %1

O job volta para o **Foreground — Primeiro Plano**.

---

### Encadeamento básico

O fluxo mais importante é:

    comando
        ↓
    Ctrl + Z
        ↓
    Stopped
        ↓
    bg
        ↓
    Running em Background
        ↓
    fg
        ↓
    Running em Foreground

---

### Job ID × PID

Exemplo:

    sleep 300 &

Saída:

    [1] 1250

Temos:

    Job ID → 1
    PID    → 1250

Para trabalhar com jobs:

    fg %1
    bg %1
    kill %1

Para trabalhar diretamente com o processo:

    kill 1250

⚠️ O `%` indica que estamos usando um **Job ID**.

---

### Atalhos importantes

| Comando/Tecla | Função |
|---|---|
| `&` | Executar em Background |
| `Ctrl + Z` | Suspender o processo atual |
| `jobs` | Listar jobs |
| `bg` | Continuar em Background |
| `fg` | Trazer para Foreground |

---

### Exemplo completo

Iniciar:

    sleep 300

Suspender:

    Ctrl + Z

Ver os jobs:

    jobs

Continuar em segundo plano:

    bg %1

Ver novamente:

    jobs

Trazer para primeiro plano:

    fg %1

---

### ⚠️ Atenção para a prova LPIC-1

Memorize:

    &       → iniciar em Background
    jobs    → listar Jobs
    Ctrl+Z  → suspender
    bg      → continuar em Background
    fg      → trazer para Foreground

E principalmente:

**Job ID ≠ PID**

Exemplo:

    [1] 1250

**`1`** → Job ID  
**`1250`** → PID

> **Conhecimento só tem valor quando é compartilhado** - Laerte Costa
