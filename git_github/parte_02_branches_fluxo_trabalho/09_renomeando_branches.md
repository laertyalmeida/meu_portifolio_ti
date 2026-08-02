**Tempo estimado:** 15 minutos

**Nível:** Iniciante

# Capítulo 09 — Renomeando Branches

---

# Pré-requisitos

Antes de iniciar este capítulo é recomendado compreender como criar, alternar e excluir Branches.

---

# Neste capítulo você aprenderá

* Como renomear uma Branch.
* O comando `git branch -m`.
* A diferença entre renomear a Branch atual e outra Branch.
* Como verificar se a alteração foi realizada corretamente.

---

# Por que renomear uma Branch?

Durante o desenvolvimento, pode acontecer de uma Branch receber um nome inadequado ou que não siga o padrão adotado pelo projeto.

Nesses casos, o Git permite alterar o nome da Branch sem perder seu histórico de commits.

---

# Comandos

Para renomear a Branch atual:

```bash
git branch -m novo-nome
```

Para renomear outra Branch:

```bash
git branch -m nome-antigo novo-nome
```

---

# Significado do comando

## `git`

Sistema de controle de versão distribuído.

### `branch`

Gerencia as Branches do repositório.

### `-m`

**Tradução:** **move** (mover ou renomear).

Altera o nome de uma Branch existente.

### `novo-nome`

Novo nome que será atribuído à Branch.

### `nome-antigo`

Nome atual da Branch que será renomeada.

---

# Resultado

Exemplo:

```bash
git branch -m login autenticacao
```

O comando normalmente não exibe nenhuma mensagem.

Para confirmar a alteração, execute:

```bash
git branch
```

Resultado:

```text
* autenticacao
main
```

A Branch `login` passou a se chamar `autenticacao`.

---

# Explicação da saída

O símbolo `*` indica a Branch atualmente ativa.

Observe que o nome anterior não aparece mais na listagem.

Todos os commits permanecem preservados.

---

# O que aconteceu internamente?

Ao renomear uma Branch, o Git altera apenas o nome da referência.

Os commits continuam exatamente os mesmos.

Exemplo:

Antes:

```text
main

A ─── B ─── C
             \
login         D ─── E
```

Depois:

```text
main

A ─── B ─── C
             \
autenticacao  D ─── E
```

O histórico não é modificado.

Apenas o nome da Branch é atualizado.

---

# Atenção

Caso já exista uma Branch com o novo nome informado, o Git impedirá a alteração para evitar duplicidade.

Antes de renomear uma Branch, utilize:

```bash
git branch
```

para verificar os nomes existentes.

---

# Resumo

Neste capítulo você aprendeu como renomear Branches utilizando `git branch -m`. Também compreendeu que essa operação altera apenas o nome da referência, preservando todo o histórico de commits.

---

# Próximo capítulo

## Capítulo 10 — Fluxo de Trabalho com Branches

No próximo capítulo você aprenderá como organizar o desenvolvimento utilizando Branches, desde a criação de uma funcionalidade até sua integração à Branch principal, seguindo um fluxo de trabalho utilizado em projetos reais.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

