Sistemas de Arquivos

File System — Sistema de Arquivos

Um File System (Sistema de Arquivos) define como os arquivos e diretórios serão organizados dentro de uma partição.

Sem ele, o Linux não teria uma forma organizada de guardar e encontrar os arquivos.

Disco
  ↓
Partição
  ↓
Sistema de Arquivos
  ↓
Arquivos e diretórios

---

Principais sistemas de arquivos

ext4 — Fourth Extended Filesystem

É um dos sistemas de arquivos mais usados em Linux.

Características:

- Suporta arquivos e discos grandes
- Possui journaling
- É estável e muito comum

---

XFS — X File System

Sistema de arquivos criado para trabalhar bem com grandes volumes de dados.

É bastante usado em servidores Linux.

---

Btrfs — B-tree File System

Sistema de arquivos moderno com recursos avançados.

Entre eles:

- Snapshots
- Compressão
- Checksums
- Subvolumes

---

Journaling — Registro de alterações

Journaling (Registro de alterações) é um recurso que registra operações antes que elas sejam concluídas.

Isso ajuda o sistema de arquivos a se recuperar após uma interrupção inesperada, como uma queda de energia.

O ext4 possui journaling.

---

Como descobrir o sistema de arquivos?

"lsblk" — List Block Devices (Listar Dispositivos de Bloco)

Podemos usar "-f" para mostrar informações sobre o sistema de arquivos.

lsblk -f

"-f" — Filesystem (Sistema de Arquivos)

Mostra informações como:

- Tipo do sistema de arquivos
- UUID
- Label

Exemplo:

NAME   FSTYPE UUID
sda1   ext4   xxxx-xxxx
sda2   xfs    xxxx-xxxx

---

"blkid" — Block Device ID (ID do Dispositivo de Bloco)

Mostra informações sobre dispositivos de bloco, incluindo o sistema de arquivos e o UUID.

sudo blkid

---

LPIC-1 — O que saber

- Sistema de arquivos organiza os dados dentro de uma partição.
- ext4 é muito comum no Linux.
- XFS é usado em muitos sistemas e servidores.
- Btrfs possui recursos avançados como snapshots e compressão.
- Journaling ajuda na recuperação após falhas.
- "lsblk -f" mostra o sistema de arquivos.
- "blkid" mostra informações dos dispositivos, incluindo UUID.

---

Resumo

ext4 → comum e estável
XFS  → bom para grandes volumes
Btrfs → recursos avançados

lsblk -f → mostra o filesystem
blkid     → mostra informações do dispositivo

-f → Filesystem
