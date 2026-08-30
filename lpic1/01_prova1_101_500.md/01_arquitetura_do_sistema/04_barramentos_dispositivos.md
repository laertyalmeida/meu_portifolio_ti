Barramentos e Dispositivos

Bus — Barramento

Um bus (barramento) é o caminho usado pelos componentes do computador para trocar informações.

Imagine uma estrada:

CPU ───────────────┐
                   │
Memória ───────────┼── Barramento ──→ Dispositivos
                   │
SSD ───────────────┘

O barramento permite que diferentes partes do computador se comuniquem.

---

PCI — Peripheral Component Interconnect

PCI é um padrão usado para conectar componentes ao computador.

Sua versão mais comum atualmente é:

PCIe — PCI Express

É usada para conectar dispositivos como:

- Placas de vídeo
- Placas de rede
- Placas de som
- Controladoras de armazenamento

---

USB — Universal Serial Bus (Barramento Serial Universal)

USB é um padrão usado para conectar dispositivos externos.

Exemplos:

- Teclado
- Mouse
- Pendrive
- HD externo
- Adaptador de rede

---

SATA — Serial ATA

SATA é uma tecnologia usada principalmente para conectar dispositivos de armazenamento.

Exemplo:

Placa-mãe
   ↓
SATA
   ↓
SSD / HD

---

Como o Linux identifica os dispositivos?

O Linux disponibiliza informações sobre dispositivos através de arquivos e diretórios do sistema.

Um dos locais principais é:

/dev

Também podemos consultar informações do hardware com comandos específicos.

---

"lspci" — List PCI (Listar PCI)

Mostra os dispositivos conectados ao barramento PCI/PCIe.

lspci

Exemplo:

Ethernet controller
VGA controller
USB controller

---

"lsusb" — List USB (Listar USB)

Mostra os dispositivos USB conectados.

lsusb

Exemplo:

Keyboard
Mouse
USB Storage

---

Flags importantes

"-v" — Verbose (Detalhado)

Mostra mais informações sobre os dispositivos.

lspci -v

ou:

lsusb -v

"-k" — Kernel Driver (Driver do Kernel)

No "lspci", mostra informações sobre o driver do kernel usado pelo dispositivo.

lspci -k

---

LPIC-1 — O que saber

- Bus = caminho de comunicação entre componentes.
- PCIe conecta placas e outros dispositivos internos.
- USB conecta dispositivos externos.
- SATA é usado para armazenamento.
- "/dev" representa dispositivos para o Linux.
- "lspci" mostra dispositivos PCI/PCIe.
- "lsusb" mostra dispositivos USB.
- "-v" significa Verbose e mostra informações detalhadas.
- "-k" mostra o driver do kernel usado pelo dispositivo no "lspci".

---

Resumo

PCIe → dispositivos internos

USB → dispositivos externos

SATA → HD / SSD

lspci → dispositivos PCI/PCIe
lsusb → dispositivos USB

-v → informações detalhadas
-k → driver do kernel
