# Tempo estimado de leitura

**15 minutos**

**Nível:** Iniciante

**Capítulo:** 01 — Introdução às Branches

---

# Pré-requisitos

Antes de iniciar este capítulo é recomendado compreender os capítulos anteriores da Parte 1.

---

# Neste capítulo você aprenderá

* O que é uma Branch.
* Por que utilizar Branches.
* Como o Git organiza diferentes linhas de desenvolvimento.
* O conceito de `HEAD`.
* Como visualizar as Branches existentes.

---

# O que é uma Branch?

Uma **Branch** é uma linha independente de desenvolvimento dentro do repositório.

Ela permite criar novas funcionalidades, corrigir erros ou realizar testes sem modificar diretamente a Branch principal.

Isso torna o desenvolvimento mais seguro e organizado, principalmente quando várias pessoas trabalham no mesmo projeto.

---

# Representação visual

Antes da criação de uma nova Branch:

```text
main

A ─── B ─── C
```

Após criar uma Branch chamada `login`:

```text
main

A ─── B ─── C
             \
              login
```

Inicialmente, as duas Branches apontam para o mesmo commit.

Somente após novos commits seus históricos começam a se diferenciar.

---

# O conceito de HEAD

O **HEAD** é um ponteiro em forma de * *(asterisco)* utilizado pelo Git para indicar qual Branch está ativa.

Todos os commits serão registrados na Branch apontada pelo HEAD.

Exemplo:

```text
        HEAD
         │
         ▼

main

A ─── B ─── C
```

Se o HEAD estiver apontando para `main`, todos os novos commits serão adicionados nessa Branch.

---

# Glossário

| Termo     | Tradução    | Significado                           |
| --------- | ----------- | ------------------------------------- |
| Branch    | Ramificação | Linha independente de desenvolvimento |
| HEAD      | Cabeça      | Ponteiro para a Branch atual (*)      |
| Commit    | Registro    | Alteração salva no histórico          |
| Reference | Referência  | Ponteiro para um commit               |

---

# Comando

Para visualizar as Branches existentes utilize:

```bash
git branch
```

---

# Significado do comando

## `git`

Sistema de controle de versão distribuído.

---

## `branch`

**Tradução:** Ramificação.

Quando utilizado sem argumentos, lista todas as Branches existentes no repositório.

---

# Resultado

Exemplo:

```text
* main
```

---

# Explicação da saída

### `*`

Indica a Branch atualmente ativa.

### `main`

Nome da Branch onde o HEAD está apontando.

Caso existam outras Branches:

```text
feature-login
* main
```

Apenas a Branch marcada com `*` está ativa.

---

# O que aconteceu internamente?

Ao executar:

```bash
git branch
```

o Git consulta as referências armazenadas no repositório e exibe as Branches existentes.

Esse comando:

* não cria commits;
* não altera arquivos;
* não modifica o histórico;
* apenas consulta informações.

---

# Resumo

Neste capítulo você conheceu o conceito de Branch e compreendeu que ela representa uma linha independente de desenvolvimento. Também aprendeu a função do HEAD, utilizou o comando `git branch` para listar as Branches existentes e interpretou a saída apresentada pelo Git.

---

# Próximo capítulo

## Capítulo 02 — Criando Branches

No próximo capítulo você aprenderá como criar novas Branches utilizando os comandos:

```bash
git branch nome-da-branch
```

e

```bash
git switch -c nome-da-branch
```

Além disso, entenderá quando utilizar cada comando e as diferenças entre eles.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

