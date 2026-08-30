# 📖 PÁGINA 16 — LSUSB

# 🧠 1. O QUE É `lsusb`?

`lsusb` é um comando utilizado para listar dispositivos conectados ao barramento **USB**.

### Tradução

`ls`

→ **list → listar**

`usb`

→ **Universal Serial Bus**

→ Barramento Serial Universal.

Portanto:

**lsusb → list USB → listar dispositivos USB**

---

# 🔌 2. USO BÁSICO

Comando:

`lsusb`

Mostra os dispositivos USB detectados pelo sistema.

Exemplo:

`Bus 001 Device 002: ID 1234:5678 ...`

Podemos encontrar dispositivos como:

- Teclado
- Mouse
- Webcam
- Pendrive
- Adaptador Wi-Fi USB
- Celular
- Impressora

---

# 🔢 3. ENTENDENDO A SAÍDA

Exemplo:

`Bus 001 Device 002: ID 1234:5678 Example Device`

### `Bus 001`

Número do barramento USB.

### `Device 002`

Número atribuído ao dispositivo naquele barramento.

### `ID 1234:5678`

Identificadores do dispositivo.

Normalmente:

`1234`

→ Vendor ID.

`5678`

→ Product/Device ID.

Portanto:

**Bus → Device → ID → Fabricante/Dispositivo**

---

# 🔍 4. `lsusb -v`

Comando:

`lsusb -v`

### Tradução

`-v`

→ **verbose → detalhado**

Mostra informações detalhadas sobre os dispositivos USB.

⚠️ A saída pode ser bastante grande.

---

# 🔬 5. `lsusb -vv`

Comando:

`lsusb -vv`

Aumenta ainda mais o nível de detalhes.

`-vv`

→ **very verbose → muito detalhado**

---

# 🆔 6. `lsusb -n`

Comando:

`lsusb -n`

### Tradução

`-n`

→ **numeric → numérico**

Mostra identificadores numéricos dos dispositivos.

Isso é útil para identificar dispositivos através de seus IDs.

---

# 🆔 7. `lsusb -t`

Comando:

`lsusb -t`

### Tradução

`-t`

→ **tree → árvore**

Mostra os dispositivos USB em uma estrutura de árvore.

Isso permite visualizar a hierarquia de conexão dos dispositivos USB.

---

# 🧠 8. `lsusb -s`

A opção:

`-s`

permite selecionar um dispositivo específico pelo endereço:

**bus:device**

Exemplo:

`lsusb -s 001:002`

Significa:

→ consultar o dispositivo `002` do barramento `001`.

### `-s`

→ **select → selecionar**

---

# 🔎 9. `lsusb -d`

A opção:

`-d`

permite selecionar dispositivos através do:

**Vendor ID:Product ID**

Exemplo:

`lsusb -d 1234:5678`

### `-d`

→ **device → dispositivo**

Na prática:

→ seleciona dispositivos pelo ID.

---

# 🌳 10. USB E HIERARQUIA

O USB possui uma estrutura hierárquica de conexão.

Um computador pode possuir:

**Controlador USB**

↓

**Hub USB**

↓

**Dispositivo USB**

O comando:

`lsusb -t`

ajuda a visualizar essa estrutura.

---

# 🔧 11. USB E DRIVERS

Assim como outros dispositivos, USB depende do suporte do kernel.

Fluxo:

**Dispositivo USB**

↓

**Kernel**

↓

**Driver**

↓

**Dispositivo disponível para o sistema**

Podemos consultar mensagens do kernel relacionadas a USB com:

`dmesg | grep -i usb`

### `grep`

→ procurar.

### `-i`

→ **ignore case → ignorar maiúsculas/minúsculas**

Portanto:

`dmesg | grep -i usb`

→ procura mensagens relacionadas a USB nas mensagens do kernel.

---

# 📂 12. USB E `/sys`

O kernel também disponibiliza informações sobre USB através de:

`/sys/bus/usb/`

Os dispositivos USB podem ser encontrados em:

`/sys/bus/usb/devices/`

Podemos listar:

`ls /sys/bus/usb/devices/`

### Relação

**lsusb**

→ ferramenta para consultar dispositivos USB.

**/sys/bus/usb/**

→ informações sobre USB disponibilizadas pelo kernel.

---

# 🧰 13. `usb-devices`

Outro comando que pode ser encontrado em sistemas Linux é:

`usb-devices`

Ele apresenta informações sobre dispositivos USB.

### Tradução

**usb**

→ Universal Serial Bus.

**devices**

→ dispositivos.

Portanto:

**usb-devices → dispositivos USB**

Para a prova, o principal comando é:

**lsusb**

---

# 📝 14. COMANDOS NECESSÁRIOS

### Listar dispositivos USB

`lsusb`

→ list USB → listar dispositivos USB.

### Informações detalhadas

`lsusb -v`

→ `-v = verbose → detalhado`

### Informações muito detalhadas

`lsusb -vv`

→ `-vv = very verbose → muito detalhado`

### IDs numéricos

`lsusb -n`

→ `-n = numeric → numérico`

### Mostrar árvore USB

`lsusb -t`

→ `-t = tree → árvore`

### Selecionar dispositivo por Bus/Device

`lsusb -s 001:002`

→ `-s = selecionar`.

### Selecionar por Vendor/Product ID

`lsusb -d 1234:5678`

→ `-d = device → dispositivo`.

### Mensagens do kernel relacionadas ao USB

`dmesg | grep -i usb`

→ procura mensagens USB.

### Informações pelo sysfs

`ls /sys/bus/usb/devices/`

→ lista dispositivos USB expostos pelo kernel.

---

# 🎯 15. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- Para que serve `lsusb`.
- Que `lsusb` lista dispositivos USB.
- O significado de USB.
- Interpretar uma saída básica do `lsusb`.
- Entender Bus e Device.
- Entender Vendor ID e Product ID.
- Usar `lsusb -v`.
- Saber que `-v` significa verbose.
- Usar `lsusb -vv`.
- Usar `lsusb -n`.
- Saber que `-n` significa numeric.
- Usar `lsusb -t`.
- Saber que `-t` significa tree.
- Conhecer `lsusb -s`.
- Conhecer `lsusb -d`.
- Entender a relação entre USB, kernel e drivers.
- Conhecer `/sys/bus/usb/`.
- Conhecer `/sys/bus/usb/devices/`.
- Saber consultar mensagens USB com `dmesg`.

---

# 🧠 RESUMO

**USB**

→ Universal Serial Bus.

→ Barramento utilizado para conectar dispositivos.

**lsusb**

→ list USB.

→ lista dispositivos USB.

**-v**

→ verbose → detalhado.

**-vv**

→ very verbose → muito detalhado.

**-n**

→ numeric → numérico.

**-t**

→ tree → árvore.

**-s**

→ seleciona por Bus:Device.

**-d**

→ seleciona por Vendor ID:Product ID.

**/sys/bus/usb/**

→ informações USB fornecidas pelo kernel.

---

# 🔄 PARA MEMORIZAR

```text
lsusb
│
├── -v       → verbose → detalhado
├── -vv      → muito detalhado
├── -n       → numeric → numérico
├── -t       → tree → árvore
├── -s       → selecionar Bus:Device
└── -d       → selecionar Vendor:Product
```

# 🎯 COMANDO PRINCIPAL

```bash
lsusb
```

**Lista os dispositivos USB detectados pelo Linux.**

# 🔌 RELAÇÃO COM O KERNEL

```text
Dispositivo USB
       ↓
Controlador USB
       ↓
Kernel
       ↓
Driver
       ↓
Sistema Linux
```

# ✅ FIM DA PÁGINA 16
