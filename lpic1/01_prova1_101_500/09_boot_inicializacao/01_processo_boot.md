# 09 — Boot e Inicialização
## 01 — Processo de Boot

### Boot — Inicialização

**Boot** é o processo que acontece desde o momento em que o computador é ligado até o Linux estar inicializado e pronto para uso.

De forma simplificada:

    Hardware
       ↓
    Firmware
       ↓
    Bootloader
       ↓
    Kernel
       ↓
    init / systemd
       ↓
    Serviços
       ↓
    Login

---

### 1. Firmware — Firmware (Software do Hardware)

Quando o computador é ligado, o **firmware** inicia.

Os dois tipos mais importantes são:

- **BIOS — Basic Input/Output System**
- **UEFI — Unified Extensible Firmware Interface**

O firmware:

- inicializa e verifica o hardware;
- identifica dispositivos de armazenamento;
- procura uma forma de iniciar o sistema operacional.

Em computadores modernos, **UEFI** é predominante.

---

### 2. Bootloader — Carregador de Inicialização

Depois do firmware, entra em ação o **Bootloader**.

Um dos mais conhecidos no Linux é:

    GRUB

**GRUB — GRand Unified Bootloader**

Sua função principal é carregar o kernel Linux e iniciar o processo de boot.

Também pode apresentar um menu para escolher:

- sistema operacional;
- versão do kernel;
- opções de inicialização.

---

### 3. Kernel — Núcleo do Linux

O Bootloader carrega o **Kernel — Núcleo** para a memória.

O kernel então:

- inicializa componentes do hardware;
- gerencia memória;
- inicializa drivers;
- prepara o ambiente do sistema;
- inicia o primeiro processo do espaço de usuário.

Em sistemas modernos, normalmente:

    PID 1 → systemd

---

### 4. init / systemd — Sistema de Inicialização

Depois que o kernel é carregado, o sistema inicia o processo de inicialização.

Em distribuições modernas, geralmente:

    systemd

Ele assume o:

    PID 1

O `systemd` é responsável por iniciar e gerenciar diversos serviços e recursos do sistema.

---

### 5. Services — Serviços

O sistema de inicialização começa os serviços necessários.

Exemplos:

    NetworkManager
    sshd
    cron
    systemd-logind

Os serviços podem fornecer:

- rede;
- acesso remoto;
- agendamento de tarefas;
- gerenciamento de sessões;
- outros recursos do sistema.

---

### 6. Login — Entrada do Usuário

Depois que os componentes necessários são inicializados, o sistema disponibiliza uma forma de login.

Pode ser:

**TTY — Teletype Terminal**
→ terminal de texto.

Ou:

**Display Manager — Gerenciador de Exibição**
→ tela gráfica de login.

Exemplos de display managers:

    GDM
    SDDM
    LightDM

---

### BIOS × UEFI

| BIOS | UEFI |
|---|---|
| Firmware tradicional | Firmware moderno |
| Mais antigo | Mais atual |
| Usa normalmente MBR no processo tradicional de boot | Trabalha naturalmente com GPT |
| Limitações maiores | Recursos mais avançados |

⚠️ **UEFI não é o bootloader.**

UEFI é o **firmware**.

O GRUB é um **bootloader**.

---

### Bootloader × Kernel

Não confunda:

**Bootloader**
→ carrega o kernel.

**Kernel**
→ assume o controle do sistema e inicializa o ambiente Linux.

Fluxo:

    Firmware
       ↓
    GRUB
       ↓
    Kernel Linux

---

### Ver informações do Kernel

Depois que o sistema iniciou:

    uname -r

- `-r` — release (versão/release do kernel)

Exemplo:

    6.14.0-...

Também podemos usar:

    uname -a

- `-a` — all (todas as informações disponíveis)

---

### Ver o processo de boot

Em sistemas com `systemd`:

    systemd-analyze

Mostra informações sobre o tempo de inicialização.

Exemplo:

    Startup finished in 2.1s (firmware) + 1.2s (loader) + 3.4s (kernel) + 5.0s (userspace)

Os valores variam de acordo com o sistema.

---

### Ver serviços demorados

    systemd-analyze blame

Mostra quanto tempo diferentes unidades levaram para iniciar.

---

### ⚠️ Atenção para a prova LPIC-1

Memorize a sequência:

    Firmware
       ↓
    Bootloader
       ↓
    Kernel
       ↓
    PID 1
       ↓
    Serviços
       ↓
    Login

**BIOS / UEFI**
→ firmware.

**GRUB**
→ bootloader.

**Kernel**
→ núcleo do sistema.

**systemd**
→ sistema de inicialização e gerenciamento de serviços; normalmente PID 1 em distribuições modernas.

**PID 1**
→ primeiro processo do espaço de usuário.

> **Conhecimento só tem valor quando é compartilhado** - Laerte Costa
