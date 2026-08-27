# 🐧 LPIC-1 — PARTE 3

# PROCESSO DE BOOT DO LINUX

---

## 1. O QUE É BOOT?

**Boot** é o processo de inicialização do computador.

Quando você aperta o botão de ligar, o Linux ainda não está funcionando.

O computador precisa passar por várias etapas até chegar ao sistema operacional.

De forma simplificada:

```text
ENERGIA
   ↓
CPU começa a executar instruções
   ↓
BIOS / UEFI
   ↓
Bootloader
   ↓
GRUB
   ↓
Kernel Linux
   ↓
initramfs
   ↓
systemd
   ↓
Serviços
   ↓
Linux pronto para uso
```

### Em outras palavras:

O computador precisa responder a uma pergunta:

> "O que eu devo executar depois que fui ligado?"

É justamente isso que o processo de boot organiza.

---

# 2. O QUE ACONTECE QUANDO APERTAMOS O BOTÃO DE LIGAR?

Quando você aperta o botão:

```text
Botão Power
     ↓
Placa-mãe recebe o comando
     ↓
Energia é estabilizada
     ↓
CPU começa a funcionar
     ↓
CPU começa a executar instruções
```

A CPU não sabe automaticamente onde está o Linux.

Ela precisa de um programa inicial que diga o que fazer.

Esse primeiro código vem do:

```text
BIOS ou UEFI
```

Esse firmware está armazenado em memória não volátil da placa-mãe.

---

# 3. BIOS / UEFI

A BIOS ou UEFI realiza as primeiras tarefas necessárias para colocar o computador em condições de iniciar um sistema operacional.

Entre essas tarefas estão:

* inicializar hardware;
* verificar componentes;
* identificar dispositivos de armazenamento;
* identificar memória;
* preparar o processo de inicialização;
* localizar algo que possa ser executado para continuar o boot.

Depois disso, BIOS/UEFI entrega o controle para o próximo estágio.

Esse próximo estágio normalmente é o:

```text
BOOTLOADER
```

No Linux, o bootloader mais conhecido é:

```text
GRUB
```

---

# 4. O QUE É BOOTLOADER?

**Bootloader** significa literalmente:

> carregador de inicialização.

É um pequeno programa responsável por iniciar o sistema operacional.

Ele fica entre o firmware e o sistema operacional:

```text
BIOS / UEFI
     ↓
BOOTLOADER
     ↓
KERNEL
     ↓
LINUX
```

O bootloader não é o Linux inteiro.

Sua função principal é localizar e carregar o Kernel.

---

# 5. GRUB

No Linux, um dos bootloaders mais utilizados é o:

```text
GRUB
```

GRUB significa:

```text
GRand Unified Bootloader
```

Em muitas instalações Linux, o GRUB é responsável por apresentar o menu de inicialização e carregar o Kernel.

Por exemplo:

```text
GRUB
 ├── Debian
 ├── Debian — modo recuperação
 └── Memtest
```

Quando você escolhe Debian:

```text
GRUB
   ↓
localiza o Kernel
   ↓
carrega o Kernel na RAM
   ↓
passa parâmetros para o Kernel
   ↓
Kernel começa a execução
```

---

# 6. BIOS + MBR

Em computadores que utilizam o modo tradicional BIOS, é comum encontrarmos:

```text
BIOS
 ↓
MBR
 ↓
GRUB
 ↓
Kernel
```

### O que é MBR?

MBR significa:

```text
Master Boot Record
```

Ele fica no início do disco.

Historicamente, o MBR possui espaço muito pequeno para código de inicialização.

Por isso, o GRUB tradicional utiliza mais de uma etapa para conseguir carregar a si próprio.

De forma simplificada:

```text
BIOS
 ↓
MBR
 ↓
GRUB
 ↓
Kernel
```

---

# 7. UEFI + GPT

Em computadores modernos, é comum utilizar:

```text
UEFI
 ↓
ESP
 ↓
GRUB
 ↓
Kernel
```

Aqui aparece um conceito importante:

```text
ESP
```

ESP significa:

```text
EFI System Partition
```

É uma partição especial utilizada pelo firmware UEFI para armazenar arquivos de inicialização.

Normalmente ela utiliza o sistema de arquivos:

```text
FAT32
```

---

# 8. O QUE É A ESP?

A **EFI System Partition** é uma partição criada para armazenar arquivos utilizados no processo de inicialização UEFI.

Exemplo:

```text
DISCO
│
├── ESP
│    └── arquivos EFI
│
├── /
│
└── /home
```

Um sistema Linux instalado em modo UEFI normalmente possui uma ESP.

Ela pode aparecer no Linux como algo semelhante a:

```text
/dev/sda1
```

ou:

```text
/dev/nvme0n1p1
```

O nome depende do dispositivo de armazenamento.

---

# 9. BIOS/UEFI NÃO É O KERNEL

Essa diferença é muito importante.

São coisas diferentes:

```text
BIOS / UEFI
    ↓
Firmware da placa-mãe

GRUB
    ↓
Bootloader

Kernel
    ↓
Núcleo do sistema operacional

systemd
    ↓
Sistema de inicialização e gerenciamento de serviços
```

Não devemos misturar essas funções.

---

# 10. O QUE É O KERNEL?

O **Kernel** é o núcleo do sistema operacional.

No Linux, ele é responsável por controlar e organizar o acesso aos recursos do computador.

Por exemplo:

```text
             KERNEL
                │
      ┌─────────┼─────────┐
      ↓         ↓         ↓
     CPU       RAM      Hardware
                         │
                 ┌───────┼───────┐
                 ↓       ↓       ↓
               Disco   Rede     USB
```

O Kernel faz a ponte entre os programas e o hardware.

Por exemplo:

```text
Programa
   ↓
Sistema operacional
   ↓
Kernel
   ↓
Driver
   ↓
Hardware
```

---

# 11. O GRUB CARREGA O KERNEL

Depois que o GRUB assume o controle, ele precisa localizar o Kernel.

Em uma instalação Linux, normalmente encontramos o Kernel em:

```text
/boot/
```

Por exemplo:

```text
/boot/
├── vmlinuz-6.x.x
├── initrd.img-6.x.x
├── config-6.x.x
└── System.map-6.x.x
```

O arquivo:

```text
vmlinuz
```

representa uma imagem do Kernel Linux.

---

# 12. O QUE É INITRAMFS?

Aqui começa uma parte muito importante.

Antes de o Kernel conseguir montar completamente o sistema de arquivos raiz, ele pode precisar de alguns recursos.

Por exemplo:

* drivers;
* módulos;
* ferramentas;
* scripts;
* informações necessárias para encontrar o sistema raiz.

Para isso existe o:

```text
initramfs
```

Significa:

```text
initial RAM filesystem
```

É um pequeno sistema de arquivos carregado na RAM durante o processo inicial de boot.

---

# 13. POR QUE O INITRAMFS EXISTE?

Imagine que seu sistema esteja instalado em:

```text
/dev/nvme0n1p2
```

Mas para acessar essa partição o Kernel precisa primeiro carregar determinado driver ou montar uma estrutura específica.

O initramfs pode fornecer esses recursos antes de o sistema raiz estar completamente disponível.

Simplificando:

```text
Kernel
  ↓
precisa acessar o sistema raiz
  ↓
initramfs fornece ferramentas/drivers necessários
  ↓
sistema raiz pode ser encontrado/montado
  ↓
continuação da inicialização
```

---

# 14. KERNEL + INITRAMFS

Durante o boot, o GRUB pode carregar dois elementos importantes:

```text
Kernel
   +
initramfs
```

Na prática:

```text
GRUB
 │
 ├── Kernel
 │
 └── initramfs
```

O Kernel começa a executar e utiliza o initramfs para realizar tarefas iniciais.

---

# 15. PARÂMETROS DO KERNEL

O GRUB também pode passar parâmetros para o Kernel.

Por exemplo:

```text
root=/dev/sda2
```

Isso informa qual dispositivo deve ser utilizado como sistema de arquivos raiz.

Outro exemplo:

```text
ro
```

Significa:

```text
read-only
```

Ou seja, inicialmente o sistema raiz pode ser montado como somente leitura.

Um parâmetro muito conhecido também é:

```text
quiet
```

Ele reduz a quantidade de mensagens exibidas durante o boot.

---

# 16. ONDE O GRUB GUARDA ESSAS CONFIGURAÇÕES?

No Debian, uma configuração muito conhecida relacionada ao GRUB é:

```text
/etc/default/grub
```

Por exemplo:

```text
GRUB_TIMEOUT=5
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```

Depois de alterar configurações, normalmente é necessário regenerar a configuração do GRUB.

Um comando comum é:

```bash
sudo update-grub
```

Esse comando gera novamente a configuração utilizada pelo GRUB.

---

# 17. O KERNEL COMEÇA A EXECUTAR

Depois que o GRUB carrega o Kernel:

```text
GRUB
 ↓
Kernel
```

Agora o Kernel começa a assumir o controle do computador.

Ele começa a:

* inicializar estruturas internas;
* detectar hardware;
* carregar módulos necessários;
* inicializar drivers;
* preparar memória;
* preparar dispositivos;
* preparar o ambiente necessário para continuar o boot.

---

# 18. E DEPOIS?

Depois das tarefas iniciais do Kernel, o sistema precisa iniciar o processo de inicialização em espaço de usuário.

Em sistemas Linux modernos, normalmente temos:

```text
Kernel
   ↓
systemd
```

O `systemd` normalmente é o primeiro processo do espaço de usuário.

Ele recebe o:

```text
PID 1
```

---

# 19. O QUE É PID 1?

PID significa:

```text
Process ID
```

É o identificador de um processo.

O primeiro processo iniciado pelo sistema recebe:

```text
PID 1
```

Em muitas distribuições Linux modernas:

```text
PID 1 = systemd
```

Podemos verificar isso com:

```bash
ps -p 1
```

ou:

```bash
ps -p 1 -o pid,comm,args
```

Podemos encontrar algo semelhante a:

```text
PID COMMAND
1   systemd
```

---

# 20. SYSTEMD CONTINUA A INICIALIZAÇÃO

Agora temos:

```text
BIOS / UEFI
      ↓
GRUB
      ↓
Kernel
      ↓
initramfs
      ↓
systemd
```

O systemd passa a iniciar e gerenciar diversos componentes do sistema.

Por exemplo:

```text
systemd
   ↓
rede
   ↓
login
   ↓
serviços
   ↓
outros processos
```

Até chegarmos ao sistema pronto para utilização.

---

# 21. VISÃO COMPLETA DO BOOT

Agora podemos juntar tudo:

```text
┌─────────────────────┐
│      POWER ON       │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│    CPU começa       │
│    a executar       │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│     BIOS / UEFI     │
│ inicializa hardware │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│      BOOTLOADER     │
│        GRUB         │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│       KERNEL        │
│      vmlinuz        │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│      INITRAMFS      │
│ drivers + ferramentas│
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│      SYSTEMD        │
│       PID 1         │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│      SERVIÇOS       │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│   SISTEMA PRONTO    │
└─────────────────────┘
```

---

# 22. BIOS/UEFI × GRUB × KERNEL × SYSTEMD

Uma maneira muito boa de memorizar é separar as responsabilidades:

| Componente | Função                                    |
| ---------- | ----------------------------------------- |
| BIOS       | Firmware tradicional                      |
| UEFI       | Firmware moderno                          |
| ESP        | Partição usada no boot UEFI               |
| GRUB       | Bootloader                                |
| Kernel     | Núcleo do Linux                           |
| initramfs  | Ambiente inicial temporário               |
| systemd    | Inicialização e gerenciamento de serviços |
| PID 1      | Primeiro processo do espaço de usuário    |

---

# 23. UMA ANALOGIA PARA ENTENDER

Imagine uma empresa.

### BIOS/UEFI

É o funcionário que abre a empresa.

```text
"Vamos ligar tudo e preparar o prédio."
```

### GRUB

É o gerente que decide:

```text
"Qual sistema vamos iniciar?"
```

### Kernel

É o responsável pela infraestrutura:

```text
"Eu vou controlar os recursos e conversar com o hardware."
```

### initramfs

É a equipe temporária que fornece as ferramentas necessárias para colocar a infraestrutura inicial em funcionamento.

### systemd

É o gerente operacional:

```text
"Agora vamos iniciar os serviços."
```

### Serviços

São os diversos setores:

```text
rede
SSH
DNS
interface gráfica
login
etc.
```

---

# 24. O MAIS IMPORTANTE PARA O LPIC-1

Não memorize apenas:

```text
BIOS → GRUB → Kernel → systemd
```

Entenda a responsabilidade de cada um:

```text
BIOS/UEFI
    ↓
inicia o hardware e procura algo para executar

GRUB
    ↓
carrega o Kernel

Kernel
    ↓
assume o controle do hardware e do sistema

initramfs
    ↓
fornece ambiente inicial para o Kernel

systemd
    ↓
assume a inicialização do espaço de usuário

serviços
    ↓
colocam o sistema em funcionamento
```

---

# 25. COMANDOS IMPORTANTES PARA INVESTIGAR O BOOT

### Ver o Kernel em execução

```bash
uname -r
```

Exemplo:

```text
6.12.74-amd64
```

---

### Ver informações completas do Kernel

```bash
uname -a
```

---

### Ver o processo PID 1

```bash
ps -p 1
```

---

### Ver o systemd

```bash
ps -p 1 -o pid,comm,args
```

---

### Ver arquivos relacionados ao Kernel

```bash
ls -lh /boot/
```

---

### Ver informações do GRUB

```bash
ls /etc/default/grub
```

---

### Regenerar configuração do GRUB no Debian

```bash
sudo update-grub
```

---

# 26. RESUMO MENTAL

```text
                BOOT
                 │
        ┌────────┴────────┐
        ↓                 ↓
      BIOS              UEFI
        │                 │
       MBR               ESP
        │                 │
        └────────┬────────┘
                 ↓
                GRUB
                 ↓
               KERNEL
                 ↓
             INITRAMFS
                 ↓
              SYSTEMD
               PID 1
                 ↓
              SERVIÇOS
                 ↓
          LINUX FUNCIONANDO
```

---

# 🎯 CONCEITO CENTRAL

O processo de boot é uma **cadeia de transferência de controle**.

Cada etapa prepara o computador e entrega o controle para a próxima:

```text
CPU
 ↓
BIOS / UEFI
 ↓
GRUB
 ↓
Kernel
 ↓
initramfs
 ↓
systemd
 ↓
serviços
 ↓
usuário
```

A ideia principal é:

> **Uma etapa não simplesmente "liga" a próxima. Ela executa código que prepara o ambiente e entrega o controle para o próximo estágio.**

Isso é fundamental para entender Linux, troubleshooting de boot e vários assuntos cobrados no LPIC-1.

