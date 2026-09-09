# Memória

## 03 — free e vmstat

### 1. free — Exibir Uso da Memória

`free` mostra o uso da **RAM** e da **Swap**.

    free

Para uma visualização mais fácil:

    free -h

`-h` — Human Readable — Legível por Humanos

Exemplo:

    $ free -h
                  total   used   free   shared   buff/cache   available
    Mem:           16Gi    6Gi    2Gi     500Mi       8Gi         9Gi
    Swap:           2Gi    0Gi    2Gi

---

### 2. Principais campos do free

| Campo | Inglês | Significado |
|---|---|---|
| `total` | Total | Quantidade total |
| `used` | Used | Memória em uso |
| `free` | Free | Memória completamente livre |
| `shared` | Shared | Memória compartilhada |
| `buff/cache` | Buffers/Cache | Memória usada por buffers e cache |
| `available` | Available | Estimativa de memória disponível para novos programas |

> **Importante:** `free` não significa simplesmente "memória que pode ser usada".  
> Para avaliar quanto ainda está disponível sem recorrer à Swap, observe principalmente **`available`**.

---

### 3. Mostrar em diferentes unidades

    free -m

`-m` — Megabytes — Megabytes

    free -g

`-g` — Gigabytes — Gigabytes

    free -b

`-b` — Bytes — Bytes

    free -h

`-h` — Human Readable — Legível por Humanos

---

### 4. Atualizar continuamente

    free -h -s 2

`-s` — Seconds — Segundos

Atualiza os valores a cada **2 segundos**.

Também é possível:

    free -h -c 5

`-c` — Count — Quantidade de Atualizações

Executa **5 atualizações**.

---

# vmstat

### 5. vmstat — Relatório de Memória Virtual

`vmstat` significa:

**Virtual Memory Statistics — Estatísticas da Memória Virtual**

Mostra informações sobre:

- processos;
- memória;
- Swap;
- entrada e saída (I/O);
- sistema;
- CPU.

Comando básico:

    vmstat

---

### 6. Exemplo

    $ vmstat

    procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
     r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs  us sy id wa st
     1  0      0  2048   1024   6144    0    0    10    20  500 1000   5  2 92  1  0

---

### 7. Principais campos

#### Processos

| Campo | Significado |
|---|---|
| `r` | Processos executáveis ou aguardando CPU |
| `b` | Processos bloqueados, normalmente esperando I/O |

#### Memória

| Campo | Significado |
|---|---|
| `swpd` | Quantidade de memória virtual usada |
| `free` | Memória livre |
| `buff` | Memória usada por buffers |
| `cache` | Memória usada pelo cache |

#### Swap

| Campo | Inglês | Significado |
|---|---|---|
| `si` | Swap In | Dados trazidos da Swap para a RAM |
| `so` | Swap Out | Dados enviados da RAM para a Swap |

> `si` e `so` altos de forma contínua podem indicar pressão de memória, mas devem ser analisados junto com outros indicadores.

#### I/O

| Campo | Inglês | Significado |
|---|---|---|
| `bi` | Blocks In | Blocos recebidos do dispositivo |
| `bo` | Blocks Out | Blocos enviados ao dispositivo |

#### Sistema

| Campo | Inglês | Significado |
|---|---|---|
| `in` | Interrupts | Interrupções por segundo |
| `cs` | Context Switches | Trocas de contexto por segundo |

#### CPU

| Campo | Inglês | Significado |
|---|---|---|
| `us` | User | Tempo em modo usuário |
| `sy` | System | Tempo em modo kernel |
| `id` | Idle | CPU ociosa |
| `wa` | I/O Wait | Espera por I/O |
| `st` | Steal | Tempo retirado pela virtualização |

---

### 8. Atualização contínua

    vmstat 2

Atualiza a cada **2 segundos**.

Executar 5 vezes:

    vmstat 2 5

    vmstat [intervalo] [quantidade]

Exemplo:

    vmstat 1 10

→ atualiza a cada 1 segundo e mostra 10 relatórios.

---

### 9. free × vmstat

| Comando | Principal objetivo |
|---|---|
| `free` | Ver RAM e Swap |
| `vmstat` | Ver memória, Swap, I/O, processos, sistema e CPU |

**free** é mais simples para verificar rapidamente a memória.

**vmstat** oferece uma visão mais ampla do comportamento do sistema.

---

## Resumo LPIC-1

- `free` → mostra **RAM e Swap**.
- `free -h` → mostra valores em formato legível.
- `available` → indica uma estimativa mais útil da memória disponível.
- `vmstat` → **Virtual Memory Statistics — Estatísticas da Memória Virtual**.
- `vmstat 2` → atualiza a cada 2 segundos.
- `vmstat 2 5` → atualiza a cada 2 segundos, 5 vezes.
- `si` → dados entrando da Swap para a RAM.
- `so` → dados saindo da RAM para a Swap.
- `r` → processos esperando/aptos a executar na CPU.
- `b` → processos bloqueados.
- `us` → CPU em modo usuário.
- `sy` → CPU em modo sistema.
- `id` → CPU ociosa.
- `wa` → CPU aguardando I/O.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
