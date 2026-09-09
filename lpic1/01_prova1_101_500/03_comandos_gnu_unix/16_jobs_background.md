# Comandos GNU/UNIX

## 16 — Jobs e Background

**Job — Tarefa**

Um *job* é um comando ou processo que o Shell está controlando.

**Background — Segundo Plano**

Executar um comando em *background* permite continuar usando o terminal enquanto ele continua executando.

**Foreground — Primeiro Plano**

É quando o comando ocupa o terminal e recebe a entrada diretamente dele.

---

## 1. Foreground — Primeiro Plano

Normalmente, quando executamos:

    sleep 30

O terminal fica ocupado durante 30 segundos.

O comando está em **foreground**.

---

## 2. Background — Segundo Plano

Use `&` no final do comando:

    sleep 30 &

O Shell libera o terminal imediatamente.

Exemplo:

    [1] 12345

- `[1]` → número do **Job — Tarefa**.
- `12345` → **PID — Process ID — Identificador do Processo**.

---

## 3. `jobs` — Jobs — Tarefas

Mostra os jobs controlados pelo Shell:

    jobs

Exemplo:

    [1]+  Running    sleep 100 &
    [2]-  Running    sleep 200 &

Estados comuns:

| Estado | English | Português |
|---|---|---|
| `Running` | Running | Executando |
| `Stopped` | Stopped | Parado |
| `Done` | Done | Concluído |

---

## 4. `Ctrl+Z` — Suspender

Durante um comando em foreground:

    sleep 100

Pressione:

    Ctrl+Z

O Shell suspende o job.

Exemplo:

    [1]+  Stopped    sleep 100

**Ctrl+Z não encerra o processo.**

Ele apenas o suspende.

---

## 5. `bg` — Background — Segundo Plano

Depois de suspender um job:

    bg

O job continua executando em segundo plano.

Exemplo:

    [1]+ sleep 100 &

---

## 6. `fg` — Foreground — Primeiro Plano

Para trazer um job de volta ao primeiro plano:

    fg

Exemplo:

    fg

O último job controlado pelo Shell volta para o foreground.

---

## 7. Trabalhar com vários jobs

Criar dois jobs:

    sleep 100 &
    sleep 200 &

Ver:

    jobs

Exemplo:

    [1]-  Running    sleep 100 &
    [2]+  Running    sleep 200 &

Trazer o job `1` para foreground:

    fg %1

Trazer o job `2`:

    fg %2

---

## 8. `%` — Identificador do Job

O `%` indica que estamos usando o número do **job**, e não o PID.

Exemplo:

    fg %1

ou:

    bg %2

O número depois de `%` corresponde ao número mostrado por `jobs`.

---

## 9. `kill` — Encerrar um Job ou Processo

Podemos usar o PID:

    kill 12345

Ou o número do job:

    kill %1

Por padrão, `kill` envia o sinal:

    SIGTERM

**SIGTERM — Terminate — Terminar**

Solicita que o processo seja encerrado de forma normal.

---

## 10. `Ctrl+C` × `Ctrl+Z`

| Tecla | Ação |
|---|---|
| `Ctrl+C` | Interrompe/solicita encerramento do comando |
| `Ctrl+Z` | Suspende o comando |
| `bg` | Continua o job em background |
| `fg` | Traz o job para foreground |

---

## 11. `nohup` — No Hang Up — Não Desligar

`nohup` permite que um comando continue executando mesmo após o encerramento da sessão, em situações apropriadas.

Exemplo:

    nohup comando &

Por padrão, a saída pode ser direcionada para:

    nohup.out

Exemplo:

    nohup ./script.sh &

---

## 12. `disown` — Remover do Controle do Shell

Remove um job da tabela de jobs do Shell:

    disown %1

Depois disso, o Bash deixa de controlar aquele job.

Pode ser útil quando queremos que um processo não fique associado ao controle normal de jobs daquela sessão.

---

## 13. `wait` — Esperar

`wait` faz o Shell esperar a conclusão de um job ou processo.

Exemplo:

    sleep 5 &
    wait

O Shell espera o `sleep` terminar.

Com um job específico:

    sleep 10 &
    wait %1

---

## 14. Fluxo completo

Executar:

    sleep 100

Suspender:

    Ctrl+Z

Continuar em background:

    bg

Ver:

    jobs

Trazer para foreground:

    fg

Encerrar:

    Ctrl+C

---

## 15. Conceitos importantes

**Job — Tarefa**

É a forma como o Shell identifica um trabalho sob seu controle.

**Process — Processo**

É uma instância de um programa em execução.

**PID — Process ID — Identificador do Processo**

Número usado pelo sistema para identificar um processo.

**Foreground — Primeiro Plano**

O comando está associado diretamente ao terminal.

**Background — Segundo Plano**

O comando continua executando enquanto o terminal fica disponível.

**Job Control — Controle de Jobs**

Conjunto de recursos do Shell para suspender, continuar, colocar em background e trazer jobs para foreground.

---

## Resumo LPIC-1

- `comando &` → executa o comando em **background**.
- `jobs` → mostra jobs controlados pelo Shell.
- `Ctrl+Z` → suspende um job.
- `bg` → continua um job em background.
- `fg` → traz um job para foreground.
- `fg %1` → traz o job 1 para foreground.
- `bg %1` → continua o job 1 em background.
- `kill %1` → envia sinal para o job 1.
- `Ctrl+C` → interrompe o comando em foreground.
- `nohup comando &` → permite que o comando continue após a saída da sessão, conforme o ambiente.
- `disown` → remove o job do controle do Shell.
- `wait` → espera um job/processo terminar.
- `[1]` → número do job.
- **PID** → identificador do processo.
- **Job ≠ PID**: o job é controlado pelo Shell; o PID identifica o processo no sistema.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
