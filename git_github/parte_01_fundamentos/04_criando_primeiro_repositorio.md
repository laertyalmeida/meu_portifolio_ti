# Tempo estimado de leitura

**10 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* Criar um diretório para um projeto.
* Inicializar um repositório Git.
* Identificar a pasta `.git`.
* Verificar o estado do repositório com `git status`.

---

# Git e GitHub — Guia de Estudos

---

# Informações do capítulo

| Campo                   | Informação                         |
| ----------------------- | ---------------------------------- |
| **Capítulo**            | 04                                 |
| **Título**              | Criando o Primeiro Repositório Git |
| **Autor**               | Laerte Costa                       |
| **Sistema Operacional** | Debian GNU/Linux                   |
| **Terminal**            | Bash                               |
| **Última atualização**  | Julho de 2026                      |

---

# Pré-requisitos

Recomenda-se ter concluído os capítulos anteriores.

---

# Conceito teórico

## O que é um repositório?

Um **repositório** é um diretório que passou a ser controlado pelo Git.

A partir desse momento, o Git pode acompanhar as alterações realizadas nos arquivos do projeto e manter um histórico de suas versões.

---

# Criando um diretório para o projeto

Primeiro, crie uma pasta para o projeto.

### Comando

```bash
mkdir meu_projeto
```

**mkdir** → *mk* → *make* → *criar* → *dir* → *directory* → *diretório* → *criar um novo diretório (nova pasta)*

Acesse o diretório criado.

### Comando

```bash
cd meu_projeto
```
**cd** → *change directory* → *mudar de diretório*
**cd meu_projeto** → *mudar para o diretório: meu_projeto/*

---

# Inicializando o repositório

Dentro do diretório onde foi acessaceo pelo comando cd, execute:

### Comando

```bash
git init
```

**init** → *initialize* → *inicializar* → *inicializar, começar um novo repositório*


Se tudo ocorrer corretamente, será exibida uma mensagem semelhante a esta:

```text
Initialized empty Git repository in /home/usuario/meu_projeto/.git/
```

Isso indica que o diretório foi transformado em um repositório Git.

---

# O que mudou?

Após executar `git init`, o Git cria uma pasta oculta chamada:

```text
.git
```

Para visualizá-la, utilize:

### Comando

```bash
ls -a
```
**ls -a** → *ls* → *list* → *lista* → *-a* → *all* → *todos* → *listar todos os arquivos, inclusive os ocultos*

Exemplo:

```text
.
..
.git
```

A pasta `.git` contém as informações utilizadas pelo Git para controlar o repositório.

---

# Verificando o estado do repositório

Para verificar a situação atual do repositório, utilize:

### Comando

```bash
git status
```

**status** → *estado* → *o status, apresenta o estado de modificações/realizações feitas no repositório*

Exemplo:

```text
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

Como o repositório acabou de ser criado, ainda não existem arquivos sendo controlados nem commits realizados.

---

# O que foi aprendido

* um repositório é um diretório controlado pelo Git;
* `mkdir` cria um diretório;
* `cd` acessa um diretório;
* `git init` inicializa um repositório Git;
* `ls -a` permite visualizar a pasta `.git`;
* `git status` mostra a situação atual do repositório.

---

# Resumo

Neste capítulo você criou seu primeiro repositório Git.

Também aprendeu que o comando `git init` cria a estrutura necessária para que o Git acompanhe as alterações do projeto.

---

# Próximo capítulo

## 05 - Salvando Alterações com o Primeiro Commit

No próximo capítulo você criará seu primeiro arquivo, aprenderá a utilizar os comandos `git add` e `git commit` e registrará a primeira versão do projeto.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

