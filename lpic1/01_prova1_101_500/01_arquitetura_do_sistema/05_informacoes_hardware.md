Informações de Hardware

O Linux possui vários comandos para descobrir informações sobre o hardware do computador.

Esses comandos são muito úteis para identificar dispositivos e investigar problemas.

---

"lscpu" — List CPU (Listar CPU)

Mostra informações sobre o processador.

lscpu

Pode mostrar:

- Modelo da CPU
- Arquitetura
- Quantidade de cores
- Quantidade de threads
- Fabricante

"-e" — Extended (Estendido)

Mostra informações sobre os processadores lógicos.

lscpu -e

---

"lsmem" — List Memory (Listar Memória)

Mostra informações sobre a memória RAM.

lsmem

---

"lsblk" — List Block Devices (Listar Dispositivos de Bloco)

Mostra discos e partições.

lsblk

Exemplo:

NAME   SIZE TYPE
sda    500G disk
├─sda1 100G part
└─sda2 400G part

---

"lspci" — List PCI (Listar PCI)

Mostra dispositivos conectados ao PCI/PCIe.

lspci

Por exemplo:

VGA controller
Ethernet controller
Audio controller

---

"lsusb" — List USB (Listar USB)

Mostra dispositivos USB.

lsusb

---

"lshw" — List Hardware (Listar Hardware)

Mostra informações detalhadas sobre o hardware.

sudo lshw

"-short" — Short (Resumido)

Mostra uma visão mais curta das informações.

sudo lshw -short

---

"/proc/cpuinfo" — Informações da CPU

O arquivo "/proc/cpuinfo" contém informações sobre os processadores disponíveis para o Linux.

cat /proc/cpuinfo

---

"/proc/meminfo" — Informações da Memória

O arquivo "/proc/meminfo" contém informações sobre a memória do sistema.

cat /proc/meminfo

---

LPIC-1 — O que saber

Comando/arquivo| Para que serve
"lscpu"| Informações da CPU
"lsmem"| Informações da RAM
"lsblk"| Discos e partições
"lspci"| Dispositivos PCI/PCIe
"lsusb"| Dispositivos USB
"lshw"| Informações do hardware
"/proc/cpuinfo"| Informações da CPU
"/proc/meminfo"| Informações da memória

Flags importantes

- "-e" — Extended (Estendido) → usado pelo "lscpu" para mostrar informações dos processadores lógicos.
- "-short" — Short (Resumido) → usado pelo "lshw" para exibir informações resumidas.

---

Resumo

CPU      → lscpu
RAM      → lsmem
Discos   → lsblk
PCI/PCIe → lspci
USB      → lsusb
Hardware → lshw

/proc/cpuinfo → CPU
/proc/meminfo → Memória
