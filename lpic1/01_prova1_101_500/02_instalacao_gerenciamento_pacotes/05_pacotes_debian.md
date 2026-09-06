Pacotes Debian

Package — Pacote

Um Package (Pacote) é um arquivo que contém os arquivos necessários para instalar um programa no Linux.

Em sistemas Debian, o formato mais comum é:

.deb

Distribuições que usam esse formato incluem:

- Debian
- Ubuntu
- Linux Mint

---

"dpkg" — Debian Package

O "dpkg" é uma ferramenta de baixo nível para trabalhar com pacotes ".deb".

Instalar

sudo dpkg -i pacote.deb

"-i" — Install (Instalar)

Instala o pacote.

---

Remover

sudo dpkg -r nome-do-pacote

"-r" — Remove (Remover)

Remove o pacote, mas normalmente mantém arquivos de configuração.

---

Remover completamente

sudo dpkg -P nome-do-pacote

"-P" — Purge (Eliminar completamente)

Remove o pacote e seus arquivos de configuração.

---

Verificar se está instalado

dpkg -l

"-l" — List (Listar)

Lista os pacotes instalados/conhecidos pelo "dpkg".

---

"apt" — Advanced Package Tool

O APT é usado para instalar e gerenciar pacotes e suas dependências.

Diferente do "dpkg", o APT consegue buscar pacotes nos repositórios e resolver dependências automaticamente.

Atualizar lista de pacotes

sudo apt update

Instalar

sudo apt install nome-do-pacote

Remover

sudo apt remove nome-do-pacote

Atualizar pacotes

sudo apt upgrade

---

"dpkg" x "apt"

.deb
 ↓
dpkg → trabalha diretamente com o pacote

Repositórios
 ↓
apt → busca pacotes e resolve dependências

---

LPIC-1 — O que saber

- Debian usa pacotes ".deb".
- "dpkg" trabalha diretamente com pacotes ".deb".
- "apt" gerencia pacotes e dependências.
- "dpkg -i" instala um pacote.
- "dpkg -r" remove um pacote.
- "dpkg -P" remove o pacote e suas configurações.
- "dpkg -l" lista pacotes.
- "apt update" atualiza a lista de pacotes.
- "apt install" instala pacotes.
- "apt remove" remove pacotes.
- "apt upgrade" atualiza pacotes.

---

Resumo

.deb
 ↓
dpkg → pacote local

apt
 ↓
Repositórios
 ↓
Pacotes + dependências

Principais flags

-i → Install (Instalar)
-r → Remove (Remover)
-P → Purge (Eliminar completamente)
-l → List (Listar)
