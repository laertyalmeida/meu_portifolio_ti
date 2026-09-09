# Processos

## 05 — Signals e kill

### Signal — Sinal

Um **Signal — Sinal** é uma mensagem enviada pelo Linux para um processo.

Os sinais podem:

- solicitar que um processo termine;
- interromper um processo;
- pausar um processo;
- continuar um processo;
- informar que ocorreu algum evento.

O comando mais conhecido para enviar sinais é:

    kill

---

## kill — Send Signal — Enviar Sinal

Apesar do nome `kill`, o comando não serve apenas para "matar" processos.

Ele envia um **sinal** para um processo através do seu PID.

    kill 1520

Por padrão, envia:

    SIGTERM

---

## SIGTERM — Terminate — Terminar

**SIGTERM (15)** solicita que o processo termine.

    kill 1520

É a forma recomendada para tentar encerrar um processo normalmente.

O processo pode receber o sinal e realizar tarefas de encerramento antes de sair.

---

## SIGKILL — Kill — Forçar Encerramento

**SIGKILL (9)** força o encerramento do processo.

    kill -9 1520

**`-9` → SIGKILL**

O processo não pode ignorar ou tratar o `SIGKILL`.

> Use `SIGKILL` somente quando necessário. Primeiro tente `SIGTERM`.

---

## SIGINT — Interrupt — Interrupção

**SIGINT (2)** normalmente é enviado quando pressionamos:

    Ctrl+C

Exemplo:

    ping localhost

Pressione:

    Ctrl+C

Isso normalmente interrompe o processo.

Também podemos enviar:

    kill -2 1520

---

## SIGSTOP — Stop — Parar

**SIGSTOP (19)** pausa o processo.

    kill -STOP 1520

O processo fica parado até receber um sinal para continuar.

---

## SIGCONT — Continue — Continuar

**SIGCONT (18)** faz um processo parado continuar sua execução.

    kill -CONT 1520

---

## SIGTSTP — Terminal Stop — Parada pelo Terminal

**SIGTSTP (20)** normalmente é enviado quando pressionamos:

    Ctrl+Z

Ele suspende o processo e devolve o controle ao shell.

Exemplo:

    sleep 100

Pressione:

    Ctrl+Z

Depois:

    jobs

O processo aparecerá como parado.

---

## Principais sinais para LPIC-1

| Número | Sinal | English | Português |
|---:|---|---|---|
| `1` | `SIGHUP` | Hangup | Desconexão |
| `2` | `SIGINT` | Interrupt | Interrupção |
| `9` | `SIGKILL` | Kill | Encerramento forçado |
| `15` | `SIGTERM` | Terminate | Solicitação de término |
| `18` | `SIGCONT` | Continue | Continuar |
| `19` | `SIGSTOP` | Stop | Parar |
| `20` | `SIGTSTP` | Terminal Stop | Parada pelo terminal |

> Os números podem variar para alguns sinais entre arquiteturas, mas esses são os valores usuais em Linux.

---

## Listar os sinais

Podemos listar os sinais disponíveis com:

    kill -l

**`-l` — List — Listar**

Exemplo:

    kill -l

Também podemos usar o nome do sinal:

    kill -TERM 1520

ou:

    kill -SIGTERM 1520

---

## Número ou nome

As duas formas podem ser utilizadas:

    kill -15 1520

    kill -TERM 1520

    kill -SIGTERM 1520

Todas representam o envio de **SIGTERM**.

---

## killall — Kill All — Encerrar Todos

O `killall` permite enviar um sinal aos processos pelo nome.

Exemplo:

    killall firefox

Isso envia o sinal padrão para os processos chamados `firefox`.

Também podemos especificar o sinal:

    killall -9 firefox

> Cuidado: o comando pode atingir vários processos com o mesmo nome.

---

## pkill — Process Kill — Encerrar Processos

O `pkill` também permite selecionar processos por nome e outros critérios.

Exemplo:

    pkill firefox

Enviar SIGTERM:

    pkill -TERM firefox

---

## kill × killall × pkill

| Comando | Seleção |
|---|---|
| `kill PID` | Por PID |
| `killall nome` | Pelo nome do processo |
| `pkill nome` | Por critérios de seleção do processo |

---

## Fluxo recomendado

Para tentar encerrar um processo:

    kill 1520

Se ele não terminar e realmente for necessário forçar:

    kill -9 1520

Para verificar:

    ps -p 1520

---

## Resumo LPIC-1

- **Signal** → Sinal enviado a um processo.
- `kill` → envia um sinal para um processo.
- `SIGTERM (15)` → solicita encerramento normal.
- `SIGKILL (9)` → força o encerramento.
- `SIGINT (2)` → interrupção, normalmente `Ctrl+C`.
- `SIGSTOP (19)` → pausa o processo.
- `SIGCONT (18)` → continua um processo parado.
- `SIGTSTP (20)` → suspensão pelo terminal, normalmente `Ctrl+Z`.
- `kill -l` → lista os sinais.
- `killall` → envia sinal pelo nome do processo.
- `pkill` → seleciona processos e envia sinal.
- Prefira `SIGTERM` antes de `SIGKILL`.

**Conhecimento só tem valor quando é compartilhado** - Laerte Costa
