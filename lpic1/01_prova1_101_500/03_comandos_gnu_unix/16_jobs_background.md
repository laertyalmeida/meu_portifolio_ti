Jobs and Background — Jobs e Segundo Plano

Job — Tarefa

Um Job (Tarefa) é um comando que está sendo executado pelo shell.

Um programa pode rodar:

Foreground → Primeiro Plano
Background → Segundo Plano

---

Foreground — Primeiro Plano

Quando executamos:

sleep 60

o terminal fica ocupado pelo comando durante 60 segundos.

Você precisa esperar o comando terminar para usar aquele terminal normalmente.

---

"&" — Background (Segundo Plano)

Podemos executar um comando em segundo plano:

sleep 60 &

O terminal fica disponível imediatamente.

sleep 60
     ↓
     &
     ↓
Background

"&"

& → Background → Segundo Plano

---

"jobs" — Jobs (Tarefas)

Mostra os jobs da sessão atual:

jobs

Exemplo:

[1]+ Running    sleep 60 &

"Running" — Executando

O job está em execução.

---

"Ctrl + Z" — Stop Temporarily (Suspender)

Se um programa está rodando em primeiro plano:

sleep 100

pressione:

Ctrl + Z

O processo será suspenso.

Exemplo:

[1]+ Stopped    sleep 100

"Stopped" — Suspenso

O processo não terminou; ele está apenas parado.

---

"bg" — Background (Segundo Plano)

Depois de suspender um processo com "Ctrl + Z", podemos continuar sua execução em segundo plano:

bg

Funcionamento:

Foreground
     ↓
 Ctrl + Z
     ↓
 Suspenso
     ↓
    bg
     ↓
Background

---

"fg" — Foreground (Primeiro Plano)

Traz um job do segundo plano para o primeiro plano:

fg

Podemos especificar o número:

fg %1

"fg"

fg → Foreground → Primeiro Plano

---

Exemplo completo

Execute:

sleep 100

Depois pressione:

Ctrl + Z

Agora:

jobs

O job estará suspenso.

Coloque em segundo plano:

bg

Confira:

jobs

Traga novamente para primeiro plano:

fg

---

"kill" — Enviar Sinal

Também podemos encerrar um processo usando "kill".

kill %1

Aqui:

%1 → Job número 1

Podemos também usar o PID:

kill 1234

1234 → PID do processo

---

🧠 Para a LPIC-1

Memorize:

&       → executar em segundo plano
jobs    → mostrar jobs
Ctrl+Z  → suspender
bg      → continuar em segundo plano
fg      → trazer para primeiro plano
kill    → enviar sinal

Sequência importante

comando
   ↓
Ctrl + Z
   ↓
suspenso
   ↓
bg
   ↓
segundo plano
   ↓
fg
   ↓
primeiro plano

---

Regra simples

Foreground
→ terminal ocupado

Background
→ terminal disponível

E lembre:

comando &

→ executa diretamente em segundo plano.

jobs

→ mostra as tarefas do shell.

fg %1

→ traz o job 1 para o primeiro plano.
