# Instalação e Gerenciamento de Pacotes

## 07 — Repositórios

### Repository — Repositório

**Repository — Repositório** é um local onde ficam armazenados pacotes de software que podem ser instalados pelo sistema.

Um repositório normalmente fornece:

- pacotes;
- versões dos pacotes;
- informações sobre dependências;
- atualizações;
- informações de segurança.

Fluxo:

    Sistema
       ↓
    Gerenciador de Pacotes
       ↓
    Repositório
       ↓
    Pacote
       ↓
    Instalação

---

## Package Manager — Gerenciador de Pacotes

O gerenciador de pacotes consulta os repositórios para encontrar e instalar programas.

### Debian

    apt
       ↓
    repositórios
       ↓
    .deb

### Red Hat

    dnf
       ↓
    repositórios
       ↓
    .rpm

---

## Debian — Repositórios

As configurações principais ficam em:

    /etc/apt/sources.list

- `/etc` — etcetera — configuração do sistema
- `/apt` — arquivos de configuração do APT
- `sources.list` — lista de fontes/repositórios

Também podem existir:

    /etc/apt/sources.list.d/

- `sources.list.d` — diretório para arquivos adicionais de repositórios

Exemplo:

    deb http://servidor/debian stable main

- `deb` — pacote binário Debian
- `stable` — estável
- `main` — seção principal do repositório

---

## apt update

Antes de instalar ou atualizar pacotes, é importante atualizar as informações dos repositórios:

    sudo apt update

- `update` — atualizar

Esse comando **não atualiza os programas instalados**.

Ele atualiza a lista de informações disponíveis nos repositórios.

Depois:

    sudo apt upgrade

- `upgrade` — atualizar

Esse comando atualiza os pacotes instalados quando existem versões mais recentes disponíveis.

---

## Red Hat — Repositórios

Em sistemas modernos baseados em Red Hat, o **DNF** gerencia os repositórios.

Ver os repositórios:

    dnf repolist

- `repolist` — repository list — lista de repositórios

Pesquisar um pacote:

    dnf search programa

- `search` — pesquisar

Instalar:

    sudo dnf install programa

- `install` — instalar

---

## Repository Configuration — Configuração de Repositórios

No DNF, os arquivos de configuração normalmente ficam em:

    /etc/yum.repos.d/

- `/etc` — configuração do sistema
- `yum.repos.d` — arquivos de configuração dos repositórios

Os arquivos normalmente possuem a extensão:

    .repo

Exemplo:

    /etc/yum.repos.d/meu-repositorio.repo

---

## Main Repository — Repositório Principal

Um sistema pode possuir vários repositórios.

Exemplo:

    Repositório oficial
          ↓
    Pacotes principais
          ↓
    Atualizações
          ↓
    Segurança

É preferível utilizar repositórios confiáveis e compatíveis com a distribuição.

---

## Mirror — Espelho

**Mirror — Espelho** é um servidor que mantém uma cópia dos pacotes de um repositório.

Exemplo:

    Repositório principal
            ↓
        Mirror 1
        Mirror 2
        Mirror 3

Isso permite distribuir a carga e melhorar a velocidade de download.

---

## Local Repository — Repositório Local

Também é possível utilizar um diretório ou servidor local como fonte de pacotes.

Isso é comum em ambientes corporativos onde muitos computadores precisam instalar os mesmos pacotes.

---

## Repository Metadata — Metadados do Repositório

**Metadata — Metadados** são informações sobre os pacotes.

Podem incluir:

- nome;
- versão;
- arquitetura;
- dependências;
- informações de assinatura;
- localização do pacote.

O gerenciador utiliza esses dados para encontrar e instalar corretamente os pacotes.

---

## GPG — GNU Privacy Guard

**GPG — GNU Privacy Guard — Guardião de Privacidade GNU** é utilizado para verificar assinaturas e autenticidade de pacotes e repositórios.

Isso ajuda a proteger contra pacotes modificados ou de origem não confiável.

---

## Repositório × Pacote

Não confunda:

    Repositório
        ↓
    contém muitos pacotes

    Pacote
        ↓
    contém um programa ou componentes do programa

Exemplo:

    Repositório Debian
       ├── bash.deb
       ├── vim.deb
       ├── nginx.deb
       └── curl.deb

---

## Comandos importantes

| Comando | Tradução | Função |
|---|---|---|
| `apt update` | atualizar | Atualizar informações dos repositórios |
| `apt upgrade` | atualizar | Atualizar pacotes instalados |
| `apt search` | pesquisar | Procurar pacotes |
| `apt install` | instalar | Instalar pacote |
| `dnf repolist` | lista de repositórios | Mostrar repositórios |
| `dnf search` | pesquisar | Procurar pacotes |
| `dnf install` | instalar | Instalar pacote |

---

## Resumo LPIC-1

- **Repository — Repositório** = fonte de pacotes.
- **Package Manager — Gerenciador de Pacotes** = ferramenta que consulta e gerencia pacotes.
- Debian utiliza principalmente `apt` com pacotes `.deb`.
- Sistemas da família Red Hat utilizam `dnf` com pacotes `.rpm`.
- `/etc/apt/sources.list` = configuração principal de fontes do APT.
- `/etc/apt/sources.list.d/` = configurações adicionais do APT.
- `/etc/yum.repos.d/` = arquivos de repositórios usados pelo DNF/YUM.
- `apt update` = atualiza a lista de informações dos repositórios.
- `apt upgrade` = atualiza pacotes instalados.
- `dnf repolist` = lista os repositórios.
- **Mirror — Espelho** = servidor que mantém uma cópia de um repositório.
- **Metadata — Metadados** = informações utilizadas para localizar e gerenciar pacotes.
- **GPG** = utilizado para verificar assinaturas e autenticidade.
- Repositório **não é o mesmo que pacote**.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
