BIOS e UEFI

BIOS — Basic Input/Output System (Sistema Básico de Entrada/Saída)

A BIOS é um programa gravado na placa-mãe.

Quando você liga o computador, ela é uma das primeiras coisas a funcionar.

Ela verifica o hardware básico e procura onde está o sistema que deve ser iniciado.

---

UEFI — Unified Extensible Firmware Interface (Interface de Firmware Extensível Unificada)

O UEFI é o padrão mais moderno que substituiu a BIOS tradicional.

Ele também inicia quando o computador é ligado, verifica o hardware e procura o sistema para iniciar.

O UEFI possui recursos mais modernos, como:

- Suporte a GPT
- Secure Boot
- Suporte a discos grandes
- Inicialização mais moderna

---

BIOS x UEFI

BIOS| UEFI
Mais antigo| Mais moderno
Normalmente usa MBR| Pode usar GPT
Mais limitado| Mais recursos
Boot tradicional| Boot moderno
Sem Secure Boot tradicional| Pode usar Secure Boot

---

Boot — Inicialização

Boot é o processo de iniciar o computador e carregar o sistema operacional.

No Linux, podemos simplificar assim:

BIOS / UEFI
     ↓
GRUB
     ↓
Kernel Linux
     ↓
Systemd
     ↓
Linux funcionando

Não precisamos estudar GRUB, Kernel e Systemd agora. Cada um terá sua própria página.

---

Firmware — Firmware

Firmware é o software que fica gravado no equipamento e controla seu funcionamento básico.

BIOS e UEFI são exemplos de firmware.

---

No Linux

Podemos verificar se o Linux foi iniciado usando UEFI:

ls /sys/firmware/efi

Se o diretório existir, o Linux provavelmente foi iniciado em UEFI.

---

LPIC-1 — O que saber

- BIOS é o padrão mais antigo.
- UEFI é o padrão moderno.
- UEFI pode usar GPT.
- UEFI pode usar Secure Boot.
- BIOS/UEFI participa do início do processo de boot.
- Depois do firmware, o bootloader inicia o carregamento do Linux.

---

Resumo

BIOS → antigo
UEFI → moderno

UEFI → GPT
UEFI → Secure Boot

BIOS / UEFI
     ↓
   GRUB
     ↓
  Kernel
     ↓
 Systemd
     ↓
  Linux
