Processos

Process — Processo

Um Process (Processo) é um programa que está sendo executado.

Por exemplo, quando você executa:

firefox

o Linux cria um processo para o Firefox.

Programa
   ↓
Execução
   ↓
Processo

---

PID — Process ID (Identificador do Processo)

Cada processo recebe um número chamado PID.

Podemos visualizar processos com:

ps

Exemplo:

PID   TTY      TIME     CMD
1234  pts/0    00:00    bash

Nesse exemplo:

1234 → PID do processo

---

"ps" — Process Status (Estado dos Processos)

Mostra processos em execução.

ps

"-e" — Every (Todos)

Mostra todos os processos.

ps -e

"-f" — Full (Completo)

Mostra informações mais detalhadas.

ps -ef

---

"top" — Top (Principal)

Mostra processos em execução e atualiza as informações continuamente.

top

É útil para observar:

- CPU
- Memória
- Processos
- PID

Para sair:

q

"q" — Quit (Sair)

---

"kill" — Kill (Encerrar)

Envia um sinal para um processo.

kill 1234

Aqui:

1234 → PID

Por padrão, o "kill" envia o sinal SIGTERM, pedindo que o processo termine.

---

"kill -9"

kill -9 1234

"-9" — SIGKILL (Encerramento Forçado)

Encerra o processo imediatamente.

Use somente quando necessário, porque o programa não tem oportunidade de finalizar corretamente.

---

"jobs" — Jobs (Tarefas)

Mostra trabalhos executados em segundo plano pelo shell atual.

jobs

---

"&" — Background (Segundo Plano)

Podemos iniciar um comando em segundo plano:

comando &

Exemplo:

sleep 60 &

O terminal continua disponível enquanto o processo executa.

---

"fg" — Foreground (Primeiro Plano)

Traz um processo do segundo plano para o primeiro plano.

fg

---

"bg" — Background (Segundo Plano)

Continua um processo parado em segundo plano.

bg

---

LPIC-1 — O que saber

- Processo = programa em execução.
- PID = identificação numérica do processo.
- "ps" mostra processos.
- "top" acompanha processos em tempo real.
- "kill" envia sinais para processos.
- "kill -9" envia SIGKILL.
- "jobs" mostra tarefas do shell.
- "&" executa em segundo plano.
- "fg" traz para primeiro plano.
- "bg" continua em segundo plano.
- "-e" = Every (Todos).
- "-f" = Full (Completo).

---

Resumo

ps       → listar processos
top      → acompanhar processos
kill PID → enviar sinal
jobs     → tarefas do shell
fg       → primeiro plano
bg       → segundo plano
&        → iniciar em segundo plano

Fluxo simples

comando
   ↓
processo
   ↓
PID
   ↓
kill PID
   ↓
processo encerrado
