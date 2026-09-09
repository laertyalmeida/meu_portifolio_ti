# Processos

## 02 — PID e PPID

### PID — Process ID — ID do Processo

O **PID** é o número que identifica um processo enquanto ele está em execução.

Exemplo:

    PID
    1520

Cada processo recebe um PID pelo kernel.

Para visualizar:

    ps

Exemplo:

    PID TTY          TIME CMD
    1520 pts/0    00:00:00 bash

Nesse caso:

    PID = 1520

---

### PPID — Parent Process ID — ID do Processo Pai

O **PPID** identifica o processo que criou o processo atual.

Exemplo:

    PID    PPID
    1520   1400

Significa:

    Processo Pai
    PID 1400
         │
         ↓
    Processo Filho
    PID 1520

O processo `1520` foi criado pelo processo `1400`.

---

## PID × PPID

| Identificação | Significado |
|---|---|
| PID | Identifica o próprio processo |
| PPID | Identifica o processo pai |
| Parent Process | Processo Pai |
| Child Process | Processo Filho |

Exemplo:

    PID    PPID    CMD
    1400   1000    bash
    1520   1400    sleep

O `sleep` possui:

    PID  = 1520
    PPID = 1400

Portanto, o `bash` é o processo pai do `sleep`.

---

## Visualizando PID e PPID

### ps -ef

    ps -ef

**`-e` — Every Process — Todos os Processos**

**`-f` — Full Format — Formato Completo**

Exemplo:

    UID      PID   PPID  C STIME TTY          TIME CMD
    laerte  1520   1400  0 10:20 pts/0    00:00:00 sleep 100

Aqui:

- `PID` → `1520`
- `PPID` → `1400`
- `CMD` → `sleep 100`

---

### ps -o

Podemos escolher quais informações serão exibidas:

    ps -o pid,ppid,cmd

**`-o` — Output Format — Formato de Saída**

Exemplo:

    PID    PPID CMD
    1520   1400 sleep 100

---

## $$ — PID do Shell Atual

No Bash, a variável especial:

    $$

representa o **PID do shell atual**.

Exemplo:

    echo $$

Resultado:

    1520

---

## $PPID — PID do Processo Pai

No Bash:

    echo $PPID

mostra o **PPID do shell atual**.

Exemplo:

    echo $PPID

Resultado:

    1400

Assim:

    $$      → PID do shell atual
    $PPID   → PID do processo pai

---

## PID 1

O primeiro processo iniciado pelo sistema recebe normalmente:

    PID 1

Em sistemas modernos que utilizam `systemd`:

    PID 1 → systemd

Outros processos podem formar uma árvore abaixo dele.

    PID 1
      │
      ├── PID 1000
      │     ├── PID 1200
      │     └── PID 1300
      │
      └── PID 1400
            └── PID 1520

---

## Encontrar o processo pai

Podemos consultar:

    ps -o pid,ppid,cmd -p 1520

**`-p` — Process ID — ID do Processo**

Mostra informações do PID especificado.

Também podemos usar:

    pstree -p

**pstree — Process Tree — Árvore de Processos**

Mostra os processos em forma de árvore, facilitando a visualização da relação entre pais e filhos.

---

## Resumo LPIC-1

- **PID** → *Process ID* — ID do Processo.
- **PPID** → *Parent Process ID* — ID do Processo Pai.
- PID identifica o próprio processo.
- PPID identifica o processo que criou o processo atual.
- Um processo pode criar processos filhos.
- `ps -ef` → mostra processos em formato completo.
- `ps -o pid,ppid,cmd` → mostra PID, PPID e comando.
- `$$` → PID do shell atual.
- `$PPID` → PID do processo pai do shell atual.
- `PID 1` → primeiro processo do espaço de usuário; em sistemas modernos geralmente é `systemd`.
- `pstree -p` → mostra a árvore de processos.

**Conhecimento só tem valor quando é compartilhado** - Laerte Costa
