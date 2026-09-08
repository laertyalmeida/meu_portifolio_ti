# 08 — Memória
## 03 — free e vmstat

### free — Display Memory Usage (Exibir Uso da Memória)

O `free` mostra o uso da **RAM** e da **Swap**.

    free

Para facilitar a leitura:

    free -h

- `-h` — human-readable (legível por humanos)

Exemplo:

    free -h

                  total   used   free   shared  buff/cache  available
    Mem:             8Gi    3Gi    1Gi      1Gi       4Gi        5Gi
    Swap:            2Gi    0Gi    2Gi

---

### Campos do free

| Campo | Inglês | Português |
|---|---|---|
| `total` | Total | Total disponível |
| `used` | Used | Em uso |
| `free` | Free | Completamente livre |
| `shared` | Shared | Memória compartilhada |
| `buff/cache` | Buffers/Cache | Buffers e cache |
| `available` | Available | Estimada disponível |

⚠️ Para avaliar quanta memória ainda pode ser utilizada, o campo **`available`** é geralmente mais útil que `free`.

---

### Mostrar valores em MB

    free -m

- `-m` — megabytes (megabytes)

Mostrar em bytes:

    free -b

- `-b` — bytes (bytes)

Mostrar continuamente:

    free -h -s 2

- `-s` — seconds (segundos)

Nesse exemplo, o `free` atualiza a cada **2 segundos**.

---

# vmstat — Virtual Memory Statistics (Estatísticas da Memória Virtual)

O `vmstat` apresenta informações sobre:

- processos;
- memória;
- Swap;
- I/O;
- sistema;
- CPU.

Comando básico:

    vmstat

---

### Atualização contínua

    vmstat 2

O `2` define o intervalo de atualização:

    vmstat 2

→ atualiza a cada **2 segundos**.

Para limitar a quantidade de atualizações:

    vmstat 2 5

Significa:

    intervalo = 2 segundos
    atualizações = 5

---

### Principais campos do vmstat

Exemplo simplificado:

    procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu------
     r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs  us sy id wa st

#### Processos

| Campo | Significado |
|---|---|
| `r` | processos executáveis ou aguardando CPU |
| `b` | processos em espera não interrompível |

#### Memória

| Campo | Significado |
|---|---|
| `swpd` | memória virtual usada |
| `free` | memória livre |
| `buff` | memória usada para buffers |
| `cache` | memória usada para cache |

#### Swap

| Campo | Inglês | Português |
|---|---|---|
| `si` | swap in | entrada da Swap |
| `so` | swap out | saída para a Swap |

**`si`**
→ quantidade de memória trazida da Swap para a RAM.

**`so`**
→ quantidade de memória enviada da RAM para a Swap.

⚠️ Valores altos e constantes de `si`/`so` podem indicar pressão de memória.

---

### I/O — Input/Output (Entrada/Saída)

| Campo | Inglês | Português |
|---|---|---|
| `bi` | blocks in | blocos recebidos |
| `bo` | blocks out | blocos enviados |

Esses campos mostram atividade de entrada e saída relacionada aos dispositivos de armazenamento.

---

### CPU — Central Processing Unit (Unidade Central de Processamento)

| Campo | Inglês | Português |
|---|---|---|
| `us` | user | CPU em processos de usuário |
| `sy` | system | CPU em processos do kernel |
| `id` | idle | CPU ociosa |
| `wa` | I/O wait | aguardando I/O |
| `st` | steal | tempo "roubado" por outro sistema virtual |

Exemplo:

    us sy id wa st
    20  5 70  5  0

---

### free × vmstat

| Comando | Principal objetivo |
|---|---|
| `free` | visualizar RAM e Swap |
| `vmstat` | analisar memória, Swap, processos, I/O e CPU |

Use:

    free -h

quando quiser uma visão rápida da memória.

Use:

    vmstat 2

quando quiser observar o comportamento do sistema ao longo do tempo.

---

### ⚠️ Atenção para a prova LPIC-1

Memorize:

    free -h
    free -m
    vmstat
    vmstat 2
    vmstat 2 5

**`free`**
→ mostra o uso da RAM e Swap.

**`vmstat`**
→ mostra estatísticas de memória virtual, processos, I/O e CPU.

**`si`**
→ Swap In — dados saindo da Swap para a RAM.

**`so`**
→ Swap Out — dados saindo da RAM para a Swap.

**`us`**
→ CPU usada por processos de usuário.

**`sy`**
→ CPU usada pelo sistema/kernel.

**`id`**
→ CPU ociosa.

**`wa`**
→ CPU aguardando I/O.

> **Conhecimento só tem valor quando é compartilhado** - Laerte Costa
