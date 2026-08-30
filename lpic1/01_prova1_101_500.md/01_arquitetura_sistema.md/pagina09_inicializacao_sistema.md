# 📖 PÁGINA 9 — INICIALIZAÇÃO DO SISTEMA

# 🧠 1. O QUE É BOOT?

**Boot** significa:

**inicialização**

É o processo que acontece desde o momento em que o computador é ligado até o sistema operacional estar carregado e pronto para uso.

De forma simplificada:

**Ligar → Firmware → Bootloader → Kernel → Init → Serviços → Sistema pronto**

---

# ⚙️ 2. PRIMEIRA ETAPA — FIRMWARE

Quando o computador é ligado, o firmware é executado.

Pode ser:

**BIOS**

ou:

**UEFI**

O firmware realiza a inicialização básica do hardware e procura um dispositivo de boot.

Fluxo:

**Computador ligado**

↓

**BIOS/UEFI**

↓

**Dispositivo de boot**

---

# 🥾 3. SEGUNDA ETAPA — BOOTLOADER

Depois do firmware, entra em ação o **bootloader**.

**Bootloader**

→ programa responsável por iniciar o sistema operacional.

No Linux, um bootloader muito comum é:

**GRUB**

**GRUB = GRand Unified Bootloader**

O GRUB localiza e carrega o kernel Linux.

Fluxo:

**BIOS/UEFI → GRUB → Kernel**

---

# 🧠 4. TERCEIRA ETAPA — KERNEL

O **kernel** é o núcleo do sistema operacional.

Depois de carregado, ele começa a assumir o controle do computador.

O kernel é responsável por gerenciar recursos como:

- CPU
- Memória
- Dispositivos
- Processos
- Sistema de arquivos

Fluxo:

**Firmware → Bootloader → Kernel**

---

# 📦 5. INITRAMFS

Durante o boot, o kernel pode utilizar um:

**initramfs**

**initramfs = initial RAM filesystem**

Tradução:

**sistema de arquivos RAM inicial**

É um sistema de arquivos temporário carregado na memória durante a inicialização.

Ele fornece ferramentas e módulos necessários para que o kernel consiga acessar o sistema de arquivos raiz.

Por exemplo, pode ser necessário carregar um driver antes de o kernel conseguir acessar o disco onde está o sistema `/`.

Fluxo simplificado:

**Bootloader → Kernel + initramfs → Sistema de arquivos raiz**

---

# 🚀 6. INIT

Depois que o kernel é inicializado, ele inicia o primeiro processo do espaço de usuário.

Tradicionalmente, esse processo é chamado de:

**init**

O primeiro processo recebe normalmente o:

**PID 1**

**PID = Process ID**

Tradução:

**Identificador do processo**

No Linux moderno, o PID 1 normalmente é:

**systemd**

Portanto:

**Kernel → PID 1 → systemd → Serviços**

---

# ⚙️ 7. SYSTEMD

**systemd** é um sistema de inicialização e gerenciamento de serviços utilizado por muitas distribuições Linux.

Ele normalmente ocupa:

**PID 1**

Depois que o kernel inicia o espaço de usuário:

**systemd**

começa a iniciar e gerenciar serviços.

Exemplos:

- Rede
- SSH
- Login
- Serviços do sistema

---

# 🔄 8. FLUXO COMPLETO

Memorize esta sequência:

**1. Computador ligado**

↓

**2. BIOS/UEFI**

↓

**3. Hardware inicializado**

↓

**4. Bootloader**

↓

**5. GRUB**

↓

**6. Kernel Linux**

↓

**7. initramfs**

↓

**8. PID 1**

↓

**9. systemd**

↓

**10. Serviços**

↓

**11. Sistema pronto**

---

# 🔍 9. COMO IDENTIFICAR O PID 1

O comando:

`ps`

é utilizado para visualizar processos.

### Tradução

**ps = process status**

Tradução:

**status dos processos**

Para visualizar o processo de PID 1:

`ps -p 1`

### `-p`

**process ID**

→ identifica um processo pelo PID.

Exemplo:

`PID TTY          TIME CMD`

`1   ?            ...  systemd`

Isso mostra que o `systemd` está executando como PID 1.

---

# 🧠 10. `ps -p 1 -o`

Podemos escolher quais informações serão exibidas:

`ps -p 1 -o pid,comm`

### `-o`

**output = saída**

Permite escolher as colunas exibidas.

### `pid`

**Process ID**

→ identificador do processo.

### `comm`

**command = comando**

→ nome do comando/processo.

Exemplo:

`PID COMMAND`

`1   systemd`

---

# 📜 11. `journalctl`

Depois que o sistema iniciou, podemos consultar mensagens do sistema com:

`journalctl`

### Tradução

**journal**

→ diário/registro.

**ctl**

→ control → controle.

Portanto:

**journalctl**

→ ferramenta para consultar o journal do systemd.

Para visualizar mensagens do boot atual:

`journalctl -b`

### `-b`

**boot = inicialização**

Mostra mensagens relacionadas ao boot.

---

# 🔎 12. `journalctl -b -0`

A opção:

`-b`

seleciona um boot.

`-0`

representa o boot atual.

Comando:

`journalctl -b -0`

→ mostra as mensagens do boot atual.

Um boot anterior pode ser consultado com:

`journalctl -b -1`

Onde:

`-1`

→ boot anterior.

---

# 🛠️ 13. `systemctl`

O comando:

`systemctl`

é utilizado para controlar e consultar o systemd.

### Tradução

**system**

→ sistema.

**ctl**

→ control → controle.

Portanto:

**systemctl → system control → controle do sistema**

Para verificar o estado geral:

`systemctl status`

Para verificar um serviço específico:

`systemctl status ssh`

---

# 🎯 14. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que significa boot.
- Que boot significa inicialização.
- O papel do BIOS/UEFI no início do boot.
- O que é bootloader.
- O que é GRUB.
- O papel do GRUB.
- O que é o kernel.
- O papel do kernel durante a inicialização.
- O que é initramfs.
- O significado de `initramfs`.
- Por que o initramfs pode ser necessário.
- O que é o processo `init`.
- Que o primeiro processo possui PID 1.
- Que sistemas Linux modernos normalmente utilizam `systemd` como PID 1.
- A sequência geral de inicialização.
- Usar `ps -p 1`.
- Saber que `ps` significa **process status**.
- Saber que `-p` seleciona um PID.
- Usar `journalctl -b`.
- Saber que `-b` significa **boot**.
- Conhecer `systemctl`.
- Saber que `ctl` significa **control**.

---

# 🧠 RESUMO

**BOOT**

→ inicialização do sistema.

**BIOS/UEFI**

→ inicializa o hardware e inicia o processo de boot.

**BOOTLOADER**

→ inicia o sistema operacional.

**GRUB**

→ bootloader muito utilizado no Linux.

**KERNEL**

→ núcleo do sistema operacional.

→ assume o controle dos recursos do computador.

**INITRAMFS**

→ sistema de arquivos inicial carregado na RAM.

→ auxilia o kernel durante o início do boot.

**PID 1**

→ primeiro processo do espaço de usuário.

**SYSTEMD**

→ normalmente ocupa o PID 1 em sistemas Linux modernos.

→ gerencia a inicialização e os serviços.

**ps**

→ process status → status dos processos.

**ps -p 1**

→ mostra o processo com PID 1.

**journalctl**

→ consulta o journal do systemd.

**journalctl -b**

→ mostra mensagens do boot.

**systemctl**

→ system control → controle do systemd.

---

# 🔄 FLUXO PARA MEMORIZAR

**LIGAR**

↓

**BIOS / UEFI**

↓

**HARDWARE**

↓

**BOOTLOADER / GRUB**

↓

**KERNEL**

↓

**INITRAMFS**

↓

**PID 1**

↓

**SYSTEMD**

↓

**SERVIÇOS**

↓

**SISTEMA PRONTO**

# ✅ FIM DA PÁGINA 9
