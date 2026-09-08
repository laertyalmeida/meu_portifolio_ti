# 09 — Boot e Inicialização
## 07 — journalctl

### O que é o journalctl?

`journalctl` é o comando usado para consultar os **logs (registros)** armazenados pelo **systemd-journald**.

Ele é muito importante para descobrir:

- erros durante o boot;
- falhas de serviços;
- mensagens do kernel;
- problemas de hardware;
- eventos de usuários e processos;
- histórico de inicialização.

---

## 1. Ver todos os logs

    journalctl

Mostra os registros disponíveis no **systemd journal**.

---

## 2. Ver os logs mais recentes

    journalctl -e

**-e — end (fim)**

Vai diretamente para o final dos registros.

---

## 3. Acompanhar logs em tempo real

    journalctl -f

**-f — follow (acompanhar)**

Funciona de maneira semelhante ao:

    tail -f

Útil para acompanhar um serviço enquanto ele está funcionando.

Para sair:

    Ctrl + C

---

## 4. Ver logs do boot atual

    journalctl -b

**-b — boot (inicialização)**

Mostra os registros desde a inicialização atual do sistema.

---

## 5. Ver logs de boots anteriores

Listar os boots registrados:

    journalctl --list-boots

Exemplo:

    -2
    -1
     0

O número `0` representa o boot atual.

Para consultar o boot anterior:

    journalctl -b -1

**-1** → boot anterior

Outro exemplo:

    journalctl -b -2

→ dois boots atrás.

---

## 6. Ver mensagens do Kernel

    journalctl -k

**-k — kernel (núcleo)**

Mostra mensagens relacionadas ao kernel.

É semelhante ao uso de:

    dmesg

---

## 7. Ver logs de um serviço

Exemplo:

    journalctl -u ssh

**-u — unit (unidade)**

Mostra os registros relacionados à unit `ssh`.

Também pode ser usado:

    journalctl -u ssh.service

---

## 8. Acompanhar um serviço em tempo real

    journalctl -u ssh -f

Combina:

**-u** → unidade

**-f** → acompanhar

Muito útil para investigar um serviço enquanto ele recebe novas mensagens.

---

## 9. Ver somente erros

    journalctl -p err

**-p — priority (prioridade)**

**err — error (erro)**

Mostra mensagens com prioridade de erro ou mais grave.

Níveis comuns:

| Código | Nome | Português |
|---|---|---|
| 0 | emerg | Emergência |
| 1 | alert | Alerta |
| 2 | crit | Crítico |
| 3 | err | Erro |
| 4 | warning | Aviso |
| 5 | notice | Aviso importante |
| 6 | info | Informação |
| 7 | debug | Depuração |

---

## 10. Logs por período

### Desde uma determinada data

    journalctl --since "2026-09-08 08:00:00"

**--since** → desde

### Até uma determinada data

    journalctl --until "2026-09-08 10:00:00"

**--until** → até

Também podemos usar expressões:

    journalctl --since "1 hour ago"

→ últimos 60 minutos.

    journalctl --since today

→ registros desde o início do dia.

---

## 11. Ver logs de uma unidade específica

    journalctl -u NetworkManager

Exemplo para procurar problemas de rede:

    journalctl -u NetworkManager -p err

---

## 12. Ver logs de um processo

Podemos filtrar pelo PID:

    journalctl _PID=1234

**_PID** → identificador do processo.

---

## 13. Ver logs de um usuário

Também podemos filtrar pelo UID:

    journalctl _UID=1000

**_UID** → identificador do usuário.

---

## 14. Formato mais simples

    journalctl -o short

**-o — output (saída/formato)**

`short` apresenta o formato tradicional.

Outros formatos importantes:

    journalctl -o json

→ saída em JSON.

    journalctl -o verbose

→ informações detalhadas.

---

## 15. Limitar quantidade de linhas

    journalctl -n 20

**-n — lines (linhas)**

Mostra as últimas 20 linhas.

Exemplo:

    journalctl -n 50

→ últimas 50 mensagens.

---

## 16. Ver logs do boot + erros

Uma combinação muito útil:

    journalctl -b -p err

Interpretação:

**-b** → boot atual

**-p err** → erros e prioridades mais graves

---

## 17. Logs do kernel durante o boot

    journalctl -b -k

Mostra as mensagens do kernel relacionadas ao boot atual.

---

## 18. journalctl x dmesg

### journalctl

Consulta o journal do `systemd`.

    journalctl

Pode mostrar:

- serviços;
- kernel;
- boot;
- processos;
- usuários;
- outros eventos registrados.

### dmesg

Consulta principalmente as mensagens do **kernel**.

    dmesg

Resumo:

    journalctl → journal do systemd
    dmesg      → mensagens do kernel

---

# 🔑 Comandos essenciais para LPIC-1

| Comando | Função |
|---|---|
| `journalctl` | Ver logs |
| `journalctl -e` | Ir para o final |
| `journalctl -f` | Acompanhar em tempo real |
| `journalctl -b` | Logs do boot atual |
| `journalctl --list-boots` | Listar boots |
| `journalctl -b -1` | Logs do boot anterior |
| `journalctl -k` | Logs do kernel |
| `journalctl -u ssh` | Logs de um serviço |
| `journalctl -p err` | Erros e mais graves |
| `journalctl -n 20` | Últimas 20 linhas |
| `journalctl -b -p err` | Erros do boot atual |
| `journalctl --since "1 hour ago"` | Última hora |
| `journalctl --until "..."` | Até determinado momento |

---

## 🎯 Pegadinhas LPIC-1

### `-b`

Não significa "background".

    journalctl -b

**-b → boot (inicialização)**

---

### `-u`

Não significa "user".

    journalctl -u ssh

**-u → unit (unidade)**

---

### `-f`

Não significa "file".

    journalctl -f

**-f → follow (acompanhar)**

---

### `-k`

**-k → kernel**

    journalctl -k

---

## 🧠 Para decorar

    journalctl
        ↓
    CONSULTAR LOGS

    -b
        ↓
    BOOT

    -k
        ↓
    KERNEL

    -u
        ↓
    UNIT

    -f
        ↓
    FOLLOW

    -p
        ↓
    PRIORITY

    -n
        ↓
    NUMBER OF LINES

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
