# Boot e Inicialização

## 02 — Kernel Linux

### 1. O que é o Kernel?

**Kernel — Núcleo**

O **Kernel Linux** é o núcleo do sistema operacional. Ele faz a ligação entre o **hardware** e os programas que estão sendo executados.

    Aplicações
        ↓
    Shell / Serviços
        ↓
    Kernel Linux
        ↓
    Hardware

O usuário normalmente não acessa o hardware diretamente. Os programas fazem solicitações ao kernel.

---

### 2. Principais funções

O kernel é responsável por gerenciar:

| Recurso | Função |
|---|---|
| CPU | Distribuir tempo de processamento |
| RAM | Controlar memória e memória virtual |
| Processos | Criar e gerenciar processos |
| Dispositivos | Comunicar-se com o hardware |
| Arquivos | Trabalhar com sistemas de arquivos |
| Rede | Gerenciar comunicação de rede |
| Drivers | Controlar dispositivos de hardware |

---

### 3. Kernel durante o Boot

Depois que o **Bootloader** carrega o kernel na memória, o kernel começa sua inicialização.

    BIOS / UEFI
         ↓
      GRUB
         ↓
    Kernel Linux
         ↓
      initramfs
         ↓
    PID 1 / systemd
         ↓
      Serviços

Durante essa etapa, o kernel inicializa recursos necessários para continuar o boot.

---

### 4. Kernel e Drivers

**Driver — Controlador de Dispositivo**

É o software que permite ao kernel trabalhar com determinado hardware.

Exemplos:

    placa de rede
    placa de vídeo
    disco
    USB
    áudio

Muitos drivers Linux são implementados como **módulos do kernel**.

---

### 5. Módulos do Kernel

**Kernel Module — Módulo do Kernel**

É um componente que pode ser carregado ou removido do kernel conforme necessário.

Ver módulos carregados:

    lsmod

**lsmod — List Modules — Listar Módulos**

Carregar um módulo:

    sudo modprobe nome_do_modulo

**modprobe — Manage Kernel Modules — Gerenciar Módulos do Kernel**

Remover um módulo:

    sudo modprobe -r nome_do_modulo

`-r` — Remove — Remover

---

### 6. Descobrir a versão do Kernel

Comando:

    uname -r

**uname — Unix Name — Informações do Sistema Unix**

`-r` — Kernel Release — Versão/Release do Kernel

Exemplo:

    6.14.0-29-generic

Também:

    uname -a

`-a` — All — Todas as informações

---

### 7. Arquivos do Kernel

Os kernels instalados normalmente podem ser encontrados em:

    /boot

Exemplos:

    /boot/vmlinuz-6.x.x
    /boot/initrd.img-6.x.x

**vmlinuz** → imagem comprimida do kernel.

**initrd/initramfs** → sistema de arquivos inicial usado durante o boot.

---

### 8. Parâmetros do Kernel

O bootloader pode passar parâmetros para o kernel.

Eles podem ser consultados em:

    cat /proc/cmdline

**`/proc/cmdline` — Kernel Command Line — Linha de Comando do Kernel**

Exemplo:

    BOOT_IMAGE=/boot/vmlinuz-6.x.x root=UUID=xxxx ro quiet

Alguns parâmetros comuns:

| Parâmetro | Significado |
|---|---|
| `root=` | Define o dispositivo/sistema de arquivos raiz |
| `ro` | Read Only — Somente leitura |
| `rw` | Read Write — Leitura e escrita |
| `quiet` | Reduz mensagens exibidas durante o boot |

---

### 9. Mensagens do Kernel

O kernel registra mensagens durante sua execução.

Visualizar:

    dmesg

**dmesg — Display Message — Exibir Mensagens do Kernel**

Em sistemas com `systemd`:

    journalctl -k

`-k` — Kernel — Mostrar mensagens do kernel

Esses comandos são úteis para investigar:

- problemas de hardware;
- drivers;
- discos;
- dispositivos USB;
- rede;
- problemas durante o boot.

---

### 10. Informações do Kernel pelo /proc

Algumas informações podem ser encontradas em:

    /proc/version

    /proc/cmdline

    /proc/modules

    /proc/sys/

O `/proc` é um sistema de arquivos virtual fornecido pelo kernel.

---

## Resumo LPIC-1

- **Kernel — Núcleo** → coração do sistema Linux.
- Faz a ligação entre **programas e hardware**.
- Gerencia CPU, memória, processos, dispositivos, arquivos e rede.
- O Bootloader carrega o kernel durante o boot.
- `uname -r` → mostra a versão do kernel.
- `lsmod` → mostra módulos carregados.
- `modprobe` → carrega ou remove módulos.
- `/boot` → contém imagens usadas no processo de inicialização.
- `/proc/cmdline` → mostra parâmetros passados ao kernel.
- `dmesg` → mostra mensagens do kernel.
- `journalctl -k` → mostra mensagens do kernel no journal.

**Fluxo:**

    BIOS/UEFI
        ↓
      GRUB
        ↓
    Kernel Linux
        ↓
    initramfs
        ↓
    PID 1 / systemd
        ↓
    Serviços

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
