# Boot e Inicialização

## 07 — journalctl

### 1. O que é journalctl?

**journalctl — Journal Control — Controle do Journal**

É o comando usado para **consultar os registros (logs) gerenciados pelo `systemd-journald`**.

Esses registros podem conter informações sobre:

- inicialização do sistema;
- serviços;
- kernel;
- erros;
- processos;
- hardware;
- desligamentos e reinicializações.

---

### 2. Visualizar os logs

    journalctl

Mostra os registros disponíveis no **systemd journal**.

Para visualizar de forma mais simples:

    journalctl --no-pager

`--no-pager` — Sem Paginação

---

### 3. Logs do boot atual

    journalctl -b

`-b` — **Boot — Inicialização**

Mostra os registros relacionados ao boot atual.

Ver o boot anterior:

    journalctl -b -1

`-1` → boot anterior.

Outros exemplos:

    journalctl -b 0
    journalctl -b -1
    journalctl -b -2

---

### 4. Logs do Kernel

    journalctl -k

`-k` — **Kernel — Núcleo**

Mostra mensagens do kernel.

É semelhante ao uso de:

    dmesg

para consultar mensagens relacionadas ao kernel.

---

### 5. Logs de um serviço

    journalctl -u ssh

`-u` — **Unit — Unidade**

Mostra os registros da unidade `ssh`.

Também:

    journalctl -u ssh.service

---

### 6. Acompanhar logs em tempo real

    journalctl -f

`-f` — **Follow — Acompanhar**

Fica acompanhando novas mensagens conforme elas aparecem.

Muito útil para observar o comportamento de um serviço enquanto ele está sendo executado.

---

### 7. Últimas mensagens

    journalctl -n

`-n` — **Lines — Linhas**

Mostra as últimas linhas do journal.

Exemplo:

    journalctl -n 50

→ mostra as últimas 50 mensagens.

---

### 8. Logs desde o início do boot

    journalctl -b

Somente mensagens de erro do boot:

    journalctl -b -p err

`-p` — **Priority — Prioridade**

`err` — **Error — Erro**

---

### 9. Prioridades

O journal utiliza níveis de prioridade.

| Nível | Nome | Português |
|---|---|---|
| `0` | `emerg` | Emergência |
| `1` | `alert` | Alerta |
| `2` | `crit` | Crítico |
| `3` | `err` | Erro |
| `4` | `warning` | Aviso |
| `5` | `notice` | Notificação |
| `6` | `info` | Informação |
| `7` | `debug` | Depuração |

Exemplo:

    journalctl -p warning

Mostra mensagens de `warning` e prioridades mais graves.

---

### 10. Filtrar por período

Desde determinado momento:

    journalctl --since "1 hour ago"

`--since` — Desde

Até determinado momento:

    journalctl --until "30 minutes ago"

`--until` — Até

Exemplo:

    journalctl --since today

→ mensagens desde o início do dia.

---

### 11. Logs de um serviço + tempo real

    journalctl -u ssh -f

Combina:

    -u → serviço específico
    -f  → acompanhar em tempo real

Muito útil para diagnosticar um serviço enquanto ele está funcionando.

---

### 12. Ver mensagens de uma inicialização anterior

Listar os boots registrados:

    journalctl --list-boots

Exemplo:

    journalctl --list-boots

Pode mostrar:

    0   atual
    -1  anterior
    -2  dois boots atrás

Consultar um boot específico:

    journalctl -b -1

---

### 13. Logs do kernel + boot

    journalctl -b -k

Mostra as mensagens do kernel referentes ao boot selecionado.

---

### 14. Usuário e serviço

O journal pode registrar informações de diferentes fontes.

É possível filtrar por:

- unidade;
- prioridade;
- boot;
- período;
- PID;
- usuário;
- processo.

Exemplo por PID:

    journalctl _PID=1234

---

### 15. Diagnóstico de problemas

Um fluxo simples:

    1. Identificar o problema
            ↓
    2. Ver o serviço
            ↓
    systemctl status serviço
            ↓
    3. Consultar o journal
            ↓
    journalctl -u serviço
            ↓
    4. Procurar erros
            ↓
    journalctl -p err

---

### 16. journalctl × dmesg

| Comando | Principal uso |
|---|---|
| `journalctl` | Logs gerenciados pelo systemd journal |
| `journalctl -k` | Mensagens do kernel no journal |
| `dmesg` | Mensagens do buffer do kernel |

Em sistemas modernos, `journalctl -k` é especialmente útil para consultar mensagens do kernel que foram registradas no journal.

---

## Resumo LPIC-1

- `journalctl` → consulta os logs do **systemd journal**.
- `journalctl -b` → logs do boot atual.
- `journalctl -b -1` → logs do boot anterior.
- `journalctl --list-boots` → lista boots registrados.
- `journalctl -k` → mensagens do kernel.
- `journalctl -u serviço` → logs de uma unidade/serviço.
- `journalctl -f` → acompanha logs em tempo real.
- `journalctl -n 50` → últimas 50 mensagens.
- `journalctl -p err` → mensagens de erro e prioridades mais graves.
- `journalctl --since` → filtra a partir de determinado momento.
- `journalctl --until` → filtra até determinado momento.
- `journalctl -b -k` → mensagens do kernel do boot selecionado.

### Comandos essenciais

    journalctl
    journalctl -b
    journalctl -k
    journalctl -u ssh
    journalctl -f
    journalctl -n 50
    journalctl -p err
    journalctl --list-boots

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
