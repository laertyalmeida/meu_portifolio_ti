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
**diff** → *difference* → diferença → *mostra as diferenças dos registros, o antes e o depois*

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

## Explicando linha por linha

diff --git a/README.md b/README.md
mostra registros a b, diferenças do arquivo README

index e69de29..c8d3f81 1000644
código de referência (hash)

--- a/README.md (sinal de menos, versão antiga)
houve um registro a de tudo que foi retirado do arquivo

+++ b/README.md (sinal de mais, versão atual)
houve um registro b de tudo que foi adicionado/modificado no arquivo

@@ -1,1 +1,3 @@
-1,1 começa na linha 1 e tem 1 linha
+1,3 começa na linha 1 e tem 3 linhas

Meu projeto 
mensagem já existia no arquivo, não foi modificado

+
adicionado uma linha em branco

+Este projeto foi criado para aprendere Git
mensagem adicionada no arquivo 

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

**staged** → *encenado* 
**cached** → *em cache*

*staged ou cached ignoram (não mostram) as partes modificadas do arquivo que ainda não foram adicionadas para área de preparação(git add) mostrando apenas as partes do arquivo que já estão adicionadas*
 
---

# Por que utilizar o `git diff`?

Imagine que você alterou diversos arquivos.

Antes de criar um commit, você pode utilizar o `git diff` para revisar todas as modificações realizadas.

Isso ajuda a identificar erros, alterações indesejadas ou informações que não deveriam ser registradas.

É uma forma simples de revisar seu trabalho antes de salvá-lo no histórico do projeto.

---

# Navegar pelo diff

Na pesquisa diff, o Git abre o paginador less para visualização.

Use:

Espaço → próxima página
b → página anterior
/texto → pesquisar
n → próxima ocorrência
q → sair

## Alguns tipos de pesquisas

**git diff --name-only** → *name only* → *apenas o nome* → *exibe os nomes dos registros alterados*

**git diff <nome_do_arquivo>** → *exibe as modificações de arquivo específico*

**git diff --stat** → *stat* → *imediatamete* → *resumidas* → *mostra as quantidades de alterações em números*

 | 7 ++++---
1 file changed, 4 insertions(+), 3 deletions(-)

**1 file changed** → *file* → *arquivo* → *changed* → *mudado* 
1 arquivo mudado

**insertions(+)** → *inserções* → *conteúdos adcionados no arquivo*

**deletions(-)** → *exclusões* → *conteúdos apagados do arquivo*

**git diff --color-words** → *color words* → *palavras de cor (coloridas)* → *antes de adicionar,(add), o conteúdo da última mudança fica verde e a que foi tirada fica em vermelho*

**git difftool** → *toll* → *ferramenta* → *ferramenta de comparação de diferencas* → *abre duas janelas e mostra as diferenças de cada linha* → *para sair da ferramenta, executar :q duas vezes

**git diff -U1 <nome_do-arquivo>** → *-U* → *Unified Context → *texto unificado* → *-U1* → *1* → *quantidade de linhas* → *mostra a modificação antes e depois*   

---

# O que foi aprendido

* `git diff` compara alterações na Área de Trabalho;
* `git diff --staged` exibe alterações da Área de Preparação;
* o símbolo `+` representa conteúdo adicionado;
* o símbolo `-` representa conteúdo removido;
* Tipos de buscas;
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

