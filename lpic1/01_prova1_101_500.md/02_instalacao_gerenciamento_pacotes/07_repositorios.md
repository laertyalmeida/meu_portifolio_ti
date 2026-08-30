Repositórios

Repository — Repositório

Um Repository (Repositório) é um local onde uma distribuição Linux mantém pacotes disponíveis para instalação.

Em vez de procurar um programa na internet e instalar manualmente, podemos usar o gerenciador de pacotes.

Repositório
     ↓
Gerenciador de pacotes
     ↓
Baixa o pacote
     ↓
Instala no Linux

---

APT

Em sistemas Debian e derivados, os repositórios usados pelo APT são configurados principalmente em:

/etc/apt/sources.list

Também podem existir arquivos em:

/etc/apt/sources.list.d/

Podemos consultar:

cat /etc/apt/sources.list

---

"apt update"

Atualiza a lista de pacotes disponíveis nos repositórios.

sudo apt update

Importante: "apt update" não atualiza os programas instalados. Ele atualiza a lista de informações sobre os pacotes.

Para atualizar os programas:

sudo apt upgrade

---

DNF

Em sistemas baseados em RPM, como Fedora, os repositórios são utilizados pelo DNF.

Para atualizar as informações dos repositórios:

sudo dnf check-update

Para instalar um pacote:

sudo dnf install nome-do-pacote

---

Repository Configuration — Configuração do Repositório

Um repositório normalmente informa:

- Onde encontrar os pacotes.
- Qual distribuição está sendo usada.
- Qual versão.
- Qual arquitetura.
- Informações para verificar os pacotes.

---

Por que usar repositórios?

Eles facilitam:

- Instalação de programas.
- Atualizações.
- Controle de versões.
- Resolução de dependências.
- Verificação dos pacotes.

---

LPIC-1 — O que saber

- Repositório é uma fonte de pacotes.
- APT usa repositórios para sistemas Debian.
- DNF usa repositórios em sistemas baseados em RPM.
- "/etc/apt/sources.list" contém configurações de repositórios do APT.
- "/etc/apt/sources.list.d/" pode conter configurações adicionais.
- "apt update" atualiza a lista de pacotes.
- "apt upgrade" atualiza os pacotes instalados.
- Repositórios facilitam a instalação e atualização dos programas.

---

Resumo

Repository
    ↓
Pacotes
    ↓
APT / DNF
    ↓
Instalação e atualização

apt update  → atualiza a lista
apt upgrade → atualiza os programas
