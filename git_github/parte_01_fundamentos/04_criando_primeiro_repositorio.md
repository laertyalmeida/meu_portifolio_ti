# Tempo estimado de leitura

**10 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* Criar um diretório para um projeto.
* Inicializar um repositório Git.
* Identificar a pasta `.git`.
* Verificar o estado do repositório com `git status`.
* Compreender a estrutura básica de um repositório Git.

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

# Objetivo deste capítulo

Aprender a criar um diretório para um projeto, inicializar um repositório Git e compreender as alterações realizadas pelo comando `git init`.

---

# Pré-requisitos

Recomenda-se ter concluído os capítulos anteriores.

---

# Conceito teórico

## O que é um repositório?

Um **repositório** é um diretório que passou a ser controlado pelo Git.

A partir desse momento, o Git passa a acompanhar todas as alterações realizadas nos arquivos do projeto, mantendo um histórico organizado de suas versões.

Todo projeto versionado pelo Git possui um repositório.

---

# Criando um diretório para o projeto

Primeiro, crie uma pasta para armazenar o projeto.

### Comando

```bash
mkdir meu_projeto
```

### Explicação

O comando `mkdir` cria um novo diretório no sistema.

**mkdir** → *make directory* → *criar diretório.*

---

Agora acesse o diretório criado.

### Comando

```bash
cd meu_projeto
```

### Explicação

O comando `cd` altera o diretório atual do terminal.

**cd** → *change directory* → *mudar de diretório.*

**meu_projeto** → *nome do diretório que será acessado.*

---

# Inicializando o repositório

Dentro do diretório recém-criado, execute:

### Comando

```bash
git init
```

### Explicação

Esse comando inicializa um novo repositório Git dentro do diretório atual.

A partir desse momento, o Git passa a controlar o projeto.

**git** → *programa executado.*

**init** → *initialize* → *inicializar* → *cria um novo repositório Git.*

Se tudo ocorrer corretamente, será exibida uma mensagem semelhante a esta:

```text
Initialized empty Git repository in /home/usuario/meu_projeto/.git/
```

Isso indica que o diretório foi transformado em um repositório Git.

> **Observação**
>
> O comando `git init` precisa ser executado apenas uma vez em cada projeto.

---

# O que mudou?

Após executar `git init`, o Git cria um diretório oculto chamado:

```text
.git
```

Esse diretório contém todas as informações necessárias para o funcionamento do Git.

Nele são armazenados, entre outros dados:

- histórico de commits;
- branches;
- configurações do repositório;
- referências internas utilizadas pelo Git.

---

# Visualizando a pasta `.git`

Como esse diretório é oculto, utilize o comando abaixo para visualizá-lo.

### Comando

```bash
ls -a
```

### Explicação

O comando `ls` lista os arquivos e diretórios.

A opção `-a` também exibe os arquivos ocultos.

**ls** → *list* → *listar.*

**-a** → *all* → *todos* → *inclui arquivos ocultos.*

Exemplo:

```text
.
..
.git
```

Se o diretório `.git` estiver presente, significa que o repositório foi criado com sucesso.

---

# Verificando o estado do repositório

Para verificar a situação atual do repositório, utilize:

### Comando

```bash
git status
```

### Explicação

Esse comando informa a situação atual do repositório.

Ele mostra, por exemplo:

- arquivos modificados;
- arquivos novos;
- arquivos preparados para commit;
- branch atual.

**status** → *estado* → *apresenta o estado atual do repositório.*

Exemplo:

```text
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

Como o repositório acabou de ser criado, ainda não existem arquivos sendo controlados nem commits realizados.

> **Boa prática**
>
> Acostume-se a executar `git status` antes e depois de realizar alterações. Esse comando será um dos mais utilizados durante o desenvolvimento de projetos.

---

## Curiosidade

Embora a pasta `.git` seja apenas mais um diretório do sistema, ela é considerada o "coração" do repositório.

Se ela for removida, o projeto continuará existindo, mas deixará de ser um repositório Git e todo o histórico de versionamento será perdido.

---

# Resumo

Neste capítulo você criou seu primeiro repositório Git.

Também aprendeu que o comando `git init` cria a estrutura necessária para que o Git acompanhe todas as alterações realizadas no projeto.

Além disso, conheceu a pasta `.git` e utilizou o comando `git status` para consultar o estado do repositório.

---

# O que você aprendeu

Ao concluir este capítulo, você é capaz de:

- ✅ Criar um diretório para um projeto.
- ✅ Inicializar um repositório Git.
- ✅ Identificar a pasta `.git`.
- ✅ Verificar o estado do repositório.
- ✅ Compreender a função do comando `git status`.

---

# Próximo capítulo

## Capítulo 05 — Salvando Alterações com o Primeiro Commit

No próximo capítulo você criará seu primeiro arquivo, aprenderá a utilizar os comandos `git add` e `git commit` e registrará a primeira versão do projeto.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

