# Boot e Inicialização

## 09 — Troubleshooting de Boot

### 1. O que é Troubleshooting?

**Troubleshooting — Solução de Problemas**

É o processo de identificar a causa de uma falha e corrigi-la.

Quando o Linux não inicia corretamente, devemos investigar o boot **por etapas**.

    BIOS / UEFI
          ↓
      Bootloader
          ↓
       Kernel
          ↓
      initramfs
          ↓
    systemd / init
          ↓
      Serviços
          ↓
       Login

---

### 2. Primeiro: identificar onde parou

| Etapa | Possível problema |
|---|---|
| BIOS / UEFI | Hardware, ordem de boot, disco não detectado |
| Bootloader | GRUB, configuração ou entrada de boot |
| Kernel | Kernel, parâmetros ou drivers |
| initramfs | Driver, disco raiz, LVM, RAID |
| systemd | Serviço ou dependência |
| Login | Interface gráfica, display manager ou usuário |

---

### 3. Verificar mensagens do Kernel

Depois de conseguir iniciar o sistema:

    dmesg

Filtrar erros:

    dmesg | grep -i error

`-i` — **Ignore Case — Ignorar Maiúsculas/Minúsculas**

Também:

    dmesg | grep -i fail

---

### 4. Consultar o Journal

Ver mensagens do boot atual:

    journalctl -b

Somente erros:

    journalctl -b -p err

`-p` — **Priority — Prioridade**

Ver mensagens do kernel:

    journalctl -b -k

Ver o boot anterior:

    journalctl -b -1

Listar boots registrados:

    journalctl --list-boots

---

### 5. Verificar serviços com falha

    systemctl --failed

Ou:

    systemctl list-units --failed

Se um serviço específico falhou:

    systemctl status nome-do-servico

Depois:

    journalctl -u nome-do-servico

Fluxo:

    systemctl status
          ↓
    identificar serviço
          ↓
    journalctl -u serviço
          ↓
    analisar erro

---

### 6. Problemas com o sistema de arquivos raiz

Se o sistema não consegue encontrar ou montar `/`, verifique:

    /etc/fstab

Também:

    lsblk -f

    blkid

Esses comandos ajudam a confirmar:

- dispositivo;
- partição;
- UUID;
- sistema de arquivos;
- ponto de montagem.

Um UUID incorreto no `/etc/fstab` pode impedir a montagem esperada.

---

### 7. Problemas com /etc/fstab

O arquivo:

    /etc/fstab

define sistemas de arquivos que devem ser montados.

Depois de iniciar o sistema, podemos testar:

    sudo mount -a

Se houver erro, o comando normalmente informa qual entrada não conseguiu montar.

Antes de alterar o arquivo:

    sudo cp /etc/fstab /etc/fstab.backup

---

### 8. Problemas com GRUB

**GRUB — GRand Unified Bootloader — Carregador de Inicialização Unificado**

Se o computador não chega ao carregamento do Linux, o problema pode estar no bootloader.

Verifique:

    /boot

E, dependendo do sistema:

    /boot/grub/

Em sistemas UEFI, também pode existir:

    /boot/efi/

---

### 9. Kernel não inicia

Se o GRUB aparece, mas o kernel não inicia corretamente, podem existir problemas relacionados a:

- kernel;
- parâmetros de boot;
- initramfs;
- drivers;
- sistema de arquivos raiz;
- hardware.

Os parâmetros utilizados pelo kernel podem ser vistos depois que o sistema inicia:

    cat /proc/cmdline

---

### 10. initramfs

**initramfs — Initial RAM Filesystem — Sistema de Arquivos Inicial em RAM**

É usado durante os primeiros momentos do boot.

Problemas no initramfs podem impedir o sistema de encontrar ou montar o sistema de arquivos raiz.

A investigação pode envolver:

    dmesg

    journalctl -b

    lsblk

    blkid

---

### 11. Rescue Mode

**Rescue Mode — Modo de Recuperação**

O `systemd` possui:

    rescue.target

Pode ser usado para entrar em um ambiente de recuperação com poucos serviços.

Consultar:

    systemctl get-default

---

### 12. Emergency Mode

**Emergency Mode — Modo de Emergência**

O `systemd` também possui:

    emergency.target

É um ambiente ainda mais mínimo, usado para situações graves de recuperação.

Pode ser necessário quando o sistema não consegue atingir o estado normal de inicialização.

---

### 13. Ordem prática para investigar

Uma sequência simples:

    01. Verificar onde o boot parou
            ↓
    02. Verificar mensagens do kernel
            ↓
        dmesg
            ↓
    03. Verificar o journal
            ↓
        journalctl -b
            ↓
    04. Procurar serviços com falha
            ↓
        systemctl --failed
            ↓
    05. Verificar sistema de arquivos
            ↓
        lsblk -f
        blkid
            ↓
    06. Verificar /etc/fstab
            ↓
        mount -a
            ↓
    07. Investigar GRUB / kernel / initramfs

---

### 14. Comandos essenciais

| Comando | Uso |
|---|---|
| `dmesg` | Mensagens do kernel |
| `journalctl -b` | Logs do boot atual |
| `journalctl -b -1` | Logs do boot anterior |
| `journalctl -k` | Logs do kernel |
| `journalctl -p err` | Erros |
| `systemctl --failed` | Unidades com falha |
| `systemctl status` | Estado do sistema/serviço |
| `lsblk -f` | Discos, partições e sistemas de arquivos |
| `blkid` | UUID, LABEL e tipo de sistema de arquivos |
| `mount -a` | Testar montagens do `/etc/fstab` |
| `cat /proc/cmdline` | Parâmetros do kernel |

---

## Resumo LPIC-1

- **Troubleshooting** → Solução de Problemas.
- Investigue o boot **por etapas**.
- `dmesg` → mensagens do kernel.
- `journalctl -b` → mensagens do boot atual.
- `journalctl -b -1` → mensagens do boot anterior.
- `journalctl -k` → mensagens do kernel.
- `systemctl --failed` → unidades que falharam.
- `systemctl status serviço` → estado de um serviço.
- `journalctl -u serviço` → logs de um serviço.
- `lsblk -f` → verificar discos, partições e sistemas de arquivos.
- `blkid` → verificar UUID, LABEL e tipo de sistema de arquivos.
- `mount -a` → testar entradas do `/etc/fstab`.
- `/boot` → arquivos relacionados ao boot.
- `/boot/efi` → normalmente contém a ESP em sistemas UEFI.
- `rescue.target` → recuperação.
- `emergency.target` → recuperação mínima.

### Fluxo de diagnóstico

    Boot falhou
        ↓
    Onde parou?
        ↓
    Kernel?
        ↓
    initramfs?
        ↓
    systemd?
        ↓
    Serviço?
        ↓
    Sistema de arquivos?
        ↓
    GRUB / configuração / hardware

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
