Dispositivos e Periféricos

Device — Dispositivo

No Linux, um device (dispositivo) é um componente de hardware que o sistema consegue acessar.

Exemplos:

- HD/SSD
- Teclado
- Mouse
- Placa de rede
- Placa de vídeo
- USB

O Linux representa muitos desses dispositivos através de arquivos dentro de:

/dev

---

Peripheral — Periférico

Peripheral (Periférico) é um dispositivo conectado ao computador que ajuda na entrada, saída ou comunicação de dados.

Exemplos:

Teclado  → entrada
Mouse    → entrada
Monitor  → saída
Impressora → saída
USB      → armazenamento/comunicação

---

"/dev" — Devices (Dispositivos)

O diretório "/dev" contém arquivos especiais usados pelo Linux para acessar dispositivos.

Veja alguns exemplos:

ls /dev

Discos podem aparecer como:

/dev/sda
/dev/sdb

Discos NVMe podem aparecer como:

/dev/nvme0n1

Partições podem aparecer como:

/dev/sda1
/dev/sda2

---

Device File — Arquivo de Dispositivo

O Linux usa arquivos especiais para representar dispositivos.

Isso permite que programas interajam com o hardware através de uma interface comum do sistema.

Não significa que "/dev/sda" seja um arquivo comum contendo os dados do disco. É uma representação do dispositivo.

---

Block Device — Dispositivo de Bloco

Dispositivos que trabalham com dados em blocos, como discos e SSDs.

Exemplos:

/dev/sda
/dev/sdb
/dev/nvme0n1

---

Character Device — Dispositivo de Caractere

Dispositivos que trabalham com dados de forma sequencial, caractere por caractere.

Exemplos comuns:

/dev/tty
/dev/console

---

Comando

"ls" — List (Listar)

Mostra o conteúdo de um diretório.

ls /dev

---

"lsblk" — List Block Devices (Listar Dispositivos de Bloco)

Mostra os discos e suas partições.

lsblk

Exemplo de resultado:

NAME        SIZE TYPE
sda         500G disk
├─sda1      100G part
└─sda2      400G part

---

LPIC-1 — O que saber

- "/dev" contém arquivos que representam dispositivos.
- Discos são Block Devices.
- "sda", "sdb" são nomes comuns de discos.
- "nvme0n1" é um nome comum para um dispositivo NVMe.
- "lsblk" mostra discos e partições.
- Block Device e Character Device são tipos diferentes de dispositivos.

---

Resumo

Hardware
   ↓
Linux
   ↓
/dev
   ↓
Arquivos de dispositivos
   ↓
Programas acessam o dispositivo

Comando principal:

lsblk

→ Mostra os dispositivos de armazenamento e suas partições.
