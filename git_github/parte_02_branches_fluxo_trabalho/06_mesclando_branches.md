**Tempo estimado:** 25 minutos

**Nível:** Iniciante

# Capítulo 06 — Mesclando Branches (`git merge`)
---

# Pré-requisitos

Antes de iniciar este capítulo é recomendado compreender como criar, alternar, trabalhar e comparar Branches.

---

# Neste capítulo você aprenderá

* O que é um merge.
* Como unir duas Branches.
* O comando `git merge`.
* Como interpretar o resultado da mesclagem.
* O que acontece com o histórico após um merge.

---

# O que é um Merge?

**Merge** significa **mesclar** ou **unir**.

No Git, um merge é utilizado para integrar as alterações de uma Branch em outra.

Esse é o momento em que uma funcionalidade desenvolvida separadamente passa a fazer parte da Branch principal.

Exemplo:

```text
main

A ─── B ─── C
             \
login         D ─── E
```

Após concluir a funcionalidade da Branch `login`, podemos incorporá-la à `main`.

---

# Representação visual

Antes do merge:

```text
main
 │
 ▼

A ─── B ─── C
             \
login         D ─── E
```

Depois do merge:

```text
main
 │
 ▼

A ─── B ─── C ─────── M
             \      /
login         D ─── E
```

O commit `M` representa o commit de mesclagem (*merge commit*), quando necessário.

---

# Comando

Primeiro, **alterne para a Branch que receberá as alterações**.

```bash
git switch main
```

Em seguida, execute:

```bash
git merge login
```

---

# Significado do comando

## `git`

Sistema de controle de versão distribuído.

### `merge`

**Tradução:** Mesclar ou unir.

Integra o histórico de outra Branch à Branch atual.

### `login`

Nome da Branch cujas alterações serão incorporadas.

---

# Resultado

Se não houver conflitos, o Git poderá apresentar uma saída semelhante a:

```text
Updating 8f21d7a..5c8d913
Fast-forward
 login.py | 12 ++++++++++++
 1 file changed, 12 insertions(+)
```

Ou, dependendo do histórico:

```text
Merge made by the 'ort' strategy.
```

---

# Explicação da saída

### `Updating`

O Git está atualizando a Branch atual.

### `Fast-forward`

Significa que a Branch atual apenas avançou até o último commit da outra Branch, sem necessidade de criar um commit de merge.

### `Merge made`

Indica que foi criado um commit de merge para unir os históricos.

---

# O que aconteceu internamente?

Ao executar:

```bash
git merge login
```

o Git compara o histórico das duas Branches.

Se as alterações forem compatíveis, ele integra automaticamente os commits.

Dependendo da situação, o Git poderá:

* realizar um **Fast-forward**, apenas movendo o ponteiro da Branch; ou
* criar um **Merge Commit**, preservando a união dos dois históricos.

Nenhuma alteração é perdida durante esse processo.

---

# Atenção

O comando:

```bash
git merge login
```

deve ser executado na Branch que receberá as alterações.

Exemplo correto:

```bash
git switch main
git merge login
```

Nesse caso, *a Branch `main` recebe os commits da Branch `login`*.

---

# Resumo

Neste capítulo você aprendeu que o comando `git merge` é utilizado para integrar o histórico de uma Branch em outra. Também compreendeu que o Git pode realizar essa integração automaticamente por meio de um **Fast-forward** ou criando um **Merge Commit**, dependendo da estrutura do histórico.

---

# Próximo capítulo

## Capítulo 07 — Resolvendo Conflitos de Merge

No próximo capítulo você aprenderá por que os conflitos acontecem, como identificá-los e como resolvê-los de forma segura durante uma mesclagem.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

