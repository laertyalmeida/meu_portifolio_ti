# 07 — Processos

## 01 — O que é um Processo?

## Process — Processo

Um **processo** é um **programa em execução**.

Quando um programa é iniciado, o Linux cria um processo para executar suas instruções e controlar os recursos utilizados por ele.

Exemplo:

    firefox

Ao abrir o Firefox, o Linux cria um ou mais processos relacionados ao navegador.

---

## 1. Programa × Processo

Não confunda:

**Program — Programa**

É o arquivo ou conjunto de arquivos que contém o código.

**Process — Processo**

É o programa **em execução** na memória.

Exemplo:

    Programa → /usr/bin/firefox
                  ↓
              execução
                  ↓
    Processo  → Firefox em execução

Um mesmo programa pode criar vários processos.

---

## 2. PID — Process ID

Todo processo possui um número de identificação chamado:

**PID — Process ID (ID do Processo)**

Exemplo:

    PID = 1234

O PID permite identificar e administrar um processo específico.

Para visualizar processos:

    ps

---

## 3. Processo `init` / `systemd`

O processo inicial do sistema normalmente possui:

    PID 1

Em sistemas modernos que utilizam `systemd`:

    systemd → PID 1

Ele é responsável por iniciar e gerenciar diversos serviços e processos do sistema.

---

## 4. PPID — Parent Process ID

**PPID — Parent Process ID (ID do Processo Pai)**

Um processo pode ser criado por outro processo.

O processo que cria outro é chamado de:

**Parent Process — Processo Pai**

O processo criado é:

**Child Process — Processo Filho**

Exemplo:

    Processo Pai
        │
        └── Processo Filho

Para visualizar PID e PPID:

    ps -ef

`-e` — every process (todos os processos)

`-f` — full format (formato completo)

---

## 5. Processo em primeiro plano

**Foreground Process — Processo em Primeiro Plano**

É um processo que está sendo executado diretamente no terminal atual.

Exemplo:

    ping localhost

O terminal fica ocupado enquanto o comando estiver executando.

---

## 6. Processo em segundo plano

**Background Process — Processo em Segundo Plano**

Pode continuar executando sem ocupar diretamente o terminal.

Exemplo:

    ping localhost &

O `&` envia o processo para o **background**.

Podemos consultar os trabalhos:

    jobs

---

## 7. Processos e recursos

Um processo pode utilizar recursos como:

- CPU — Processador
- Memory — Memória
- Files — Arquivos
- Network — Rede
- Devices — Dispositivos

O sistema operacional controla esses recursos para cada processo.

---

## 8. Estados de um processo

Um processo pode assumir diferentes estados.

Com:

    ps

ou:

    ps -l

podemos visualizar informações sobre o estado dos processos.

Estados comuns:

| Código | Inglês | Português |
|---|---|---|
| `R` | Running | Executando |
| `S` | Sleeping | Dormindo/aguardando |
| `D` | Uninterruptible Sleep | Espera não interrompível |
| `T` | Stopped | Parado |
| `Z` | Zombie | Zumbi |

---

## 9. Zombie Process — Processo Zumbi

Um processo **zumbi** já terminou sua execução, mas ainda possui uma entrada na tabela de processos aguardando que o processo pai recolha seu status de término.

Estado:

    Z

Um processo zumbi **não continua executando o programa**.

---

## 10. Ver processos

### `ps` — Process Status (Status dos Processos)

    ps

Mostra processos associados à sessão atual.

Para uma visão mais completa:

    ps -ef

Ou:

    ps aux

As opções de `ps` possuem diferenças de sintaxe conforme o estilo utilizado, por isso não confunda `ps -ef` com `ps aux`.

---

## 11. Process Tree — Árvore de Processos

Podemos visualizar a relação entre processos usando:

    pstree

**pstree — Process Tree (Árvore de Processos)**

Exemplo conceitual:

    systemd
    ├── sshd
    │   └── bash
    │       └── comando
    └── outros processos

Isso ajuda a entender a relação entre **processos pai e filhos**.

---

## 12. LPIC-1 — O que lembrar

- **Process** = programa em execução.
- Cada processo possui um **PID**.
- `PID 1` é o processo inicial do sistema.
- `PPID` identifica o processo pai.
- Processos podem criar processos filhos.
- `ps` → visualizar processos.
- `pstree` → visualizar árvore de processos.
- `R` → Running (executando).
- `S` → Sleeping (dormindo/aguardando).
- `T` → Stopped (parado).
- `Z` → Zombie (zumbi).
- `&` → executa o comando em background.

### Resumo

    Programa
       ↓
    execução
       ↓
    Processo
       │
       ├── PID
       ├── PPID
       ├── Estado
       └── Recursos

    ps
    ps -ef
    ps aux
    pstree
    jobs

> **"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
