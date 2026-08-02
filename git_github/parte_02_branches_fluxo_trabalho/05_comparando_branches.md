**Tempo estimado:** 20 minutos

**Nível:** Iniciante

# Capítulo 05 — Comparando Branches

---

# Pré-requisitos

Antes de iniciar este capítulo é recomendado compreender como criar, alternar e trabalhar em Branches.

---

# Neste capítulo você aprenderá

* Como comparar Branches.
* O comando `git diff`.
* Como visualizar alterações antes de realizar um merge.
* Como interpretar a saída do `git diff`.

---

# Comparando Branches

Durante o desenvolvimento é comum possuir duas ou mais Branches com alterações diferentes.

Antes de integrá-las, é recomendável verificar quais mudanças foram realizadas.

Para isso utilizamos o comando:

```bash
git diff branch-origem branch-destino
```

---

# Representação visual

```text
main

A ─── B ─── C
             \
login         D ─── E
```

Nesse exemplo, a Branch `login` possui dois commits que ainda não existem na `main`.

---

# Comando

Para comparar as Branches `main` e `login`:

```bash
git diff main login
```

---

# Significado do comando

## `git`

Sistema de controle de versão distribuído.

### `diff`

**Tradução:** Diferença.

Compara arquivos, commits ou Branches.

### `main`

Branch de origem da comparação.

### `login`

Branch que será comparada.

---

# Resultado

O Git exibirá as diferenças encontradas entre as duas Branches.

Exemplo simplificado:

```diff
diff --git a/login.py b/login.py
index 3f1d4a2..6f8d7b1 100644

- print("Login antigo")
+ print("Novo sistema de login")
```

---

# Explicação da saída

### `-`

Linha removida.

### `+`

Linha adicionada.

As demais linhas servem como contexto para facilitar a identificação das alterações.

---

# O que aconteceu internamente?

Ao executar:

```bash
git diff main login
```

o Git compara os snapshots das duas Branches.

Nenhum arquivo é modificado.

Nenhum commit é criado.

O comando apenas analisa o conteúdo armazenado no histórico e apresenta as diferenças encontradas.

---

# Atenção

O comando:

```bash
git diff main login
```

não altera o repositório.

Ele apenas exibe informações.

Caso nenhuma diferença seja encontrada, nenhuma saída será apresentada.

---

# Resumo

Neste capítulo você aprendeu como comparar duas Branches utilizando `git diff`. Também compreendeu que esse comando apenas exibe diferenças entre os conteúdos, sendo uma ferramenta importante para revisar alterações antes de integrar Branches.

---

# Próximo capítulo

## Capítulo 06 — Mesclando Branches (`git merge`)

No próximo capítulo você aprenderá como unir o histórico de duas Branches utilizando o comando `git merge`, preservando os commits realizados durante o desenvolvimento.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

