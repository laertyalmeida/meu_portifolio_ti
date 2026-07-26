# Tempo estimado de leitura

**12 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* Criar o primeiro arquivo do projeto.
* Verificar o estado do repositório.
* Adicionar arquivos à área de preparação.
* Registrar a primeira versão do projeto com um commit.
* Entender o fluxo básico de trabalho do Git.

---

# Git e GitHub — Guia de Estudos

---

# Informações do capítulo

| Campo                   | Informação                                 |
| ----------------------- | ------------------------------------------ |
| **Capítulo**            | 05                                         |
| **Título**              | Primeiras Alterações em um Repositório Git |
| **Autor**               | Laerte Costa                               |
| **Sistema Operacional** | Debian GNU/Linux                           |
| **Terminal**            | Bash                                       |
| **Última atualização**  | Julho de 2026                              |

---

# Pré-requisitos

Recomenda-se ter concluído os capítulos anteriores.

---

# Conceito teórico

## Como o Git controla os arquivos?

Depois que um repositório é criado, o Git não registra automaticamente as alterações dos arquivos.

Antes de criar um **commit**, é necessário informar quais arquivos farão parte da próxima versão do projeto.

Esse processo acontece em três etapas:

1. Criar ou modificar um arquivo.
2. Adicionar o arquivo à área de preparação.
3. Registrar as alterações com um commit.

---

# Criando o primeiro arquivo

Dentro do diretório do projeto, crie um arquivo chamado `README.md`.

### Comando

```bash
touch README.md
```

**touch** → *touch* → *usado para criar arquivo* → *touch = tocar* → *apenar tocar o arquivo sem modificar seu conteúdo, apenas para alterar data/hora do arquivo* → *se não houver arquivo com o nome informado é criado um novo*

O arquivo README.md, normalmente é utilizado para apresentar informações sobre o projeto, como um índice.

---

# Verificando o estado do repositório

Após criar o arquivo, execute:

### Comando

```bash
git status
```

Exemplo:

```text
On branch master

No commits yet

Untracked files:
  README.md
```

A mensagem **Untracked files** indica que o arquivo existe, mas ainda não está sendo controlado pelo Git.

**untracked files** → *untracked* → *não rastreado* → *file* → *arquivos*

---

# Adicionando o arquivo

Para informar ao Git que esse arquivo deverá fazer parte da próxima versão do projeto, utilize:

### Comando

```bash
git add README.md
```

**add** → *adicionar*


Também é possível adicionar todos os arquivos do diretório utilizando:

```bash
git add .
```

**.** *o "ponto" . separado no final do comando indica o diretório local* → *tudo que tiver no diretório*

---

# Verificando novamente

Execute novamente:

### Comando

```bash
git status
```

Agora será exibida uma mensagem semelhante a:

```text
Changes to be committed:
  new file: README.md
```

**new file** → *new* → *novo* → *novo arquivo*

Isso significa que o arquivo foi adicionado à área de **preparação** e está pronto para ser registrado.

---

# Criando o primeiro commit

Agora registre a primeira versão do projeto.

### Comando

```bash
git commit -m "Primeiro commit"
```

**git commit -m "Primeiro commit" → *commit* → *registro* → *-m* → *message* → **mensagem* → *"Primeiro commit" → *mensagem informada para o nome do registro*

O comando está informando: Esse registro terá essa mensagem como nome. No log cada registro terá seu nome para identificá-lo.

Exemplo de saída:

```text
[master (root-commit) abc1234] Primeiro commit
 1 file changed
 create mode 100644 README.md
```

O commit cria um ponto no histórico do projeto.

A partir desse momento, o Git passa a controlar o arquivo.

---

# Verificando o repositório

Após o commit, execute novamente:

### Comando

```bash
git status
```

Resultado esperado:

```text
On branch master

nothing to commit, working tree clean
```

Essa mensagem indica que não existem alterações pendentes.

---

# Fluxo básico do Git

```text
Criar ou modificar um arquivo
             │
             ▼
       git status (verifica arquivos modificados)
             │
             ▼
         git add (inclui os arquios para serem registrados)
             │
             ▼
       git commit (registra os arquivos)
             │
             ▼
      Alteração registrada
```

---

# O que foi aprendido

* criar arquivos com `touch`;
* verificar o estado do repositório com `git status`;
* adicionar arquivos para áre de preparação utilizando `git add`;
* registrar alterações com `git commit`;
* compreender o fluxo básico de trabalho do Git.

---

# Resumo

Neste capítulo você criou o primeiro arquivo do projeto, adicionou esse arquivo ao Git e registrou a primeira versão utilizando um commit.

A partir de agora, o projeto possui um histórico de alterações que poderá ser consultado a qualquer momento.

---

# Próximo capítulo

## 06 - Consultando o Histórico de Alterações

No próximo capítulo você aprenderá a utilizar o comando `git log` para visualizar todos os commits realizados no repositório.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

