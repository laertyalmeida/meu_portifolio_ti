# 09 — Boot e Inicialização
## 09 — Troubleshooting de Boot

### O que é Troubleshooting?

**Troubleshooting — Solução de problemas**

É o processo de identificar e corrigir problemas.

Quando o Linux não inicia corretamente, devemos descobrir **em qual etapa do boot ocorreu a falha**.

---

# 1. Sequência do Boot

A sequência básica é:

    Firmware
       ↓
    Bootloader
       ↓
    Kernel
       ↓
    initramfs
       ↓
    systemd / init
       ↓
    Services
       ↓
    Login

Cada etapa pode apresentar problemas diferentes.

---

# 2. Problema no Firmware

**Firmware — Firmware**

Pode ser:

- BIOS;
- UEFI.

Problemas comuns:

- disco não detectado;
- ordem de boot incorreta;
- configuração de UEFI/Legacy;
- dispositivo de boot incorreto.

### Verificar dispositivos

    lsblk

**lsblk — list block devices (listar dispositivos de bloco)**

---

# 3. Problema no Bootloader

**Bootloader — Carregador de inicialização**

Em muitos sistemas Linux, o bootloader é o **GRUB**.

Problemas comuns:

- GRUB não aparece;
- configuração incorreta;
- entrada de kernel incorreta;
- partição `/boot` com problemas.

Quando o GRUB funciona, normalmente ainda é possível selecionar outro kernel ou uma opção de recuperação, dependendo da configuração.

---

# 4. Problema no Kernel

Se o kernel não consegue iniciar corretamente, podem aparecer:

- kernel panic;
- mensagens de erro;
- travamento durante a inicialização;
- problemas com drivers.

Ver a versão do kernel quando o sistema consegue iniciar:

    uname -r

**-r — release (versão/release)**

---

# 5. initramfs

**initramfs — Initial RAM Filesystem (Sistema de arquivos inicial em RAM)**

É carregado antes do sistema de arquivos raiz.

Ele contém ferramentas e módulos necessários para preparar o sistema para montar a raiz.

Problemas podem ocorrer quando:

- o driver necessário não está disponível;
- a configuração está incorreta;
- o sistema de arquivos raiz não pode ser encontrado.

Mensagens como:

    unable to mount root filesystem

podem indicar problemas nessa etapa.

---

# 6. Problema no Root Filesystem

**Root Filesystem — Sistema de arquivos raiz**

O kernel precisa encontrar e montar o `/`.

Problemas comuns:

- UUID incorreto;
- dispositivo inexistente;
- sistema de arquivos corrompido;
- entrada incorreta no `/etc/fstab`.

Ver os dispositivos e UUIDs:

    lsblk -f

    blkid

---

# 7. Problemas no /etc/fstab

O arquivo:

    /etc/fstab

define sistemas de arquivos que devem ser montados.

Uma configuração incorreta pode impedir ou atrasar o boot.

Exemplo:

    UUID=xxxx-xxxx /data ext4 defaults 0 2

Verificar o arquivo:

    cat /etc/fstab

Depois que o sistema estiver funcionando, testar as entradas:

    sudo mount -a

**-a — all (todos)**

Se houver erro, o terminal normalmente mostrará qual entrada está causando o problema.

---

# 8. Problemas no systemd

Se o kernel iniciou, mas algum serviço falhou, podemos investigar com:

    systemctl --failed

**--failed — falhas**

Ver o estado de um serviço:

    systemctl status nome-do-servico

---

# 9. Consultar os Logs

O `journalctl` é uma das ferramentas mais importantes para troubleshooting.

Ver logs do boot atual:

    journalctl -b

Ver somente erros:

    journalctl -b -p err

Ver mensagens do kernel:

    journalctl -b -k

**-k — kernel (núcleo)**

---

# 10. Ver Boots Anteriores

Listar boots registrados:

    journalctl --list-boots

Consultar o boot anterior:

    journalctl -b -1

Isso é especialmente útil quando:

- o sistema iniciou agora;
- o problema aconteceu no boot anterior;
- queremos comparar os registros.

---

# 11. Ver o Tempo de Boot

O `systemd-analyze` ajuda a investigar o processo de inicialização.

    systemd-analyze

Mostra informações sobre o tempo gasto no boot.

Para identificar serviços que demoraram mais:

    systemd-analyze blame

**blame — apontar responsáveis**

Exemplo de interpretação:

    8.2s serviço-A.service
    3.7s serviço-B.service
    1.4s serviço-C.service

Isso ajuda a encontrar serviços lentos.

---

# 12. Kernel Messages

O comando:

    dmesg

mostra mensagens do kernel.

Para procurar erros:

    dmesg | grep -i error

**grep -i**

**-i — ignore case (ignorar maiúsculas/minúsculas)**

Outro exemplo:

    dmesg | grep -i fail

---

# 13. Quando o sistema não inicia

Uma estratégia de diagnóstico:

### 1 — Firmware

Verificar:

    BIOS / UEFI

### 2 — Bootloader

Verificar:

    GRUB

### 3 — Kernel

Procurar:

    kernel panic
    driver errors

### 4 — initramfs

Verificar:

    root filesystem
    drivers
    storage

### 5 — Root filesystem

Verificar:

    UUID
    filesystem
    /etc/fstab

### 6 — systemd

Verificar:

    systemctl --failed

### 7 — Logs

Consultar:

    journalctl -b -p err

---

# 14. Rescue Mode

**Rescue Mode — Modo de recuperação**

O `systemd` possui:

    rescue.target

É utilizado para manutenção e diagnóstico.

Pode ser ativado:

    systemctl isolate rescue.target

Em uma máquina que não inicia normalmente, também pode ser possível selecionar uma opção de recuperação no bootloader, dependendo da configuração do sistema.

---

# 15. Emergency Mode

**Emergency Mode — Modo de emergência**

O target:

    emergency.target

fornece um ambiente ainda mais mínimo para recuperação.

É utilizado quando o sistema precisa de intervenção antes de conseguir iniciar normalmente.

---

# 16. Checklist de Troubleshooting

Quando o Linux apresenta problemas no boot:

    1. O firmware detecta o disco?
           ↓
    2. O GRUB inicia?
           ↓
    3. O kernel carrega?
           ↓
    4. O initramfs encontra a raiz?
           ↓
    5. O / é montado?
           ↓
    6. O systemd inicia?
           ↓
    7. Existem serviços com falha?
           ↓
    8. O journal mostra o erro?

---

# 🔑 Comandos essenciais

| Comando | Função |
|---|---|
| `lsblk` | Listar dispositivos |
| `lsblk -f` | Mostrar sistemas de arquivos |
| `blkid` | Mostrar UUIDs e tipos |
| `cat /etc/fstab` | Ver configurações de montagem |
| `mount -a` | Tentar montar entradas do `fstab` |
| `systemctl --failed` | Ver units com falha |
| `systemctl status` | Ver estado de serviço |
| `journalctl -b` | Logs do boot atual |
| `journalctl -b -p err` | Erros do boot |
| `journalctl -b -k` | Logs do kernel no boot |
| `journalctl --list-boots` | Listar boots |
| `dmesg` | Mensagens do kernel |
| `systemd-analyze` | Analisar boot |
| `systemd-analyze blame` | Identificar serviços demorados |

---

## 🎯 LPIC-1 — O que memorizar

**GRUB** → carrega o kernel.

**Kernel** → núcleo do sistema operacional.

**initramfs** → prepara o ambiente inicial para encontrar/montar a raiz.

**systemd** → processo de inicialização e gerenciamento de serviços.

**journalctl** → consulta logs.

**dmesg** → consulta mensagens do kernel.

**systemctl --failed** → procura unidades que falharam.

**/etc/fstab** → configura sistemas de arquivos para montagem.

**lsblk -f / blkid** → ajudam a verificar dispositivos, UUIDs e sistemas de arquivos.

---

## 🧠 Regra prática

Quando o sistema **não chega ao login**, pense:

    Firmware
        ↓
    GRUB
        ↓
    Kernel
        ↓
    initramfs
        ↓
    /
        ↓
    systemd
        ↓
    services
        ↓
    login

E use:

    journalctl
    dmesg
    systemctl
    lsblk
    blkid

para descobrir **onde a inicialização parou**.

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
