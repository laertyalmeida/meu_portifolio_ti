# 01 — Arquitetura do Sistema

## 04 — Barramentos e Dispositivos

### Bus — Barramento

**Bus — Barramento** é o meio de comunicação utilizado pelos componentes do computador para trocar informações.

Ele permite a comunicação entre:

- CPU — processador
- Memory — memória
- Devices — dispositivos
- Peripheral — periféricos

---

### PCI — Peripheral Component Interconnect

**PCI — Interconexão de Componentes Periféricos** é uma tecnologia utilizada para conectar dispositivos internos ao computador.

### PCIe — PCI Express

**PCIe — PCI Express** é a evolução do PCI e oferece maior velocidade de comunicação.

Exemplos:

- Placa de vídeo
- Placa de rede
- Controladoras
- SSD NVMe

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

- HDD — Hard Disk Drive — Unidade de Disco Rígido
- SSD — Solid State Drive — Unidade de Estado Sólido
- Unidade óptica

Um disco SATA pode aparecer no Linux como:

    /dev/sda

---

### NVMe — Non-Volatile Memory Express

**NVMe — Memória Não Volátil Expressa** é um protocolo de armazenamento desenvolvido para aproveitar interfaces de alta velocidade, normalmente através de PCIe.

Um dispositivo NVMe pode aparecer como:

    /dev/nvme0n1

---

### Dispositivos no Linux

O Linux representa muitos dispositivos através de arquivos especiais no diretório:

    /dev

**`/dev` — devices — dispositivos**

Exemplos:

    /dev/sda
    /dev/sda1
    /dev/nvme0n1

---

### Character Device — Dispositivo de Caractere

**Character Device — Dispositivo de Caractere** trabalha com dados como um fluxo de caracteres.

Exemplo:

    /dev/tty

No `ls -l`, é identificado por:

    c

`c` — **character — caractere**

---

### Block Device — Dispositivo de Bloco

**Block Device — Dispositivo de Bloco** trabalha com dados organizados em blocos.

É utilizado principalmente para armazenamento.

Exemplo:

    /dev/sda

No `ls -l`, é identificado por:

    b

`b` — **block — bloco**

---

### Comandos importantes

**lspci — List PCI — Listar dispositivos PCI**

    lspci

`-k` — **kernel driver — driver do kernel**

    lspci -k

Mostra o driver do kernel utilizado pelo dispositivo.

---

**lsusb — List USB — Listar dispositivos USB**

    lsusb

`-t` — **tree — árvore**

    lsusb -t

Mostra os dispositivos USB em formato de árvore.

---

**lsblk — List Block Devices — Listar Dispositivos de Bloco**

    lsblk

`-f` — **filesystem — sistema de arquivos**

    lsblk -f

Mostra informações sobre sistemas de arquivos.

---

**dmesg — Diagnostic Messages — Mensagens de Diagnóstico**

    dmesg

Exibe mensagens do kernel, incluindo eventos relacionados à detecção de hardware.

---

### `/sys` — System — Sistema

O diretório:

    /sys

é um sistema de arquivos virtual utilizado pelo kernel para disponibilizar informações sobre:

- Hardware
- Dispositivos
- Drivers
- Barramentos

---

## Resumo LPIC-1

- **Bus — Barramento** → meio de comunicação entre componentes.
- **PCI — Peripheral Component Interconnect** → Interconexão de Componentes Periféricos.
- **PCIe — PCI Express** → evolução do PCI.
- **USB — Universal Serial Bus** → Barramento Serial Universal.
- **SATA — Serial ATA** → interface para armazenamento.
- **NVMe — Non-Volatile Memory Express** → protocolo de armazenamento.
- **Character Device** → dispositivo de caractere.
- **Block Device** → dispositivo de bloco.
- `c` → **character — caractere**.
- `b` → **block — bloco**.
- `/dev` → **devices — dispositivos**.
- `/sys` → **system — sistema**.
- `lspci` → **List PCI — Listar dispositivos PCI**.
- `lsusb` → **List USB — Listar dispositivos USB**.
- `lsblk` → **List Block Devices — Listar Dispositivos de Bloco**.
- `dmesg` → **Diagnostic Messages — Mensagens de Diagnóstico**.
- `-k` → **kernel driver — driver do kernel**.
- `-t` → **tree — árvore**.
- `-f` → **filesystem — sistema de arquivos**.

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
