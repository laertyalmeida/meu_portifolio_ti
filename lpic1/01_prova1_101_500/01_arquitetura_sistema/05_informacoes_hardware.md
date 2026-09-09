# 01 — Arquitetura do Sistema

## 05 — Informações de Hardware

### Hardware — Equipamento físico

**Hardware — Equipamento físico** são os componentes físicos do computador, como:

- CPU — processador
- RAM — memória
- Discos
- Placa de vídeo
- Placa de rede
- Dispositivos USB
- Placa-mãe

O Linux disponibiliza diversas ferramentas para identificar e consultar essas informações.

---

### lscpu — List CPU — Listar informações da CPU

    lscpu

Exibe informações sobre o processador.

Principais informações:

- Architecture — Arquitetura
- CPU(s) — CPUs lógicas
- Core(s) — Núcleos
- Thread(s) — Threads
- Model name — Nome do modelo

---

### lsblk — List Block Devices — Listar dispositivos de bloco

    lsblk

Mostra discos, partições e dispositivos de armazenamento.

Para mostrar sistemas de arquivos:

    lsblk -f

`-f` — **filesystem — sistema de arquivos**

---

### lspci — List PCI — Listar dispositivos PCI

    lspci

Lista dispositivos conectados ao barramento PCI/PCIe.

Exemplos:

- Placa de vídeo
- Placa de rede
- Controladoras
- Controladores USB

Para mostrar informações detalhadas:

    lspci -v

`-v` — **verbose — detalhado**

---

### lsusb — List USB — Listar dispositivos USB

    lsusb

Lista dispositivos conectados através de USB.

Para visualizar a estrutura:

    lsusb -t

`-t` — **tree — árvore**

---

### dmidecode — DMI Decode — Decodificar DMI

    sudo dmidecode

**DMI — Desktop Management Interface — Interface de Gerenciamento do Computador**

O `dmidecode` consulta informações fornecidas pelo firmware através das tabelas **DMI/SMBIOS**.

Pode mostrar informações sobre:

- Fabricante do computador
- Modelo
- Placa-mãe
- Memória
- BIOS/UEFI
- Processador

---

### /proc/cpuinfo

**`/proc` — processes — processos**

Sistema de arquivos virtual que fornece informações do kernel.

    cat /proc/cpuinfo

**`/proc/cpuinfo`** → informações sobre os processadores.

**cat — concatenate — concatenar/exibir conteúdo**

---

### /proc/meminfo

    cat /proc/meminfo

Mostra informações sobre a memória do sistema.

Exemplos de informações:

- MemTotal — memória total
- MemFree — memória livre
- MemAvailable — memória disponível
- SwapTotal — swap total
- SwapFree — swap livre

---

### /sys — System — Sistema

    /sys

**`/sys` — system — sistema** é um sistema de arquivos virtual utilizado pelo kernel para disponibilizar informações sobre:

- Hardware
- Dispositivos
- Drivers
- Barramentos

---

### dmesg — Diagnostic Messages — Mensagens de Diagnóstico

    dmesg

Exibe mensagens do kernel, incluindo informações sobre a detecção e inicialização de hardware.

Para procurar informações específicas:

    dmesg | grep -i usb

**grep — Global Regular Expression Print — localizar linhas correspondentes a um padrão**

`-i` — **ignore case — ignorar maiúsculas e minúsculas**

---

### Hardware Detection — Detecção de Hardware

O Linux detecta diversos dispositivos durante a inicialização.

Uma forma de observar essas mensagens é:

    dmesg

Também podemos consultar dispositivos específicos:

    lspci
    lsusb
    lsblk
    lscpu

---

## Resumo LPIC-1

- **Hardware** → componentes físicos do computador.
- `lscpu` → **List CPU — Listar informações da CPU**.
- `lsblk` → **List Block Devices — Listar dispositivos de bloco**.
- `lspci` → **List PCI — Listar dispositivos PCI**.
- `lsusb` → **List USB — Listar dispositivos USB**.
- `dmidecode` → **DMI Decode — Decodificar informações DMI**.
- `dmesg` → **Diagnostic Messages — Mensagens de Diagnóstico**.
- `/proc` → **processes — processos**; fornece informações do kernel.
- `/proc/cpuinfo` → informações dos processadores.
- `/proc/meminfo` → informações da memória.
- `/sys` → **system — sistema**; informações sobre hardware, dispositivos e drivers.
- `-f` → **filesystem — sistema de arquivos**.
- `-v` → **verbose — detalhado**.
- `-t` → **tree — árvore**.
- `-i` → **ignore case — ignorar maiúsculas e minúsculas**.
- `sudo` → **Superuser Do — executar como superusuário**.
- `cat` → **concatenate — concatenar/exibir conteúdo**.

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
