# 🖥️ LPIC-1 — CPU E ARQUITETURA

## 1. CPU — UNIDADE CENTRAL DE PROCESSAMENTO

CPU significa:

**Central Processing Unit**

Em português:

**Unidade Central de Processamento.**

A CPU é o componente responsável por **executar instruções**.

Um programa é formado por instruções que precisam ser executadas.

Por exemplo, uma instrução pode pedir:

```text
some dois números
compare dois valores
mova um dado
leia uma posição da memória
grave um resultado
faça um cálculo
```

A CPU recebe essas instruções, interpreta o que precisa ser feito e executa as operações.

### Uma visão simples

```text
PROGRAMA
   ↓
INSTRUÇÕES
   ↓
CPU
   ↓
EXECUÇÃO
   ↓
RESULTADO
```

---

# 2. COMO A CPU EXECUTA INSTRUÇÕES

A CPU não simplesmente recebe um programa inteiro e "faz tudo de uma vez".

Ela trabalha continuamente com instruções.

Um modelo simplificado é:

```text
BUSCAR
  ↓
DECODIFICAR
  ↓
EXECUTAR
  ↓
BUSCAR PRÓXIMA
  ↓
DECODIFICAR
  ↓
EXECUTAR
```

Esse processo é chamado de **ciclo de instrução**.

---

# 3. CICLO DE INSTRUÇÃO

Podemos dividir o ciclo básico em três etapas:

```text
FETCH
  ↓
DECODE
  ↓
EXECUTE
```

## FETCH — BUSCA

A CPU busca a próxima instrução que precisa executar.

Ela precisa saber:

> "Qual é a próxima instrução?"

Para isso, existe um registrador chamado **Program Counter (PC)**, também conhecido em algumas arquiteturas como **Instruction Pointer (IP)**.

Ele indica a localização da próxima instrução a ser buscada.

---

## DECODE — DECODIFICAÇÃO

A CPU recebe a instrução e precisa descobrir:

> "O que essa instrução significa?"

A Unidade de Controle interpreta a instrução.

Por exemplo:

```text
INSTRUÇÃO:
somar A + B
```

A CPU precisa identificar:

```text
Operação → soma
Dados    → A e B
Destino  → onde colocar o resultado
```

---

## EXECUTE — EXECUÇÃO

Agora a CPU realiza a operação.

Por exemplo:

```text
A = 10
B = 5

10 + 5

RESULTADO = 15
```

A operação pode ser realizada pela **ALU**.

---

# 4. COMPONENTES IMPORTANTES DA CPU

Podemos imaginar a CPU assim:

```text
                 CPU
                  │
       ┌──────────┼──────────┐
       ↓          ↓          ↓
 Unidade de      ALU    Registradores
 Controle
       │                     │
       └─────────┬───────────┘
                 ↓
               Cache
```

Os principais componentes que precisamos entender são:

* Unidade de Controle;
* ALU;
* registradores;
* cache;
* clock.

---

# 5. UNIDADE DE CONTROLE — CU

CU significa:

**Control Unit**

Em português:

**Unidade de Controle.**

Ela coordena a execução das instruções.

De forma simplificada:

```text
Instrução
   ↓
Unidade de Controle
   ↓
"o que precisa ser feito?"
   ↓
coordena a execução
```

Ela ajuda a determinar quais operações devem acontecer e em qual ordem.

---

# 6. ALU

ALU significa:

**Arithmetic Logic Unit**

Em português:

**Unidade Lógica e Aritmética.**

É responsável por operações matemáticas e lógicas.

### Operações matemáticas

```text
+
-
×
÷
```

### Operações lógicas

```text
AND
OR
XOR
NOT
```

Também realiza operações de comparação.

Por exemplo:

```text
10 > 5
```

Resultado:

```text
VERDADEIRO
```

---

# 7. REGISTRADORES

Registradores são pequenas áreas de armazenamento **dentro da CPU**.

Eles são extremamente rápidos.

Podemos pensar assim:

```text
DISCO
  ↓
RAM
  ↓
CACHE
  ↓
REGISTRADORES
  ↓
CPU
```

Os registradores ficam muito próximos da unidade de execução da CPU e armazenam valores necessários para as operações.

Exemplo:

```text
10 + 20
```

A CPU pode trabalhar com:

```text
Registrador A → 10
Registrador B → 20
```

Depois:

```text
ALU
 ↓
10 + 20
 ↓
30
```

O resultado pode ser colocado novamente em um registrador.

---

# 8. PROGRAM COUNTER

Um registrador muito importante é o:

**Program Counter (PC)**.

Ele mantém a referência da próxima instrução que deve ser buscada.

Imagine:

```text
1000 → instrução A
1004 → instrução B
1008 → instrução C
1012 → instrução D
```

O PC indica onde está a próxima instrução.

```text
PC = 1000
 ↓
executa A

PC = 1004
 ↓
executa B

PC = 1008
 ↓
executa C
```

Esse conceito é fundamental para entender como a CPU percorre um programa.

---

# 9. CACHE

A CPU é muito rápida comparada à memória RAM.

Se a CPU tivesse que esperar a RAM toda vez que precisasse de um dado, haveria desperdício de tempo.

Por isso existem caches.

As principais são:

```text
L1
L2
L3
```

### L1

* Muito rápida.
* Muito pequena.
* Fica extremamente próxima das unidades de execução.

### L2

* Maior que L1.
* Um pouco mais lenta que L1.
* Ainda muito rápida.

### L3

* Maior.
* Normalmente compartilhada entre vários núcleos.
* Mais lenta que L1 e L2.
* Ainda muito mais rápida que acessar a RAM em muitos cenários.

Simplificando:

```text
REGISTRADORES
     ↓
    L1
     ↓
    L2
     ↓
    L3
     ↓
    RAM
     ↓
   DISCO
```

Quanto mais próximo da CPU:

```text
mais rápido
menor capacidade
maior custo
```

---

# 10. CLOCK

A CPU trabalha sincronizada por ciclos de clock.

A frequência é medida em:

```text
Hz
MHz
GHz
```

1 GHz significa aproximadamente:

```text
1 bilhão de ciclos por segundo
```

Porém, cuidado:

> **1 GHz não significa necessariamente 1 bilhão de instruções por segundo.**

Uma instrução pode exigir vários ciclos, e CPUs diferentes podem realizar quantidades diferentes de trabalho por ciclo.

Por isso:

```text
GHz ≠ desempenho total
```

---

# 11. NÚCLEOS — CORES

Um **core** é um núcleo de processamento.

Uma CPU pode possuir:

```text
1 core
2 cores
4 cores
8 cores
16 cores
...
```

Por exemplo:

```text
CPU
├── Core 1
├── Core 2
├── Core 3
└── Core 4
```

Uma CPU com 4 núcleos possui quatro unidades de processamento capazes de executar trabalho de forma concorrente.

---

# 12. THREADS

Thread é uma unidade de execução.

Uma CPU pode apresentar ao sistema operacional mais threads lógicas do que possui núcleos físicos.

Por exemplo:

```text
4 cores
8 threads
```

Uma forma simplificada de visualizar:

```text
Core 1 → Thread 1 + Thread 2
Core 2 → Thread 3 + Thread 4
Core 3 → Thread 5 + Thread 6
Core 4 → Thread 7 + Thread 8
```

Isso pode ocorrer através de tecnologias como:

```text
SMT
Hyper-Threading
```

Dependendo do fabricante.

### Importante

Não pense:

```text
4 cores + 8 threads = 8 cores
```

Não são 8 núcleos físicos.

São:

```text
4 núcleos físicos
8 threads lógicas
```

---

# 13. CPU EM 100%

Quando o sistema mostra:

```text
CPU = 100%
```

isso significa que a capacidade de processamento disponível está sendo totalmente utilizada durante aquele intervalo de medição.

Por exemplo:

```text
4 cores

Core 1 → 100%
Core 2 → 100%
Core 3 → 100%
Core 4 → 100%
```

A CPU está muito ocupada.

Mas:

> CPU em 100% não significa necessariamente que o computador está com problema.

Pode ser um programa realizando uma tarefa pesada.

---

# 14. ARQUITETURA DE COMPUTADORES

Agora chegamos a um dos conceitos mais importantes.

**Arquitetura** é o conjunto de características e regras que definem como o computador e o processador funcionam do ponto de vista que os programas precisam conhecer.

Um dos elementos mais importantes é a:

**ISA — Instruction Set Architecture**

Ou:

**Arquitetura do Conjunto de Instruções.**

A ISA define, entre outras coisas:

```text
quais instruções a CPU entende
quais registradores existem
como as instruções funcionam
como os dados são manipulados
```

---

# 15. ISA

Imagine que a CPU fale uma determinada linguagem.

Uma arquitetura define essa linguagem.

Por exemplo:

```text
Programa
   ↓
instruções
   ↓
ISA
   ↓
CPU entende
```

Se um programa foi compilado para uma determinada arquitetura, ele precisa utilizar instruções que aquela CPU consiga entender.

Por isso existe diferença entre:

```text
x86
x86-64
ARM
```

---

# 16. 32 BITS × 64 BITS

Agora vamos conectar isso ao que estudamos anteriormente.

Quando falamos:

```text
32 bits
64 bits
```

estamos falando de características da arquitetura, incluindo o tamanho de determinados elementos internos, como registradores e operações, além do modelo de endereçamento.

### 32 bits

Um sistema de 32 bits trabalha com valores de 32 bits em determinados contextos arquiteturais.

### 64 bits

Um sistema de 64 bits trabalha com valores de 64 bits em determinados contextos arquiteturais.

Isso permite trabalhar com espaços de endereçamento muito maiores.

---

# 17. ENDEREÇAMENTO DE MEMÓRIA

Imagine que a RAM seja uma enorme sequência de posições.

Cada posição precisa ser identificada.

```text
Endereço 0
Endereço 1
Endereço 2
Endereço 3
...
```

A CPU utiliza endereços para localizar dados na memória.

Com 32 bits, teoricamente existem:

```text
2³²
```

possíveis combinações de endereços.

Isso corresponde a:

```text
4.294.967.296
```

aproximadamente:

```text
4 GiB
```

de espaço de endereçamento em um modelo simples de endereçamento byte a byte.

Já 64 bits permite:

```text
2⁶⁴
```

combinações teóricas.

É um espaço de endereçamento gigantesco.

### Atenção

Isso **não significa** que uma CPU 64-bit necessariamente possui fisicamente 2⁶⁴ bytes de RAM.

Os processadores atuais normalmente implementam menos bits de endereço físico do que 64.

O ponto principal é:

> 64 bits permite um espaço de endereçamento muito maior que 32 bits.

---

# 18. x86

Originalmente, x86 está relacionado à família de arquiteturas derivadas dos processadores Intel 8086 e seus sucessores.

Historicamente tivemos:

```text
8086
80286
80386
80486
...
```

Daí surgiu a denominação:

```text
x86
```

Atualmente, "x86" também é frequentemente utilizado de forma genérica para se referir à família de processadores compatíveis com essa arquitetura.

---

# 19. AMD64 / x86-64

A AMD desenvolveu uma extensão de 64 bits para a arquitetura x86.

Ela ficou conhecida como:

```text
AMD64
```

Também encontramos:

```text
x86-64
x64
```

Esses nomes estão relacionados à arquitetura x86 de 64 bits.

Portanto:

```text
AMD64
   ↓
arquitetura x86 de 64 bits
```

Não significa que somente processadores AMD podem utilizá-la.

Processadores Intel modernos também implementam essa arquitetura de 64 bits.

---

# 20. RISC × CISC

Agora vamos comparar duas filosofias de arquitetura.

## CISC

**Complex Instruction Set Computer**

Ideia geral:

```text
instruções mais complexas
```

A família x86 é tradicionalmente classificada como CISC.

---

## RISC

**Reduced Instruction Set Computer**

Ideia geral:

```text
instruções mais simples
```

Arquiteturas ARM são associadas à filosofia RISC.

---

# 21. RISC NÃO SIGNIFICA "CPU FRACA"

Isso é muito importante.

RISC não significa:

```text
menos potência
```

CISC não significa:

```text
mais potência
```

São filosofias diferentes de projeto.

Hoje as diferenças são mais complexas do que simplesmente:

```text
RISC = simples
CISC = complexo
```

Processadores modernos utilizam diversas técnicas internas para aumentar o desempenho.

---

# 22. PROCESSAMENTO

Agora podemos entender melhor o que significa **processar**.

Quando um programa solicita alguma coisa:

```text
Programa
   ↓
instruções
   ↓
CPU
```

A CPU:

```text
busca
 ↓
decodifica
 ↓
executa
```

Durante a execução, ela pode:

```text
calcular
comparar
mover dados
carregar dados
armazenar dados
tomar decisões
```

---

# 23. DADOS × INSTRUÇÕES

É importante diferenciar:

### Instrução

Diz **o que fazer**.

```text
some
compare
carregue
grave
pule
```

### Dado

É aquilo sobre o qual a operação trabalha.

```text
10
20
"João"
arquivo
endereço
etc.
```

Por exemplo:

```text
INSTRUÇÃO:
somar

DADOS:
10 + 20
```

A CPU executa a instrução utilizando os dados necessários.

---

# 24. CPU × RAM

A CPU não utiliza o armazenamento do computador da mesma forma que utiliza a RAM.

Uma visão simplificada:

```text
SSD / HDD
   ↓
RAM
   ↓
CACHE
   ↓
REGISTRADORES
   ↓
CPU
```

Quando um programa está sendo executado, seus dados e instruções precisam estar disponíveis para o processador.

A RAM funciona como uma área de trabalho muito mais rápida que o armazenamento permanente.

---

# 25. POR QUE A RAM PODE DEIXAR O COMPUTADOR LENTO?

Imagine:

```text
CPU → muito rápida
RAM → capacidade limitada
```

Se a RAM disponível acabar, o sistema pode precisar utilizar armazenamento como parte do gerenciamento de memória.

Isso é muito mais lento que RAM.

Simplificando:

```text
RAM disponível
     ↓
CPU trabalha normalmente

RAM insuficiente
     ↓
uso maior de memória virtual
     ↓
armazenamento
     ↓
latência muito maior
     ↓
sistema pode ficar lento
```

Portanto, nem sempre a CPU é o problema.

---

# 26. CPU × SISTEMA OPERACIONAL

O sistema operacional gerencia a utilização da CPU.

Imagine vários programas:

```text
Firefox
Terminal
Editor
SSH
Servidor
etc.
```

Todos querem executar.

A CPU precisa decidir qual trabalho será executado em determinado momento.

O Kernel utiliza um mecanismo chamado:

**escalonamento (scheduling).**

---

# 27. PROCESSO

Um processo é uma instância de um programa em execução.

Por exemplo:

```text
Programa:
Firefox

Processo:
Firefox em execução
```

O Kernel acompanha esses processos e determina quando eles recebem tempo de CPU.

---

# 28. THREAD × PROCESSO

Um processo pode possuir uma ou várias threads.

```text
PROCESSO
   │
   ├── Thread
   ├── Thread
   └── Thread
```

As threads representam unidades de execução dentro do processo.

O sistema operacional agenda essas unidades para execução nos processadores lógicos disponíveis.

---

# 29. ESCALONAMENTO

Imagine:

```text
CPU
 │
 ├── Firefox
 ├── Terminal
 ├── SSH
 └── Serviço DNS
```

Todos querem utilizar a CPU.

O Kernel organiza o acesso.

De forma simplificada:

```text
Processo A
   ↓
CPU
   ↓
Processo B
   ↓
CPU
   ↓
Processo C
   ↓
CPU
```

Isso acontece em intervalos muito pequenos.

Para o usuário, parece que vários programas estão executando simultaneamente.

---

# 30. MODO USUÁRIO × MODO KERNEL

O processador possui diferentes níveis de privilégio.

Dois conceitos importantes no Linux são:

```text
USER SPACE
KERNEL SPACE
```

### User Space

Onde normalmente executam os programas dos usuários.

```text
Firefox
Terminal
Python
Editor
etc.
```

### Kernel Space

Onde o Kernel executa código com privilégios maiores para controlar recursos do sistema.

---

# 31. SYSTEM CALL

Um programa normalmente não acessa diretamente determinados recursos privilegiados do hardware.

Ele solicita ao Kernel.

Por exemplo:

```text
Programa
   ↓
System Call
   ↓
Kernel
   ↓
Hardware
```

Uma system call é uma forma de um programa solicitar um serviço ao Kernel.

Exemplos de operações:

```text
abrir arquivo
ler arquivo
gravar arquivo
criar processo
alocar recursos
comunicar-se
```

---

# 32. CPU × KERNEL × HARDWARE

Agora podemos juntar tudo:

```text
              APLICAÇÃO
                  ↓
             SYSTEM CALL
                  ↓
                KERNEL
                  ↓
               DRIVER
                  ↓
               HARDWARE
```

E quem executa o código do programa e do Kernel?

```text
CPU
```

A CPU é o componente que executa as instruções.

O Kernel é o software que gerencia os recursos do computador.

---

# 33. CPU × DRIVER

Um driver é software que permite ao sistema operacional trabalhar com determinado hardware.

Por exemplo:

```text
Kernel
  ↓
Driver
  ↓
Placa de rede
```

O driver contém código que sabe como trabalhar com aquele dispositivo.

Por isso, quando estudamos Linux, aparecem módulos como:

```text
e1000e
```

Esse é um exemplo de módulo/driver associado a determinados dispositivos de rede Intel.

---

# 34. CPU × BARRAMENTOS

A CPU também precisa se comunicar com outros componentes.

Existem tecnologias e barramentos como:

```text
PCIe
USB
SATA
NVMe
```

Por meio dessas estruturas, o sistema consegue comunicar-se com dispositivos.

Uma visão simplificada:

```text
                 CPU
                  │
              Barramentos
                  │
       ┌──────────┼──────────┐
       ↓          ↓          ↓
      RAM       PCIe        USB
                  │
            ┌─────┼─────┐
            ↓     ↓     ↓
          GPU    NIC   NVMe
```

---

# 35. VISÃO COMPLETA

Agora podemos conectar tudo que estudamos:

```text
                    COMPUTADOR
                        │
              ┌─────────┴─────────┐
              ↓                   ↓
             CPU                  RAM
              │
      ┌───────┼────────┐
      ↓       ↓        ↓
     CU      ALU    REGISTRADORES
              │
             CACHE
              │
              ↓
       EXECUÇÃO DE INSTRUÇÕES
              │
              ↓
            KERNEL
              │
       ┌──────┼───────┐
       ↓      ↓       ↓
    PROCESSOS THREAD  DRIVERS
                       │
                       ↓
                    HARDWARE
```

---

# 36. O QUE ACONTECE QUANDO VOCÊ ABRE UM PROGRAMA?

Vamos imaginar que você execute:

```bash
firefox
```

De forma simplificada:

```text
Você executa o comando
        ↓
Shell solicita ao Kernel
        ↓
Kernel cria/inicia um processo
        ↓
Programa é carregado na memória
        ↓
CPU começa a executar suas instruções
        ↓
CPU busca instruções e dados
        ↓
Cache/registradores são utilizados
        ↓
CPU executa as operações
        ↓
Programa continua funcionando
```

Se o programa precisar acessar um dispositivo:

```text
Programa
   ↓
System Call
   ↓
Kernel
   ↓
Driver
   ↓
Hardware
```

---

# 37. A IDEIA MAIS IMPORTANTE

Não pense na CPU como:

> "uma coisa que faz tudo".

Pense nela como:

> **a máquina que executa as instruções.**

O restante do sistema fornece o ambiente para que essas instruções possam ser executadas.

```text
PROGRAMA
   ↓
INSTRUÇÕES + DADOS
   ↓
KERNEL ORGANIZA OS RECURSOS
   ↓
CPU EXECUTA AS INSTRUÇÕES
   ↓
HARDWARE É UTILIZADO
   ↓
RESULTADO
```

---

# 38. RESUMO FINAL

```text
CPU
│
├── Executa instruções
│
├── Possui núcleos
│
├── Possui registradores
│
├── Possui cache
│
├── Trabalha com clock
│
└── Executa código do usuário e do Kernel


ARQUITETURA
│
├── Define características da máquina
│
├── Define a ISA
│
├── Define instruções disponíveis
│
├── Pode ser 32 ou 64 bits
│
├── x86 / x86-64
│
└── ARM


PROCESSAMENTO
│
├── Busca
├── Decodifica
└── Executa


SISTEMA OPERACIONAL
│
├── Gerencia processos
├── Gerencia threads
├── Escalona CPU
├── Gerencia memória
├── Gerencia dispositivos
└── Utiliza drivers
```

---

# 🧠 MAPA MENTAL

```text
                         CPU
                          │
             ┌────────────┼────────────┐
             ↓            ↓            ↓
            CU           ALU      REGISTRADORES
             │                         │
             └──────────┬──────────────┘
                        ↓
                      CACHE
                        ↓
                  INSTRUÇÕES
                        │
             ┌──────────┼──────────┐
             ↓          ↓          ↓
           FETCH      DECODE     EXECUTE
                        │
                        ↓
                    PROCESSAMENTO
                        │
                        ↓
                     KERNEL
                        │
             ┌──────────┼──────────┐
             ↓          ↓          ↓
         PROCESSOS    THREADS    DRIVERS
                                   │
                                   ↓
                                HARDWARE


ARQUITETURA
     │
     ├── ISA
     ├── 32 bits
     ├── 64 bits
     ├── x86
     ├── x86-64 / AMD64
     ├── ARM
     ├── CISC
     └── RISC
```

---

# 🎯 FRASE PARA MEMORIZAR

> **A arquitetura define as regras e instruções que a CPU entende; a CPU executa essas instruções usando seus núcleos, registradores, cache e unidades de execução, enquanto o Kernel gerencia os recursos necessários para que os programas funcionem.**

---

# 🔗 CONEXÃO COM O PRÓXIMO ESTUDO

Agora temos:

```text
PARTE 1
CPU + ARQUITETURA
        ↓
entendemos quem executa as instruções

PARTE 2
BIOS + UEFI
        ↓
entendemos quem inicia o computador

PARTE 3
BOOT DO LINUX
        ↓
entendemos como o Linux começa a ser carregado

PARTE 4
KERNEL
        ↓
vamos entender profundamente quem assume
o controle do hardware e dos recursos do sistema
```

