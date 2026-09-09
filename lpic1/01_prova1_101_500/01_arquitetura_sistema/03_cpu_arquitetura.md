# 01 — Arquitetura do Sistema

## 03 — CPU e Arquitetura

### CPU — Central Processing Unit

**CPU — Unidade Central de Processamento** é o componente responsável por executar as instruções dos programas.

A CPU realiza operações como:

- Cálculos
- Comparações
- Operações lógicas
- Execução de instruções
- Controle das tarefas do sistema

---

### Architecture — Arquitetura

**Architecture — Arquitetura** define como o processador executa instruções e como o sistema operacional trabalha com o hardware.

Algumas arquiteturas encontradas no Linux:

- **x86** → arquitetura de 32 bits.
- **x86_64 — x86 64-bit — x86 de 64 bits**.
- **amd64 — AMD 64-bit — AMD de 64 bits**.
- **ARM — Advanced RISC Machine — arquitetura baseada em RISC**.
- **aarch64 — ARM 64-bit — ARM de 64 bits**.

---

### 32-bit e 64-bit

**32-bit — 32 bits**

Arquitetura com espaço de endereçamento menor.

**64-bit — 64 bits**

Arquitetura capaz de trabalhar com um espaço de endereçamento muito maior.

Atualmente, a maioria dos computadores pessoais e servidores utiliza sistemas de 64 bits.

---

### Core — Núcleo

**Core — Núcleo** é uma unidade física de processamento dentro da CPU.

Uma CPU pode possuir vários núcleos:

    4 cores — 4 núcleos

Cada núcleo pode executar instruções.

---

### Thread — Linha de Execução

**Thread — Linha de Execução** é uma unidade lógica de execução.

Uma CPU com:

    4 cores / 8 threads

possui 4 núcleos físicos e pode apresentar 8 unidades lógicas de processamento ao sistema operacional.

---

### Verificar a arquitetura

**uname — System Information — Informações do Sistema**

    uname -m

`-m` — **machine — máquina**

Mostra a arquitetura da máquina.

Exemplo:

    x86_64

---

### lscpu — List CPU — Listar informações da CPU

    lscpu

Mostra informações detalhadas sobre o processador, incluindo:

- Arquitetura
- Modelo da CPU
- Núcleos
- Threads
- CPUs lógicas
- Recursos suportados

---

### /proc/cpuinfo

**`/proc` — processes — processos**

É um sistema de arquivos virtual que fornece informações do kernel.

O arquivo:

    /proc/cpuinfo

contém informações sobre os processadores disponíveis para o sistema.

Para visualizar:

    cat /proc/cpuinfo

**cat — concatenate — concatenar/exibir conteúdo**

---

### CPU física e CPU lógica

**Physical CPU — CPU física**  
Representa o processador físico instalado no computador.

**Logical CPU — CPU lógica**  
Representa uma unidade de processamento apresentada ao sistema operacional.

Tecnologias como **SMT — Simultaneous Multithreading — Multithreading Simultâneo** permitem que um núcleo físico apresente mais de uma CPU lógica.

---

## Resumo LPIC-1

- **CPU — Central Processing Unit** → Unidade Central de Processamento.
- **Architecture** → arquitetura do processador/sistema.
- **x86** → arquitetura de 32 bits.
- **x86_64 / amd64** → arquitetura de 64 bits.
- **ARM — Advanced RISC Machine** → arquitetura baseada em RISC.
- **aarch64** → ARM de 64 bits.
- **Core** → núcleo físico do processador.
- **Thread** → linha de execução lógica.
- **Physical CPU** → CPU física.
- **Logical CPU** → CPU lógica.
- `uname` → **System Information — Informações do Sistema**.
- `-m` → **machine — máquina**; mostra a arquitetura.
- `lscpu` → **List CPU — Listar informações da CPU**.
- `/proc` → **processes — processos**.
- `/proc/cpuinfo` → informações dos processadores.
- `cat` → **concatenate — concatenar/exibir conteúdo**.
- **SMT — Simultaneous Multithreading** → Multithreading Simultâneo.

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
