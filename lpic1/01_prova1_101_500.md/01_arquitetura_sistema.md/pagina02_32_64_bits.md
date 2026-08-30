# 📖 PÁGINA 2 — 32 BITS E 64 BITS

# 🧠 1. O QUE SIGNIFICA 32 BITS E 64 BITS?

**32 bits** e **64 bits** são características da arquitetura do processador e do sistema.

De forma simplificada:

```text
32 bits
└── Arquitetura de 32 bits

64 bits
└── Arquitetura de 64 bits
```

O número de bits está relacionado à forma como o processador trabalha com dados e endereços.

---

# 💻 2. 32 BITS

Um sistema de 32 bits utiliza uma arquitetura de 32 bits.

Um exemplo de arquitetura x86 de 32 bits é:

```text
i386
i486
i586
i686
```

O termo **i686** pode aparecer para identificar sistemas Linux de 32 bits da família x86.

### ⚠️ IMPORTANTE

32 bits não significa:

```text
❌ 32 cores
❌ 32 threads
❌ 32 GHz
```

É uma característica da arquitetura.

---

# 🚀 3. 64 BITS

Um sistema de 64 bits utiliza uma arquitetura de 64 bits.

Na família x86, a arquitetura de 64 bits normalmente aparece como:

```text
x86_64
amd64
```

Esses dois nomes normalmente representam a mesma família de arquitetura x86 de 64 bits.

```text
x86_64
└── x86 de 64 bits

amd64
└── x86 de 64 bits
```

### ⚠️ IMPORTANTE

`amd64` não significa que somente processadores AMD podem utilizar essa arquitetura.

Processadores Intel também podem utilizar `amd64`.

---

# 🧩 4. 32 BITS x 64 BITS

A diferença mais importante para a prova é reconhecer a arquitetura.

```text
32 bits
├── i386
├── i486
├── i586
└── i686

64 bits
├── x86_64
├── amd64
└── x64
```

Além da arquitetura x86, existem outras famílias:

```text
ARM 32 bits
└── arm

ARM 64 bits
└── aarch64
```

---

# 🧠 5. 64 BITS NÃO É VELOCIDADE

Um erro comum é pensar:

```text
64 bits = processador mais rápido
```

Isso está errado.

A quantidade de bits é uma característica da arquitetura.

A velocidade do processador envolve outros fatores, como frequência, arquitetura interna, número de núcleos e outras características.

Portanto:

```text
64 bits ≠ GHz

64 bits ≠ quantidade de cores

64 bits ≠ quantidade de threads
```

---

# 🖥️ 6. ARQUITETURA DO SISTEMA x ARQUITETURA DA CPU

É importante diferenciar:

```text
CPU
└── Possui uma determinada arquitetura

Sistema operacional
└── É compilado para uma determinada arquitetura
```

Por exemplo:

```text
CPU
└── x86_64

Linux
└── x86_64
```

Nesse caso, o sistema Linux está utilizando a arquitetura x86 de 64 bits.

---

# 🔍 7. COMO IDENTIFICAR A ARQUITETURA

## `uname -m`

### Tradução

**uname = Unix name**

Pode ser entendido como:

> Nome/informações do Unix

### `-m`

**machine = máquina**

Mostra a arquitetura da máquina.

```bash
uname -m
```

Exemplo:

```text
x86_64
```

Interpretação:

```text
uname
└── Unix name → informações do sistema

-m
└── machine → máquina

x86_64
└── arquitetura x86 de 64 bits
```

---

# 🏛️ 8. `arch`

### Tradução

**arch = architecture**

Significa:

> arquitetura

O comando mostra a arquitetura da máquina.

```bash
arch
```

Exemplo:

```text
x86_64
```

Interpretação:

```text
arch
└── architecture → arquitetura
```

---

# 🖥️ 9. `lscpu`

### Tradução

`lscpu` pode ser entendido como:

```text
ls
└── list → listar

cpu
└── Central Processing Unit
    → Unidade Central de Processamento
```

Portanto:

```text
lscpu
└── list CPU → listar informações da CPU
```

Comando:

```bash
lscpu
```

Procure principalmente:

```text
Architecture:
```

Exemplo:

```text
Architecture: x86_64
```

Interpretação:

```text
Architecture
└── Arquitetura

x86_64
└── x86 de 64 bits
```

---

# 🔎 10. `lscpu -b`

A opção:

```text
-b
```

significa:

**--bytes**

O comando:

```bash
lscpu -b
```

exibe os tamanhos de memória em bytes quando aplicável.

### ⚠️ Para esta página

Não é necessário decorar essa opção para identificar 32/64 bits.

O mais importante é saber utilizar:

```bash
lscpu
```

e identificar:

```text
Architecture:
```

---

# 📂 11. `/proc/cpuinfo`

O arquivo:

```text
/proc/cpuinfo
```

contém informações sobre os processadores disponíveis para o sistema.

Podemos visualizar com:

```bash
cat /proc/cpuinfo
```

### `cat`

**cat = concatenate**

Significa:

> concatenar

O comando também é utilizado para exibir o conteúdo de arquivos.

```text
cat
└── concatenate → exibir/concatenar conteúdo
```

No `/proc/cpuinfo`, podemos encontrar informações como:

```text
model name
cpu cores
flags
```

---

# 🏷️ 12. IDENTIFICANDO 32 OU 64 BITS NA PRÁTICA

Execute:

```bash
uname -m
```

Se aparecer:

```text
x86_64
```

Temos:

```text
x86
└── Família de arquitetura

64
└── 64 bits
```

Se aparecer algo como:

```text
i686
```

Temos:

```text
i686
└── x86 de 32 bits
```

Se aparecer:

```text
aarch64
```

Temos:

```text
ARM
└── 64 bits
```

---

# 📝 13. COMANDOS NECESSÁRIOS

Para este assunto, concentre-se principalmente nestes comandos:

### Identificar arquitetura

```bash
uname -m
```

```text
uname
└── Unix name → informações do sistema

-m
└── machine → máquina/arquitetura
```

### Identificar arquitetura

```bash
arch
```

```text
arch
└── architecture → arquitetura
```

### Ver informações da CPU

```bash
lscpu
```

```text
ls
└── list → listar

cpu
└── Central Processing Unit → Unidade Central de Processamento
```

### Consultar informações diretamente do kernel

```bash
cat /proc/cpuinfo
```

```text
cat
└── concatenate → exibir/concatenar conteúdo

/proc/cpuinfo
└── informações sobre a CPU
```

---

# 🎯 14. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que significa 32 bits.
- O que significa 64 bits.
- Que 32/64 bits é uma característica da arquitetura.
- Reconhecer `i386`, `i486`, `i586` e `i686` como arquiteturas x86 de 32 bits.
- Reconhecer `x86_64`, `amd64` e `x64` como arquiteturas x86 de 64 bits.
- Reconhecer `aarch64` como ARM de 64 bits.
- Saber que `amd64` também é utilizado por processadores Intel.
- Saber que 64 bits não significa quantidade de cores.
- Saber que 64 bits não significa quantidade de threads.
- Saber que 64 bits não significa GHz.
- Usar `uname -m`.
- Saber que `-m` significa **machine**.
- Usar `arch`.
- Saber que `arch` significa **architecture**.
- Usar `lscpu`.
- Identificar `Architecture:` na saída do `lscpu`.
- Conhecer `/proc/cpuinfo`.
- Usar `cat /proc/cpuinfo`.

---

# 🧠 RESUMO

```text
32 BITS
├── i386
├── i486
├── i586
└── i686

64 BITS
├── x86_64
├── amd64
├── x64
└── aarch64 → ARM de 64 bits

64 bits
≠ cores
≠ threads
≠ GHz

uname -m
└── machine → mostra a arquitetura

arch
└── architecture → mostra a arquitetura

lscpu
└── list CPU → informações da CPU

/proc/cpuinfo
└── informações dos processadores
```

# ✅ FIM DA PÁGINA 2
