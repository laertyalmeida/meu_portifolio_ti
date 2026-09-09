# Processos

## 07 — jobs

### jobs — Jobs — Tarefas do Shell

O comando `jobs` mostra os **jobs — tarefas** iniciados pelo shell atual.

Esses jobs podem estar:

- em **Foreground — Primeiro Plano**
- em **Background — Segundo Plano**
- **Stopped — Parados**

Exemplo:

    jobs

Saída:

    [1]+  Running    sleep 100 &
    [2]-  Stopped    vim

---

## Job ID × PID

Um **Job ID** é diferente de um **PID**.

### Job ID — Identificador da Tarefa

É um número atribuído pelo shell.

Exemplo:

    [1]

### PID — Process ID — ID do Processo

É o identificador atribuído pelo sistema ao processo.

Exemplo:

    1520

Podemos ter:

    Job ID → [1]
    PID    → 1520

O Job ID é usado principalmente pelos comandos de controle de jobs do shell.

---

## Executar em Background

Adicionar `&` ao final do comando:

    sleep 100 &

O shell inicia o processo em segundo plano e devolve o prompt.

Consultar:

    jobs

Exemplo:

    [1]+  Running    sleep 100 &

---

## Ctrl+Z — Suspender

Durante a execução de um processo em primeiro plano:

    Ctrl+Z

O processo é suspenso.

Depois:

    jobs

Exemplo:

    [1]+  Stopped    vim

---

## bg — Background — Segundo Plano

O `bg` continua um job suspenso em segundo plano.

    bg %1

**`%1` → Job 1 — Tarefa 1**

Depois:

    jobs

O resultado poderá mostrar:

    [1]+  Running    vim &

---

## fg — Foreground — Primeiro Plano

O `fg` traz um job para o primeiro plano.

    fg %1

Agora o processo volta a ocupar o terminal.

---

## Identificando o job atual

O shell utiliza símbolos como:

    [1]+
    [2]-

O:

    +

indica o **Current Job — Job Atual**.

O:

    -

indica o **Previous Job — Job Anterior**.

---

## Encerrar um job

Podemos usar `kill` com o Job ID:

    kill %1

Ou usar o PID:

    kill 1520

Também podemos usar:

    fg %1

e depois:

    Ctrl+C

---

## wait — Wait — Aguardar

O `wait` faz o shell esperar um job ou processo terminar.

    wait %1

Também pode ser usado com um PID:

    wait 1520

É especialmente útil em scripts.

---

## Comandos principais

| Comando | English | Português |
|---|---|---|
| `jobs` | Jobs | Listar tarefas do shell |
| `bg` | Background | Continuar em segundo plano |
| `fg` | Foreground | Trazer para primeiro plano |
| `kill` | Send Signal | Enviar sinal |
| `wait` | Wait | Aguardar término |
| `&` | Background Operator | Executar em segundo plano |
| `Ctrl+Z` | Suspend | Suspender processo |
| `Ctrl+C` | Interrupt | Interromper processo |

---

## Fluxo completo

Iniciar:

    sleep 100

Suspender:

    Ctrl+Z

Verificar:

    jobs

Continuar em segundo plano:

    bg %1

Verificar:

    jobs

Trazer para o primeiro plano:

    fg %1

Interromper:

    Ctrl+C

---

## jobs × ps

`jobs` mostra principalmente os **jobs controlados pelo shell atual**.

    jobs

`ps` mostra informações sobre **processos do sistema**.

    ps

Portanto:

    jobs → tarefas do shell
    ps   → processos

---

## Resumo LPIC-1

- `jobs` → **Jobs — Tarefas do Shell**.
- `jobs` → mostra jobs do shell atual.
- `&` → executa um comando em background.
- `Ctrl+Z` → suspende um processo.
- `bg` → continua um job em background.
- `fg` → traz um job para foreground.
- `%1` → referencia o Job ID 1.
- `kill %1` → envia sinal ao Job 1.
- `wait` → aguarda o término de um job/processo.
- **Job ID** → identificador usado pelo shell.
- **PID** → identificador do processo pelo sistema.
- `jobs` e `ps` não são a mesma coisa.

**Conhecimento só tem valor quando é compartilhado** - Laerte Costa
