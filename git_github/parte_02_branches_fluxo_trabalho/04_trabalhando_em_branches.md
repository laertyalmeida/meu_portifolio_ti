**Tempo estimado:** 20 minutos

**Nível:** Iniciante

## Capítulo 04 — Trabalhando em Branches

---

# Pré-requisitos

Antes de iniciar este capítulo é recomendado compreender como criar e alternar entre Branches.

---

# Neste capítulo você aprenderá

* Como trabalhar dentro de uma Branch.
* Como os commits ficam isolados.
* Como visualizar o histórico da Branch atual.
* Por que diferentes Branches podem possuir conteúdos diferentes.

---

# Trabalhando em uma Branch

Depois de criar e alternar para uma Branch, todas as alterações realizadas passam a pertencer somente a ela.

Isso significa que você pode modificar arquivos, criar novos commits e testar funcionalidades sem afetar outras Branches do projeto.

Exemplo:

```text
main

A ─── B ─── C
             \
login         D ─── E
```

Enquanto você trabalha na Branch `login`, a Branch `main` permanece apontando para o commit `C`.

---

# Representação visual

Antes de novos commits:

```text
main
 │
 ▼

A ─── B ─── C
      ▲
      │
    login
```

Após dois commits na Branch `login`:

```text
main
 │
 ▼

A ─── B ─── C
             \
login         D ─── E
              ▲
              │
             HEAD
```

Observe que apenas a Branch `login` recebeu novos commits.

---

# Comandos

Para visualizar o histórico da Branch atual:

```bash
git log
```

---

# Significado dos comandos

## `git`

Sistema de controle de versão distribuído.

### `log`

**Tradução:** Histórico.

Exibe os commits pertencentes ao histórico da Branch atual.

---

# Resultado

Exemplo do comando:

```bash
git log
```

Saída:

```text
commit e7b41366d30bdf9d51491ccc4625cd2afb907e30
Author: Laerte Costa
Date: Sat Aug 1 18:51:24 2026 -0300

    Padronizar Rodapé
```

---

# Explicação da saída

### `commit`

Identificador único (hash) do commit.

### `Author`

Autor que realizou o commit.

### `Date`

Data e horário do registro.

### Mensagem

Descrição informada durante o commit.

Cada novo commit realizado na Branch será adicionado ao histórico exibido pelo `git log`.

---

# O que aconteceu internamente?

Sempre que um novo commit é criado, o Git atualiza apenas a Branch atual.

Exemplo:

Antes:

```text
main
 │
 ▼

A ─── B ─── C
      ▲
      │
    login
```

Após um novo commit:

```text
main
 │
 ▼

A ─── B ─── C
             \
login         D
              ▲
              │
             HEAD
```

A Branch `main` continua apontando para o commit `C`.

Somente a Branch `login` avança para o commit `D`.

Esse isolamento permite desenvolver novas funcionalidades sem modificar a versão principal do projeto.

---

# Atenção

Criar commits em uma Branch **não atualiza automaticamente** as demais Branches.

Cada Branch possui seu próprio histórico até que seja realizada uma integração utilizando comandos como `git merge`, assunto que será estudado mais adiante.

---

# Resumo

Neste capítulo você aprendeu que cada Branch possui seu próprio histórico de commits. Também compreendeu que novos commits afetam apenas a Branch ativa, permitindo desenvolver funcionalidades e corrigir problemas de forma isolada e segura.

---

# Próximo capítulo

## Capítulo 05 — Comparando Branches

No próximo capítulo você aprenderá como comparar Branches, visualizar diferenças entre elas e identificar alterações antes de realizar uma integração.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

