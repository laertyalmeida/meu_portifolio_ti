# BIOS / UEFI — PARTE 2
## Do momento em que o computador liga até o GRUB

---

# 1. POST

POST significa:

**Power-On Self-Test**

É o teste inicial realizado pelo firmware quando o computador é ligado.

Podemos imaginar assim:

    Você aperta o botão POWER
             ↓
        Computador liga
             ↓
       BIOS / UEFI inicia
             ↓
            POST
             ↓
    Verificação do hardware
             ↓
       Processo de BOOT

O POST verifica se os principais componentes necessários para iniciar o computador estão funcionando.

Exemplos:

- CPU
- Memória RAM
- Vídeo
- Teclado
- Controladores de armazenamento
- Outros componentes básicos

### O que o POST faz?

Ele não está iniciando o Linux ainda.

Ele está basicamente perguntando:

> "O hardware necessário para continuar funcionando está presente e respondendo?"

Se existir um problema grave, o computador pode:

- emitir bipes;
- mostrar uma mensagem de erro;
- acender códigos/LEDs de diagnóstico;
- ou simplesmente não continuar o processo de inicialização.

---

# 2. Firmware identifica os dispositivos

Depois das verificações iniciais, o BIOS/UEFI precisa descobrir quais dispositivos estão disponíveis.

Por exemplo:

- SSD
- HD
- pendrive
- DVD
- placa de rede
- outros dispositivos

Imagine:

    BIOS / UEFI
         ↓
    "Quais dispositivos existem?"
         ↓
    SSD
    HD
    USB
    Rede
         ↓
    "De qual deles devo iniciar?"

É aqui que entra a **ordem de boot**.

---

# 3. Ordem de Boot

A ordem de boot determina onde o firmware vai procurar algo que possa iniciar o sistema.

Exemplo:

    1º USB
    2º SSD
    3º Rede

O firmware tenta seguir essa ordem.

Se não encontrar algo inicializável no USB, pode tentar o SSD.

Exemplo:

    USB
     ↓
    Não encontrou boot
     ↓
    SSD
     ↓
    Encontrou boot
     ↓
    Continua a inicialização

Essa configuração pode ser alterada no BIOS/UEFI.

---

# 4. BIOS tradicional + MBR

Em computadores que utilizam o modo tradicional de BIOS, uma forma comum de inicialização é através do **MBR**.

MBR significa:

**Master Boot Record**

O MBR fica no início do dispositivo de armazenamento.

Exemplo:

    HD / SSD
    ┌──────────────────────────┐
    │ MBR                      │
    ├──────────────────────────┤
    │ Partições                │
    │                          │
    │                          │
    │ Dados                    │
    └──────────────────────────┘

O BIOS localiza o dispositivo de boot e procura o código inicial no MBR.

Esse código pode iniciar o processo do bootloader.

### Importante

O MBR não é simplesmente "o bootloader inteiro".

Ele possui uma pequena área de código usada para iniciar o processo.

No caso do GRUB em sistemas BIOS, partes adicionais do GRUB podem estar em outras áreas do disco.

---

# 5. Limitações do MBR

O esquema MBR é antigo e possui algumas limitações importantes.

Entre elas:

- máximo tradicional de 4 partições primárias;
- uso de partições estendidas para contornar essa limitação;
- limite de aproximadamente 2 TiB para discos usando setores de 512 bytes;
- estrutura de boot mais limitada.

Por isso surgiu uma abordagem mais moderna:

**GPT + UEFI**

---

# 6. UEFI + GPT

UEFI é o firmware moderno que substituiu o BIOS tradicional em grande parte dos computadores atuais.

GPT significa:

**GUID Partition Table**

O GPT é um esquema moderno de particionamento.

Podemos representar:

    SSD
    ┌───────────────────────────────┐
    │ GPT                           │
    ├──────────┬────────────────────┤
    │ ESP      │ Linux              │
    │          │                    │
    │          │                    │
    ├──────────┴────────────────────┤
    │ outras partições              │
    └───────────────────────────────┘

UEFI + GPT trabalham muito bem juntos.

---

# 7. ESP — EFI System Partition

Quando o computador utiliza UEFI, normalmente existe uma partição chamada:

**ESP**

Significa:

**EFI System Partition**

É uma partição especial usada para armazenar arquivos necessários para o processo de inicialização.

Normalmente utiliza o sistema de arquivos FAT32.

Exemplo:

    SSD
    ┌───────────────────────────────┐
    │ GPT                           │
    ├───────────────────────────────┤
    │ ESP                           │
    │ /boot/efi                     │
    │                               │
    │ arquivos EFI                  │
    ├───────────────────────────────┤
    │ Sistema Linux                 │
    ├───────────────────────────────┤
    │ Dados                         │
    └───────────────────────────────┘

No Linux, a ESP frequentemente é montada em:

    /boot/efi

Mas isso pode variar dependendo da distribuição e da configuração.

---

# 8. Como o UEFI encontra o bootloader?

Essa é uma diferença muito importante.

No BIOS tradicional:

    BIOS
      ↓
    MBR
      ↓
    código de boot
      ↓
    GRUB

No UEFI:

    UEFI
      ↓
    ESP
      ↓
    arquivo EFI
      ↓
    GRUB
      ↓
    Kernel

O UEFI consegue trabalhar com arquivos EFI armazenados na ESP.

Por isso o processo é diferente do BIOS tradicional.

---

# 9. Bootloader

Agora chegamos ao:

**BOOTLOADER**

Bootloader significa:

**carregador de inicialização**

No Linux, um dos mais conhecidos é:

**GRUB**

GRUB significa:

**GRand Unified Bootloader**

O trabalho principal do bootloader é preparar e iniciar o sistema operacional.

Simplificando:

    Firmware
       ↓
    Bootloader
       ↓
    Kernel
       ↓
    Sistema operacional

---

# 10. O que o GRUB faz?

O GRUB pode:

- localizar sistemas operacionais;
- apresentar um menu de inicialização;
- permitir escolher um kernel;
- passar parâmetros para o kernel;
- carregar o kernel na memória;
- carregar o initramfs;
- iniciar o processo de carregamento do Linux.

Exemplo:

    GRUB
      ↓
    Menu
      ↓
    Debian
      ↓
    Kernel Linux
      ↓
    initramfs
      ↓
    systemd
      ↓
    Sistema funcionando

---

# 11. Kernel

Depois que o GRUB seleciona e carrega o kernel, o controle passa para o:

**Kernel Linux**

O kernel é o núcleo do sistema operacional.

Ele começa a assumir o controle do hardware e dos recursos do sistema.

Entre suas funções estão:

- gerenciamento da CPU;
- gerenciamento da memória;
- gerenciamento dos dispositivos;
- gerenciamento de processos;
- comunicação com hardware;
- gerenciamento de arquivos e sistemas de arquivos;
- comunicação entre programas e hardware.

Podemos simplificar:

    Aplicações
        ↓
    Sistema operacional
        ↓
      Kernel
        ↓
      Hardware

---

# 12. Initramfs

Antes de o Linux conseguir montar completamente o sistema de arquivos principal, pode ser necessário carregar alguns componentes e ferramentas temporárias.

É aí que entra o:

**initramfs**

Significa:

**Initial RAM Filesystem**

É um pequeno sistema de arquivos carregado na RAM durante o início do boot.

Ele pode conter:

- módulos do kernel;
- ferramentas;
- scripts;
- componentes necessários para localizar e montar o sistema de arquivos raiz.

Exemplo:

    GRUB
      ↓
    Kernel
      ↓
    initramfs
      ↓
    Localiza/prepara o sistema raiz
      ↓
    Sistema de arquivos /
      ↓
    systemd

---

# 13. systemd

Depois que o kernel já está funcionando e o ambiente inicial foi preparado, o Linux precisa iniciar os serviços do sistema.

Em muitas distribuições modernas, quem assume essa função é o:

**systemd**

Ele é o sistema de inicialização e gerenciamento de serviços.

Pode iniciar coisas como:

- rede;
- login;
- SSH;
- serviços;
- dispositivos;
- logs;
- outros processos necessários ao sistema.

Simplificando:

    Kernel
      ↓
    systemd
      ↓
    Serviços
      ↓
    Ambiente do usuário
      ↓
    Linux pronto

---

# 14. Secure Boot

UEFI também pode trabalhar com:

**Secure Boot**

O Secure Boot ajuda a impedir que componentes de inicialização não autorizados sejam executados.

A ideia simplificada é:

    UEFI
      ↓
    Verifica assinatura
      ↓
    Bootloader autorizado?
       ↙       ↘
     SIM       NÃO
      ↓          ↓
   Executa     Bloqueia

Isso ajuda a proteger o processo de inicialização contra determinados tipos de software malicioso que tentam executar código antes do sistema operacional.

---

# 15. Variáveis UEFI

O UEFI também possui informações armazenadas em uma área chamada:

**NVRAM**

NVRAM significa:

**Non-Volatile Random Access Memory**

Essas informações podem incluir entradas de boot.

Por exemplo:

    UEFI
      ↓
    NVRAM
      ↓
    Entradas de boot
      ↓
    Debian
    Windows
    USB
    etc.

No Linux, podemos verificar informações relacionadas ao UEFI através de:

    /sys/firmware/efi/

Se esse diretório existir, normalmente significa que o Linux foi iniciado em modo UEFI.

---

# 16. Verificando BIOS ou UEFI no Linux

Podemos usar:

    test -d /sys/firmware/efi && echo UEFI || echo BIOS

Interpretação:

    test -d
        ↓
    verifica se o diretório existe

Se existir:

    /sys/firmware/efi/

o comando mostra:

    UEFI

Caso contrário:

    BIOS

---

# 17. efibootmgr

Em sistemas inicializados em UEFI, podemos usar:

    efibootmgr

Ele permite visualizar e gerenciar entradas de boot armazenadas no firmware UEFI.

Exemplo conceitual:

    Boot0000* debian
    Boot0001* Windows Boot Manager
    Boot0002* USB

Isso mostra que o firmware possui entradas que apontam para diferentes opções de inicialização.

---

# 18. Diferença fundamental: BIOS x UEFI

## BIOS tradicional

    BIOS
      ↓
    POST
      ↓
    Dispositivo de boot
      ↓
    MBR
      ↓
    Bootloader
      ↓
    Kernel

## UEFI

    UEFI
      ↓
    POST
      ↓
    Dispositivo de boot
      ↓
    GPT
      ↓
    ESP
      ↓
    Bootloader EFI
      ↓
    Kernel

---

# 19. O processo completo

Agora podemos juntar tudo.

## Computador com UEFI + Linux

    🔌 Energia
         ↓
    ⚙️ UEFI inicia
         ↓
    🔍 POST
         ↓
    🧩 Hardware é verificado
         ↓
    💽 UEFI identifica dispositivos
         ↓
    📋 Ordem de boot
         ↓
    🗂️ GPT
         ↓
    📁 ESP
         ↓
    🚀 GRUB
         ↓
    🧠 Kernel Linux
         ↓
    💾 initramfs
         ↓
    ⚙️ systemd
         ↓
    🔧 Serviços
         ↓
    🖥️ Sistema Linux funcionando

---

# 20. Uma analogia simples

Imagine uma empresa.

### UEFI/BIOS

É o **porteiro**.

Ele verifica:

> "O prédio está em condições para funcionar?"

---

### POST

É a **vistoria inicial**.

Verifica:

> "Tem energia? Os equipamentos básicos estão funcionando?"

---

### Ordem de boot

É a instrução:

> "Primeiro procure a chave aqui. Se não encontrar, procure ali."

---

### ESP

É o **local onde estão guardadas as instruções de entrada** no sistema UEFI.

---

### GRUB

É o **responsável por escolher e chamar o sistema que será iniciado**.

---

### Kernel

É o **núcleo que passa a administrar toda a empresa**.

Ele controla os recursos:

- CPU;
- memória;
- dispositivos;
- processos;
- arquivos.

---

### systemd

É o **gerente que começa a colocar os serviços para funcionar**.

---

# 21. O mais importante para a LPIC-1

Você não precisa decorar apenas uma sequência.

Precisa entender a relação:

    Firmware
       ↓
    Inicializa/verifica hardware
       ↓
    Escolhe dispositivo de boot
       ↓
    Encontra o bootloader
       ↓
    Bootloader carrega o kernel
       ↓
    Kernel inicia
       ↓
    initramfs prepara o ambiente inicial
       ↓
    systemd assume a inicialização
       ↓
    Serviços começam
       ↓
    Sistema operacional funcionando

E principalmente:

    BIOS → MBR → Bootloader

    UEFI → ESP → Bootloader EFI

---

# 22. Resumo final

**BIOS**
- Firmware antigo/tradicional.
- Pode iniciar através do MBR.
- Possui limitações do esquema MBR.

**UEFI**
- Firmware moderno.
- Trabalha normalmente com GPT.
- Utiliza a ESP para arquivos EFI.
- Pode utilizar Secure Boot.
- Possui variáveis armazenadas em NVRAM.

**POST**
- Verifica o hardware durante a inicialização.

**Bootloader**
- Carrega o sistema operacional.
- No Linux, o GRUB é muito comum.

**Kernel**
- Núcleo do Linux.
- Controla CPU, memória, dispositivos, processos etc.

**initramfs**
- Sistema de arquivos inicial carregado na RAM.
- Ajuda a preparar o ambiente antes do sistema raiz.

**systemd**
- Inicializa e gerencia serviços depois que o kernel assume o controle.

---

# MAPA MENTAL

                    COMPUTADOR LIGADO
                           │
                           ▼
                    BIOS / UEFI
                           │
                           ▼
                         POST
                           │
                           ▼
                  VERIFICA HARDWARE
                           │
                           ▼
                    ORDEM DE BOOT
                           │
                 ┌─────────┴─────────┐
                 │                   │
               BIOS                 UEFI
                 │                   │
                MBR                 GPT
                 │                   │
                 │                  ESP
                 │                   │
                 └─────────┬─────────┘
                           ▼
                       BOOTLOADER
                          GRUB
                           │
                           ▼
                        KERNEL
                           │
                           ▼
                       INITRAMFS
                           │
                           ▼
                        SYSTEMD
                           │
                           ▼
                       SERVIÇOS
                           │
                           ▼
                   LINUX FUNCIONANDO
