# LPIC-1 - Módulo 01

## 1. CPU e Arquitetura

### 1.1 CPU

**CPU — Central Processing Unit**
**Tradução:** Unidade Central de Processamento.
Também conhecida como **processador**.

A CPU é o componente físico responsável por **executar as instruções dos programas**.

Podemos pensar de forma simples:

```text
Programa
   ↓
Sistema Operacional (OS - Operating System)
   ↓
Instruções
   ↓
CPU
   ↓
Executa as instruções
```

A CPU não "entende" diretamente programas como nós os vemos. Ela recebe **instruções em um formato definido pela arquitetura do processador** e executa essas instruções.

---

### 1.2 Arquitetura (Architecture)

A **arquitetura do processador** é o conjunto de regras que define **como a CPU representa, interpreta e executa instruções e trabalha com os dados**.

Podemos imaginar a arquitetura como uma espécie de **"linguagem" ou conjunto de regras que a CPU conhece**.

Ela define, entre outras coisas:

* quais instruções a CPU consegue executar;
* quais registradores existem;
* como os dados são representados;
* como a memória é endereçada;
* o tamanho dos dados que podem ser trabalhados;
* como os componentes internos da CPU são organizados.

```text
ARQUITETURA
     ↓
Define como a CPU entende e trabalha com os dados
     ↓
┌─────────────────────────────┐
│ Instruções                  │
│ Registradores               │
│ Tamanho dos dados           │
│ Endereçamento de memória    │
│ Organização da CPU          │
└─────────────────────────────┘
```

> **Importante:** arquitetura não é simplesmente o "desenho físico" do processador. Ela define principalmente as **regras e características que determinam como o processador funciona do ponto de vista lógico**.

---

### 1.3 Elementos relacionados ao funcionamento da CPU

#### Instruções

São comandos que dizem à CPU **qual operação deve ser realizada**.

Exemplos de operações:

* realizar cálculos;
* comparar valores;
* mover dados;
* acessar a memória;
* realizar operações lógicas;
* alterar o fluxo de execução de um programa.

---

#### Registradores (Registers)

São **pequenas áreas de armazenamento extremamente rápidas dentro da CPU**.

São utilizadas para guardar temporariamente:

* valores;
* endereços;
* resultados de operações;
* informações necessárias para a execução das instruções.

```text
CPU
┌─────────────────────────────┐
│ Registradores               │ ← extremamente rápidos
│ Unidade de controle         │
│ Unidades de execução        │
│ Cache                       │
└─────────────────────────────┘
```

---

#### Memória RAM

A **RAM — Random Access Memory** (Memória de Acesso Aleatório) é a memória principal utilizada para armazenar **temporariamente os programas e dados que estão sendo utilizados pelo sistema**.

Exemplo:

```text
Programa armazenado no disco
          ↓
       Carregado
          ↓
         RAM
          ↓
         CPU
          ↓
     Processamento
```

A RAM é diferente dos registradores porque fica **fora da CPU**, embora seja diretamente utilizada durante o processamento.

---

#### Cache

A **cache** é uma memória extremamente rápida utilizada para armazenar dados e instruções que podem ser necessários novamente pela CPU.

Seu objetivo é **reduzir o tempo necessário para acessar informações**, evitando que a CPU precise buscar tudo diretamente na RAM.

```text
CPU
 ↓
Cache
 ↓
RAM
 ↓
Armazenamento
```

Quanto mais próximo da CPU, normalmente **mais rápido e menor** é o armazenamento.

---

#### Núcleos (Cores)

Um **núcleo (core)** é uma unidade de processamento dentro da CPU capaz de executar instruções.

Uma CPU pode possuir vários núcleos.

Exemplo:

```text
CPU
├── Núcleo 1
├── Núcleo 2
├── Núcleo 3
└── Núcleo 4
```

Uma CPU com quatro núcleos possui **quatro unidades de processamento**, permitindo executar várias tarefas simultaneamente ou em paralelo, dependendo do sistema e dos programas.

---

## 1.4 Tipos de Arquitetura

Existem diferentes arquiteturas de processadores. Cada uma possui seu próprio conjunto de regras e instruções.

As duas famílias que aparecem com frequência no estudo de Linux são:

* **x86 / x86-64**
* **ARM / AArch64**

---

### 1.4.1 Arquitetura x86

A **x86** é uma família de arquiteturas de processadores que evoluiu ao longo do tempo.

De forma simplificada:

```text
x86
 │
 ├── 16 bits
 │
 ├── 32 bits → IA-32 / i386
 │
 └── 64 bits → x86-64 / AMD64
```

#### i386 / i686

São referências à família **x86 de 32 bits**.

* **i386** → representa a arquitetura x86 de 32 bits.
* **i686** → representa uma evolução dentro da família x86 de 32 bits.

No Linux, esses nomes também aparecem para identificar arquiteturas ou plataformas compatíveis.

---

### 1.4.2 x86-64 / AMD64

**x86-64** é a extensão de 64 bits da arquitetura x86.

Ela também é conhecida como:

* **AMD64**
* **x86_64**

A AMD foi responsável por desenvolver a extensão da arquitetura x86 de 32 bits para 64 bits.

```text
x86
 │
 ├── 16 bits
 │
 ├── 32 bits → IA-32 / i386
 │
 └── 64 bits → x86-64 / AMD64
```

**AMD — Advanced Micro Devices**
Tradução aproximada: **Dispositivos Micro Avançados**.

> **Importante:** AMD64 não significa que a arquitetura funciona apenas em processadores AMD. Processadores Intel também podem utilizar a arquitetura **x86-64**.

---

### 1.4.3 Arquitetura ARM

**ARM** é uma família de arquiteturas baseada na filosofia **RISC**.

**RISC — Reduced Instruction Set Computer**
**Tradução:** Computador com Conjunto Reduzido de Instruções.

A ideia é utilizar um conjunto de instruções mais simples e eficiente.

Isso favorece projetos que buscam:

* eficiência;
* menor consumo de energia;
* menor geração de calor;
* simplicidade no projeto do processador.

ARM é muito utilizada em:

* smartphones;
* tablets;
* dispositivos embarcados;
* equipamentos de rede;
* servidores;
* computadores modernos.

---

### 1.4.4 ARM32 e AArch64

De forma simplificada:

```text
ARM
 │
 ├── ARM32 → 32 bits
 │
 └── AArch64 → 64 bits
```

**AArch64** é o conjunto de execução de 64 bits da arquitetura ARM.

Em sistemas Linux, também é comum encontrar referências como:

* `arm` → ARM de 32 bits;
* `aarch64` → ARM de 64 bits.

---

## 1.5 O que significa 32 bits e 64 bits?

Quando falamos que um processador é de **32 ou 64 bits**, estamos falando de características relacionadas à quantidade de bits que sua arquitetura consegue manipular e, principalmente, ao seu modelo de endereçamento e aos registradores.

De forma simplificada:

```text
32 bits → trabalha com valores de até 32 bits em determinadas operações
64 bits → trabalha com valores de até 64 bits em determinadas operações
```

Um processador de 64 bits também pode executar sistemas e programas de 32 bits quando existe compatibilidade.

> **Importante:** 64 bits não significa simplesmente "duas vezes mais rápido" que 32 bits. Ele permite, entre outras coisas, trabalhar com endereços de memória muito maiores e com valores de 64 bits em determinadas operações.

---

## 1.6 Como tudo se relaciona?

Uma forma simples de visualizar o funcionamento é:

```text
Programa
   ↓
Sistema Operacional
   ↓
Instruções
   ↓
Arquitetura
   ↓
CPU interpreta as instruções
   ↓
CPU executa as operações
   ↓
Registradores / Cache / RAM
```

A arquitetura funciona como o **conjunto de regras que define como a CPU deve interpretar e executar as instruções**.

Por exemplo:

```text
Programa
   ↓
"Instrução"
   ↓
Arquitetura x86-64
   ↓
CPU entende a instrução
   ↓
CPU executa
```

---

## 1.7 Bits → Instrução → Arquitetura → CPU

Podemos representar de forma simplificada:

```text
Bits
 ↓
010101...
 ↓
Instrução codificada
 ↓
Arquitetura interpreta
 ↓
CPU executa
```

Os bits são a forma básica de representação das informações dentro do computador.

Entretanto, **não devemos pensar que qualquer sequência de bits representa uma instrução válida**. A arquitetura define como determinadas sequências de bits devem ser interpretadas.

---

## 1.8 Comparação entre x86-64 e ARM64

```text
x86
 └── x86-64 / AMD64
      └── 64 bits

ARM
 └── AArch64 / ARM64
      └── 64 bits
```

As duas podem ser arquiteturas de **64 bits**, mas possuem **conjuntos de instruções e regras diferentes**.

Por isso, um programa compilado especificamente para x86-64 normalmente não pode ser executado diretamente em ARM64 sem uma versão compatível, recompilação ou algum mecanismo de tradução/emulação.

---

## 1.9 Resumo

* **CPU** é o processador responsável por executar instruções.
* **Arquitetura** define as regras que determinam como a CPU interpreta e executa essas instruções.
* **Instruções** são operações que a CPU consegue executar.
* **Registradores** são pequenas áreas de armazenamento extremamente rápidas dentro da CPU.
* **Cache** é uma memória muito rápida utilizada para reduzir o tempo de acesso a dados e instruções.
* **RAM** armazena temporariamente programas e dados em uso.
* **Núcleos (cores)** são unidades de processamento dentro da CPU.
* **x86** é uma família de arquiteturas que evoluiu de 16 para 32 e posteriormente para 64 bits.
* **x86-64 / AMD64** é a versão de 64 bits da família x86.
* **ARM** é uma família de arquiteturas baseada na filosofia RISC.
* **AArch64 / ARM64** representa a arquitetura ARM de 64 bits.
* **32 e 64 bits** representam características da arquitetura relacionadas à manipulação de dados, registradores e principalmente ao endereçamento de memória.
* **AMD64 não significa que é exclusivo da AMD**: processadores Intel também utilizam x86-64.

### 📌 Ideia principal para memorizar

> **A arquitetura define as regras. A CPU segue essas regras para interpretar e executar as instruções dos programas.**

