# Tempo estimado de leitura

**10 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* O que é o comando `git diff`.
* Comparar alterações realizadas em um arquivo.
* Entender a saída do `git diff`.
* Descobrir por que esse comando é importante antes de criar um commit.

---

# Git e GitHub — Guia de Estudos

---

# Informações do capítulo

| Campo                   | Informação                           |
| ----------------------- | ------------------------------------ |
| **Capítulo**            | 08                                   |
| **Título**              | Comparando Alterações com `git diff` |
| **Autor**               | Laerte Costa                         |
| **Sistema Operacional** | Debian GNU/Linux                     |
| **Terminal**            | Bash                                 |
| **Última atualização**  | Julho de 2026                        |

---

# Pré-requisitos

Recomenda-se ter concluído os capítulos anteriores.

---

# Conceito teórico

O comando `git diff` compara duas versões de um arquivo e exibe as diferenças entre elas.

# signicifado do comando.

**git** → *nome da ferramenta*
**diff** → *difference* → *diferença* → *mostra as diferenças, alterações*

## O que é o `git diff`?

Durante o desenvolvimento de um projeto, é comum modificar um ou mais arquivos antes de criar um commit.

O comando `git diff` permite visualizar exatamente quais alterações foram realizadas.

Isso ajuda a revisar o trabalho antes de registrá-lo no histórico do projeto.

---

# Fazendo uma alteração

Abra o arquivo `README.md` e adicione uma nova linha.

Exemplo:

```text
# Meu Projeto

Este projeto foi criado para aprender Git.
```

Salve o arquivo.

---

# Verificando o estado do repositório

Antes de comparar as alterações, execute:

### Comando

```bash
git status
```

O Git informará que o arquivo foi modificado.

---

# Comparando as alterações

### Comando

```bash
git diff
```

Exemplo:

```diff
diff --git a/README.md b/README.md
index e69de29..c8d3f81 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,3 @@
 # Meu Projeto
+
+Este projeto foi criado para aprender Git.
```

---

# Entendendo a saída do comando

Ao utilizar `git diff`, algumas linhas possuem significados especiais.

As linhas iniciadas com:

```text
+
```

indicam conteúdo **adicionado**.

As linhas iniciadas com:

```text
-
```

indicam conteúdo **removido**.

As demais linhas servem para mostrar o contexto da alteração.

---

# O que acontece após o `git add`?

Execute:

### Comando

```bash
git add README.md
```

Agora execute novamente:

### Comando

```bash
git diff
```

Nenhuma alteração será exibida.

Isso acontece porque o `git diff` compara apenas as alterações que ainda estão na Área de Trabalho.

---

**git diff** → *mostra as últimas alterações* *q para sair*

**git diff --name-only** → *name = nome, only = apenas* → *apenas o nome*
Mostra apenas o nome do arquivo que foi alterado

**git difftool* → *ferrameneta de diferenças* → abre uma comparação em 2 telas
*:q 2 vezes parea sair*
**git difftol nome_do_arquivo.md 

# Comparando arquivos da Área de Preparação

Depois do `git add`, utilize:

### Comando

```bash
git diff --staged
```

**staged** → *encenada, preparada* → *preparada para cache*

ou

```bash
git diff --cached
```
**cached** → *armazenado em cache para commit*

Agora o Git exibirá as alterações que estão na Área de Preparação e que serão registradas no próximo commit.

---

# Por que utilizar o `git diff`?

Imagine que você alterou diversos arquivos durante o dia.

Antes de criar um commit, você pode utilizar o `git diff` para revisar todas as modificações realizadas.

Isso ajuda a identificar erros, alterações indesejadas ou informações que não deveriam ser registradas.

É uma forma simples de revisar seu trabalho antes de salvá-lo no histórico do projeto.

---

# Você sabia?

Os comandos `git diff` e `git status` costumam ser utilizados em conjunto.

Enquanto o `git status` informa **quais arquivos foram modificados**, o `git diff` mostra **o que foi alterado dentro desses arquivos**.

---

# O que foi aprendido

* `git diff` compara alterações na Área de Trabalho;
* `git diff --staged` exibe alterações da Área de Preparação;
* o símbolo `+` representa conteúdo adicionado;
* o símbolo `-` representa conteúdo removido;
* revisar alterações antes de criar um commit é uma boa prática.

---

# Resumo

Neste capítulo você aprendeu a comparar alterações utilizando o comando `git diff`.

Também conheceu a diferença entre comparar arquivos da Área de Trabalho e da Área de Preparação, tornando o processo de criação de commits mais seguro.

---

# Próximo capítulo

## 09 - Ignorando Arquivos com `.gitignore`

No próximo capítulo você aprenderá como impedir que arquivos temporários, logs e outros arquivos desnecessários sejam adicionados ao repositório.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

