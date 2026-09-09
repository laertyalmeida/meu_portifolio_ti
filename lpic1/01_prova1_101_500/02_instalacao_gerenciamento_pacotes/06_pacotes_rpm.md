# Instalação e Gerenciamento de Pacotes

## 06 — Pacotes RPM

### RPM — Red Hat Package Manager — Gerenciador de Pacotes Red Hat

**RPM — Red Hat Package Manager — Gerenciador de Pacotes Red Hat** é o formato e o sistema de gerenciamento de pacotes utilizado por distribuições da família Red Hat.

A extensão normalmente é:

    .rpm

Exemplo:

    programa.rpm

Distribuições que utilizam RPM incluem:

- Fedora
- RHEL — Red Hat Enterprise Linux — Red Hat Enterprise Linux
- Rocky Linux
- AlmaLinux
- openSUSE utiliza RPM como formato de pacote, embora tenha ferramentas próprias de gerenciamento.

---

## rpm — Gerenciador de Pacotes

O comando `rpm` trabalha diretamente com pacotes `.rpm`.

### Instalar

    sudo rpm -i programa.rpm

- `-i` — install — instalar

### Atualizar

    sudo rpm -U programa.rpm

- `-U` — upgrade — atualizar

### Remover

    sudo rpm -e programa

- `-e` — erase — apagar/remover

### Consultar pacote instalado

    rpm -q programa

- `-q` — query — consultar

### Listar todos os pacotes instalados

    rpm -qa

- `-q` — query — consultar
- `-a` — all — todos

### Mostrar informações do pacote

    rpm -qi programa

- `-q` — query — consultar
- `-i` — information — informações

### Listar arquivos instalados

    rpm -ql programa

- `-q` — query — consultar
- `-l` — list — listar

### Descobrir qual pacote fornece um arquivo

    rpm -qf /caminho/arquivo

- `-q` — query — consultar
- `-f` — file — arquivo

---

## Dependências

### Dependency — Dependência

Assim como nos pacotes `.deb`, um pacote `.rpm` pode depender de outros pacotes.

Exemplo:

    programa
       ↓
    biblioteca A
       ↓
    biblioteca B

O comando `rpm` trabalha diretamente com o pacote, mas **não é a ferramenta ideal para resolver automaticamente as dependências através dos repositórios**.

Para isso são utilizadas ferramentas de alto nível.

---

## DNF — Dandified YUM

**DNF — Dandified YUM — YUM modernizado** é o gerenciador de pacotes de alto nível utilizado atualmente em várias distribuições da família Red Hat.

### Atualizar informações dos repositórios

    sudo dnf check-update

- `check-update` — verificar atualizações

### Instalar

    sudo dnf install programa

- `install` — instalar

### Remover

    sudo dnf remove programa

- `remove` — remover

### Atualizar pacotes

    sudo dnf upgrade

- `upgrade` — atualizar

### Pesquisar

    dnf search programa

- `search` — pesquisar

### Mostrar informações

    dnf info programa

- `info` — informações

---

## YUM — Yellowdog Updater, Modified

**YUM — Yellowdog Updater, Modified — Atualizador Yellowdog Modificado** é uma ferramenta tradicional de gerenciamento de pacotes RPM.

Exemplos:

    sudo yum install programa
    sudo yum remove programa
    sudo yum update

Em sistemas modernos, o **DNF** é a ferramenta principal em muitas distribuições que anteriormente utilizavam YUM.

---

## Repositórios

### Repository — Repositório

Um **Repository — Repositório** é uma fonte de pacotes utilizada pelos gerenciadores de alto nível.

O DNF pode consultar os repositórios configurados para:

- localizar pacotes;
- resolver dependências;
- instalar pacotes;
- atualizar pacotes.

---

## RPM × DNF

| Ferramenta | Função |
|---|---|
| `rpm` | Gerenciamento direto de pacotes `.rpm` |
| `dnf` | Gerenciamento de alto nível |
| `yum` | Ferramenta tradicional de alto nível |
| `rpm -i` | Instalar `.rpm` |
| `rpm -U` | Atualizar `.rpm` |
| `rpm -e` | Remover pacote |
| `rpm -qa` | Listar pacotes instalados |
| `dnf install` | Instalar pelo repositório |
| `dnf remove` | Remover |
| `dnf upgrade` | Atualizar |

### Comparação com Debian

    Debian
       ↓
    .deb
       ↓
    dpkg
       ↓
    apt

    Red Hat
       ↓
    .rpm
       ↓
    rpm
       ↓
    dnf

---

## Resumo LPIC-1

- **RPM — Red Hat Package Manager** = sistema/formato de pacotes da família Red Hat.
- `.rpm` = formato de pacote RPM.
- `rpm -i` = instalar.
- `rpm -U` = atualizar.
- `rpm -e` = remover.
- `rpm -q` = consultar.
- `rpm -qa` = listar todos os pacotes instalados.
- `rpm -qi` = mostrar informações.
- `rpm -ql` = listar arquivos instalados.
- `rpm -qf` = descobrir qual pacote fornece um arquivo.
- **DNF — Dandified YUM** = gerenciador de alto nível.
- `dnf install` = instalar.
- `dnf remove` = remover.
- `dnf upgrade` = atualizar.
- `dnf search` = pesquisar.
- **YUM** = ferramenta tradicional de gerenciamento de pacotes RPM.
- **Dependency — Dependência** = outro pacote necessário para o funcionamento de um programa.
- `rpm` trabalha diretamente com `.rpm`; `dnf` trabalha com repositórios e resolve dependências.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
