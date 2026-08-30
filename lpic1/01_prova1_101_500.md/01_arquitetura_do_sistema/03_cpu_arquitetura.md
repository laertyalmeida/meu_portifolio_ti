CPU e Arquitetura

CPU — Central Processing Unit (Unidade Central de Processamento)

A CPU é o componente responsável por executar as instruções dos programas.

De forma simples:

Programa
   ↓
CPU
   ↓
Executa instruções
   ↓
Resultado

---

Core — Núcleo

Um core (núcleo) é uma unidade de processamento dentro da CPU.

Uma CPU pode ter vários núcleos:

CPU
├── Core 1
├── Core 2
├── Core 3
└── Core 4

Mais núcleos permitem que o sistema execute várias tarefas ao mesmo tempo.

---

Thread — Linha de Execução

Uma thread (linha de execução) é uma sequência de trabalho que pode ser executada pela CPU.

Exemplo:

4 cores / 8 threads

Significa que a CPU possui 4 núcleos e consegue trabalhar com até 8 threads simultaneamente.

---

32-bit e 64-bit

32-bit e 64-bit são arquiteturas que definem, entre outras coisas, como o processador trabalha com dados e endereços de memória.

Hoje, sistemas Linux modernos normalmente usam 64-bit.

---

"uname" — Unix Name (Nome do Unix)

Mostra informações sobre o sistema.

Para descobrir a arquitetura:

uname -m

"-m" — Machine (Máquina)

Mostra a arquitetura do computador.

Exemplo:

x86_64

→ Sistema usando arquitetura x86 de 64-bit.

Outro exemplo:

aarch64

→ Sistema usando arquitetura ARM de 64-bit.

---

Arquitetura x86

x86 é uma família de arquiteturas muito comum em computadores.

Alguns nomes:

i386    → 32-bit
i686    → 32-bit
x86_64  → 64-bit

amd64 também é usado como nome para x86_64.

---

Arquitetura ARM

ARM é outra família de arquiteturas.

É muito usada em:

- Smartphones
- Raspberry Pi
- Servidores
- Computadores

Uma arquitetura ARM de 64-bit normalmente aparece no Linux como:

aarch64

---

LPIC-1 — O que saber

- CPU executa as instruções dos programas.
- Core é um núcleo de processamento.
- Thread é uma linha de execução.
- "uname" mostra informações do sistema.
- "-m" significa Machine e mostra a arquitetura.
- "x86_64" representa x86 de 64-bit.
- "amd64" é outro nome para x86_64.
- "aarch64" representa ARM de 64-bit.

---

Resumo

CPU
 ↓
Cores
 ↓
Threads
 ↓
Executam instruções

x86_64 → x86 64-bit
aarch64 → ARM 64-bit

uname -m
   ↓
Machine
   ↓
Arquitetura do sistema
