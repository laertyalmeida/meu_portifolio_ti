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

## O que é o `git diff`?

Durante o desenvolvimento de um projeto, é comum modificar um ou mais arquivos antes de criar um commit.

O comando `git diff` permite visualizar exatamente quais alterações foram realizadas.

Ele ajuda a revisar o trabalho antes de registrar as modificações no histórico do projeto.

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

**diff** → *difference* → diferença → mostra as diferenças entre duas versões de um arquivo.

Exemplo:

```diff
diff --git a/README.md b/README.md
index e69de29..c8d3f81 100644
--- a/README.md
+++ b/README.md
@@ -1,1 +1,3 @@
 # Meu Projeto
+
+Este projeto foi criado para aprender Git.
```

---

# Explicando linha por linha

```text
diff --git a/README.md b/README.md
```

Mostra os dois lados da comparação:

* `a/README.md` → versão anterior do arquivo.
* `b/README.md` → versão atual do arquivo.

As letras `a` e `b` são apenas identificadores usados pelo Git para representar as duas versões comparadas.

---

```text
index e69de29..c8d3f81 100644
```

Mostra informações internas do Git:

* `e69de29` → hash da versão anterior.
* `c8d3f81` → hash da versão atual.
* `100644` → permissão do arquivo no sistema Linux.

---

```text
--- a/README.md
```

Indica a versão anterior do arquivo.

O símbolo `---` representa o arquivo antigo que será comparado.

---

```text
+++ b/README.md
```

Indica a versão atual do arquivo.

O símbolo `+++` representa o arquivo novo após as alterações.

---

```text
@@ -1,1 +1,3 @@
```

Mostra o trecho onde ocorreu a alteração.

Parte antiga:

```text
-1,1
```

Significa:

* começa na linha 1;
* mostra 1 linha da versão antiga.

Parte nova:

```text
+1,3
```

Significa:

* começa na linha 1;
* mostra 3 linhas da versão nova.

---

# Entendendo os símbolos

Linhas iniciadas com:

```text
+
```

indicam conteúdo adicionado.

Linhas iniciadas com:

```text
-
```

indicam conteúdo removido.

As demais linhas mostram o contexto da alteração.

---

# O que acontece após o `git add`?

Execute:

```bash
git add README.md
```

Agora execute novamente:

```bash
git diff
```

Nenhuma alteração será exibida.

Isso acontece porque o `git diff` compara a **Área de Trabalho (Working Tree)** com a **Área de Preparação (Staging Area)**.

Após o `git add`, a alteração foi enviada para a Área de Preparação, deixando esses dois estados iguais.

---

# Comparando arquivos da Área de Preparação

Depois do `git add`, utilize:

### Comando

```bash
git diff --staged
```

ou

```bash
git diff --cached
```

Significados:

**staged** → preparado → alterações que estão na Área de Preparação.

**cached** → armazenado no índice (*index*) → nome antigo utilizado pelo Git para acessar a Área de Preparação.

Esses comandos mostram as alterações que já foram adicionadas pelo `git add` e que serão incluídas no próximo commit.

---

# Por que utilizar o `git diff`?

Imagine que você alterou diversos arquivos.

Antes de criar um commit, você pode utilizar o `git diff` para revisar todas as modificações realizadas.

Isso ajuda a identificar erros, alterações indesejadas ou informações que não deveriam ser registradas.

É uma forma simples de revisar seu trabalho antes de salvá-lo no histórico do projeto.

---

# Fluxo de comparação no Git

O processo de revisão segue este fluxo:

```text
Arquivo modificado
        |
        v
   git diff
        |
        v
     git add
        |
        v
git diff --staged
        |
        v
   git commit
```

O `git diff` permite revisar alterações antes de enviá-las para a Área de Preparação.

O `git diff --staged` permite revisar aquilo que já foi preparado para o próximo commit.

---

# Navegar pelo diff

Durante a visualização do diff, o Git utiliza o paginador `less`.

Comandos:

```
Espaço → próxima página
b → página anterior
/texto → pesquisar
n → próxima ocorrência
q → sair
```

---

# Alguns tipos de pesquisas

### Mostrar apenas nomes dos arquivos alterados

```bash
git diff --name-only
```

**name only** → apenas nome → exibe somente os nomes dos arquivos modificados.

---

### Comparar um arquivo específico

```bash
git diff <nome_do_arquivo>
```

Exibe somente as modificações de um arquivo específico.

---

### Mostrar resumo das alterações

```bash
git diff --stat
```

**stat** → estatística → mostra um resumo das alterações.

Exemplo:

```text
1 file changed, 4 insertions(+), 3 deletions(-)
```

Significado:

**1 file changed** → 1 arquivo modificado.

**insertions(+)** → inserções → conteúdos adicionados ao arquivo.

**deletions(-)** → exclusões → conteúdos removidos do arquivo.

---

### Mostrar diferenças por palavras

```bash
git diff --color-words
```

**color words** → palavras coloridas → mostra alterações individuais por palavras.

Normalmente:

* verde → conteúdo adicionado;
* vermelho → conteúdo removido.

---

### Utilizar uma ferramenta visual de comparação

```bash
git difftool
```

**tool** → ferramenta → ferramenta de comparação de diferenças.

Pode abrir uma interface visual mostrando as diferenças entre versões.

Para sair da ferramenta no terminal:

```bash
:q
```

---

### Controlar quantidade de linhas exibidas

```bash
git diff -U1 <nome_do_arquivo>
```

**-U** → *Unified Context* → contexto unificado.

**-U1** → mostra 1 linha de contexto antes e depois da alteração.

---

# O que foi aprendido

* `git diff` compara alterações da Área de Trabalho;
* `git diff --staged` exibe alterações da Área de Preparação;
* o símbolo `+` representa conteúdo adicionado;
* o símbolo `-` representa conteúdo removido;
* existem diferentes formas de pesquisar e visualizar alterações;
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

