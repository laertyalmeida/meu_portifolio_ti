# 01 — Arquitetura do Sistema

## 06 — /proc e /sys

### `/proc` — Process Information — Informações de Processos

**`/proc` — Process Information — Informações de Processos** é um **Virtual Filesystem — Sistema de Arquivos Virtual** fornecido pelo kernel Linux.

Ele não funciona como um diretório comum armazenado no disco. Seu conteúdo é criado e atualizado pelo kernel.

O `/proc` fornece informações sobre:

- Processos
- CPU
- Memória
- Kernel
- Hardware
- Parâmetros do sistema

---

### Processos no `/proc`

Cada processo possui normalmente um diretório identificado pelo seu **PID — Process ID — Identificador de Processo**.

Exemplo:

    /proc/1

    /proc/1234

O número representa o PID do processo.

Para consultar informações de um processo:

    cat /proc/1234/status

**status — estado** → mostra informações sobre o processo.

---

### `/proc/cpuinfo`

    cat /proc/cpuinfo

**`/proc/cpuinfo` — informações da CPU**

Mostra informações sobre os processadores disponíveis no sistema.

---

### `/proc/meminfo`

    cat /proc/meminfo

**`/proc/meminfo` — informações da memória**

Mostra informações sobre RAM e Swap.

---

### `/proc/cmdline`

    cat /proc/cmdline

**`/proc/cmdline` — linha de comandos**

Mostra os parâmetros passados ao kernel durante a inicialização.

---

### `/proc/version`

    cat /proc/version

Mostra informações sobre a versão do kernel Linux.

---

## `/sys` — System — Sistema

**`/sys` — System — Sistema** é outro **Virtual Filesystem — Sistema de Arquivos Virtual** utilizado pelo kernel.

Ele é baseado no **sysfs — System Filesystem — Sistema de Arquivos do Sistema**.

O `/sys` fornece informações sobre:

- Hardware
- Dispositivos
- Drivers
- Barramentos
- Kernel

---

### Estrutura do `/sys`

Alguns diretórios importantes:

    /sys/class

**class — classe**

Organiza dispositivos por classes, como rede, armazenamento e entrada.

    /sys/block

**block — bloco**

Contém informações sobre dispositivos de bloco.

    /sys/bus

**bus — barramento**

Contém informações sobre os barramentos e dispositivos conectados a eles.

    /sys/devices

**devices — dispositivos**

Contém a representação dos dispositivos detectados pelo kernel.

---

### Verificar dispositivos

Para listar dispositivos de bloco:

    ls /sys/block

**ls — list — listar**

Para visualizar informações sobre dispositivos PCI:

    ls /sys/bus/pci/devices

**pci — Peripheral Component Interconnect — Interconexão de Componentes Periféricos**

---

### `/proc` × `/sys`

| `/proc` | `/sys` |
|---|---|
| Informações do kernel e processos | Informações de hardware e dispositivos |
| Processos | Dispositivos |
| CPU e memória | Drivers |
| Parâmetros do kernel | Barramentos |
| `/proc/1234` | `/sys/devices` |

---

### Comandos úteis

**cat — concatenate — concatenar/exibir conteúdo**

    cat /proc/cpuinfo

**ls — list — listar**

    ls /sys/class

**grep — Global Regular Expression Print — localizar linhas correspondentes a um padrão**

    grep MemTotal /proc/meminfo

**`MemTotal` — memória total**

---

## Resumo LPIC-1

- `/proc` → **Process Information — Informações de Processos**.
- `/proc` → sistema de arquivos virtual fornecido pelo kernel.
- `/proc/PID` → informações relacionadas a um processo.
- `/proc/cpuinfo` → informações da CPU.
- `/proc/meminfo` → informações da memória.
- `/proc/cmdline` → parâmetros passados ao kernel no boot.
- `/proc/version` → informações sobre a versão do kernel.
- `/sys` → **System — Sistema**.
- **sysfs — System Filesystem — Sistema de Arquivos do Sistema**.
- `/sys/class` → dispositivos organizados por classe.
- `/sys/block` → dispositivos de bloco.
- `/sys/bus` → informações sobre barramentos.
- `/sys/devices` → representação dos dispositivos.
- `cat` → **concatenate — concatenar/exibir conteúdo**.
- `ls` → **list — listar**.
- `grep` → **Global Regular Expression Print — localizar linhas correspondentes a um padrão**.

**Memorização:**

`/proc` → **processos + informações do kernel**

`/sys` → **hardware + dispositivos + drivers**

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
