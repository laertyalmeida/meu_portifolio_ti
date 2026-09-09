# 01 — Arquitetura do Sistema

## 02 — Dispositivos e Periféricos

### Devices — Dispositivos

No Linux, os dispositivos são representados principalmente por arquivos especiais dentro do diretório:

    /dev

**`/dev` — devices — dispositivos**

Esse modelo permite que o sistema e os programas interajam com o hardware através de uma interface de arquivos.

---

### Character Device — Dispositivo de Caractere

**Character Device — Dispositivo de Caractere** trabalha com dados como um fluxo contínuo de caracteres.

Exemplos:

    /dev/tty
    /dev/console

No `ls -l`, é identificado pela letra:

    c

`c` — **character — caractere**

---

### Block Device — Dispositivo de Bloco

**Block Device — Dispositivo de Bloco** trabalha com dados organizados em blocos.

É utilizado principalmente para dispositivos de armazenamento.

Exemplos:

    /dev/sda
    /dev/sda1
    /dev/nvme0n1

No `ls -l`, é identificado pela letra:

    b

`b` — **block — bloco**

---

### Dispositivos de armazenamento

Um disco SATA pode aparecer como:

    /dev/sda

Uma partição desse disco:

    /dev/sda1

Um dispositivo NVMe pode aparecer como:

    /dev/nvme0n1

Uma partição NVMe:

    /dev/nvme0n1p1

---

### PCI — Peripheral Component Interconnect

**PCI — Interconexão de Componentes Periféricos** é utilizado para conectar dispositivos internos ao computador.

**PCIe — PCI Express — PCI Express** é a evolução do PCI.

Exemplos:

- Placa de vídeo
- Placa de rede
- Controladoras
- Dispositivos NVMe

**lspci — List PCI — Listar dispositivos PCI**

    lspci

---

### USB — Universal Serial Bus

**USB — Barramento Serial Universal** é utilizado principalmente para conectar dispositivos externos.

Exemplos:

- Teclado
- Mouse
- Pen drive
- Webcam
- HD externo

**lsusb — List USB — Listar dispositivos USB**

    lsusb

---

### SATA — Serial ATA

**SATA — ATA Serial** é uma interface utilizada principalmente para conectar dispositivos de armazenamento.

Exemplos:

- HDD
- SSD SATA
- Unidade óptica

---

### NVMe — Non-Volatile Memory Express

**NVMe — Memória Não Volátil Expressa** é um protocolo desenvolvido para dispositivos de armazenamento de alta velocidade, normalmente utilizando PCIe.

---

### Comandos importantes

**lsblk — List Block Devices — Listar Dispositivos de Bloco**

    lsblk

`-f` — **filesystem — sistema de arquivos**

    lsblk -f

Mostra informações sobre discos, partições e sistemas de arquivos.

---

**lspci — List PCI — Listar dispositivos PCI**

    lspci

`-k` — **kernel driver — driver do kernel**

    lspci -k

Mostra o driver do kernel associado aos dispositivos.

---

**lsusb — List USB — Listar dispositivos USB**

    lsusb

`-t` — **tree — árvore**

    lsusb -t

Mostra os dispositivos USB em formato de árvore.

---

**dmesg — Diagnostic Messages — Mensagens de Diagnóstico**

    dmesg

Mostra mensagens do kernel, incluindo informações sobre dispositivos detectados.

---

### Diretórios importantes

**`/dev` — devices — dispositivos**  
Contém arquivos especiais que representam dispositivos.

**`/sys` — system — sistema**  
Sistema de arquivos virtual que disponibiliza informações sobre hardware, dispositivos, drivers e kernel.

**`/proc` — processes — processos**  
Sistema de arquivos virtual que disponibiliza informações sobre processos e informações do kernel.

---

## Resumo LPIC-1

- `/dev` → **devices — dispositivos**.
- **Character Device** → dispositivo de caractere.
- **Block Device** → dispositivo de bloco.
- `c` → **character — caractere**.
- `b` → **block — bloco**.
- `/dev/sda` → exemplo de disco SATA.
- `/dev/sda1` → exemplo de partição.
- `/dev/nvme0n1` → exemplo de dispositivo NVMe.
- **PCI — Peripheral Component Interconnect** → Interconexão de Componentes Periféricos.
- **USB — Universal Serial Bus** → Barramento Serial Universal.
- **SATA — Serial ATA** → interface para armazenamento.
- **NVMe — Non-Volatile Memory Express** → protocolo para armazenamento.
- `lspci` → **List PCI — Listar dispositivos PCI**.
- `lsusb` → **List USB — Listar dispositivos USB**.
- `lsblk` → **List Block Devices — Listar Dispositivos de Bloco**.
- `dmesg` → **Diagnostic Messages — Mensagens de Diagnóstico**.
- `-f` → **filesystem — sistema de arquivos**.
- `-k` → **kernel driver — driver do kernel**.
- `-t` → **tree — árvore**.
- `/sys` → **system — sistema**.
- `/proc` → **processes — processos**.

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
