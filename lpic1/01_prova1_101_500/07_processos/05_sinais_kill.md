# 07 — Processos
## 05 — Sinais e kill

### Signal — Sinal

Um **sinal** é uma mensagem enviada pelo Linux para um processo.

Os sinais podem:

- encerrar um processo;
- interromper sua execução;
- pausar ou continuar um processo;
- informar que ocorreu algum evento.

O comando principal para enviar sinais é:

    kill

---

### kill — Send Signal (Enviar Sinal)

Apesar do nome `kill` significar **matar**, ele não serve apenas para encerrar processos.

Sintaxe:

    kill [sinal] PID

Exemplo:

    kill 1250

Por padrão, o `kill` envia:

    SIGTERM

---

### SIGTERM — Terminate (Solicitar encerramento)

    kill -TERM 1250

- `-TERM` — Terminate (encerrar)

Também podemos usar o número:

    kill -15 1250

O `SIGTERM` solicita que o processo encerre de forma **organizada**.

O programa pode receber o sinal e realizar tarefas de limpeza antes de terminar.

---

### SIGKILL — Kill (Forçar encerramento)

    kill -KILL 1250

ou:

    kill -9 1250

- `-KILL` — Kill (forçar encerramento)

O `SIGKILL` força o encerramento imediatamente.

O processo **não pode ignorar nem tratar** esse sinal.

⚠️ Por isso, normalmente tente `SIGTERM` antes de `SIGKILL`.

    kill -TERM PID
    kill -KILL PID

---

### SIGSTOP — Stop (Parar)

    kill -STOP 1250

ou:

    kill -19 1250

O processo é suspenso.

Diferentemente de sinais comuns, `SIGSTOP` não pode ser ignorado pelo processo.

---

### SIGCONT — Continue (Continuar)

Depois de um `SIGSTOP`:

    kill -CONT 1250

ou:

    kill -18 1250

O processo continua sua execução.

---

### Sinais importantes para LPIC-1

| Sinal | Número | Significado |
|---|---:|---|
| `SIGHUP` | 1 | Hang Up — desligamento da sessão |
| `SIGINT` | 2 | Interrupt — interrupção |
| `SIGQUIT` | 3 | Quit — sair com encerramento |
| `SIGKILL` | 9 | Kill — encerramento forçado |
| `SIGTERM` | 15 | Terminate — solicitar encerramento |
| `SIGSTOP` | 19 | Stop — parar |
| `SIGCONT` | 18 | Continue — continuar |

> Os números podem ser usados com `kill`, mas o nome do sinal é geralmente mais fácil de entender.

---

### SIGINT — Interrupt (Interromper)

Quando pressionamos:

    Ctrl + C

Normalmente o terminal envia:

    SIGINT

Esse sinal solicita a interrupção do processo em primeiro plano.

---

### SIGTSTP — Terminal Stop (Parar pelo Terminal)

Quando pressionamos:

    Ctrl + Z

Normalmente é enviado:

    SIGTSTP

O processo é suspenso e pode ser retomado posteriormente.

---

### Listando os sinais

Use:

    kill -l

- `-l` — list (listar)

Isso mostra os sinais disponíveis no sistema.

---

### Enviando um sinal pelo nome

    kill -TERM 1250

Também podemos usar:

    kill -15 1250

Os dois comandos enviam `SIGTERM`.

---

### pkill — Process Kill (Encerrar por nome)

O `pkill` permite enviar um sinal usando o nome do processo.

    pkill firefox

Por padrão, envia `SIGTERM`.

Exemplo forçado:

    pkill -9 firefox

- `-9` — SIGKILL (encerramento forçado)

⚠️ Cuidado: o comando pode atingir **mais de um processo** que corresponda ao nome.

---

### killall — Kill All Matching Processes (Encerrar processos correspondentes)

    killall firefox

Envia um sinal aos processos com o nome correspondente.

⚠️ Também pode atingir vários processos.

---

### kill × pkill × killall

| Comando | Seleção |
|---|---|
| `kill PID` | Por PID |
| `pkill nome` | Pelo nome/padrão |
| `killall nome` | Pelo nome |

---

### ⚠️ Atenção para a prova LPIC-1

Memorize principalmente:

    kill PID
    kill -15 PID
    kill -9 PID
    kill -STOP PID
    kill -CONT PID
    kill -l

**SIGTERM (15)**
→ solicita encerramento.

**SIGKILL (9)**
→ força encerramento e não pode ser capturado/ignorado.

**SIGSTOP (19)**
→ para o processo.

**SIGCONT (18)**
→ continua um processo parado.

**Ctrl + C**
→ normalmente `SIGINT`.

**Ctrl + Z**
→ normalmente `SIGTSTP`.

> **Conhecimento só tem valor quando é compartilhado** - Laerte Costa
