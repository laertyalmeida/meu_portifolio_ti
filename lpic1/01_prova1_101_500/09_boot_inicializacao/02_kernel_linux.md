# 09 — Boot e Inicialização
## 02 — Kernel Linux

### Kernel — Núcleo do Linux

O **Kernel** é o núcleo do sistema operacional. Ele faz a comunicação entre o **hardware** e os programas que executamos.

    Aplicações
        ↓
    Bibliotecas / Sistema
        ↓
    Kernel Linux
        ↓
    Hardware

O kernel controla recursos fundamentais como:

- CPU;
- memória;
- processos;
- dispositivos;
- sistemas de arquivos;
- rede.

---

### O que acontece durante o boot?

Depois que o **Bootloader — Carregador de Inicialização** carrega o kernel na memória, o kernel começa sua inicialização.

Fluxo:

    Firmware
       ↓
    Bootloader
       ↓
    Kernel Linux
       ↓
    Drivers e subsistemas
       ↓
    PID 1
       ↓
    Serviços

O kernel prepara o sistema e, posteriormente, inicia o primeiro processo do espaço de usuário.

Em sistemas modernos:

    PID 1 → systemd

---

### Kernel Image — Imagem do Kernel

O kernel utilizado no boot é uma **imagem** armazenada no disco.

Em sistemas Linux, normalmente encontramos arquivos relacionados ao kernel em:

    /boot

Exemplo:

    /boot/vmlinuz-6.x.x

`vmlinuz` é um nome tradicional usado para imagens do kernel Linux.

---

### initramfs — Initial RAM Filesystem (Sistema de Arquivos Inicial em RAM)

Durante o boot, o kernel pode utilizar um:

    initramfs

O **initramfs** é um sistema de arquivos temporário carregado na RAM durante a inicialização.

Ele contém ferramentas e módulos necessários para preparar o sistema antes que o sistema de arquivos raiz real seja montado.

Fluxo simplificado:

    Bootloader
       ↓
    Kernel + initramfs
       ↓
    Drivers necessários
       ↓
    Sistema de arquivos raiz
       ↓
    PID 1

---

### Kernel Modules — Módulos do Kernel

Algumas funcionalidades podem ser carregadas como **módulos** em vez de ficarem incorporadas diretamente ao kernel.

Os módulos geralmente ficam em:

    /lib/modules/

Para listar módulos carregados:

    lsmod

- `lsmod` — list modules (listar módulos)

---

### modprobe — Load/Remove Kernel Module (Carregar/Remover Módulo)

Para carregar um módulo:

    sudo modprobe nome_do_modulo

Para remover:

    sudo modprobe -r nome_do_modulo

- `-r` — remove (remover)

O `modprobe` também resolve dependências entre módulos.

---

### Ver informações do Kernel

    uname -r

- `-r` — release (versão/release)

Exemplo:

    6.14.0-...

Informações completas:

    uname -a

- `-a` — all (todas as informações)

---

### /proc/version

Também podemos consultar:

    cat /proc/version

Esse arquivo apresenta informações sobre a versão do kernel e o compilador utilizado para construí-lo.

---

### /proc/cmdline

O kernel recebe parâmetros durante o boot.

Eles podem ser consultados com:

    cat /proc/cmdline

Exemplo:

    BOOT_IMAGE=/boot/vmlinuz-6.x.x root=/dev/sda2 ro quiet

Esses parâmetros podem alterar o comportamento do kernel durante a inicialização.

---

### Mensagens do Kernel

Durante e depois do boot, o kernel registra mensagens importantes.

Podemos consultar:

    dmesg

**dmesg — Display Message (Exibir Mensagens)**

Mostra mensagens do buffer de mensagens do kernel.

Para pesquisar algo específico:

    dmesg | grep -i error

- `|` — pipe (encaminhar saída)
- `-i` — ignore case (ignorar maiúsculas/minúsculas)

Em sistemas com `systemd`:

    journalctl -k

- `-k` — kernel (mostrar mensagens do kernel)

---

### Kernel Space × User Space

O Linux separa a execução em dois ambientes principais:

**Kernel Space — Espaço do Kernel**
→ onde o kernel executa com privilégios elevados.

**User Space — Espaço do Usuário**
→ onde normalmente executam aplicações e serviços.

    User Space
    ┌──────────────────────┐
    │ Aplicações           │
    │ Serviços             │
    └──────────┬───────────┘
               │
        System Calls
               ↓
    ┌──────────────────────┐
    │ Kernel Space         │
    │ Kernel Linux         │
    └──────────┬───────────┘
               ↓
            Hardware

---

### System Call — Chamada de Sistema

Programas em **User Space** não acessam diretamente os recursos privilegiados do hardware.

Eles utilizam **System Calls — Chamadas de Sistema** para solicitar serviços ao kernel.

Exemplos de operações que envolvem chamadas de sistema:

- abrir arquivos;
- criar processos;
- acessar dispositivos;
- usar recursos de rede;
- alocar memória.

---

### ⚠️ Atenção para a prova LPIC-1

Memorize:

**Kernel**
→ núcleo do sistema Linux.

**`/boot`**
→ normalmente contém arquivos usados no processo de inicialização, incluindo imagens do kernel.

**initramfs**
→ sistema de arquivos inicial carregado na RAM para auxiliar o boot.

**`/lib/modules/`**
→ módulos do kernel.

**`lsmod`**
→ lista módulos carregados.

**`modprobe`**
→ carrega ou remove módulos.

**`uname -r`**
→ mostra a versão/release do kernel.

**`dmesg`**
→ mostra mensagens do kernel.

**`journalctl -k`**
→ mostra mensagens do kernel no journal do `systemd`.

### Resumo

    Bootloader
       ↓
    Kernel
       ↓
    initramfs
       ↓
    Drivers / subsistemas
       ↓
    Sistema de arquivos raiz
       ↓
    PID 1
       ↓
    Serviços

> **Conhecimento só tem valor quando é compartilhado** - Laerte Costa
