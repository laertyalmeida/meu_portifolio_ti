# BIOS / UEFI — PARTE 1
## Fundamentos da inicialização do computador

---

# 1. O QUE É FIRMWARE?

Antes de entender BIOS e UEFI, precisamos entender o que é:

**FIRMWARE**

Firmware é um software especial que fica armazenado em um dispositivo eletrônico e tem a função de controlar e inicializar o hardware em um nível básico.

No computador, o firmware da placa-mãe é responsável por iniciar as primeiras etapas quando apertamos o botão POWER.

Podemos imaginar:

    HARDWARE
       ↑
       │
    FIRMWARE
       ↑
       │
    SISTEMA OPERACIONAL

O firmware fica entre o hardware e o sistema operacional durante as primeiras etapas da inicialização.

---

# 2. O QUE ACONTECE QUANDO APERTAMOS O POWER?

Quando você aperta o botão de ligar, o Linux ainda não está funcionando.

O computador precisa primeiro preparar o próprio hardware.

De forma simplificada:

    POWER
      ↓
    Energia chega aos componentes
      ↓
    CPU começa a executar instruções
      ↓
    Firmware entra em execução
      ↓
    Hardware é inicializado/verificado
      ↓
    Firmware procura algo para iniciar
      ↓
    Bootloader
      ↓
    Kernel Linux
      ↓
    Sistema operacional

Portanto:

**O Linux não é a primeira coisa que roda quando o computador liga.**

Existe todo um processo antes dele.

---

# 3. BIOS

BIOS significa:

**Basic Input/Output System**

É o firmware tradicional utilizado durante décadas nos computadores.

Sua função é realizar as primeiras tarefas necessárias para colocar o computador em condições de iniciar um sistema operacional.

Entre suas funções estão:

- inicializar componentes básicos;
- realizar o POST;
- detectar hardware;
- identificar dispositivos de armazenamento;
- determinar a ordem de boot;
- procurar um dispositivo inicializável;
- iniciar o processo do bootloader.

---

# 4. BIOS NÃO É O SISTEMA OPERACIONAL

Essa diferença é muito importante.

BIOS não é:

- Linux;
- Windows;
- Ubuntu;
- Debian.

BIOS é o **firmware da placa-mãe**.

Podemos representar:

    HARDWARE
       ↓
    BIOS
       ↓
    BOOTLOADER
       ↓
    SISTEMA OPERACIONAL

A BIOS prepara o computador para que o sistema operacional possa ser carregado.

---

# 5. UEFI

UEFI significa:

**Unified Extensible Firmware Interface**

É a interface de firmware moderna que substituiu o BIOS tradicional na maioria dos computadores atuais.

Muitas pessoas continuam chamando a tela de configuração de "BIOS", mesmo quando o computador utiliza UEFI.

Tecnicamente:

    BIOS = firmware tradicional

    UEFI = firmware/interface moderna

UEFI trouxe vários recursos e melhorias em relação ao modelo tradicional.

---

# 6. PRINCIPAIS CARACTERÍSTICAS DO UEFI

Entre suas características estão:

- suporte moderno a discos e particionamento;
- utilização de GPT;
- suporte à ESP;
- possibilidade de Secure Boot;
- armazenamento de entradas de boot;
- ambiente de firmware mais estruturado;
- possibilidade de executar aplicações EFI.

Uma característica importante é que o UEFI consegue localizar e executar arquivos EFI armazenados na partição ESP.

---

# 7. BIOS x UEFI

Uma forma simples de visualizar:

## BIOS tradicional

    BIOS
      ↓
    POST
      ↓
    Disco
      ↓
    MBR
      ↓
    Código de boot
      ↓
    Bootloader
      ↓
    Kernel

## UEFI

    UEFI
      ↓
    POST
      ↓
    Disco
      ↓
    GPT
      ↓
    ESP
      ↓
    Arquivo EFI
      ↓
    Bootloader
      ↓
    Kernel

Essa diferença é muito importante para o LPIC-1.

---

# 8. POST

POST significa:

**Power-On Self-Test**

É o teste realizado durante a inicialização do computador.

A ideia é verificar se os componentes básicos necessários para continuar a inicialização estão funcionando.

Exemplos:

- CPU;
- RAM;
- vídeo;
- teclado;
- controladores;
- dispositivos básicos.

Imagine o POST como uma inspeção:

    Computador ligado
          ↓
        POST
          ↓
    "A memória está funcionando?"
          ↓
    "A CPU está funcionando?"
          ↓
    "Consigo inicializar o vídeo?"
          ↓
    "Os componentes necessários estão disponíveis?"
          ↓
       Continua

Se houver um problema grave, o computador pode não conseguir continuar o boot.

---

# 9. O FIRMWARE DETECTA O HARDWARE

Depois das primeiras verificações, o firmware precisa identificar os dispositivos disponíveis.

Por exemplo:

    CPU
    RAM
    SSD
    HD
    USB
    placa de vídeo
    placa de rede
    teclado
    etc.

Isso é importante porque o firmware precisa saber de onde poderá iniciar o sistema.

---

# 10. ORDEM DE BOOT

O computador pode ter vários dispositivos capazes de iniciar um sistema.

Por exemplo:

    SSD
    HD
    Pendrive
    DVD
    Rede

Então existe uma configuração chamada:

**Boot Order**

ou:

**Ordem de Boot**

Exemplo:

    1º USB
    2º SSD
    3º HD
    4º Rede

O firmware tenta seguir essa ordem.

Imagine:

    USB
     ↓
    Não encontrou sistema inicializável
     ↓
    SSD
     ↓
    Encontrou
     ↓
    Continua o boot

---

# 11. DISPOSITIVO DE BOOT

Um dispositivo de boot é um dispositivo que contém aquilo que o computador precisa para iniciar um sistema.

Pode ser:

- SSD;
- HD;
- pendrive;
- DVD;
- rede.

Exemplo:

    Pendrive Linux
          ↓
    Arquivos de inicialização
          ↓
    Pode ser usado para iniciar o Linux

O firmware precisa encontrar uma estrutura de inicialização válida.

---

# 12. MBR

MBR significa:

**Master Boot Record**

É uma estrutura localizada no início de um dispositivo de armazenamento.

Em sistemas que utilizam o método tradicional de boot com BIOS, o MBR possui um papel importante na inicialização.

Uma representação simplificada:

    DISCO
    ┌───────────────────────┐
    │ MBR                   │
    ├───────────────────────┤
    │ Partição 1            │
    ├───────────────────────┤
    │ Partição 2            │
    ├───────────────────────┤
    │ Partição 3            │
    └───────────────────────┘

O MBR possui:

- código de inicialização;
- tabela de partições;
- assinatura do disco.

---

# 13. MBR E O BOOT

No modo BIOS tradicional, o processo pode ser entendido assim:

    BIOS
      ↓
    encontra disco de boot
      ↓
    lê o MBR
      ↓
    executa o código inicial
      ↓
    continua o carregamento do bootloader
      ↓
    GRUB
      ↓
    Kernel

Por isso, quando estudamos boot tradicional, encontramos frequentemente:

**BIOS + MBR**

---

# 14. LIMITAÇÃO DO MBR

O MBR é uma tecnologia antiga.

Entre suas principais limitações está o tamanho máximo tradicional de aproximadamente:

**2 TiB**

quando utilizado com setores de 512 bytes.

Também existe a limitação tradicional de:

**4 partições primárias**

Para contornar isso, pode-se utilizar:

- partições estendidas;
- partições lógicas.

Mas essa estrutura ficou limitada para as necessidades dos computadores modernos.

Por isso surgiu o GPT.

---

# 15. GPT

GPT significa:

**GUID Partition Table**

É um esquema moderno de particionamento.

Em vez de utilizar a estrutura tradicional do MBR como principal tabela de particionamento, o GPT utiliza uma estrutura mais moderna.

Exemplo:

    DISCO GPT
    ┌──────────────────────────────┐
    │ GPT                          │
    ├──────────────────────────────┤
    │ Partição 1                   │
    ├──────────────────────────────┤
    │ Partição 2                   │
    ├──────────────────────────────┤
    │ Partição 3                   │
    ├──────────────────────────────┤
    │ Partição 4                   │
    └──────────────────────────────┘

GPT permite trabalhar com discos muito maiores e com muito mais partições do que o modelo tradicional MBR.

---

# 16. UEFI + GPT

Uma combinação muito comum atualmente é:

**UEFI + GPT**

O processo pode ser representado assim:

    UEFI
      ↓
    identifica o disco
      ↓
    encontra a estrutura GPT
      ↓
    encontra a ESP
      ↓
    encontra o arquivo EFI
      ↓
    executa o bootloader
      ↓
    GRUB
      ↓
    Kernel

---

# 17. ESP

ESP significa:

**EFI System Partition**

É uma partição especial utilizada pelo UEFI para armazenar arquivos de inicialização.

Normalmente utiliza:

**FAT32**

Um disco Linux moderno pode ter algo parecido com:

    SSD
    ├── ESP
    ├── /
    └── swap

A ESP pode aparecer no Linux como:

    /boot/efi

Mas o ponto importante é:

**ESP é uma partição usada pelo firmware UEFI para armazenar arquivos EFI de inicialização.**

---

# 18. O QUE EXISTE DENTRO DA ESP?

Podemos encontrar arquivos relacionados aos bootloaders.

Por exemplo, em um sistema Linux:

    /boot/efi/
        EFI/
            debian/
                ...

Em uma instalação com Debian, por exemplo, podem existir arquivos EFI associados ao carregador de inicialização.

O UEFI consegue localizar esses arquivos e executá-los.

---

# 19. GRUB

GRUB significa:

**GRand Unified Bootloader**

É um bootloader muito utilizado em sistemas Linux.

O GRUB fica entre o firmware e o kernel.

Podemos representar:

    BIOS/UEFI
         ↓
       GRUB
         ↓
       Kernel
         ↓
      Linux

O GRUB não é o kernel.

Ele é o **carregador de inicialização**.

---

# 20. FUNÇÃO DO GRUB

O GRUB pode:

- apresentar um menu de boot;
- selecionar um sistema operacional;
- selecionar uma versão do kernel;
- carregar o kernel;
- carregar o initramfs;
- passar parâmetros para o kernel.

Por exemplo, se existirem vários kernels:

    GRUB
      ↓
    Debian
      ├── Linux 6.x
      ├── Linux 6.y
      └── Linux 6.z

O usuário pode selecionar qual será iniciado.

---

# 21. KERNEL

Depois do bootloader, chegamos ao:

**KERNEL**

O kernel é o núcleo do sistema operacional.

No Linux:

**Linux = kernel**

É ele que passa a assumir o controle do computador em um nível muito mais profundo.

O kernel gerencia:

- CPU;
- memória RAM;
- processos;
- dispositivos;
- drivers/módulos;
- sistemas de arquivos;
- comunicação entre programas e hardware.

---

# 22. FIRMWARE, GRUB E KERNEL

É muito importante não misturar as funções.

### Firmware

    BIOS / UEFI

Responsável pelas primeiras etapas de inicialização.

### Bootloader

    GRUB

Responsável por carregar o sistema operacional/kernel.

### Kernel

    Linux

Responsável por administrar os recursos do computador.

Podemos resumir:

    BIOS/UEFI
       ↓
    "Vou preparar o computador."
       ↓
    GRUB
       ↓
    "Vou carregar o Linux."
       ↓
    Kernel
       ↓
    "Agora eu assumo o controle."

---

# 23. SECURE BOOT

Secure Boot é um recurso associado ao UEFI.

Seu objetivo é ajudar a garantir que somente componentes de boot autorizados sejam executados.

A ideia simplificada:

    UEFI
      ↓
    verifica assinatura
      ↓
    componente autorizado?
       ↓
    SIM → executa
    NÃO → bloqueia

Isso ajuda a proteger a inicialização contra determinados tipos de código malicioso que tentariam executar antes do sistema operacional.

---

# 24. NVRAM

UEFI pode armazenar informações em uma memória não volátil chamada:

**NVRAM**

Essas informações podem incluir entradas de boot.

Por exemplo:

    NVRAM
      │
      ├── Debian
      ├── Windows Boot Manager
      └── USB

Assim, o firmware pode saber quais opções de boot existem e qual deve ser priorizada.

---

# 25. efibootmgr

No Linux, quando o sistema está sendo executado em UEFI, podemos usar:

    efibootmgr

para consultar e administrar entradas de boot UEFI.

Por exemplo:

    efibootmgr

pode mostrar entradas como:

    Boot0000* debian
    Boot0001* Windows Boot Manager

Isso representa entradas armazenadas no firmware.

---

# 26. COMO SABER SE O LINUX ESTÁ EM UEFI?

Podemos verificar:

    /sys/firmware/efi/

Se esse diretório existir, normalmente o Linux foi iniciado em modo UEFI.

Um comando simples:

    test -d /sys/firmware/efi && echo UEFI || echo BIOS

Resultado:

    UEFI

ou:

    BIOS

### Atenção

Isso indica o modo em que o Linux foi iniciado.

Não significa necessariamente que o computador seja incapaz de usar o outro modo.

Alguns computadores possuem modos de compatibilidade.

---

# 27. LEGACY / CSM

Alguns computadores possuem recursos de compatibilidade com o modo BIOS tradicional.

Um nome que pode aparecer é:

**CSM**

Compatibility Support Module.

Ele permite que determinados sistemas antigos sejam inicializados em um ambiente UEFI utilizando compatibilidade com o modelo tradicional.

Assim podemos encontrar:

    UEFI
      │
      ├── Boot UEFI
      │
      └── Legacy / CSM

Em computadores modernos, normalmente é preferível utilizar UEFI nativo quando o sistema foi instalado dessa forma.

---

# 28. BIOS/UEFI NÃO CARREGA O LINUX INTEIRO

Esse é um ponto muito importante.

Quando falamos:

> "A BIOS inicia o Linux."

Isso é uma simplificação.

O processo real envolve várias etapas.

Por exemplo:

    BIOS/UEFI
       ↓
    Bootloader
       ↓
    Kernel
       ↓
    initramfs
       ↓
    systemd
       ↓
    serviços
       ↓
    ambiente do usuário

Cada componente possui uma responsabilidade diferente.

---

# 29. VISÃO GERAL DO BOOT

Agora podemos visualizar o processo inteiro:

    ┌───────────────────────┐
    │      POWER ON         │
    └───────────┬───────────┘
                ↓
    ┌───────────────────────┐
    │     BIOS / UEFI       │
    └───────────┬───────────┘
                ↓
    ┌───────────────────────┐
    │         POST          │
    └───────────┬───────────┘
                ↓
    ┌───────────────────────┐
    │ Detecta o hardware    │
    └───────────┬───────────┘
                ↓
    ┌───────────────────────┐
    │   Ordem de Boot       │
    └───────────┬───────────┘
                ↓
          ┌─────┴─────┐
          │           │
        BIOS         UEFI
          │           │
         MBR         GPT
          │           │
          │          ESP
          │           │
          └─────┬─────┘
                ↓
    ┌───────────────────────┐
    │       BOOTLOADER      │
    │          GRUB         │
    └───────────┬───────────┘
                ↓
    ┌───────────────────────┐
    │        KERNEL         │
    │        Linux          │
    └───────────────────────┘

---

# 30. ANALOGIA DA CASA

Para memorizar, imagine que o computador é uma casa.

### Firmware

É como o responsável por abrir a casa.

    BIOS/UEFI
        ↓
    "Vamos preparar tudo."

### POST

É a inspeção:

    "Tem energia?"
    "Os equipamentos básicos estão funcionando?"

### Boot Order

É a decisão:

    "Qual porta/dispositivo devo usar?"

### MBR / ESP

São diferentes formas de encontrar as instruções necessárias para continuar a entrada.

### GRUB

É o responsável por dizer:

    "Qual sistema devo carregar?"

### Kernel

É quem assume a administração da casa.

    CPU
    RAM
    Dispositivos
    Processos
    Arquivos

Tudo passa a ser administrado pelo kernel.

---

# 31. O QUE VOCÊ PRECISA REALMENTE ENTENDER

Não tente decorar tudo de uma vez.

O principal é entender esta sequência:

    1. Computador recebe energia
              ↓
    2. CPU começa a executar instruções
              ↓
    3. BIOS/UEFI inicia
              ↓
    4. POST verifica componentes
              ↓
    5. Firmware identifica dispositivos
              ↓
    6. Firmware segue a ordem de boot
              ↓
    7. Encontra o mecanismo de inicialização
              ↓
    8. Bootloader é executado
              ↓
    9. Bootloader carrega o kernel
             ↓
   10. Kernel assume o controle

---

# 32. PONTOS IMPORTANTES PARA LPIC-1

## Firmware

Software de baixo nível responsável pela inicialização e controle inicial do hardware.

## BIOS

Firmware tradicional.

## UEFI

Firmware moderno que substituiu o BIOS tradicional.

## POST

Power-On Self-Test.

Verificação inicial do hardware.

## MBR

Master Boot Record.

Estrutura tradicional associada ao boot BIOS e ao particionamento MBR.

## GPT

GUID Partition Table.

Esquema moderno de particionamento.

## ESP

EFI System Partition.

Partição usada pelo UEFI para arquivos EFI de inicialização.

## GRUB

Bootloader muito utilizado no Linux.

## Kernel

Núcleo do Linux.

## Secure Boot

Recurso do UEFI que verifica componentes de inicialização assinados/autorizados.

## NVRAM

Área de memória não volátil usada pelo firmware para armazenar informações, incluindo entradas de boot.

---

# 33. FRASES PARA MEMORIZAR

**BIOS/UEFI não é o sistema operacional.**

É o firmware que participa da inicialização do computador.

---

**POST verifica o hardware antes do sistema operacional iniciar.**

---

**BIOS tradicional está associado ao MBR.**

---

**UEFI normalmente trabalha com GPT e utiliza a ESP para arquivos EFI.**

---

**GRUB é bootloader, não é kernel.**

---

**Linux é o kernel; o kernel assume o controle dos recursos do computador.**

---

# 34. RESUMO FINAL

    FIRMWARE
    ↓
    BIOS / UEFI
    ↓
    Inicialização inicial
    ↓
    POST
    ↓
    Verificação do hardware
    ↓
    Ordem de boot
    ↓
    ┌──────────────────────┐
    │ BIOS → MBR           │
    │ UEFI → GPT → ESP     │
    └──────────────────────┘
    ↓
    BOOTLOADER
    ↓
    GRUB
    ↓
    KERNEL
    ↓
    Linux assume o controle
    ↓
    INITRAMFS
    ↓
    SYSTEMD
    ↓
    SERVIÇOS
    ↓
    SISTEMA PRONTO

---

# CONCEITO CENTRAL

A grande ideia desta parte é:

**O computador não liga e imediatamente executa o Linux.**

Existe uma cadeia de inicialização:

**Firmware → hardware → dispositivo de boot → bootloader → kernel → sistema operacional**

E existem dois modelos principais que precisamos reconhecer:

**BIOS → MBR → Bootloader**

**UEFI → GPT → ESP → Bootloader**

A partir daqui, o próximo estudo pode aprofundar justamente o que acontece depois que o firmware entrega o controle ao bootloader:
**GRUB → Kernel → initramfs → systemd → serviços → login.**
