# Tempo estimado de leitura

**12 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* Criar o primeiro arquivo do projeto.
* Verificar o estado do repositório.
* Adicionar arquivos à área de preparação.
* Registrar a primeira versão do projeto com um commit.
* Compreender o fluxo básico de trabalho do Git.

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

# Objetivo deste capítulo

Aprender o fluxo básico de trabalho do Git, criando o primeiro arquivo do projeto, adicionando-o à área de preparação e registrando a primeira versão do repositório por meio de um commit.

---

# Pré-requisitos

Recomenda-se ter concluído os capítulos anteriores.

---

# Conceito teórico

## Como o Git controla os arquivos?

Depois que um repositório é criado, o Git **não registra automaticamente** as alterações realizadas nos arquivos.

Antes de criar um **commit**, é necessário informar ao Git quais arquivos farão parte da próxima versão do projeto.

Esse processo ocorre em três etapas:

1. Criar ou modificar um arquivo.
2. Adicionar o arquivo à área de preparação (*Staging Area*).
3. Registrar as alterações com um commit.

Esse fluxo será utilizado durante todo o trabalho com Git.

---

# Criando o primeiro arquivo

Dentro do diretório do projeto, crie um arquivo chamado `README.md`.

### Comando

```bash
touch README.md
```

### Explicação

O comando `touch` pode criar um novo arquivo vazio ou, caso o arquivo já exista, apenas atualizar sua data e hora de modificação.

Nesse exemplo, como o arquivo ainda não existe, ele será criado.

O arquivo `README.md` normalmente é utilizado para apresentar informações sobre o projeto, como descrição, instruções de uso, documentação e índice do conteúdo.

**touch** → *tocar* → *atualiza a data e hora de um arquivo existente ou cria um novo arquivo vazio caso ele ainda não exista.*

**README** → *Read Me* → *"Leia-me"* → *arquivo utilizado para apresentar informações sobre o projeto.*

**.md** → *Markdown* → *formato de texto utilizado para documentação.*

---

# Verificando o estado do repositório

Após criar o arquivo, execute:

### Comando

```bash
git status
```

### Explicação

O comando `git status` informa a situação atual do repositório.

Exemplo:

```text
On branch master

No commits yet

Untracked files:
  README.md
```

A mensagem **Untracked files** indica que o arquivo existe no diretório, porém ainda não está sendo controlado pelo Git.

**Untracked** → *não rastreado.*

**Files** → *arquivos.*

---

# Adicionando o arquivo

Para informar ao Git que esse arquivo deverá fazer parte da próxima versão do projeto, utilize:

### Comando

```bash
git add README.md
```

### Explicação

O comando `git add` adiciona arquivos à área de preparação (*Staging Area*).

Somente os arquivos adicionados nessa área poderão ser registrados no próximo commit.

**add** → *adicionar.*

---

Também é possível adicionar todos os arquivos do diretório atual utilizando:

### Comando

```bash
git add .
```

### Explicação

O ponto (`.`) representa o diretório atual.

Assim, todos os arquivos existentes nesse diretório serão adicionados à área de preparação.

**.** → *diretório atual.*

> **Boa prática**
>
> Embora `git add .` seja muito utilizado, acostume-se a executar `git status` antes dele. Assim você evita adicionar arquivos que não deveriam fazer parte do commit.

---

# Verificando novamente

Execute novamente:

### Comando

```bash
git status
```

### Explicação

Agora será exibida uma mensagem semelhante a:

```text
Changes to be committed:
  new file: README.md
```

Isso significa que o arquivo foi adicionado à área de preparação e está pronto para ser registrado.

**Changes to be committed** → *alterações prontas para serem registradas.*

**new file** → *novo arquivo.*

---

# Criando o primeiro commit

Agora registre a primeira versão do projeto.

### Comando

```bash
git commit -m "Primeiro commit"
```

### Explicação

O comando `git commit` cria um novo registro no histórico do projeto.

A opção `-m` permite informar uma mensagem descrevendo as alterações realizadas.

Essa mensagem facilita a identificação dos commits durante a evolução do projeto.

**commit** → *comprometer* → *registro permanente das alterações.*

**-m** → *message* → *mensagem.*

**"Primeiro commit"** → *mensagem que identifica esse registro no histórico.*

Exemplo de saída:

```text
[master (root-commit) abc1234] Primeiro commit
 1 file changed
 create mode 100644 README.md
```

A partir desse momento, o Git passa a controlar o arquivo e registra a primeira versão do projeto.

---

# Verificando o repositório

Após o commit, execute novamente:

### Comando

```bash
git status
```

### Explicação

Resultado esperado:

```text
On branch master

nothing to commit, working tree clean
```

Essa mensagem indica que todas as alterações foram registradas e que o diretório de trabalho está limpo.

**nothing to commit** → *não há alterações para registrar.*

**working tree clean** → *diretório de trabalho limpo.*

---

# Fluxo básico do Git

```text
Criar ou modificar um arquivo
             │
             ▼
       git status
 (verifica o estado do repositório)
             │
             ▼
          git add
 (adiciona os arquivos à área de preparação)
             │
             ▼
        git commit
 (registra as alterações no histórico)
             │
             ▼
      Alteração registrada
```

---

## Curiosidade

A área de preparação (*Staging Area*) é um dos recursos que diferencia o Git de muitos outros sistemas de controle de versão.

Ela permite escolher exatamente quais alterações farão parte de cada commit.

---

# Resumo

Neste capítulo você criou o primeiro arquivo do projeto, adicionou esse arquivo à área de preparação e registrou a primeira versão do repositório utilizando um commit.

Você também conheceu o fluxo básico de trabalho do Git, que será utilizado em todos os capítulos seguintes.

---

# O que você aprendeu

Ao concluir este capítulo, você é capaz de:

- ✅ Criar arquivos utilizando `touch`.
- ✅ Verificar o estado do repositório com `git status`.
- ✅ Adicionar arquivos à área de preparação utilizando `git add`.
- ✅ Registrar alterações utilizando `git commit`.
- ✅ Compreender o fluxo básico de trabalho do Git.

---

# Próximo capítulo

## Capítulo 06 — Consultando o Histórico de Alterações

No próximo capítulo você aprenderá a utilizar o comando `git log` para visualizar todos os commits realizados no repositório.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**
