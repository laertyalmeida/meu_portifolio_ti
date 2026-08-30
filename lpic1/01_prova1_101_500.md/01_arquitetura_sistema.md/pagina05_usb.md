# 📖 PÁGINA 5 — USB

## 🧠 1. O QUE É USB?

**USB = Universal Serial Bus**

Tradução:

**Barramento Serial Universal**

USB é um padrão utilizado para conectar dispositivos ao computador e permitir comunicação e transferência de dados.

Exemplos:

- Teclado
- Mouse
- Pendrive
- HD externo
- Webcam
- Adaptador de rede
- Celular

---

# 🔌 2. COMO O USB FUNCIONA?

O computador possui **controladores USB**, que gerenciam a comunicação com os dispositivos conectados.

De forma simplificada:

**CPU → Controlador USB → Barramento USB → Dispositivo**

Exemplo:

**CPU → Controlador USB → Pendrive**

O sistema operacional utiliza o controlador e os drivers apropriados para se comunicar com o dispositivo.

---

# 🚌 3. BARRAMENTO USB

Um computador pode possuir vários barramentos USB.

Cada dispositivo conectado pode aparecer associado a um determinado barramento e receber um número de dispositivo.

Exemplo:

**Bus 001 Device 002**

Interpretação:

**Bus 001**

→ barramento USB número 001.

**Device 002**

→ dispositivo número 002 naquele barramento.

---

# 🔍 4. `lsusb`

O principal comando para identificar dispositivos USB é:

`lsusb`

### Tradução

`ls`

→ **list → listar**

`usb`

→ **Universal Serial Bus → Barramento Serial Universal**

Portanto:

**lsusb → list USB → listar dispositivos USB**

Execute:

`lsusb`

Exemplo:

`Bus 001 Device 002: ID 1234:5678 Example Device`

---

# 🧠 5. INTERPRETANDO `lsusb`

Considere:

`Bus 001 Device 002: ID 1234:5678 Example Device`

Podemos interpretar:

**Bus 001**

→ número do barramento USB.

**Device 002**

→ número do dispositivo dentro daquele barramento.

**ID 1234:5678**

→ identificador USB.

O identificador possui duas partes:

**1234**

→ Vendor ID (VID).

**5678**

→ Product ID (PID).

---

# 🏭 6. VID E PID

### VID

**VID = Vendor ID**

Tradução:

**Identificador do fabricante**

Identifica o fabricante do dispositivo USB.

### PID

**PID = Product ID**

Tradução:

**Identificador do produto**

Identifica o produto/dispositivo daquele fabricante.

Formato:

`VID:PID`

Exemplo:

`1234:5678`

---

# 🔎 7. `lsusb -v`

A opção:

`-v`

significa:

**verbose = detalhado**

Comando:

`lsusb -v`

Mostra informações detalhadas sobre os dispositivos USB.

Interpretação:

`lsusb`

→ list USB → listar dispositivos USB.

`-v`

→ verbose → detalhado.

### ⚠️ Atenção

A saída pode ser muito grande.

Para visualizar informações de um dispositivo específico, podemos utilizar o identificador do dispositivo.

---

# 🎯 8. `lsusb -d`

A opção:

`-d`

significa:

**device = dispositivo**

Ela permite selecionar um dispositivo específico pelo identificador de fabricante/produto.

Exemplo:

`lsusb -d 1234:5678`

Interpretação:

`lsusb`

→ lista dispositivos USB.

`-d`

→ device → seleciona um dispositivo.

`1234:5678`

→ VID:PID do dispositivo.

---

# 🧾 9. `lsusb -t`

A opção:

`-t`

significa:

**tree = árvore**

Mostra os dispositivos USB em formato de árvore.

Comando:

`lsusb -t`

Exemplo conceitual:

`/sys/devices/...`

`├── USB Controller`

`│   ├── Device`

`│   └── Device`

A opção ajuda a visualizar a relação entre:

**Controlador → Barramento → Dispositivo**

---

# 📂 10. USB E `/dev`

Dispositivos USB podem criar ou utilizar arquivos de dispositivo dentro de:

`/dev`

Por exemplo, um pendrive pode aparecer como:

`/dev/sdb`

e suas partições:

`/dev/sdb1`

### ⚠️ IMPORTANTE

O nome `/dev/sdb` não significa necessariamente que o dispositivo é USB.

Ele indica um dispositivo de armazenamento identificado pelo Linux dessa forma.

Para descobrir exatamente qual dispositivo é USB, podemos utilizar:

`lsusb`

e ferramentas como:

`lsblk`

---

# 💾 11. `lsblk`

O comando:

`lsblk`

é utilizado para listar dispositivos de bloco.

### Tradução

`ls`

→ **list → listar**

`blk`

→ **block → bloco**

Portanto:

**lsblk → list block devices → listar dispositivos de bloco**

Execute:

`lsblk`

Exemplo:

`NAME   TYPE`

`sda    disk`

`├─sda1 part`

`└─sda2 part`

` sdb   disk`

---

# 🔍 12. `lsblk -o`

A opção:

`-o`

significa:

**--output = saída**

Permite escolher quais colunas serão exibidas.

Exemplo:

`lsblk -o NAME,SIZE,TYPE,MOUNTPOINTS`

Interpretação:

`lsblk`

→ lista dispositivos de bloco.

`-o`

→ output → define as informações que serão exibidas.

`NAME`

→ nome do dispositivo.

`SIZE`

→ tamanho.

`TYPE`

→ tipo.

`MOUNTPOINTS`

→ pontos de montagem.

---

# 🧠 13. USB E O KERNEL

O Linux utiliza o kernel para gerenciar dispositivos USB.

Informações sobre dispositivos podem ser encontradas em:

`/sys`

e:

`/proc`

Além disso, mensagens relacionadas à detecção de hardware podem ser consultadas com:

`dmesg`

---

# 📜 14. `dmesg`

### Tradução

**dmesg = display message**

Pode ser entendido como:

**exibir mensagens**

O comando mostra mensagens do buffer de mensagens do kernel.

Para pesquisar mensagens relacionadas a USB:

`dmesg | grep -i usb`

### Interpretação

`dmesg`

→ mostra mensagens do kernel.

`|`

→ pipe → envia a saída de um comando para outro.

`grep`

→ procura um padrão.

`-i`

→ **ignore case → ignora maiúsculas/minúsculas**.

`usb`

→ texto que queremos procurar.

Portanto:

`dmesg | grep -i usb`

→ mostra mensagens do kernel relacionadas a USB, ignorando diferença entre letras maiúsculas e minúsculas.

---

# 📝 15. COMANDOS NECESSÁRIOS

### Listar dispositivos USB

`lsusb`

### Listar USB com detalhes

`lsusb -v`

### Selecionar dispositivo pelo VID:PID

`lsusb -d VID:PID`

### Mostrar árvore USB

`lsusb -t`

### Listar dispositivos de bloco

`lsblk`

### Escolher colunas do `lsblk`

`lsblk -o NAME,SIZE,TYPE,MOUNTPOINTS`

### Consultar mensagens do kernel

`dmesg`

### Procurar mensagens USB

`dmesg | grep -i usb`

---

# 🎯 16. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O significado de USB.
- Que USB significa **Universal Serial Bus**.
- O que é um barramento USB.
- O que é um controlador USB.
- Como identificar dispositivos USB.
- Usar `lsusb`.
- Interpretar `Bus`.
- Interpretar `Device`.
- Saber o que significa VID.
- Saber o que significa PID.
- Entender o formato `VID:PID`.
- Usar `lsusb -v`.
- Saber que `-v` significa **verbose**.
- Usar `lsusb -t`.
- Saber que `-t` significa **tree**.
- Conhecer `lsblk`.
- Saber que `lsblk` lista dispositivos de bloco.
- Usar `dmesg` para consultar mensagens do kernel.
- Usar `grep -i` para procurar mensagens relacionadas a USB.
- Saber que `/dev` contém arquivos especiais relacionados a dispositivos.
- Saber que o kernel é responsável pelo gerenciamento dos dispositivos.

---

# 🧠 RESUMO

**USB**

→ Universal Serial Bus.

→ Barramento Serial Universal.

**VID**

→ Vendor ID.

→ Identificador do fabricante.

**PID**

→ Product ID.

→ Identificador do produto.

**VID:PID**

→ Identificação do fabricante e produto.

**lsusb**

→ list USB.

→ Lista dispositivos USB.

**lsusb -v**

→ verbose.

→ Informações detalhadas.

**lsusb -d**

→ device.

→ Seleciona um dispositivo pelo VID:PID.

**lsusb -t**

→ tree.

→ Mostra os dispositivos em formato de árvore.

**lsblk**

→ list block devices.

→ Lista dispositivos de bloco.

**lsblk -o**

→ output.

→ Escolhe as colunas exibidas.

**dmesg**

→ display messages.

→ Exibe mensagens do kernel.

**grep -i**

→ ignore case.

→ Pesquisa ignorando maiúsculas/minúsculas.

**/dev**

→ device.

→ Representações de dispositivos utilizadas pelo sistema.

---

# ✅ FIM DA PÁGINA 5
