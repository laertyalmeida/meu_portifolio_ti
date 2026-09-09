# Instalação e Gerenciamento de Pacotes

## 05 — Pacotes Debian

### Debian Package — Pacote Debian

O **Debian Package — Pacote Debian** é o formato de pacote utilizado pelo Debian e por distribuições derivadas, como Ubuntu.

A extensão normalmente é:

    .deb

Exemplo:

    programa.deb

Um pacote `.deb` pode conter:

- arquivos do programa;
- bibliotecas;
- arquivos de configuração;
- informações sobre dependências;
- scripts de instalação e remoção.

---

## dpkg — Debian Package

**dpkg — Debian Package — Pacote Debian** é a ferramenta de baixo nível usada para instalar e gerenciar pacotes `.deb`.

### Instalar

    sudo dpkg -i programa.deb

- `-i` — install — instalar

### Remover

    sudo dpkg -r programa

- `-r` — remove — remover

### Remover incluindo arquivos de configuração

    sudo dpkg -P programa

- `-P` — purge — eliminar completamente

### Listar pacotes instalados

    dpkg -l

- `-l` — list — listar

### Consultar um pacote instalado

    dpkg -s programa

- `-s` — status — estado/informações

### Ver arquivos instalados por um pacote

    dpkg -L programa

- `-L` — list files — listar arquivos

### Descobrir qual pacote fornece um arquivo

    dpkg -S /caminho/arquivo

- `-S` — search — procurar

---

## APT — Advanced Package Tool

**APT — Advanced Package Tool — Ferramenta Avançada de Pacotes** é o sistema de gerenciamento de pacotes de alto nível usado em Debian e derivados.

Diferente do `dpkg`, o APT trabalha com **repositórios** e pode resolver dependências automaticamente.

### Atualizar a lista de pacotes

    sudo apt update

- `update` — atualizar

Atualiza as informações disponíveis nos repositórios.

### Atualizar pacotes instalados

    sudo apt upgrade

- `upgrade` — atualizar

Instala versões mais recentes dos pacotes instalados.

### Instalar um pacote

    sudo apt install programa

- `install` — instalar

### Remover um pacote

    sudo apt remove programa

- `remove` — remover

### Remover pacote e configurações

    sudo apt purge programa

- `purge` — eliminar completamente

---

## Dependências

### Dependency — Dependência

Um programa pode precisar de outros pacotes para funcionar.

Exemplo:

    programa
       ↓
    biblioteca A
       ↓
    biblioteca B

O **APT** consegue localizar e instalar essas dependências automaticamente.

Por isso:

    sudo apt install programa

é geralmente mais conveniente do que:

    sudo dpkg -i programa.deb

O `dpkg` instala diretamente o `.deb`, mas não é responsável por resolver automaticamente todas as dependências como o APT.

---

## Repositórios

### Repository — Repositório

É um local que contém pacotes disponíveis para instalação.

As configurações dos repositórios Debian ficam principalmente em:

    /etc/apt/sources.list

- `/etc` — etcetera — configuração do sistema
- `/apt` — arquivos de configuração do APT
- `sources.list` — lista de fontes/repositórios

Também podem existir arquivos adicionais em:

    /etc/apt/sources.list.d/

- `sources.list.d` — diretório de fontes adicionais

---

## apt-cache — Cache de Pacotes

**apt-cache — APT Cache — Cache do APT** permite consultar informações sobre os pacotes.

Pesquisar:

    apt-cache search palavra

- `search` — pesquisar

Mostrar informações:

    apt-cache show programa

- `show` — mostrar

Hoje, o comando `apt` também é muito utilizado para essas consultas:

    apt search programa
    apt show programa

---

## apt-get

**apt-get** é outra ferramenta de gerenciamento de pacotes do APT.

Exemplos:

    sudo apt-get update
    sudo apt-get install programa
    sudo apt-get remove programa

Para uso interativo, `apt` é normalmente mais amigável:

    apt update
    apt install programa

---

## Comparação

| Comando | Função |
|---|---|
| `dpkg` | Gerenciamento direto de `.deb` |
| `apt` | Gerenciamento de alto nível |
| `apt-get` | Gerenciamento de alto nível |
| `apt-cache` | Consultar informações do cache |
| `apt update` | Atualizar lista de pacotes |
| `apt install` | Instalar pacote |
| `apt remove` | Remover pacote |
| `apt purge` | Remover pacote e configurações |

---

## Resumo LPIC-1

- `.deb` = formato de pacote do Debian.
- `dpkg` = ferramenta de baixo nível para pacotes `.deb`.
- `dpkg -i` = instalar um `.deb`.
- `dpkg -r` = remover pacote.
- `dpkg -P` = remover pacote e configurações.
- `dpkg -l` = listar pacotes instalados.
- `dpkg -L` = listar arquivos de um pacote.
- `dpkg -S` = descobrir qual pacote fornece um arquivo.
- **APT — Advanced Package Tool** = ferramenta de alto nível.
- `apt update` = atualizar informações dos repositórios.
- `apt upgrade` = atualizar pacotes instalados.
- `apt install` = instalar.
- `apt remove` = remover.
- `apt purge` = remover incluindo configurações.
- **Dependency — Dependência** = pacote necessário para outro programa funcionar.
- `/etc/apt/sources.list` = configuração das fontes de pacotes.
- `apt` resolve dependências automaticamente com base nos repositórios configurados.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
