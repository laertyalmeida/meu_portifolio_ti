# 📖 PÁGINA 14 — /SYS

# 🧠 1. O QUE É `/sys`?

`/sys` é um **sistema de arquivos virtual** fornecido pelo kernel Linux.

Ele disponibiliza informações sobre:

- Hardware
- Dispositivos
- Drivers
- Barramentos
- Classes de dispositivos
- Estado de componentes do sistema

Assim como `/proc`, o `/sys` não é simplesmente um conjunto de arquivos armazenados no disco.

As informações são fornecidas pelo kernel.

---

# ⚖️ 2. `/proc` x `/sys`

Os dois são sistemas de arquivos virtuais, mas possuem focos diferentes.

### `/proc`

Principalmente:

→ processos.

→ informações do kernel.

→ estado do sistema.

### `/sys`

Principalmente:

→ dispositivos.

→ hardware.

→ drivers.

→ barramentos.

Resumo:

**/proc → processos e informações do sistema**

**/sys → dispositivos e hardware**

---

# 🧩 3. SYSFS

O sistema de arquivos utilizado em `/sys` é conhecido como:

**sysfs**

O sysfs permite ao kernel expor informações sobre dispositivos e sua estrutura.

Normalmente está montado em:

`/sys`

Podemos verificar com:

`mount | grep sysfs`

---

# 🔌 4. `/sys/class/`

O diretório:

`/sys/class/`

organiza dispositivos por **classes**.

Exemplos:

`/sys/class/net/`

→ interfaces de rede.

`/sys/class/block/`

→ dispositivos de bloco.

`/sys/class/input/`

→ dispositivos de entrada.

---

# 🌐 5. `/sys/class/net/`

O diretório:

`/sys/class/net/`

contém informações sobre as interfaces de rede.

Podemos listar:

`ls /sys/class/net/`

Exemplo:

`lo`

`eth0`

`wlan0`

Os nomes dependem do sistema.

### Tradução

**net = network → rede**

Portanto:

`/sys/class/net/`

→ dispositivos classificados como interfaces de rede.

---

# 💾 6. `/sys/class/block/`

O diretório:

`/sys/class/block/`

contém informações sobre dispositivos de bloco.

Exemplos:

`/sys/class/block/sda`

`/sys/class/block/nvme0n1`

Dispositivos de bloco incluem:

- HDD
- SSD
- Dispositivos NVMe
- Partições

---

# 🔌 7. `/sys/bus/`

O diretório:

`/sys/bus/`

organiza informações relacionadas aos barramentos.

Exemplos:

`/sys/bus/pci/`

→ barramento PCI.

`/sys/bus/usb/`

→ barramento USB.

Dentro dessas estruturas podemos encontrar informações sobre dispositivos e drivers.

---

# 🧠 8. `/sys/bus/pci/`

O diretório:

`/sys/bus/pci/`

contém informações relacionadas ao barramento PCI.

Podemos listar:

`ls /sys/bus/pci/`

Também podemos consultar:

`/sys/bus/pci/devices/`

→ dispositivos PCI.

E:

`/sys/bus/pci/drivers/`

→ drivers associados ao barramento PCI.

---

# 🔌 9. `/sys/bus/usb/`

O diretório:

`/sys/bus/usb/`

contém informações relacionadas ao barramento USB.

Podemos consultar:

`ls /sys/bus/usb/`

E:

`/sys/bus/usb/devices/`

→ dispositivos USB.

---

# 🔍 10. `/sys/devices/`

O diretório:

`/sys/devices/`

apresenta a estrutura dos dispositivos conforme a organização utilizada pelo kernel.

É uma das principais áreas do sysfs para representar a hierarquia de dispositivos.

---

# 🖥️ 11. `/sys/firmware/`

O diretório:

`/sys/firmware/`

contém informações relacionadas ao firmware.

Em sistemas inicializados em modo UEFI, podemos encontrar:

`/sys/firmware/efi/`

A existência dessa estrutura pode indicar que o sistema foi inicializado em modo UEFI.

---

# 🔎 12. `udevadm`

O comando:

`udevadm`

é utilizado para consultar e gerenciar informações relacionadas ao **udev**.

**udev**

→ sistema responsável pelo gerenciamento dinâmico de dispositivos no Linux.

Exemplo:

`udevadm info`

Pode consultar informações sobre dispositivos.

Um uso comum:

`udevadm info --query=all --name=/dev/sda`

### Tradução

**info**

→ information → informação.

**query**

→ consulta.

**all**

→ todos.

**name**

→ nome.

---

# 🧠 13. `udevadm info --query=property`

Podemos consultar propriedades de um dispositivo:

`udevadm info --query=property --name=/dev/sda`

### Interpretação

`udevadm`

→ ferramenta do udev.

`info`

→ informações.

`--query=property`

→ consultar propriedades.

`--name=/dev/sda`

→ especificar o dispositivo.

---

# 📝 14. COMANDOS NECESSÁRIOS

### Listar `/sys`

`ls /sys`

**ls = list → listar**

### Interfaces de rede

`ls /sys/class/net/`

**net = network → rede**

### Dispositivos de bloco

`ls /sys/class/block/`

**block = bloco**

### Barramento PCI

`ls /sys/bus/pci/`

### Dispositivos PCI

`ls /sys/bus/pci/devices/`

### Barramento USB

`ls /sys/bus/usb/`

### Dispositivos USB

`ls /sys/bus/usb/devices/`

### Dispositivos

`ls /sys/devices/`

### Firmware

`ls /sys/firmware/`

### Consultar informações de dispositivos

`udevadm info --query=all --name=/dev/sda`

---

# 🎯 15. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que é `/sys`.
- Que `/sys` é um sistema de arquivos virtual.
- Que `/sys` é fornecido pelo kernel.
- O que é sysfs.
- A diferença básica entre `/proc` e `/sys`.
- Que `/sys` possui informações sobre dispositivos e hardware.
- Conhecer `/sys/class/`.
- Conhecer `/sys/class/net/`.
- Conhecer `/sys/class/block/`.
- Conhecer `/sys/bus/`.
- Conhecer `/sys/bus/pci/`.
- Conhecer `/sys/bus/usb/`.
- Conhecer `/sys/devices/`.
- Conhecer `/sys/firmware/`.
- Reconhecer `/sys/firmware/efi/` no contexto de UEFI.
- Saber listar informações usando `ls`.
- Conhecer o conceito de udev.
- Saber que `udevadm` consulta informações de dispositivos.

---

# 🧠 RESUMO

**/sys**

→ sistema de arquivos virtual.

→ informações sobre dispositivos e hardware.

**sysfs**

→ sistema de arquivos que fornece a estrutura do `/sys`.

**/sys/class/**

→ dispositivos organizados por classe.

**/sys/class/net/**

→ interfaces de rede.

**/sys/class/block/**

→ dispositivos de bloco.

**/sys/bus/**

→ informações sobre barramentos.

**/sys/bus/pci/**

→ PCI.

**/sys/bus/usb/**

→ USB.

**/sys/devices/**

→ hierarquia de dispositivos.

**/sys/firmware/**

→ informações relacionadas ao firmware.

**/sys/firmware/efi/**

→ interface relacionada ao UEFI quando o sistema foi inicializado nesse modo.

**udev**

→ gerenciamento dinâmico de dispositivos.

**udevadm**

→ ferramenta para consultar informações do udev/dispositivos.

---

# ⚖️ PARA NÃO CONFUNDIR

```text
/proc
└── processos
    ├── CPU
    ├── memória
    ├── kernel
    └── estado do sistema

/sys
└── dispositivos
    ├── hardware
    ├── drivers
    ├── barramentos
    └── classes
```

# 🧠 PARA DECORAR

```text
/sys
├── class/
│   ├── net/      → rede
│   └── block/    → dispositivos de bloco
│
├── bus/
│   ├── pci/      → PCI
│   └── usb/      → USB
│
├── devices/      → dispositivos
│
└── firmware/     → firmware/UEFI
```

# ✅ FIM DA PÁGINA 14
