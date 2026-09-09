# Processos

## 06 — nice e renice

### nice — Run with Priority — Executar com Prioridade

O `nice` inicia um processo com um determinado valor de **Nice — Gentileza/Prioridade**.

Esse valor influencia a prioridade de CPU do processo.

Uso básico:

    nice comando

Exemplo:

    nice sleep 100

---

## Nice Value — Valor de Nice

O valor padrão normalmente é:

    0

No Linux, os valores normalmente vão de:

    -20 → maior prioridade
     19 → menor prioridade

Quanto **menor** o valor de nice, maior a prioridade relativa do processo para receber CPU.

| Valor | Prioridade relativa |
|---:|---|
| `-20` | Maior |
| `0` | Padrão |
| `19` | Menor |

> Nice não significa "porcentagem de CPU". É um valor usado pelo escalonador para definir a prioridade relativa entre processos.

---

## Iniciar com menor prioridade

Para iniciar um processo com nice `10`:

    nice -n 10 comando

**`-n` — Adjustment — Ajuste**

Exemplo:

    nice -n 10 ./backup.sh

O processo será iniciado com um valor de nice maior que o padrão, dando-lhe menor prioridade relativa de CPU.

---

## Iniciar com maior prioridade

Para usar um valor negativo:

    sudo nice -n -10 comando

Valores de nice mais baixos aumentam a prioridade relativa.

Usuários comuns normalmente não podem aumentar a prioridade dessa maneira; privilégios administrativos podem ser necessários.

---

# renice — Re-Nice — Alterar Prioridade

O `renice` altera o valor de nice de um processo **que já está executando**.

Exemplo:

    renice 10 -p 1520

**`-p` — PID — ID do Processo**

Nesse caso, o processo `1520` passa a ter nice `10`.

---

## Alterar pelo PID

    sudo renice -n 5 -p 1520

Altera o nice do processo `1520` para `5`.

---

## Consultar o nice

Podemos usar:

    ps -o pid,ni,cmd

O campo:

    NI

significa:

**NI — Nice Value — Valor de Nice**

Exemplo:

    PID   NI  CMD
    1520   5  backup.sh

---

## nice × renice

| Comando | Função |
|---|---|
| `nice` | Inicia um novo processo com determinado nice |
| `renice` | Altera o nice de um processo existente |
| `NI` | Valor de nice |
| `-20` | Maior prioridade relativa |
| `0` | Valor padrão |
| `19` | Menor prioridade relativa |

### Pense assim:

    nice
      ↓
    iniciar processo
      ↓
    definir prioridade

    renice
      ↓
    processo já existe
      ↓
    alterar prioridade

---

## Exemplo prático

Iniciar um processo com prioridade menor:

    nice -n 10 ./backup.sh

Descobrir o PID:

    ps -o pid,ni,cmd

Alterar o processo:

    renice 5 -p 1520

Verificar novamente:

    ps -p 1520 -o pid,ni,cmd

---

## Resumo LPIC-1

- `nice` → **Run with Priority — Executar com Prioridade**.
- `renice` → **Re-Nice — Alterar o valor de Nice**.
- `nice` → usado ao iniciar um processo.
- `renice` → usado em um processo já existente.
- `NI` → valor de nice.
- Nice padrão → `0`.
- Faixa usual → `-20` até `19`.
- `-20` → maior prioridade relativa.
- `19` → menor prioridade relativa.
- `nice -n 10 comando` → inicia com nice `10`.
- `renice 10 -p PID` → altera o nice do processo.
- Valores negativos geralmente exigem privilégios administrativos.

**Conhecimento só tem valor quando é compartilhado** - Laerte Costa
