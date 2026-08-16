# Arquitetura de Computador – Hardware

## 1. Visão geral do hardware

O **hardware** corresponde à parte física do computador, formada pelos componentes responsáveis por processar, armazenar e transportar dados. Mesmo realizando operações muito rapidamente, o computador precisa receber instruções detalhadas para saber exatamente o que deve fazer.

Um computador moderno realiza operações **aritméticas, lógicas, manipulação de dados e tomada de decisões**, normalmente trabalhando com informações representadas em formato binário. Suas operações são executadas de acordo com uma sequência de instruções, permitindo resolver problemas de maneira rápida e precisa.

A arquitetura do computador pode ser entendida de forma modular, principalmente por meio de quatro elementos:

* **CPU:** processa instruções e dados.
* **Memória:** armazena dados e instruções.
* **Módulo de entrada/saída (E/S ou I/O):** permite a comunicação com dispositivos externos.
* **Barramentos:** transportam dados, endereços e sinais entre os componentes.

---

## 2. CPU – Unidade Central de Processamento

A **CPU (Central Processing Unit)**, também chamada de processador, é responsável pelo processamento das instruções e pelo controle das operações do computador. Ela fica instalada na placa-mãe e pode, dependendo do equipamento, ser substituída.

O processador pode ser dividido principalmente em três partes:

### ULA – Unidade Lógica e Aritmética

A **ULA**, também conhecida como **ALU**, executa operações matemáticas e lógicas.

Entre suas operações estão:

* adição;
* subtração;
* operações booleanas;
* AND;
* OR;
* XOR;
* NOT.

### UC – Unidade de Controle

A **Unidade de Controle** coordena a execução das instruções. Ela busca as instruções na memória, interpreta o que precisa ser feito e envia sinais de controle para os demais componentes.

### Registradores

Os **registradores** são pequenas áreas de armazenamento localizadas dentro do processador. São utilizados para guardar temporariamente dados e informações importantes durante a execução das instruções.

Podem ser classificados, de forma geral, em:

* **registradores de propósito geral:** utilizados para armazenar dados;
* **registradores específicos:** armazenam informações necessárias para determinadas operações e são normalmente controlados pela UC.

### Funcionamento geral da CPU

A CPU trabalha em conjunto com outras unidades do computador. A **Unidade de Controle** busca e interpreta as instruções, enquanto a **ULA** executa cálculos e operações lógicas. Os **registradores** mantêm temporariamente os dados necessários para essas operações.

---

## 3. Principais unidades de um computador

Além da CPU, um computador digital pode ser compreendido por meio de cinco unidades principais:

### Unidade de entrada

Recebe dados e instruções do ambiente externo e os encaminha para a memória, onde poderão permanecer armazenados até serem utilizados.

### Unidade de memória

Armazena:

* instruções;
* dados recebidos;
* resultados de operações;
* informações que serão posteriormente encaminhadas para a saída.

### Unidade de controle

Busca as instruções armazenadas na memória, interpreta essas instruções e envia sinais para as demais unidades determinando o que deve ser realizado.

### Unidade lógica e aritmética

Executa os cálculos matemáticos e as operações lógicas solicitadas pelas instruções.

### Unidade de saída

Recebe informações processadas e apresenta os resultados de maneira que possam ser utilizados pelo usuário ou por outros sistemas.

---

## 4. Memória

A **memória** permite que um sistema digital retenha informações mesmo depois que o sinal responsável por alterá-las tenha sido removido. Essa capacidade de manter um estado é o que diferencia um circuito com memória de um circuito sem memória.

Os sistemas digitais podem utilizar memória para armazenar informações temporariamente ou permanentemente.

As memórias podem utilizar diferentes tecnologias, incluindo mecanismos magnéticos, ópticos e circuitos eletrônicos de retenção, como **latches e flip-flops**.

### Hierarquia de memória

Os computadores utilizam uma **hierarquia de memórias**, organizada de acordo com fatores como velocidade, capacidade, custo e proximidade do processador.

De forma geral, a hierarquia segue:

1. **Registradores**
2. **Memória cache**
3. **Memória principal (RAM)**
4. **Armazenamento externo**, como discos
5. **Mídias removíveis**

Quanto mais próxima do processador, normalmente a memória é mais rápida, porém apresenta menor capacidade e maior custo por unidade de armazenamento.

### Memória interna e externa

As **memórias internas** podem ser acessadas diretamente pelo processador. Entre elas estão os registradores, a cache e a memória principal.

As **memórias externas** correspondem aos dispositivos de armazenamento periféricos, que são acessados por meio dos mecanismos de entrada e saída.

---

## 5. Capacidade e unidades da memória

A capacidade da memória pode ser expressa em **bits, bytes ou palavras**.

* **1 byte = 8 bits**
* Uma palavra pode possuir diferentes tamanhos, dependendo da arquitetura.
* Exemplos de tamanhos de palavra incluem 8, 16 e 32 bits.

Existem três conceitos importantes relacionados à memória:

### Palavra

Representa uma quantidade de bits normalmente relacionada ao tamanho utilizado pelo processador para representar dados ou instruções. O tamanho da palavra depende da arquitetura.

### Unidade endereçável

É a menor unidade da memória que pode ser identificada individualmente por um endereço. Em muitos sistemas, o endereçamento ocorre no nível de **bytes**.

### Unidade de transferência

Representa a quantidade de bits transferida de uma vez entre a memória e os demais componentes.

Em memórias externas, os dados geralmente são transferidos em **blocos**, que podem ser maiores que uma palavra.

---

## 6. Classificação das memórias

### Memórias voláteis

Perdem seus dados quando a alimentação elétrica é interrompida.

Exemplos:

* registradores;
* memória cache;
* memória RAM.

### Memórias não voláteis

Mantêm as informações mesmo quando o computador é desligado.

Exemplos:

* memória flash;
* HD;
* outros dispositivos de armazenamento.

### Memória principal

A **memória principal**, normalmente representada pela **RAM**, mantém os dados e instruções que precisam estar disponíveis para o processador durante a execução dos programas.

### Memória secundária

É utilizada para armazenar grandes quantidades de dados de forma permanente. Normalmente é não volátil.

Exemplos:

* HD;
* discos ópticos;
* CDs;
* DVDs;
* Blu-rays;
* fitas magnéticas;
* outros dispositivos de armazenamento.

Para que os dados armazenados na memória secundária sejam processados pela CPU, eles normalmente precisam ser carregados na memória principal.

---

## 7. Módulo de entrada/saída – E/S ou I/O

O **módulo de entrada/saída**, também chamado de **I/O (Input/Output)**, funciona como uma interface entre o computador e os dispositivos externos.

Ele permite controlar a comunicação entre:

* CPU;
* memória principal;
* dispositivos externos.

O módulo de E/S gerencia a transferência de dados entre os dispositivos e a memória ou os registradores da CPU.

### Tipos principais de E/S

#### E/S programada

O programa controla diretamente e continuamente as operações de entrada e saída.

#### E/S controlada por interrupção

O programa inicia uma operação de E/S e continua sua execução. Quando a operação termina, o hardware gera uma **interrupção**, avisando o processador.

#### DMA – Acesso Direto à Memória

No **DMA (Direct Memory Access)**, um controlador especializado pode movimentar grandes quantidades de dados diretamente entre um dispositivo e a memória, reduzindo a necessidade de participação contínua da CPU.

### Funções do módulo de E/S

Entre suas principais funções estão:

* comunicação com a CPU;
* controle e temporização;
* comunicação com dispositivos;
* transferência e temporização dos dados;
* detecção de erros.

---

## 8. Barramentos

O **barramento** é um meio de comunicação utilizado para conectar os principais componentes do computador, permitindo a transferência de dados, endereços e sinais de controle.

A **placa-mãe** reúne componentes como CPU, memória, chips de suporte e conexões para dispositivos. Os barramentos permitem que esses componentes se comuniquem.

Um computador pode possuir vários barramentos, dependendo de sua arquitetura.

### Controladores

Os dispositivos de entrada e saída normalmente possuem um **controlador**, responsável por controlar o dispositivo e permitir sua comunicação com o barramento.

Por exemplo, quando um programa precisa acessar informações armazenadas em um disco, envia uma solicitação ao controlador do disco. O controlador coordena o acesso ao dispositivo e realiza a transferência dos dados.

### DMA e controladores

Um controlador pode acessar diretamente a memória sem depender continuamente da CPU. Esse processo é chamado de **DMA**.

Depois que a transferência termina, o controlador pode gerar uma **interrupção**. A CPU interrompe temporariamente o programa em execução, executa uma rotina específica para tratar a interrupção e, depois, retorna ao programa que estava sendo executado.

### Árbitro de barramento

Quando diferentes componentes precisam utilizar o barramento simultaneamente, é necessário controlar quem terá acesso naquele momento.

O **árbitro de barramento** é responsável por organizar e distribuir o acesso ao barramento, evitando conflitos entre os dispositivos.

---

## 9. PCI e PCI Express

O **PCI (Peripheral Component Interconnect)** foi desenvolvido para permitir a comunicação entre componentes periféricos e o restante do computador.

Com a evolução dos computadores, surgiram arquiteturas com múltiplos barramentos e tecnologias mais rápidas.

O **PCI Express (PCIe)** utiliza comunicação serial e pode trabalhar com várias **lanes**, ou pistas de comunicação.

Uma conexão PCIe pode utilizar diferentes quantidades de lanes, permitindo aumentar a largura de banda conforme a necessidade do dispositivo.

Placas gráficas, por exemplo, podem utilizar conexões com várias lanes para obter uma largura de banda elevada.

---

## 10. Visão integrada do funcionamento

O funcionamento do computador depende da interação entre seus componentes.

De maneira simplificada:

1. **A unidade de entrada** recebe dados e instruções.
2. **A memória** armazena essas informações.
3. **A CPU** busca e interpreta as instruções.
4. **A UC** coordena a execução.
5. **A ULA** realiza cálculos e operações lógicas.
6. **Os registradores** armazenam temporariamente dados necessários ao processamento.
7. **Os barramentos** transportam informações entre os componentes.
8. **O módulo de E/S** permite a comunicação com dispositivos externos.
9. **A unidade de saída** apresenta os resultados.

Assim, o computador pode ser visto como um conjunto de módulos interligados, em que cada componente possui uma função específica, mas todos trabalham de maneira integrada.

## Resumo geral

A arquitetura de hardware pode ser entendida a partir de quatro elementos principais: **CPU, memória, entrada/saída e barramentos**. A CPU processa instruções por meio da UC, ULA e registradores. A memória armazena dados e instruções em diferentes níveis de velocidade e capacidade. O módulo de E/S faz a comunicação com dispositivos externos, utilizando mecanismos como E/S programada, interrupções e DMA. Já os barramentos permitem a comunicação entre os componentes, enquanto controladores e árbitros organizam o acesso aos dispositivos e aos meios de comunicação.

📌 **Observação:** Este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo foi reorganizado e escrito em linguagem simples para facilitar a compreensão e a revisão. Não substitui o material oficial da disciplina.

