# 07 — Processos
## 02 — PID e PPID

### PID — Process ID (ID do Processo)

O **PID** é o número único usado pelo Linux para identificar um processo em execução.

Cada processo recebe um PID.

    ps

Exemplo:

    PID   TTY      TIME     CMD
    1250  pts/0    00:00:00 bash
    1387  pts/0    00:00:00 ps

- `1250` → PID do processo `bash`
- `1387` → PID do processo `ps`

### PID 1 — Primeiro Processo

O processo com **PID 1** é iniciado durante o boot e possui uma função fundamental no sistema.

Em muitas distribuições modernas:

    ps -p 1 -f

- `-p` — PID (selecionar pelo ID do processo)
- `-f` — full (mostrar informações completas)

Normalmente o PID 1 é:

    systemd

Ele pode iniciar e gerenciar diversos serviços do sistema.

---

### PPID — Parent Process ID (ID do Processo Pai)

O **PPID** identifica o processo que criou ou iniciou outro processo.

Exemplo:

    ps -ef

Saída simplificada:

    UID       PID  PPID  CMD
    root        1     0  /sbin/init
    usuario  1250     1  bash
    usuario  1387  1250  ps

Observe a relação:

    PID 1
      └── PID 1250 (bash)
            └── PID 1387 (ps)

Nesse exemplo:

- `bash` → PID `1250`
- `bash` → PPID `1`
- `ps` → PID `1387`
- `ps` → PPID `1250`

Ou seja, o `bash` iniciou o `ps`.

---

### PID × PPID

| Sigla | Inglês | Português |
|---|---|---|
| PID | Process ID | ID do Processo |
| PPID | Parent Process ID | ID do Processo Pai |

**PID** identifica o próprio processo.

**PPID** identifica o processo pai.

---

### Consultando PID e PPID

Com `ps`:

    ps -ef

Para consultar um processo específico:

    ps -p 1250 -o pid,ppid,cmd

- `-p` — PID (selecionar processo pelo ID)
- `-o` — output (definir campos exibidos)
- `pid` — Process ID (ID do processo)
- `ppid` — Parent Process ID (ID do processo pai)
- `cmd` — Command (comando)

Exemplo:

    PID   PPID CMD
    1250     1 bash

---

### Encontrando o PID do processo atual

    echo $$

`$$` representa o **PID do shell atual**.

Exemplo:

    echo $$
    1250

---

### Encontrando o PPID

    echo $PPID

Exemplo:

    echo $PPID
    1000

Nesse caso:

    Shell atual → PID 1250
    Processo pai → PID 1000

---

### Relação entre processos

Os processos normalmente formam uma estrutura de **pai e filho**:

    Processo Pai
        │
        ├── Processo Filho
        │      └── Processo Neto
        │
        └── Outro Processo Filho

O `pstree` permite visualizar essa relação:

    pstree -p

- `-p` — PID (mostrar os IDs dos processos)

Exemplo:

    systemd(1)
    └─bash(1250)
      └─ps(1387)

---

### ⚠️ Atenção para a prova LPIC-1

Memorize:

**PID**
→ identifica o próprio processo.

**PPID**
→ identifica o processo pai.

**PID 1**
→ processo inicial do espaço de usuário; frequentemente `systemd` nas distribuições modernas.

**`$$`**
→ PID do shell atual.

**`$PPID`**
→ PID do processo pai do shell atual.

---

> **Conhecimento só tem valor quando é compartilhado** - Laerte Costa
