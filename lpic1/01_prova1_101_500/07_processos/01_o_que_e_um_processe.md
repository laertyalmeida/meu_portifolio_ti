# Processos

## 01 — Process — Processo

### O que é um processo?

Um **Process — Processo** é um programa que está **sendo executado pelo sistema**.

Um arquivo de programa armazenado no disco não é, por si só, um processo.

Quando o Linux executa esse programa, ele cria um processo na memória.

Exemplo:

    programa no disco
          ↓
       execução
          ↓
       processo
          ↓
    CPU + memória + recursos

---

## Programa × Processo

| Conceito | Significado |
|---|---|
| Program — Programa | Arquivo que contém instruções |
| Process — Processo | Programa em execução |
| PID — Process ID | Identificador do processo |
| CPU | Executa as instruções |
| Memory — Memória | Armazena dados e código usados pelo processo |

Exemplo:

    firefox

O Firefox instalado no disco é um **programa**.

Quando você abre o Firefox, o Linux cria um ou mais **processos** para executá-lo.

---

## PID — Process ID — ID do Processo

Cada processo recebe um número chamado **PID**.

Exemplo:

    PID
    1234

O PID permite identificar aquele processo no sistema.

Podemos consultar processos com:

    ps

Ou:

    ps aux

---

## Processo Pai e Processo Filho

Um processo pode criar outro processo.

O processo que cria é chamado:

**Parent Process — Processo Pai**

O processo criado é chamado:

**Child Process — Processo Filho**

Exemplo:

    Processo Pai
         │
         ├── Processo Filho
         └── Processo Filho

O processo filho possui seu próprio PID e também mantém uma referência ao processo pai.

---

## PPID — Parent Process ID — ID do Processo Pai

O **PPID** identifica o processo que criou determinado processo.

Exemplo:

    PID     PPID
    1234    1000

Nesse caso:

- `PID 1234` → processo atual.
- `PPID 1000` → processo pai.

Podemos visualizar essas informações com:

    ps -ef

---

## PID 1

Durante a inicialização do sistema, um processo especial recebe normalmente o:

    PID 1

Em sistemas Linux modernos, geralmente é o:

    systemd

Ele participa da inicialização e gerenciamento dos serviços do sistema.

---

## Estado do processo

Um processo pode estar em diferentes estados.

Os principais:

| Estado | English | Português |
|---|---|---|
| `R` | Running | Executando ou pronto para executar |
| `S` | Sleeping | Dormindo, aguardando |
| `D` | Uninterruptible Sleep | Espera não interrompível |
| `T` | Stopped | Parado |
| `Z` | Zombie | Finalizado, mas ainda registrado |

O estado pode ser observado com:

    ps

---

## Recursos de um processo

Um processo pode utilizar:

- CPU
- Memória RAM
- Arquivos
- Dispositivos
- Entrada e saída — I/O
- Sinais
- Processos filhos

O Linux controla esses recursos para permitir que vários processos funcionem simultaneamente.

---

## Comandos importantes

### ps — Process Status — Status dos Processos

Mostra informações sobre processos.

    ps

    ps aux

### top — Process Monitor — Monitor de Processos

Mostra processos e consumo de recursos em tempo real.

    top

Esses comandos serão estudados em páginas posteriores.

---

## Resumo LPIC-1

- **Process** → Processo em execução.
- **Program** → Programa armazenado no sistema.
- **PID** → *Process ID* — ID do processo.
- **PPID** → *Parent Process ID* — ID do processo pai.
- **Parent Process** → Processo Pai.
- **Child Process** → Processo Filho.
- Todo processo possui um **PID**.
- Um processo pode criar processos filhos.
- O **PID 1** normalmente é o `systemd` em sistemas Linux modernos.
- `ps` → consultar processos.
- `top` → monitorar processos em tempo real.
- Processos utilizam recursos como CPU, memória e I/O.

**Conhecimento só tem valor quando é compartilhado** - Laerte Costa
