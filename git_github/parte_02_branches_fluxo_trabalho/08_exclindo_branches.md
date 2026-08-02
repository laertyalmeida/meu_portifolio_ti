**Tempo estimado:** 15 minutos

**Nível:** Iniciante

# Capítulo 08 — Excluindo Branches

---

# Pré-requisitos

Antes de iniciar este capítulo é recomendado compreender o funcionamento do comando `git merge`.

---

# Neste capítulo você aprenderá

* Como excluir uma Branch local.
* A diferença entre `-d` e `-D`.
* Como listar as Branches antes da exclusão.
* Boas práticas ao remover Branches.

---

# Por que excluir uma Branch?

Após concluir uma funcionalidade e realizar o merge, normalmente a Branch utilizada deixa de ser necessária.

Removê-la ajuda a manter o repositório organizado, facilitando a identificação das Branches que ainda estão em desenvolvimento.

---

# Comandos

Para listar as Branches existentes:

```bash
git branch
```

Para excluir uma Branch já integrada:

```bash
git branch -d nome-da-branch
```

Para forçar a exclusão de uma Branch:

```bash
git branch -D nome-da-branch
```

---

# Significado do comando

## `git`

Sistema de controle de versão distribuído.

### `branch`

Gerencia as Branches do repositório.

### `-d`

**Tradução:** **delete** (excluir).

Remove uma Branch somente se ela já tiver sido integrada ao histórico.

### `-D`

-D é um atalho para --delete --force

**Tradução:** **delete** (excluir) **force** (forçar)

Remove a Branch independentemente de ela ter sido integrada.

Equivale a forçar a exclusão.

### `nome-da-branch`

Nome da Branch que será removida.

Exemplo:

```bash
git branch -d login
```

---

# Resultado

Quando a exclusão ocorre com sucesso, o Git apresenta uma mensagem semelhante a:

```text
Deleted branch login (was 5c8d913).
```

---

# Explicação da saída

### `Deleted branch`

Indica que a Branch foi removida.

### `login`

Nome da Branch excluída.

### `(was 5c8d913)`

Mostra o último commit para o qual essa Branch apontava antes da exclusão.

Os commits **não são apagados** se continuarem acessíveis por outra Branch, como a `main`.

---

# O que aconteceu internamente?

Ao excluir uma Branch, o Git remove apenas a referência que apontava para aquele histórico.

Os commits permanecem preservados caso já tenham sido incorporados a outra Branch.

Por isso, excluir uma Branch normalmente **não significa perder o trabalho realizado**.

---

# Atenção

Não é possível excluir a Branch em que você está trabalhando.

Exemplo:

```bash
git branch -d main
```

Se a `main` for a Branch atual, o Git exibirá um erro.

Antes de excluir uma Branch, alterne para outra:

```bash
git switch main
```

ou outra Branch existente, conforme o caso.

---

# Resumo

Neste capítulo você aprendeu como excluir Branches locais utilizando `git branch -d` e `git branch -D`. Também compreendeu a diferença entre uma exclusão segura e uma exclusão forçada, além de entender que a remoção da Branch elimina apenas a referência, preservando os commits já integrados ao histórico.

---

# Próximo capítulo

## Capítulo 09 — Renomeando Branches

No próximo capítulo você aprenderá como alterar o nome de uma Branch local utilizando o comando `git branch -m`, além de conhecer situações em que essa prática é útil durante o desenvolvimento.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

