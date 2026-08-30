# 📖 PÁGINA 1 — CPU E ARQUITETURA

## 🧠 1. O QUE É A CPU?

A **CPU (Central Processing Unit)** é o componente responsável por executar as instruções dos programas (processador).

De forma simples:

```text
Programa → Instruções → CPU → Execução
```

A CPU recebe instruções, processa os dados necessários e executa as operações solicitadas.

---

## 🏗️ 2. O QUE É ARQUITETURA?

A **arquitetura do processador** define características fundamentais de como a CPU funciona e quais instruções ela consegue executar.

Exemplos:

```text
x86
x86_64
amd64
ARM
aarch64
```

---

## 🔢 3. 32 BITS E 64 BITS

Uma arquitetura pode trabalhar com diferentes tamanhos de palavra.

### 32 bits

Arquitetura que trabalha com uma palavra de 32 bits.

### 64 bits

Arquitetura que trabalha com uma palavra de 64 bits.

Atualmente, sistemas Linux modernos utilizam principalmente arquiteturas de 64 bits.

### ⚠️ ATENÇÃO

64 bits **não significa**:

```text
❌ quantidade de núcleos
❌ quantidade de threads
❌ velocidade do processador
❌ quantidade de GHz
```

É uma característica da arquitetura.

---

## 🧩 4. x86 E x86_64

### x86

`x86` normalmente se refere à arquitetura de 32 bits da família de processadores Intel/AMD.

### x86_64

`x86_64` é a extensão de 64 bits da arquitetura x86 (a AMD fez uma extensão da arquitetura X86 32bits para atender 64bits).

Também pode aparecer como:

```text
amd64
x64
```

Portanto:

```text
x86      → 32 bits
x86_64   → 64 bits
amd64    → 64 bits
x64      → 64 bits
```

### ⚠️ IMPORTANTE

`amd64` não significa que o processador precisa ser AMD.

É o nome utilizado para a arquitetura x86 de 64 bits, também utilizada por processadores Intel.

---

## 📱 5. ARM

**ARM** é outra família de arquitetura de processadores.

É comum em:

- Smartphones
- Tablets
- Dispositivos embarcados
- Servidores
- Computadores

Uma arquitetura ARM de 64 bits pode aparecer no Linux como:

```text
aarch64
```

Portanto:

```text
ARM
└── aarch64 → ARM de 64 bits
```

---

## 🧠 6. CPU, CORES E THREADS

Não confunda esses conceitos.

### CPU

É o processador.

### Core

É um núcleo de processamento dentro da CPU.

### Thread

É uma linha de execução apresentada pelo processador.

Exemplo:

```text
CPU
├── Core 1
│   ├── Thread 1
│   └── Thread 2
│
└── Core 2
    ├── Thread 1
    └── Thread 2
```

Uma CPU pode possuir vários cores (núcleos), e cada core pode apresentar uma ou mais threads.


# 🔍 7. COMANDOS E INTERPRETAÇÃO

## `uname`

### Tradução

**uname = Unix name**

Pode ser entendido como:

> **Nome/informações do Unix**

O comando `uname` mostra informações sobre o sistema.

### `-m`

**machine = máquina**

Solicita a arquitetura da máquina.

```bash
uname -m
```

Exemplo:

```text
x86_64
```

### Interpretação completa:

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

> **arquitetura**

O comando mostra a arquitetura da máquina.

```bash
arch
```

Exemplo:

```text
x86_64
```

### Interpretação:

```text
arch
└── architecture → arquitetura
```

Para este objetivo, `arch` e `uname -m` podem fornecer a mesma informação.

---

# 🖥️ 9. `lscpu`

### Tradução

`lscpu` pode ser entendido como:

**ls = list → listar**

**cpu = Central Processing Unit → Unidade Central de Processamento**

Portanto:

```text
lscpu
└── list CPU → listar informações da CPU
```

O comando mostra informações detalhadas sobre a CPU.

```bash
lscpu
```

---

## `lscpu -e`

### Tradução da flag

**-e = --extended**

**extended = estendido**

Mostra informações estendidas das CPUs em formato de tabela (itens separados).

```bash
lscpu -e
```

Interpretação:

```text
lscpu
└── list CPU → listar informações da CPU

-e
└── extended → estendido
```

---

## `lscpu -p`

### Tradução da flag

**-p = --parse**

**parse = analisar / interpretar**

Exibe informações da CPU em formato adequado para processamento.

```bash
lscpu -p
```

Interpretação:

```text
lscpu
└── list CPU → listar informações da CPU

-p
└── parse → formato para análise/processamento
```

---

# 📂 10. `/proc/cpuinfo`

O arquivo:

```text
/proc/cpuinfo
```

contém informações sobre os processadores fornecidas pelo kernel (arquivo completo das informações acima).

### `cpuinfo`

Pode ser entendido como:

```text
cpu
└── Central Processing Unit

info
└── information → informação
```

Portanto:

```text
cpuinfo
└── informações da CPU
```

Para visualizar:

```bash
cat /proc/cpuinfo
```

---

# 📖 11. `cat`

### Tradução

**cat = concatenate**

Significa:

> **concatenar**

O comando também é utilizado para exibir o conteúdo de arquivos.

```bash
cat /proc/cpuinfo
```

Interpretação:

```text
cat
└── concatenate → concatenar/exibir conteúdo

/proc/cpuinfo
└── arquivo com informações da CPU
```

---

# 🔎 12. `grep`

### Tradução

**grep = Global Regular Expression Print**

Pode ser entendido como:

> **procurar e imprimir linhas que correspondem a um padrão**

O `grep` é utilizado para pesquisar texto (filtrar partes de acordo com as nomes informadas [expressões]).

Exemplo:

```bash
grep 'model name' /proc/cpuinfo
```

Isso procura por `model name`(nome do modelo) dentro de `/proc/cpuinfo`.

---

## `grep -E`

### Tradução da flag

**-E = Extended Regular Expressions**

Significa:

> **Expressões Regulares Estendidas**

Exemplo:

```bash
grep -E '^(model name|cpu cores|siblings)' /proc/cpuinfo (extendida, mais de uma busca entre parênteses)
```

Interpretação:

```text
grep
└── procura um padrão no texto

-E
└── Extended → expressões regulares estendidas (mais de uma expressão, mais de um nome buscado)

'(...)'
└── padrão que será procurado (colocar entre parênteses e separar os nomes por pipes |)

/proc/cpuinfo
└── arquivo onde a pesquisa será realizada
```

---

# 🎯 14. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que é uma CPU.
- O que é arquitetura de CPU.
- Diferença entre 32 bits e 64 bits.
- O que significa `x86`.
- O que significa `x86_64`.
- Que `amd64` representa x86 de 64 bits.
- O que é ARM.
- Que `aarch64` representa ARM de 64 bits.
- Diferença entre CPU, core e thread.
- Que 64 bits não representa quantidade de cores.
- Que 64 bits não representa quantidade de threads.
- Que 64 bits não representa GHz.
- Usar `uname -m`.
- Saber que `uname` significa **Unix name**.
- Saber que `-m` significa **machine**.
- Usar `arch`.
- Saber que `arch` significa **architecture**.
- Usar `lscpu`.
- Entender `ls` como **list**.
- Entender `-e` como **extended**.
- Entender `-p` como **parse**.
- Conhecer `/proc/cpuinfo`.
- Entender `cpuinfo` como informações da CPU.
- Usar `cat` para visualizar arquivos.
- Entender `cat` como **concatenate**.
- Usar `grep` para pesquisar texto.
- Entender `-E` como **Extended Regular Expressions**.

---

# ✅ FIM DA PÁGINA 1
