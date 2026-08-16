# Capítulo 8 — Arquitetura de computador: software

## 1. Infraestrutura

Um sistema de computação é formado por **hardware e software**.

* **Hardware:** parte física do computador, como CPU, memória, monitor, impressora, cabos e discos.
* **Software:** conjunto de programas que orienta o hardware sobre o que deve fazer.

O software funciona como uma camada de abstração entre o usuário e o hardware. Assim, o usuário consegue realizar tarefas como salvar arquivos, acessar a internet ou utilizar dispositivos sem precisar conhecer detalhes de eletrônica ou programação.

A organização básica de um computador pode ser entendida pela seguinte hierarquia:

**Aplicativos → Utilitários → Sistema Operacional → Hardware**

O **sistema operacional (SO)** é o principal software do computador. Ele gerencia os recursos de hardware e fornece serviços para que outros programas possam funcionar.

Exemplos de sistemas operacionais:

* Windows;
* Linux;
* FreeBSD;
* OS X.

### Interface com o usuário

O usuário pode interagir com o sistema operacional principalmente de duas formas:

* **Shell:** interface baseada em comandos de texto.
* **GUI (Graphical User Interface):** interface gráfica baseada em elementos como janelas, menus e ícones.

### Modo usuário e modo núcleo

Os computadores normalmente trabalham com dois modos principais:

* **Modo usuário:** utilizado pelos programas comuns. Possui acesso limitado aos recursos do hardware.
* **Modo núcleo (kernel/supervisor):** utilizado pelo sistema operacional. Possui acesso privilegiado ao hardware e pode executar operações que não são permitidas aos programas comuns.

Essa separação aumenta a segurança e evita que um programa comum execute operações que possam danificar ou comprometer o sistema.

O **shell ou GUI** funciona como uma interface entre o usuário e os programas. Por meio dele, o usuário pode iniciar aplicações como navegador, editor de texto ou player de vídeo.

### Objetivos do sistema operacional

Os principais objetivos do SO são:

1. Esconder do usuário os detalhes do hardware.
2. Oferecer uma interface mais simples para utilização do computador.
3. Gerenciar memória, processamento e armazenamento.
4. Controlar os dispositivos de entrada e saída.
5. Organizar o uso dos recursos entre os diversos programas.

Podemos observar o SO por duas perspectivas:

* **Bottom-up:** o SO controla e distribui os recursos físicos entre os programas.
* **Top-down:** o SO fornece abstrações e serviços que facilitam o desenvolvimento e a execução dos aplicativos.

### Multiplexação de recursos

O sistema operacional precisa compartilhar recursos entre diferentes programas e usuários. Esse compartilhamento pode ocorrer de duas formas:

#### Multiplexação no tempo

Os programas utilizam um recurso **em revezamento**.

Exemplo: uma CPU executa um programa por determinado período, depois passa para outro e posteriormente retorna ao primeiro.

Também ocorre com impressoras: vários documentos podem ser enviados e aguardam em uma fila para serem impressos.

#### Multiplexação no espaço

O recurso é **dividido entre vários programas ou usuários simultaneamente**.

Exemplo: vários programas podem ocupar diferentes partes da memória RAM ao mesmo tempo.

O disco também pode ser compartilhado dessa maneira, com diferentes usuários utilizando diferentes áreas de armazenamento.

---

## 2. Tipos de sistemas operacionais

Existem diferentes tipos de sistemas operacionais, desenvolvidos de acordo com as características e necessidades do equipamento.

### 2.1 Sistemas operacionais de computadores de grande porte

São utilizados em computadores com grande capacidade de processamento, armazenamento e entrada/saída.

São comuns em:

* grandes servidores;
* comércio eletrônico;
* transações entre empresas;
* sistemas que processam enormes quantidades de dados.

Podem oferecer:

* **Processamento em lote (batch):** executa tarefas sem interação direta do usuário.
* **Processamento de transações:** processa grande quantidade de pequenas operações.
* **Tempo compartilhado (timesharing):** permite que vários usuários utilizem o computador simultaneamente.

### 2.2 Sistemas operacionais de servidores

Servidores atendem diversos usuários por meio de uma rede e fornecem recursos e serviços.

Podem oferecer:

* impressão;
* armazenamento e compartilhamento de arquivos;
* serviços web;
* suporte a clientes conectados à internet.

Exemplos:

* Linux;
* FreeBSD;
* Solaris;
* Windows Server.

### 2.3 Sistemas operacionais de multiprocessadores

São utilizados em computadores que possuem múltiplas CPUs ou processadores.

A utilização de vários processadores permite aumentar a capacidade computacional.

Esses sistemas precisam lidar com aspectos como:

* comunicação;
* conectividade;
* compartilhamento;
* consistência dos dados.

Linux e Windows, por exemplo, possuem suporte a sistemas multiprocessadores.

### 2.4 Sistemas operacionais de computadores portáteis

São utilizados em dispositivos como smartphones e tablets.

Exemplos:

* Android;
* iOS.

Esses equipamentos normalmente possuem:

* CPUs multinúcleo;
* GPS;
* câmeras;
* sensores;
* grande quantidade de memória;
* aplicativos instaláveis.

### 2.5 Sistemas operacionais embarcados

São sistemas desenvolvidos para equipamentos específicos que nem sempre são percebidos como computadores.

Exemplos:

* televisores;
* micro-ondas;
* automóveis;
* telefones tradicionais;
* aparelhos de reprodução de mídia.

Normalmente, o usuário não instala novos aplicativos. Os softwares necessários são definidos pelo fabricante e ficam armazenados no próprio dispositivo.

Exemplos de sistemas embarcados:

* Embedded Linux;
* QNX;
* VxWorks.

### 2.6 Sistemas operacionais de tempo real

Em sistemas de tempo real, o momento em que uma tarefa é executada é fundamental.

São utilizados em situações nas quais determinadas ações precisam ocorrer dentro de um intervalo de tempo específico.

Exemplos:

* controle industrial;
* robôs de linhas de produção;
* sistemas automotivos;
* sistemas multimídia.

Existem dois tipos principais:

**Tempo real crítico:** a tarefa precisa ocorrer obrigatoriamente no momento determinado. Um atraso pode causar danos graves.

**Tempo real não crítico:** pequenos atrasos podem ser aceitáveis e não provocam consequências permanentes.

Em sistemas embarcados e de tempo real, geralmente o software é instalado pelos projetistas e o usuário possui pouco ou nenhum controle sobre sua instalação.

Um exemplo é o **eCos**, um sistema gratuito e open-source voltado para aplicações embarcadas com requisitos de tempo real e pouca memória.

---

## 3. Processos

Um **processo** é, basicamente, um **programa em execução**.

Ele contém todas as informações necessárias para que o programa seja executado, incluindo:

* espaço de endereçamento;
* programa executável;
* dados;
* pilha;
* registradores;
* arquivos abertos;
* informações necessárias para continuar a execução.

O processo utiliza um espaço de endereçamento no qual pode ler e escrever dados.

### Criação de processos

Um processo pode ser criado por diferentes situações:

1. Inicialização do sistema.
2. Chamada de sistema feita por outro processo.
3. Solicitação do usuário.
4. Início de uma tarefa em lote.

### Finalização de processos

Um processo pode terminar por:

* saída normal e voluntária;
* erro fatal involuntário;
* saída voluntária devido a erro;
* encerramento provocado por outro processo.

### Estados de um processo

Um processo pode estar em três estados principais:

**Em execução:** está utilizando a CPU naquele momento.

**Pronto:** está preparado para executar, aguardando receber tempo de CPU.

**Bloqueado:** não pode continuar até que algum evento externo aconteça.

O processo pode mudar de estado conforme os acontecimentos e as decisões do sistema operacional.

### Tabela de processos

O sistema operacional mantém informações sobre os processos em uma estrutura chamada **tabela de processos**.

Ela armazena informações necessárias para controlar e posteriormente retomar os processos, incluindo dados relacionados aos registradores e ao estado de execução.

### Processos filhos

Um processo pode criar outros processos, chamados de **processos filhos**.

Esses processos filhos também podem criar novos processos, formando uma **árvore de processos**.

Essa estrutura permite visualizar a relação entre processos pais e seus respectivos processos filhos.

### Escalonador de processos

O **escalonador** é responsável por decidir qual processo receberá tempo de processamento da CPU.

Ele utiliza algoritmos de escalonamento para definir qual processo deve ser executado e em qual ordem.

Isso permite que vários programas aparentem executar simultaneamente, mesmo quando existe apenas uma CPU disponível.

---

## 4. Threads

Uma **thread**, ou linha de controle, é uma unidade de execução dentro de um processo.

Threads são mais leves que processos e, por isso, normalmente são mais rápidas para criar e destruir.

A principal diferença entre processos e threads está no uso da memória:

* **Processos:** possuem espaços de memória independentes e protegidos.
* **Threads:** compartilham o mesmo espaço de endereçamento do processo.

O compartilhamento de memória permite que várias threads trabalhem juntas de maneira eficiente.

### Exemplo de uso

Um navegador pode precisar carregar simultaneamente:

* imagens;
* vídeos;
* textos;
* outros recursos de uma página.

Com várias threads, o navegador pode realizar várias requisições praticamente ao mesmo tempo, aumentando a capacidade de resposta e o desempenho.

### Multithreading

Um processo **multithread** possui várias threads.

Em uma CPU única, as threads se alternam na execução. Em sistemas com múltiplos processadores ou núcleos, diferentes threads podem ser executadas simultaneamente.

A principal vantagem é permitir que diferentes tarefas de um mesmo processo sejam realizadas de forma concorrente, compartilhando os mesmos dados e espaço de memória.

---

## 5. Aplicativos e utilitários

Os **aplicativos** são programas desenvolvidos para realizar tarefas úteis diretamente para o usuário.

Exemplos:

* editores de texto;
* planilhas;
* navegadores;
* players de mídia.

Os **utilitários** são programas que não são obrigatórios para o funcionamento básico do computador, mas auxiliam o sistema e o usuário em tarefas específicas.

Exemplos:

* compactadores de arquivos;
* antivírus;
* desfragmentadores;
* ferramentas de backup;
* ferramentas de sincronização;
* ferramentas de configuração do sistema.

É importante diferenciar o sistema operacional desses programas. O SO é responsável por fornecer os serviços fundamentais e executar as chamadas de sistema. Aplicativos, compiladores, editores, montadores, linkers, utilitários e interpretadores de comandos não são considerados parte do sistema operacional, mesmo sendo importantes para o funcionamento e utilização do computador.

---

## Considerações finais

A arquitetura de computador também pode ser analisada pela perspectiva do **software**, especialmente pelo funcionamento do sistema operacional.

O sistema operacional atua como intermediário entre o hardware e os programas, oferecendo abstrações e gerenciando recursos como CPU, memória, armazenamento e dispositivos de entrada e saída.

Também existem diferentes tipos de sistemas operacionais, cada um adaptado a determinadas necessidades, como servidores, computadores de grande porte, dispositivos móveis, sistemas embarcados e sistemas de tempo real.

Os **processos** representam programas em execução e são controlados pelo sistema operacional por meio de estados, tabelas e mecanismos de escalonamento. As **threads** permitem dividir um processo em diferentes linhas de execução, possibilitando maior eficiência e concorrência.

Por fim, **aplicativos** atendem diretamente às necessidades dos usuários, enquanto **utilitários** auxiliam na administração, manutenção e funcionamento do sistema.

📌 **Observação:** Este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo foi reorganizado e escrito em linguagem simples para facilitar a compreensão e a revisão. Não substitui o material oficial da disciplina.

