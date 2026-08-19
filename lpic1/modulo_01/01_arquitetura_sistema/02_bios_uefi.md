# LPIC-1 - Módulo 01
## 2. BIOS e UEFI

### 2.1 O que acontece quando ligamos o computador?

Quando pressionamos o botão de ligar, o computador ainda não está executando o Linux.

Primeiro, o firmware da placa-mãe entra em ação.

O processo simplificado é:

**Botão Power → BIOS/UEFI → Inicialização do hardware → Dispositivo de boot → Bootloader → Kernel Linux → Sistema Operacional**

---

### 2.2 BIOS

**BIOS - Basic Input/Output System**

Tradução: **Sistema Básico de Entrada e Saída**.

A BIOS é um **firmware** armazenado na placa-mãe.

Sua principal função é preparar o computador para que o sistema operacional possa ser iniciado.

Entre suas funções estão:

- Inicializar componentes de hardware;
- Verificar a memória RAM;
- Detectar o processador;
- Detectar discos;
- Detectar teclado e outros dispositivos;
- Identificar dispositivos de inicialização;
- Iniciar o processo de boot.

---

### 2.3 POST

**POST - Power-On Self-Test**

Tradução: **Autoteste de Inicialização**.

É uma verificação realizada durante a inicialização do computador.

A BIOS verifica se os principais componentes de hardware estão funcionando corretamente.

Fluxo simplificado:

Computador ligado  
↓  
BIOS inicia  
↓  
POST  
↓  
Verificação do hardware  
↓  
Encontrou tudo necessário?  
↓  
SIM  
↓  
Procura dispositivo de boot

Quando existe algum problema grave de hardware, o computador pode apresentar mensagens de erro ou emitir sinais sonoros (bipes).

---

### 2.4 UEFI

**UEFI - Unified Extensible Firmware Interface**

É o firmware moderno que substituiu a BIOS tradicional em grande parte dos computadores atuais.

Embora seja comum chamar o firmware moderno simplesmente de "BIOS", tecnicamente muitos computadores atuais utilizam **UEFI**.

A função básica continua sendo semelhante:

**Inicializar o hardware e iniciar o sistema operacional.**

#### Algumas características do UEFI

- Suporte a discos grandes;
- Suporte ao particionamento GPT;
- Interface gráfica em muitos computadores;
- Suporte a mouse;
- Inicialização mais flexível;
- Utilização da EFI System Partition (ESP);
- Suporte ao Secure Boot.

---

### 2.5 BIOS tradicional × UEFI

| BIOS tradicional | UEFI |
|---|---|
| Firmware mais antigo | Firmware moderno |
| Normalmente associado ao MBR | Normalmente associado ao GPT |
| Possui mais limitações | Possui mais recursos |
| Interface geralmente simples | Pode possuir interface gráfica |
| Boot baseado no código de inicialização do disco | Boot baseado em arquivos `.efi` |
| Tecnologia antiga | Padrão moderno |

> **Importante:** BIOS/UEFI não é o sistema operacional. É o firmware responsável pela etapa inicial da inicialização do computador.

---

### 2.6 MBR e GPT

#### MBR

**MBR - Master Boot Record**

É um método antigo de particionamento de discos.

É tradicionalmente associado ao modo de inicialização **BIOS/Legacy**.

#### GPT

**GPT - GUID Partition Table**

É o padrão moderno de particionamento de discos.

É normalmente utilizado junto com o **UEFI**.

Podemos guardar inicialmente a seguinte associação:

**BIOS/Legacy → MBR**

**UEFI → GPT**

> **Observação:** essa relação é uma simplificação para facilitar o estudo. Existem combinações diferentes, mas essa associação é importante para compreender o funcionamento tradicional.

---

### 2.7 EFI System Partition - ESP

**ESP - EFI System Partition**

É uma partição especial utilizada pelo UEFI para armazenar arquivos necessários ao processo de inicialização.

Um disco pode ser organizado assim:

```text
Disco
│
├── EFI System Partition
│      └── arquivos .efi
│
├── Partição Linux
│
└── Outras partições

No Linux, a ESP normalmente é montada em:

/boot/efii

Secure Boot é um recurso do UEFI que ajuda a impedir que softwares não autorizados sejam executados durante o processo de inicialização.
A ideia simplificada é:

UEFI
 ↓
Verifica a assinatura do bootloader
 ↓
Assinatura válida?
 ↓
SIM → Continua o boot

 Sequência de inicialização

HARDWARE
   ↓
BIOS / UEFI
   ↓
POST
   ↓
BOOT
   ↓
BOOTLOADER
   ↓
KERNEL
   ↓
LINUX

Resumo
BIOS/UEFI → Firmware da placa-mãe.
BIOS → Firmware tradicional, mais antigo.
UEFI → Firmware moderno.
POST → Teste inicial do hardware.
MBR → Padrão de particionamento tradicional.
GPT → Padrão moderno de particionamento.
ESP → Partição utilizada pelo UEFI para armazenar arquivos de inicialização.
Secure Boot → Recurso de segurança do UEFI.
Bootloader → Programa responsável por iniciar o sistema operacional.
Kernel → Núcleo do sistema operacional.

📌 Conceito-chave
O BIOS/UEFI não é o Linux e também não é o bootloader.

Ele é o firmware que inicia o computador, prepara o hardware e dá início ao processo que levará à execução do bootloader, do kernel e, finalmente, do sistema operacional.
Sequência para memorizar:
BIOS/UEFI → POST → Bootloader → Kernel → Sistema Operacional

