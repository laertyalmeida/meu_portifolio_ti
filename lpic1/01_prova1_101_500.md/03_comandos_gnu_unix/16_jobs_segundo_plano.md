Jobs em Segundo Plano

Foreground — Primeiro Plano

Quando executamos um comando normalmente, o terminal fica ocupado até ele terminar.

sleep 30

Enquanto o comando estiver rodando, aquele terminal fica ocupado.

---

Background — Segundo Plano

Podemos executar um comando em segundo plano usando "&".

sleep 30 &

O comando continua executando e podemos usar o terminal novamente.

Terminal
   ↓
sleep 30 &
   ↓
Segundo plano
   ↓
Terminal disponível

---

"jobs" — Jobs (Tarefas)

Mostra os processos em segundo plano controlados pelo shell atual.

jobs

Exemplo:

[1]+  Running    sleep 30 &

"[1]" — Job ID (Identificador da Tarefa)

É o número usado pelo shell para identificar aquela tarefa.

---

"fg" — Foreground (Primeiro Plano)

Traz uma tarefa do segundo plano para o primeiro plano.

fg

Para trazer uma tarefa específica:

fg %1

%1 → Job 1

---

"bg" — Background (Segundo Plano)

Continua uma tarefa parada em segundo plano.

bg

---

"Ctrl + Z" — Stop (Parar)

Pressionar:

Ctrl + Z

suspende temporariamente o processo que está no primeiro plano.

Exemplo:

comando
   ↓
Ctrl + Z
   ↓
Stopped

Depois podemos continuar em segundo plano:

bg

Ou trazer novamente para o primeiro plano:

fg

---

Exemplo completo

Execute:

sleep 100

Pressione:

Ctrl + Z

O processo fica parado.

Agora:

bg

Ele continua executando em segundo plano.

Confira:

jobs

Depois:

fg

Ele volta para o primeiro plano.

---

"&" x "Ctrl + Z"

& 
↓
inicia diretamente em segundo plano

Ctrl + Z
↓
suspende o processo atual

Depois:

bg
↓
continua em segundo plano

---

LPIC-1 — O que saber

- Foreground = primeiro plano.
- Background = segundo plano.
- "&" inicia um comando em segundo plano.
- "jobs" mostra tarefas do shell.
- "fg" traz uma tarefa para o primeiro plano.
- "bg" continua uma tarefa em segundo plano.
- "Ctrl + Z" suspende o processo atual.
- "%1" representa o Job ID 1.

---

Resumo

comando &
   ↓
Background

jobs
   ↓
ver tarefas

fg
   ↓
Foreground

Ctrl + Z
   ↓
Suspender

bg
   ↓
Background novamente

Para memorizar

&        → iniciar em segundo plano
jobs     → ver tarefas
fg       → primeiro plano
bg       → segundo plano
Ctrl + Z → suspenderJobs em Segundo Plano

Foreground — Primeiro Plano

Quando executamos um comando normalmente, o terminal fica ocupado até ele terminar.

sleep 30

Enquanto o comando estiver rodando, aquele terminal fica ocupado.

---

Background — Segundo Plano

Podemos executar um comando em segundo plano usando "&".

sleep 30 &

O comando continua executando e podemos usar o terminal novamente.

Terminal
   ↓
   sleep 30 &
      ↓
      Segundo plano
         ↓
         Terminal disponível

         ---

         "jobs" — Jobs (Tarefas)

         Mostra os processos em segundo plano controlados pelo shell atual.

         jobs

         Exemplo:

         [1]+  Running    sleep 30 &

         "[1]" — Job ID (Identificador da Tarefa)

         É o número usado pelo shell para identificar aquela tarefa.

         ---

         "fg" — Foreground (Primeiro Plano)

         Traz uma tarefa do segundo plano para o primeiro plano.

         fg

         Para trazer uma tarefa específica:

         fg %1

         %1 → Job 1

         ---

         "bg" — Background (Segundo Plano)

         Continua uma tarefa parada em segundo plano.

         bg

         ---

         "Ctrl + Z" — Stop (Parar)

         Pressionar:

         Ctrl + Z

         suspende temporariamente o processo que está no primeiro plano.

         Exemplo:

         comando
            ↓
            Ctrl + Z
               ↓
               Stopped

               Depois podemos continuar em segundo plano:

               bg

               Ou trazer novamente para o primeiro plano:

               fg

               ---

               Exemplo completo

               Execute:

               sleep 100

               Pressione:

               Ctrl + Z

               O processo fica parado.

               Agora:

               bg

               Ele continua executando em segundo plano.

               Confira:

               jobs

               Depois:

               fg

               Ele volta para o primeiro plano.

               ---

               "&" x "Ctrl + Z"

               & 
               ↓
               inicia diretamente em segundo plano

               Ctrl + Z
               ↓
               suspende o processo atual

               Depois:

               bg
               ↓
               continua em segundo plano

               ---

               LPIC-1 — O que saber

               - Foreground = primeiro plano.
               - Background = segundo plano.
               - "&" inicia um comando em segundo plano.
               - "jobs" mostra tarefas do shell.
               - "fg" traz uma tarefa para o primeiro plano.
               - "bg" continua uma tarefa em segundo plano.
               - "Ctrl + Z" suspende o processo atual.
               - "%1" representa o Job ID 1.

               ---

               Resumo

               comando &
                  ↓
                  Background

                  jobs
                     ↓
                     ver tarefas

                     fg
                        ↓
                        Foreground

                        Ctrl + Z
                           ↓
                           Suspender

                           bg
                              ↓
                              Background novamente

                              Para memorizar

                              &        → iniciar em segundo plano
                              jobs     → ver tarefas
                              fg       → primeiro plano
                              bg       → segundo plano
                              Ctrl + Z → suspenderJobs em Segundo Plano

                              Foreground — Primeiro Plano

                              Quando executamos um comando normalmente, o terminal fica ocupado até ele terminar.

                              sleep 30

                              Enquanto o comando estiver rodando, aquele terminal fica ocupado.

                              ---

                              Background — Segundo Plano

                              Podemos executar um comando em segundo plano usando "&".

                              sleep 30 &

                              O comando continua executando e podemos usar o terminal novamente.

                              Terminal
                                 ↓
                                 sleep 30 &
                                    ↓
                                    Segundo plano
                                       ↓
                                       Terminal disponível

                                       ---

                                       "jobs" — Jobs (Tarefas)

                                       Mostra os processos em segundo plano controlados pelo shell atual.

                                       jobs

                                       Exemplo:

                                       [1]+  Running    sleep 30 &

                                       "[1]" — Job ID (Identificador da Tarefa)

                                       É o número usado pelo shell para identificar aquela tarefa.

                                       ---

                                       "fg" — Foreground (Primeiro Plano)

                                       Traz uma tarefa do segundo plano para o primeiro plano.

                                       fg

                                       Para trazer uma tarefa específica:

                                       fg %1

                                       %1 → Job 1

                                       ---

                                       "bg" — Background (Segundo Plano)

                                       Continua uma tarefa parada em segundo plano.

                                       bg

                                       ---

                                       "Ctrl + Z" — Stop (Parar)

                                       Pressionar:

                                       Ctrl + Z

                                       suspende temporariamente o processo que está no primeiro plano.

                                       Exemplo:

                                       comando
                                          ↓
                                          Ctrl + Z
                                             ↓
                                             Stopped

                                             Depois podemos continuar em segundo plano:

                                             bg

                                             Ou trazer novamente para o primeiro plano:

                                             fg

                                             ---

                                             Exemplo completo

                                             Execute:

                                             sleep 100

                                             Pressione:

                                             Ctrl + Z

                                             O processo fica parado.

                                             Agora:

                                             bg

                                             Ele continua executando em segundo plano.

                                             Confira:

                                             jobs

                                             Depois:

                                             fg

                                             Ele volta para o primeiro plano.

                                             ---

                                             "&" x "Ctrl + Z"

                                             & 
                                             ↓
                                             inicia diretamente em segundo plano

                                             Ctrl + Z
                                             ↓
                                             suspende o processo atual

                                             Depois:

                                             bg
                                             ↓
                                             continua em segundo plano

                                             ---

                                             LPIC-1 — O que saber

                                             - Foreground = primeiro plano.
                                             - Background = segundo plano.
                                             - "&" inicia um comando em segundo plano.
                                             - "jobs" mostra tarefas do shell.
                                             - "fg" traz uma tarefa para o primeiro plano.
                                             - "bg" continua uma tarefa em segundo plano.
                                             - "Ctrl + Z" suspende o processo atual.
                                             - "%1" representa o Job ID 1.

                                             ---

                                             Resumo

                                             comando &
                                                ↓
                                                Background

                                                jobs
                                                   ↓
                                                   ver tarefas

                                                   fg
                                                      ↓
                                                      Foreground

                                                      Ctrl + Z
                                                         ↓
                                                         Suspender

                                                         bg
                                                            ↓
                                                            Background novamente

                                                            Para memorizar

                                                            &        → iniciar em segundo plano
                                                            jobs     → ver tarefas
                                                            fg       → primeiro plano
                                                            bg       → segundo plano
                                                            Ctrl + Z → suspenderJobs em Segundo Plano

                                                            Foreground — Primeiro Plano

                                                            Quando executamos um comando normalmente, o terminal fica ocupado até ele terminar.

                                                            sleep 30

                                                            Enquanto o comando estiver rodando, aquele terminal fica ocupado.

                                                            ---

                                                            Background — Segundo Plano

                                                            Podemos executar um comando em segundo plano usando "&".

                                                            sleep 30 &

                                                            O comando continua executando e podemos usar o terminal novamente.

                                                            Terminal
                                                               ↓
                                                               sleep 30 &
                                                                  ↓
                                                                  Segundo plano
                                                                     ↓
                                                                     Terminal disponível

                                                                     ---

                                                                     "jobs" — Jobs (Tarefas)

                                                                     Mostra os processos em segundo plano controlados pelo shell atual.

                                                                     jobs

                                                                     Exemplo:

                                                                     [1]+  Running    sleep 30 &

                                                                     "[1]" — Job ID (Identificador da Tarefa)

                                                                     É o número usado pelo shell para identificar aquela tarefa.

                                                                     ---

                                                                     "fg" — Foreground (Primeiro Plano)

                                                                     Traz uma tarefa do segundo plano para o primeiro plano.

                                                                     fg

                                                                     Para trazer uma tarefa específica:

                                                                     fg %1

                                                                     %1 → Job 1

                                                                     ---

                                                                     "bg" — Background (Segundo Plano)

                                                                     Continua uma tarefa parada em segundo plano.

                                                                     bg

                                                                     ---

                                                                     "Ctrl + Z" — Stop (Parar)

                                                                     Pressionar:

                                                                     Ctrl + Z

                                                                     suspende temporariamente o processo que está no primeiro plano.

                                                                     Exemplo:

                                                                     comando
                                                                        ↓
                                                                        Ctrl + Z
                                                                           ↓
                                                                           Stopped

                                                                           Depois podemos continuar em segundo plano:

                                                                           bg

                                                                           Ou trazer novamente para o primeiro plano:

                                                                           fg

                                                                           ---

                                                                           Exemplo completo

                                                                           Execute:

                                                                           sleep 100

                                                                           Pressione:

                                                                           Ctrl + Z

                                                                           O processo fica parado.

                                                                           Agora:

                                                                           bg

                                                                           Ele continua executando em segundo plano.

                                                                           Confira:

                                                                           jobs

                                                                           Depois:

                                                                           fg

                                                                           Ele volta para o primeiro plano.

                                                                           ---

                                                                           "&" x "Ctrl + Z"

                                                                           & 
                                                                           ↓
                                                                           inicia diretamente em segundo plano

                                                                           Ctrl + Z
                                                                           ↓
                                                                           suspende o processo atual

                                                                           Depois:

                                                                           bg
                                                                           ↓
                                                                           continua em segundo plano

                                                                           ---

                                                                           LPIC-1 — O que saber

                                                                           - Foreground = primeiro plano.
                                                                           - Background = segundo plano.
                                                                           - "&" inicia um comando em segundo plano.
                                                                           - "jobs" mostra tarefas do shell.
                                                                           - "fg" traz uma tarefa para o primeiro plano.
                                                                           - "bg" continua uma tarefa em segundo plano.
                                                                           - "Ctrl + Z" suspende o processo atual.
                                                                           - "%1" representa o Job ID 1.

                                                                           ---

                                                                           Resumo

                                                                           comando &
                                                                              ↓
                                                                              Background

                                                                              jobs
                                                                                 ↓
                                                                                 ver tarefas

                                                                                 fg
                                                                                    ↓
                                                                                    Foreground

                                                                                    Ctrl + Z
                                                                                       ↓
                                                                                       Suspender

                                                                                       bg
                                                                                          ↓
                                                                                          Background novamente

                                                                                          Para memorizar

                                                                                          &        → iniciar em segundo plano
                                                                                          jobs     → ver tarefas
                                                                                          fg       → primeiro plano
                                                                                          bg       → segundo plano
                                                                                          Ctrl + Z → suspenderJobs em Segundo Plano

                                                                                          Foreground — Primeiro Plano

                                                                                          Quando executamos um comando normalmente, o terminal fica ocupado até ele terminar.

                                                                                          sleep 30

                                                                                          Enquanto o comando estiver rodando, aquele terminal fica ocupado.

                                                                                          ---

                                                                                          Background — Segundo Plano

                                                                                          Podemos executar um comando em segundo plano usando "&".

                                                                                          sleep 30 &

                                                                                          O comando continua executando e podemos usar o terminal novamente.

                                                                                          Terminal
                                                                                             ↓
                                                                                             sleep 30 &
                                                                                                ↓
                                                                                                Segundo plano
                                                                                                   ↓
                                                                                                   Terminal disponível

                                                                                                   ---

                                                                                                   "jobs" — Jobs (Tarefas)

                                                                                                   Mostra os processos em segundo plano controlados pelo shell atual.

                                                                                                   jobs

                                                                                                   Exemplo:

                                                                                                   [1]+  Running    sleep 30 &

                                                                                                   "[1]" — Job ID (Identificador da Tarefa)

                                                                                                   É o número usado pelo shell para identificar aquela tarefa.

                                                                                                   ---

                                                                                                   "fg" — Foreground (Primeiro Plano)

                                                                                                   Traz uma tarefa do segundo plano para o primeiro plano.

                                                                                                   fg

                                                                                                   Para trazer uma tarefa específica:

                                                                                                   fg %1

                                                                                                   %1 → Job 1

                                                                                                   ---

                                                                                                   "bg" — Background (Segundo Plano)

                                                                                                   Continua uma tarefa parada em segundo plano.

                                                                                                   bg

                                                                                                   ---

                                                                                                   "Ctrl + Z" — Stop (Parar)

                                                                                                   Pressionar:

                                                                                                   Ctrl + Z

                                                                                                   suspende temporariamente o processo que está no primeiro plano.

                                                                                                   Exemplo:

                                                                                                   comando
                                                                                                      ↓
                                                                                                      Ctrl + Z
                                                                                                         ↓
                                                                                                         Stopped

                                                                                                         Depois podemos continuar em segundo plano:

                                                                                                         bg

                                                                                                         Ou trazer novamente para o primeiro plano:

                                                                                                         fg

                                                                                                         ---

                                                                                                         Exemplo completo

                                                                                                         Execute:

                                                                                                         sleep 100

                                                                                                         Pressione:

                                                                                                         Ctrl + Z

                                                                                                         O processo fica parado.

                                                                                                         Agora:

                                                                                                         bg

                                                                                                         Ele continua executando em segundo plano.

                                                                                                         Confira:

                                                                                                         jobs

                                                                                                         Depois:

                                                                                                         fg

                                                                                                         Ele volta para o primeiro plano.

                                                                                                         ---

                                                                                                         "&" x "Ctrl + Z"

                                                                                                         & 
                                                                                                         ↓
                                                                                                         inicia diretamente em segundo plano

                                                                                                         Ctrl + Z
                                                                                                         ↓
                                                                                                         suspende o processo atual

                                                                                                         Depois:

                                                                                                         bg
                                                                                                         ↓
                                                                                                         continua em segundo plano

                                                                                                         ---

                                                                                                         LPIC-1 — O que saber

                                                                                                         - Foreground = primeiro plano.
                                                                                                         - Background = segundo plano.
                                                                                                         - "&" inicia um comando em segundo plano.
                                                                                                         - "jobs" mostra tarefas do shell.
                                                                                                         - "fg" traz uma tarefa para o primeiro plano.
                                                                                                         - "bg" continua uma tarefa em segundo plano.
                                                                                                         - "Ctrl + Z" suspende o processo atual.
                                                                                                         - "%1" representa o Job ID 1.

                                                                                                         ---

                                                                                                         Resumo

                                                                                                         comando &
                                                                                                            ↓
                                                                                                            Background

                                                                                                            jobs
                                                                                                               ↓
                                                                                                               ver tarefas

                                                                                                               fg
                                                                                                                  ↓
                                                                                                                  Foreground

                                                                                                                  Ctrl + Z
                                                                                                                     ↓
                                                                                                                     Suspender

                                                                                                                     bg
                                                                                                                        ↓
                                                                                                                        Background novamente

                                                                                                                        Para memorizar

                                                                                                                        &        → iniciar em segundo plano
                                                                                                                        jobs     → ver tarefas
                                                                                                                        fg       → primeiro plano
                                                                                                                        bg       → segundo plano
                                                                                                                        Ctrl + Z → suspenderJobs em Segundo Plano

                                                                                                                        Foreground — Primeiro Plano

                                                                                                                        Quando executamos um comando normalmente, o terminal fica ocupado até ele terminar.

                                                                                                                        sleep 30

                                                                                                                        Enquanto o comando estiver rodando, aquele terminal fica ocupado.

                                                                                                                        ---

                                                                                                                        Background — Segundo Plano

                                                                                                                        Podemos executar um comando em segundo plano usando "&".

                                                                                                                        sleep 30 &

                                                                                                                        O comando continua executando e podemos usar o terminal novamente.

                                                                                                                        Terminal
                                                                                                                           ↓
                                                                                                                           sleep 30 &
                                                                                                                              ↓
                                                                                                                              Segundo plano
                                                                                                                                 ↓
                                                                                                                                 Terminal disponível

                                                                                                                                 ---

                                                                                                                                 "jobs" — Jobs (Tarefas)

                                                                                                                                 Mostra os processos em segundo plano controlados pelo shell atual.

                                                                                                                                 jobs

                                                                                                                                 Exemplo:

                                                                                                                                 [1]+  Running    sleep 30 &

                                                                                                                                 "[1]" — Job ID (Identificador da Tarefa)

                                                                                                                                 É o número usado pelo shell para identificar aquela tarefa.

                                                                                                                                 ---

                                                                                                                                 "fg" — Foreground (Primeiro Plano)

                                                                                                                                 Traz uma tarefa do segundo plano para o primeiro plano.

                                                                                                                                 fg

                                                                                                                                 Para trazer uma tarefa específica:

                                                                                                                                 fg %1

                                                                                                                                 %1 → Job 1

                                                                                                                                 ---

                                                                                                                                 "bg" — Background (Segundo Plano)

                                                                                                                                 Continua uma tarefa parada em segundo plano.

                                                                                                                                 bg

                                                                                                                                 ---

                                                                                                                                 "Ctrl + Z" — Stop (Parar)

                                                                                                                                 Pressionar:

                                                                                                                                 Ctrl + Z

                                                                                                                                 suspende temporariamente o processo que está no primeiro plano.

                                                                                                                                 Exemplo:

                                                                                                                                 comando
                                                                                                                                    ↓
                                                                                                                                    Ctrl + Z
                                                                                                                                       ↓
                                                                                                                                       Stopped

                                                                                                                                       Depois podemos continuar em segundo plano:

                                                                                                                                       bg

                                                                                                                                       Ou trazer novamente para o primeiro plano:

                                                                                                                                       fg

                                                                                                                                       ---

                                                                                                                                       Exemplo completo

                                                                                                                                       Execute:

                                                                                                                                       sleep 100

                                                                                                                                       Pressione:

                                                                                                                                       Ctrl + Z

                                                                                                                                       O processo fica parado.

                                                                                                                                       Agora:

                                                                                                                                       bg

                                                                                                                                       Ele continua executando em segundo plano.

                                                                                                                                       Confira:

                                                                                                                                       jobs

                                                                                                                                       Depois:

                                                                                                                                       fg

                                                                                                                                       Ele volta para o primeiro plano.

                                                                                                                                       ---

                                                                                                                                       "&" x "Ctrl + Z"

                                                                                                                                       & 
                                                                                                                                       ↓
                                                                                                                                       inicia diretamente em segundo plano

                                                                                                                                       Ctrl + Z
                                                                                                                                       ↓
                                                                                                                                       suspende o processo atual

                                                                                                                                       Depois:

                                                                                                                                       bg
                                                                                                                                       ↓
                                                                                                                                       continua em segundo plano

                                                                                                                                       ---

                                                                                                                                       LPIC-1 — O que saber

                                                                                                                                       - Foreground = primeiro plano.
                                                                                                                                       - Background = segundo plano.
                                                                                                                                       - "&" inicia um comando em segundo plano.
                                                                                                                                       - "jobs" mostra tarefas do shell.
                                                                                                                                       - "fg" traz uma tarefa para o primeiro plano.
                                                                                                                                       - "bg" continua uma tarefa em segundo plano.
                                                                                                                                       - "Ctrl + Z" suspende o processo atual.
                                                                                                                                       - "%1" representa o Job ID 1.

                                                                                                                                       ---

                                                                                                                                       Resumo

                                                                                                                                       comando &
                                                                                                                                          ↓
                                                                                                                                          Background

                                                                                                                                          jobs
                                                                                                                                             ↓
                                                                                                                                             ver tarefas

                                                                                                                                             fg
                                                                                                                                                ↓
                                                                                                                                                Foreground

                                                                                                                                                Ctrl + Z
                                                                                                                                                   ↓
                                                                                                                                                   Suspender

                                                                                                                                                   bg
                                                                                                                                                      ↓
                                                                                                                                                      Background novamente

                                                                                                                                                      Para memorizar

                                                                                                                                                      &        → iniciar em segundo plano
                                                                                                                                                      jobs     → ver tarefas
                                                                                                                                                      fg       → primeiro plano
                                                                                                                                                      bg       → segundo plano
                                                                                                                                                      Ctrl + Z → suspenderJobs em Segundo Plano

                                                                                                                                                      Foreground — Primeiro Plano

                                                                                                                                                      Quando executamos um comando normalmente, o terminal fica ocupado até ele terminar.

                                                                                                                                                      sleep 30

                                                                                                                                                      Enquanto o comando estiver rodando, aquele terminal fica ocupado.

                                                                                                                                                      ---

                                                                                                                                                      Background — Segundo Plano

                                                                                                                                                      Podemos executar um comando em segundo plano usando "&".

                                                                                                                                                      sleep 30 &

                                                                                                                                                      O comando continua executando e podemos usar o terminal novamente.

                                                                                                                                                      Terminal
                                                                                                                                                         ↓
                                                                                                                                                         sleep 30 &
                                                                                                                                                            ↓
                                                                                                                                                            Segundo plano
                                                                                                                                                               ↓
                                                                                                                                                               Terminal disponível

                                                                                                                                                               ---

                                                                                                                                                               "jobs" — Jobs (Tarefas)

                                                                                                                                                               Mostra os processos em segundo plano controlados pelo shell atual.

                                                                                                                                                               jobs

                                                                                                                                                               Exemplo:

                                                                                                                                                               [1]+  Running    sleep 30 &

                                                                                                                                                               "[1]" — Job ID (Identificador da Tarefa)

                                                                                                                                                               É o número usado pelo shell para identificar aquela tarefa.

                                                                                                                                                               ---

                                                                                                                                                               "fg" — Foreground (Primeiro Plano)

                                                                                                                                                               Traz uma tarefa do segundo plano para o primeiro plano.

                                                                                                                                                               fg

                                                                                                                                                               Para trazer uma tarefa específica:

                                                                                                                                                               fg %1

                                                                                                                                                               %1 → Job 1

                                                                                                                                                               ---

                                                                                                                                                               "bg" — Background (Segundo Plano)

                                                                                                                                                               Continua uma tarefa parada em segundo plano.

                                                                                                                                                               bg

                                                                                                                                                               ---

                                                                                                                                                               "Ctrl + Z" — Stop (Parar)

                                                                                                                                                               Pressionar:

                                                                                                                                                               Ctrl + Z

                                                                                                                                                               suspende temporariamente o processo que está no primeiro plano.

                                                                                                                                                               Exemplo:

                                                                                                                                                               comando
                                                                                                                                                                  ↓
                                                                                                                                                                  Ctrl + Z
                                                                                                                                                                     ↓
                                                                                                                                                                     Stopped

                                                                                                                                                                     Depois podemos continuar em segundo plano:

                                                                                                                                                                     bg

                                                                                                                                                                     Ou trazer novamente para o primeiro plano:

                                                                                                                                                                     fg

                                                                                                                                                                     ---

                                                                                                                                                                     Exemplo completo

                                                                                                                                                                     Execute:

                                                                                                                                                                     sleep 100

                                                                                                                                                                     Pressione:

                                                                                                                                                                     Ctrl + Z

                                                                                                                                                                     O processo fica parado.

                                                                                                                                                                     Agora:

                                                                                                                                                                     bg

                                                                                                                                                                     Ele continua executando em segundo plano.

                                                                                                                                                                     Confira:

                                                                                                                                                                     jobs

                                                                                                                                                                     Depois:

                                                                                                                                                                     fg

                                                                                                                                                                     Ele volta para o primeiro plano.

                                                                                                                                                                     ---

                                                                                                                                                                     "&" x "Ctrl + Z"

                                                                                                                                                                     & 
                                                                                                                                                                     ↓
                                                                                                                                                                     inicia diretamente em segundo plano

                                                                                                                                                                     Ctrl + Z
                                                                                                                                                                     ↓
                                                                                                                                                                     suspende o processo atual

                                                                                                                                                                     Depois:

                                                                                                                                                                     bg
                                                                                                                                                                     ↓
                                                                                                                                                                     continua em segundo plano

                                                                                                                                                                     ---

                                                                                                                                                                     LPIC-1 — O que saber

                                                                                                                                                                     - Foreground = primeiro plano.
                                                                                                                                                                     - Background = segundo plano.
                                                                                                                                                                     - "&" inicia um comando em segundo plano.
                                                                                                                                                                     - "jobs" mostra tarefas do shell.
                                                                                                                                                                     - "fg" traz uma tarefa para o primeiro plano.
                                                                                                                                                                     - "bg" continua uma tarefa em segundo plano.
                                                                                                                                                                     - "Ctrl + Z" suspende o processo atual.
                                                                                                                                                                     - "%1" representa o Job ID 1.

                                                                                                                                                                     ---

                                                                                                                                                                     Resumo

                                                                                                                                                                     comando &
                                                                                                                                                                        ↓
                                                                                                                                                                        Background

                                                                                                                                                                        jobs
                                                                                                                                                                           ↓
                                                                                                                                                                           ver tarefas

                                                                                                                                                                           fg
                                                                                                                                                                              ↓
                                                                                                                                                                              Foreground

                                                                                                                                                                              Ctrl + Z
                                                                                                                                                                                 ↓
                                                                                                                                                                                 Suspender

                                                                                                                                                                                 bg
                                                                                                                                                                                    ↓
                                                                                                                                                                                    Background novamente

                                                                                                                                                                                    Para memorizar

                                                                                                                                                                                    &        → iniciar em segundo plano
                                                                                                                                                                                    jobs     → ver tarefas
                                                                                                                                                                                    fg       → primeiro plano
                                                                                                                                                                                    bg       → segundo plano
                                                                                                                                                                                    Ctrl + Z → suspenderJobs em Segundo Plano

                                                                                                                                                                                    Foreground — Primeiro Plano

                                                                                                                                                                                    Quando executamos um comando normalmente, o terminal fica ocupado até ele terminar.

                                                                                                                                                                                    sleep 30

                                                                                                                                                                                    Enquanto o comando estiver rodando, aquele terminal fica ocupado.

                                                                                                                                                                                    ---

                                                                                                                                                                                    Background — Segundo Plano

                                                                                                                                                                                    Podemos executar um comando em segundo plano usando "&".

                                                                                                                                                                                    sleep 30 &

                                                                                                                                                                                    O comando continua executando e podemos usar o terminal novamente.

                                                                                                                                                                                    Terminal
                                                                                                                                                                                       ↓
                                                                                                                                                                                       sleep 30 &
                                                                                                                                                                                          ↓
                                                                                                                                                                                          Segundo plano
                                                                                                                                                                                             ↓
                                                                                                                                                                                             Terminal disponível

                                                                                                                                                                                             ---

                                                                                                                                                                                             "jobs" — Jobs (Tarefas)

                                                                                                                                                                                             Mostra os processos em segundo plano controlados pelo shell atual.

                                                                                                                                                                                             jobs

                                                                                                                                                                                             Exemplo:

                                                                                                                                                                                             [1]+  Running    sleep 30 &

                                                                                                                                                                                             "[1]" — Job ID (Identificador da Tarefa)

                                                                                                                                                                                             É o número usado pelo shell para identificar aquela tarefa.

                                                                                                                                                                                             ---

                                                                                                                                                                                             "fg" — Foreground (Primeiro Plano)

                                                                                                                                                                                             Traz uma tarefa do segundo plano para o primeiro plano.

                                                                                                                                                                                             fg

                                                                                                                                                                                             Para trazer uma tarefa específica:

                                                                                                                                                                                             fg %1

                                                                                                                                                                                             %1 → Job 1

                                                                                                                                                                                             ---

                                                                                                                                                                                             "bg" — Background (Segundo Plano)

                                                                                                                                                                                             Continua uma tarefa parada em segundo plano.

                                                                                                                                                                                             bg

                                                                                                                                                                                             ---

                                                                                                                                                                                             "Ctrl + Z" — Stop (Parar)

                                                                                                                                                                                             Pressionar:

                                                                                                                                                                                             Ctrl + Z

                                                                                                                                                                                             suspende temporariamente o processo que está no primeiro plano.

                                                                                                                                                                                             Exemplo:

                                                                                                                                                                                             comando
                                                                                                                                                                                                ↓
                                                                                                                                                                                                Ctrl + Z
                                                                                                                                                                                                   ↓
                                                                                                                                                                                                   Stopped

                                                                                                                                                                                                   Depois podemos continuar em segundo plano:

                                                                                                                                                                                                   bg

                                                                                                                                                                                                   Ou trazer novamente para o primeiro plano:

                                                                                                                                                                                                   fg

                                                                                                                                                                                                   ---

                                                                                                                                                                                                   Exemplo completo

                                                                                                                                                                                                   Execute:

                                                                                                                                                                                                   sleep 100

                                                                                                                                                                                                   Pressione:

                                                                                                                                                                                                   Ctrl + Z

                                                                                                                                                                                                   O processo fica parado.

                                                                                                                                                                                                   Agora:

                                                                                                                                                                                                   bg

                                                                                                                                                                                                   Ele continua executando em segundo plano.

                                                                                                                                                                                                   Confira:

                                                                                                                                                                                                   jobs

                                                                                                                                                                                                   Depois:

                                                                                                                                                                                                   fg

                                                                                                                                                                                                   Ele volta para o primeiro plano.

                                                                                                                                                                                                   ---

                                                                                                                                                                                                   "&" x "Ctrl + Z"

                                                                                                                                                                                                   & 
                                                                                                                                                                                                   ↓
                                                                                                                                                                                                   inicia diretamente em segundo plano

                                                                                                                                                                                                   Ctrl + Z
                                                                                                                                                                                                   ↓
                                                                                                                                                                                                   suspende o processo atual

                                                                                                                                                                                                   Depois:

                                                                                                                                                                                                   bg
                                                                                                                                                                                                   ↓
                                                                                                                                                                                                   continua em segundo plano

                                                                                                                                                                                                   ---

                                                                                                                                                                                                   LPIC-1 — O que saber

                                                                                                                                                                                                   - Foreground = primeiro plano.
                                                                                                                                                                                                   - Background = segundo plano.
                                                                                                                                                                                                   - "&" inicia um comando em segundo plano.
                                                                                                                                                                                                   - "jobs" mostra tarefas do shell.
                                                                                                                                                                                                   - "fg" traz uma tarefa para o primeiro plano.
                                                                                                                                                                                                   - "bg" continua uma tarefa em segundo plano.
                                                                                                                                                                                                   - "Ctrl + Z" suspende o processo atual.
                                                                                                                                                                                                   - "%1" representa o Job ID 1.

                                                                                                                                                                                                   ---

                                                                                                                                                                                                   Resumo

                                                                                                                                                                                                   comando &
                                                                                                                                                                                                      ↓
                                                                                                                                                                                                      Background

                                                                                                                                                                                                      jobs
                                                                                                                                                                                                         ↓
                                                                                                                                                                                                         ver tarefas

                                                                                                                                                                                                         fg
                                                                                                                                                                                                            ↓
                                                                                                                                                                                                            Foreground

                                                                                                                                                                                                            Ctrl + Z
                                                                                                                                                                                                               ↓
                                                                                                                                                                                                               Suspender

                                                                                                                                                                                                               bg
                                                                                                                                                                                                                  ↓
                                                                                                                                                                                                                  Background novamente

                                                                                                                                                                                                                  Para memorizar

                                                                                                                                                                                                                  &        → iniciar em segundo plano
                                                                                                                                                                                                                  jobs     → ver tarefas
                                                                                                                                                                                                                  fg       → primeiro plano
                                                                                                                                                                                                                  bg       → segundo plano
                                                                                                                                                                                                                  Ctrl + Z → suspender
