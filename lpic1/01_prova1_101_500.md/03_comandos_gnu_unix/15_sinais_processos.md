Sinais de Processos

Signal — Sinal

Um Signal (Sinal) é uma mensagem enviada pelo Linux para um processo.

Os sinais podem pedir que um processo:

- Termine.
- Pare.
- Continue.
- Reaja de alguma maneira.

O comando mais usado para enviar sinais é:

kill PID

---

"SIGTERM" — Terminate (Encerrar)

É o sinal padrão enviado pelo "kill".

kill 1234

"SIGTERM" — Termination Request (Pedido de Encerramento)

Pede ao processo para terminar.

O programa pode receber o sinal e fazer uma finalização correta.

---

"SIGKILL" — Kill (Encerramento Forçado)

Número:

9

Comando:

kill -9 1234

"-9" — SIGKILL (Encerramento Forçado)

Força o encerramento do processo.

O processo não pode ignorar ou tratar o "SIGKILL".

Use quando o processo não responde ao encerramento normal.

---

"SIGSTOP" — Stop (Parar)

Número:

19

Para o processo.

kill -STOP 1234

Ou:

kill -19 1234

---

"SIGCONT" — Continue (Continuar)

Continua um processo que foi parado.

kill -CONT 1234

Ou:

kill -18 1234

---

"SIGHUP" — Hang Up (Desconexão)

Número:

1

Originalmente relacionado ao encerramento de uma conexão de terminal.

Também é usado por alguns programas para reler suas configurações.

Exemplo:

kill -HUP 1234

---

"SIGINT" — Interrupt (Interromper)

Número:

2

Normalmente enviado quando pressionamos:

Ctrl + C

É usado para interromper um processo em execução no terminal.

---

"SIGQUIT" — Quit (Sair)

Número:

3

Normalmente enviado com:

Ctrl + \

Pode fazer o processo terminar e gerar um core dump (despejo de memória).

---

Ver os sinais

Podemos listar os sinais disponíveis:

kill -l

"-l" — List (Listar)

Mostra os sinais disponíveis.

---

Tabela para memorizar

Número| Sinal| Tradução
1| SIGHUP| Desconectar
2| SIGINT| Interromper
3| SIGQUIT| Sair
9| SIGKILL| Encerrar à força
15| SIGTERM| Pedir encerramento
18| SIGCONT| Continuar
19| SIGSTOP| Parar

---

LPIC-1 — O que saber

Os sinais mais importantes para a prova são:

1  → SIGHUP
2  → SIGINT
3  → SIGQUIT
9  → SIGKILL
15 → SIGTERM
18 → SIGCONT
19 → SIGSTOP

O mais importante:

SIGTERM → pede para terminar
SIGKILL → força o término
SIGSTOP → para
SIGCONT → continua

"kill"

kill 1234

→ envia SIGTERM.

kill -9 1234

→ envia SIGKILL.

kill -l

→ lista os sinais.

Flag

-l → List (Listar)
