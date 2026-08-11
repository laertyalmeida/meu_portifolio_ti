# Capítulo 02 — Instalação do Git no Debian

**Tempo estimado de leitura:** 8 minutos
**Nível:** Iniciante

---

# Git e GitHub — Guia de Estudos

## Informações do capítulo

| Campo                   | Informação                  |
| ----------------------- | --------------------------- |
| **Capítulo**            | 02                          |
| **Título**              | Instalação do Git no Debian |
| **Autor**               | Laerte Costa                |
| **Sistema Operacional** | Debian GNU/Linux            |
| **Terminal**            | Bash                        |
| **Última atualização**  | Agosto de 2026              |

---

# Objetivo

Neste capítulo, vamos aprender a verificar se o Git já está instalado no Debian, instalar o Git usando o APT e confirmar se tudo funcionou corretamente.

---

# Conceito teórico

## O que é instalar um programa?

Instalar um programa significa colocar os arquivos necessários no sistema e realizar as configurações para que ele possa ser utilizado.

No Debian, uma das formas mais comuns de instalar programas é utilizando o **APT**.

**APT** significa **Advanced Package Tool** e é o gerenciador de pacotes utilizado pelo Debian e por outras distribuições baseadas nele.

Com o APT podemos:

* instalar programas;
* atualizar pacotes;
* remover programas;
* consultar informações sobre pacotes;
* resolver automaticamente algumas dependências.

---

# Verificando se o Git já está instalado

Antes de instalar um programa, é uma boa prática verificar se ele já está instalado.

### Comando

```bash
git --version
```

### O que o comando faz?

Mostra a versão do Git instalada no sistema.

Exemplo:

```text
git version 2.39.5
```

Se aparecer uma versão, o Git já está instalado.

Se aparecer uma mensagem como:

```text
bash: git: command not found
```

significa que o sistema não encontrou o comando `git`.

> **Boa prática**
>
> Sempre verifique primeiro se o programa já está instalado. Isso evita fazer uma instalação desnecessária.

---

# Consultando o pacote do Git

Também podemos consultar informações sobre o pacote `git` usando o APT.

### Comando

```bash
apt list git
```

### O que o comando faz?

Mostra informações sobre o pacote **git** disponível nos repositórios configurados no sistema.

Se o Git já estiver instalado, normalmente aparecerá:

```text
[installed]
```

Aqui:

* `apt` → gerenciador de pacotes;
* `list` → lista informações sobre um pacote;
* `git` → nome do pacote que queremos consultar.

---

# Atualizando a lista de pacotes

Antes de instalar um programa, é recomendado atualizar a lista de pacotes disponíveis nos repositórios.

### Comando

```bash
sudo apt update
```

### O que o comando faz?

O `apt update` consulta os repositórios configurados no Debian e atualiza a lista de programas e versões disponíveis.

Esse comando **não atualiza os programas instalados**.

Ele apenas atualiza as informações que o APT utiliza para saber quais pacotes estão disponíveis.

### Entendendo o comando

**sudo** → executa o comando com privilégios administrativos.

**apt** → gerenciador de pacotes.

**update** → atualiza a lista de pacotes disponíveis.

> **Importante**
>
> `apt update` e `apt upgrade` têm funções diferentes.
>
> * `apt update` → atualiza a lista de pacotes.
> * `apt upgrade` → atualiza os pacotes instalados.
>
> O comando `apt upgrade` será estudado posteriormente.

---

# Instalando o Git

Depois de atualizar a lista de pacotes, podemos instalar o Git.

### Comando

```bash
sudo apt install git
```

### O que o comando faz?

O APT procura o pacote `git` nos repositórios configurados, baixa os arquivos necessários e realiza a instalação.

Durante o processo, o sistema pode solicitar a senha do usuário.

### Entendendo o comando

**sudo** → executa o comando com privilégios administrativos.

**apt** → gerenciador de pacotes.

**install** → instala um pacote.

**git** → pacote que será instalado.

---

# Confirmando a instalação

Depois de instalar o Git, vamos verificar se ele está funcionando corretamente.

### Comando

```bash
git --version
```

Se aparecer a versão do Git, a instalação foi concluída com sucesso.

Exemplo:

```text
git version 2.39.5
```

---

# Localizando o executável do Git

Também podemos descobrir onde o executável do Git está localizado no sistema.

### Comando

```bash
which git
```

Exemplo:

```text
/usr/bin/git
```

### O que o comando faz?

O `which` mostra o caminho do executável que será utilizado quando o comando for executado no terminal.

**which** → mostra qual executável será utilizado.

Nesse exemplo:

```text
/usr/bin/git
```

significa que o executável do Git está localizado no diretório `/usr/bin`.

---

# Entendendo o PATH

Quando digitamos um comando no terminal, como:

```bash
git
```

o sistema procura o programa nos diretórios definidos na variável de ambiente **PATH**.

Podemos visualizar o conteúdo do PATH com:

```bash
echo $PATH
```

O comando `which git` ajuda a descobrir qual arquivo executável será encontrado pelo sistema.

---

# Curiosidade

O Debian prioriza **estabilidade e segurança**.

Por isso, a versão de um programa disponível nos repositórios oficiais pode não ser a versão mais recente lançada pelo desenvolvedor.

Isso acontece porque os pacotes passam por testes antes de serem disponibilizados para a versão estável do Debian.

Para quem está começando, utilizar os pacotes dos repositórios oficiais é uma forma simples e segura de instalar programas.

---

# Resumo do processo

```text
Verificar se o Git está instalado
              │
              ▼
 Atualizar a lista de pacotes
              │
              ▼
       Instalar o Git
              │
              ▼
 Confirmar a instalação
              │
              ▼
 Localizar o executável
```

---

# Comandos utilizados

| Comando                | Função                                  |
| ---------------------- | --------------------------------------- |
| `git --version`        | Verifica a versão do Git                |
| `apt list git`         | Consulta informações sobre o pacote Git |
| `sudo apt update`      | Atualiza a lista de pacotes             |
| `sudo apt install git` | Instala o Git                           |
| `which git`            | Mostra o caminho do executável          |
| `echo $PATH`           | Mostra os diretórios presentes no PATH  |

---

# O que você aprendeu

Neste capítulo, você aprendeu a:

* verificar se o Git está instalado;
* consultar informações sobre o pacote Git;
* atualizar a lista de pacotes do Debian;
* instalar o Git usando o APT;
* confirmar se a instalação foi realizada corretamente;
* localizar o executável do Git;
* entender de forma básica o funcionamento do `PATH`.

---

# Próximo capítulo

## Capítulo 03 — Configuração da Identidade do Git

No próximo capítulo, vamos configurar o **nome** e o **e-mail** utilizados pelo Git.

Essas informações são registradas nos commits e permitem identificar quem realizou cada alteração no projeto.

---

## 📚 Fonte de estudo

Este capítulo foi elaborado a partir dos meus estudos sobre **Git, GitHub, Linux e gerenciamento de pacotes no Debian**, utilizando os conteúdos estudados como referência e organizando as informações com minhas próprias palavras para facilitar a revisão e o aprendizado.

> **Observação:** este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo original das disciplinas e materiais utilizados como referência não deve ser reproduzido integralmente neste repositório.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

