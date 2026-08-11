# Git e GitHub — Guia de Estudos

## Capítulo 08 — Comparando Alterações com `git diff`

**Tempo estimado de leitura:** 10 minutos
**Nível:** Iniciante

---

## Neste capítulo você aprenderá

* O que é o comando `git diff`.
* Como comparar alterações feitas em um arquivo.
* Como entender a saída do `git diff`.
* A diferença entre `git diff` e `git diff --staged`.
* Por que revisar as alterações antes de criar um *commit* é importante.
* Algumas opções úteis do `git diff`.

---

# Informações do capítulo

| Campo                   | Informação                           |
| ----------------------- | ------------------------------------ |
| **Capítulo**            | 08                                   |
| **Título**              | Comparando Alterações com `git diff` |
| **Autor**               | Laerte Costa                         |
| **Sistema Operacional** | Debian GNU/Linux                     |
| **Terminal**            | Bash                                 |
| **Última atualização**  | Agosto de 2026                       |

---

# Objetivo deste capítulo

Neste capítulo, você vai aprender a verificar exatamente o que foi alterado nos arquivos antes de criar um *commit*.

Para isso, vamos utilizar o comando `git diff`.

Esse comando é muito útil para revisar o trabalho e evitar registrar alterações por engano.

---

# Pré-requisitos

É recomendado ter concluído os capítulos anteriores, principalmente os capítulos sobre:

* Área de Trabalho;
* Área de Preparação;
* `git add`;
* `git commit`.

---

# 1. O que é o `git diff`?

Durante o desenvolvimento de um projeto, é normal modificar arquivos várias vezes.

Antes de criar um *commit*, pode ser importante conferir exatamente o que foi alterado.

O comando:

```bash id="o1p8sq"
git diff
```

mostra as diferenças entre o conteúdo atual dos arquivos e a versão que está sendo comparada pelo Git.

A palavra **diff** vem de *difference*, que significa **diferença**.

> **Resumo**
>
> `git diff` → mostra as diferenças encontradas nos arquivos.

---

# 2. Fazendo uma alteração

Vamos utilizar o arquivo `README.md` como exemplo.

Abra o arquivo e adicione algumas linhas:

```text id="m9bg7x"
# Meu Projeto

Este projeto foi criado para aprender Git.
```

Salve o arquivo.

Agora temos uma alteração na **Área de Trabalho**.

---

# 3. Verificando o estado

Antes de comparar as alterações, podemos verificar o estado do repositório:

```bash id="b8l6fh"
git status
```

O Git poderá mostrar algo semelhante a:

```text id="w4z6xg"
Changes not staged for commit:
  modified: README.md
```

Isso indica que o arquivo foi modificado, mas a alteração ainda não foi adicionada à Área de Preparação.

---

# 4. Comparando as alterações

Agora execute:

```bash id="9p3c5z"
git diff
```

O Git poderá apresentar algo parecido com:

```diff id="cxkqpj"
diff --git a/README.md b/README.md
index e69de29..c8d3f81 100644
--- a/README.md
+++ b/README.md
@@ -1,1 +1,3 @@
 # Meu Projeto
+
+Este projeto foi criado para aprender Git.
```

No começo, essa saída pode parecer complicada.

Vamos entender as partes mais importantes.

---

# 5. Entendendo a saída do `git diff`

## `diff --git`

```text id="p7qf1r"
diff --git a/README.md b/README.md
```

Essa linha informa que o Git está comparando duas versões do arquivo.

* `a/README.md` → versão anterior;
* `b/README.md` → versão atual.

As letras `a` e `b` são apenas identificadores utilizados pelo Git para representar os dois lados da comparação.

---

## `---` e `+++`

```text id="1h3q9x"
--- a/README.md
+++ b/README.md
```

Essas linhas indicam os dois lados da comparação.

```text
--- → versão anterior
+++ → versão atual
```

Assim, podemos identificar de onde cada alteração veio.

---

# 6. Entendendo os sinais `+` e `-`

Essa é uma das partes mais importantes do `git diff`.

### Linha adicionada

```text id="7q9p2s"
+Este projeto foi criado para aprender Git.
```

O sinal `+` indica que essa linha foi **adicionada**.

### Linha removida

Se uma linha for removida, aparecerá assim:

```text id="e2r4z6"
-Esta linha foi removida.
```

O sinal `-` indica que a linha foi **removida**.

### Linha sem sinal

Linhas sem `+` ou `-` normalmente representam o contexto ao redor da alteração.

Por exemplo:

```diff id="o9a8k2"
 # Meu Projeto
+
+Este projeto foi criado para aprender Git.
```

A linha:

```text
# Meu Projeto
```

é mostrada apenas para ajudar a localizar a alteração.

---

# 7. Entendendo o `@@`

Você também pode encontrar uma linha como:

```text id="qj5n2w"
@@ -1,1 +1,3 @@
```

Essa informação indica a região do arquivo onde a alteração aconteceu.

Para quem está começando, não é necessário decorar todos os detalhes dessa linha.

O mais importante é saber que ela ajuda o Git a indicar **onde as alterações aconteceram**.

---

# 8. Informações internas do Git

Outra linha que pode aparecer é:

```text id="f1s8mc"
index e69de29..c8d3f81 100644
```

Essa linha contém informações utilizadas internamente pelo Git.

Ela pode incluir:

* identificadores das versões comparadas;
* informações sobre o modo/permissão do arquivo.

Neste momento, não é necessário decorar esses valores.

> **Dica**
>
> Ao começar a estudar Git, concentre-se primeiro nos sinais `+` e `-` e na localização das alterações. As outras informações podem ser estudadas posteriormente.

---

# 9. O que acontece depois do `git add`?

Agora execute:

```bash id="g1zj5q"
git add README.md
```

A alteração foi enviada para a **Área de Preparação**.

Se você executar novamente:

```bash id="lq5xj4"
git diff
```

provavelmente não verá mais aquela alteração.

Por quê?

Porque o `git diff`, sem outras opções, mostra as diferenças entre a **Área de Trabalho** e o conteúdo que está na **Área de Preparação**.

Depois do `git add`, esses dois estados estão iguais para aquela alteração.

---

# 10. Visualizando o que está na Área de Preparação

Depois do `git add`, podemos utilizar:

```bash id="v2i9dc"
git diff --staged
```

Também podemos usar:

```bash id="x7v1ka"
git diff --cached
```

Os dois comandos têm a mesma finalidade: mostrar as alterações que já foram adicionadas à **Área de Preparação** e que serão incluídas no próximo *commit*.

### Entendendo

**`--staged`** → mostra alterações que estão preparadas.

**`--cached`** → outra forma de consultar as alterações que estão no índice (*index*), utilizado pelo Git para a Área de Preparação.

---

# 11. `git diff` × `git diff --staged`

Essa diferença é muito importante:

| Comando             | O que mostra                        |
| ------------------- | ----------------------------------- |
| `git diff`          | Alterações ainda não preparadas.    |
| `git diff --staged` | Alterações que já foram preparadas. |

Podemos visualizar assim:

```text id="u7m4b8"
Área de Trabalho
       │
       │ git diff
       ↓
Área de Preparação
       │
       │ git diff --staged
       ↓
Próximo commit
```

Isso permite revisar as alterações em dois momentos diferentes.

---

# 12. Por que usar o `git diff`?

Imagine que você modificou vários arquivos durante o dia.

Antes de criar um *commit*, você pode verificar exatamente o que mudou.

Isso ajuda a encontrar:

* alterações feitas por engano;
* linhas que não deveriam estar no *commit*;
* erros de digitação;
* arquivos modificados sem necessidade;
* alterações que precisam ser corrigidas.

Por isso, revisar as mudanças antes do *commit* é uma boa prática.

---

# 13. Mostrando apenas os nomes dos arquivos

Se você quiser saber apenas quais arquivos foram modificados, pode utilizar:

```bash id="yd8u4a"
git diff --name-only
```

A opção:

```text
--name-only
```

significa que serão exibidos apenas os nomes dos arquivos.

Exemplo:

```text id="pq2s5e"
README.md
script.py
index.html
```

---

# 14. Comparando um arquivo específico

Também podemos verificar somente um arquivo.

### Comando

```bash id="6g5jqs"
git diff README.md
```

Nesse caso, o Git mostrará apenas as alterações encontradas no `README.md`.

Isso é útil quando o projeto possui muitos arquivos modificados.

---

# 15. Mostrando um resumo das alterações

Podemos utilizar:

```bash id="b1q7rx"
git diff --stat
```

A opção `--stat` apresenta um resumo das alterações.

Exemplo:

```text id="v6u4qk"
README.md | 4 ++++
1 file changed, 4 insertions(+)
```

Isso informa que:

* `1 file changed` → 1 arquivo foi alterado;
* `4 insertions(+)` → 4 linhas foram adicionadas.

Se existirem linhas removidas, elas também aparecerão:

```text
1 file changed, 2 insertions(+), 1 deletion(-)
```

---

# 16. Mostrando diferenças por palavras

Outra opção é:

```bash id="2d5c7h"
git diff --color-words
```

Essa opção pode facilitar a visualização quando apenas algumas palavras de uma linha foram modificadas.

Em terminais que suportam cores, as alterações podem ser destacadas visualmente.

---

# 17. Utilizando uma ferramenta visual

O Git também possui o comando:

```bash id="4z5s9p"
git difftool
```

O `difftool` permite utilizar uma ferramenta externa para visualizar as diferenças.

A aparência e o comportamento dependem da ferramenta configurada no sistema.

Para quem está começando, o `git diff` já é suficiente para aprender o conceito.

---

# 18. Controlando o contexto exibido

O `git diff` normalmente mostra algumas linhas ao redor da alteração para facilitar a leitura.

Podemos alterar essa quantidade utilizando `-U`.

Por exemplo:

```bash id="c4m7pf"
git diff -U1 README.md
```

Nesse caso, o Git utiliza uma linha de contexto antes e depois da alteração.

Para estudar o Git no nível iniciante, não é necessário utilizar essa opção com frequência.

---

# 19. Navegando pelo resultado

Quando o resultado do `git diff` é grande, o Git pode utilizar o `less` para facilitar a leitura.

Alguns comandos úteis:

| Tecla    | Função                                    |
| -------- | ----------------------------------------- |
| `Espaço` | Avança uma página.                        |
| `b`      | Volta uma página.                         |
| `/texto` | Procura por um texto.                     |
| `n`      | Vai para a próxima ocorrência encontrada. |
| `q`      | Sai da visualização.                      |

Por exemplo, para sair:

```text
q
```

---

# 20. Fluxo de revisão

O processo pode ser resumido desta maneira:

```text id="a6n4ky"
Modificar arquivo
       │
       ▼
   git diff
       │
       │
       ▼
   git add
       │
       ▼
git diff --staged
       │
       ▼
   git commit
```

Assim, podemos revisar as alterações antes e depois de colocá-las na Área de Preparação.

---

# Comandos vistos neste capítulo

| Comando                  | Função                                                |
| ------------------------ | ----------------------------------------------------- |
| `git diff`               | Mostra alterações ainda não preparadas.               |
| `git diff --staged`      | Mostra alterações preparadas para o próximo *commit*. |
| `git diff --cached`      | Outra forma de mostrar alterações preparadas.         |
| `git diff --name-only`   | Mostra apenas os nomes dos arquivos alterados.        |
| `git diff arquivo`       | Mostra alterações de um arquivo específico.           |
| `git diff --stat`        | Mostra um resumo das alterações.                      |
| `git diff --color-words` | Destaca diferenças por palavras.                      |
| `git difftool`           | Permite utilizar uma ferramenta visual de comparação. |

---

# Boas práticas

Antes de criar um *commit*:

1. Execute `git status`.
2. Revise as alterações com `git diff`.
3. Adicione os arquivos desejados com `git add`.
4. Revise novamente com `git diff --staged`.
5. Crie o *commit*.

Um fluxo completo pode ser:

```bash id="9u2j3x"
git status
git diff
git add README.md
git diff --staged
git commit -m "Atualiza README"
```

Esse hábito ajuda a evitar *commits* com alterações indesejadas.

---

# Resumo

O comando `git diff` permite visualizar as diferenças entre versões dos arquivos.

Os comandos mais importantes deste capítulo são:

```bash id="3h6t8v"
git diff
git diff --staged
git diff --stat
git diff --name-only
```

A diferença principal é:

```text id="b4z6sk"
git diff
    ↓
Alterações ainda não preparadas

git diff --staged
    ↓
Alterações já preparadas
```

Aprender a usar o `git diff` ajuda a revisar o trabalho antes de registrar novas alterações no histórico.

---

# O que você aprendeu

Ao concluir este capítulo, você consegue:

* ✅ Entender o que é `git diff`.
* ✅ Visualizar alterações feitas nos arquivos.
* ✅ Identificar linhas adicionadas e removidas.
* ✅ Entender os principais símbolos exibidos pelo `git diff`.
* ✅ Diferenciar `git diff` de `git diff --staged`.
* ✅ Comparar um arquivo específico.
* ✅ Mostrar apenas os nomes dos arquivos alterados.
* ✅ Visualizar um resumo das alterações.
* ✅ Revisar alterações antes de criar um *commit*.

---

# Próximo capítulo

## Capítulo 09 — Ignorando Arquivos com `.gitignore`

No próximo capítulo, você aprenderá como utilizar o arquivo `.gitignore` para impedir que determinados arquivos e diretórios sejam adicionados ao controle do Git.

Isso é útil para ignorar arquivos temporários, arquivos de configuração local, logs e outros conteúdos que não precisam fazer parte do repositório.

---

# 📚 Fonte de estudo

Este resumo foi elaborado a partir dos estudos e da prática do autor sobre **Git e GitHub**, utilizando os conteúdos da disciplina e materiais de estudo como referência.

**Observação:** este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo original das disciplinas e materiais utilizados como referência não deve ser reproduzido ou disponibilizado integralmente neste repositório.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

