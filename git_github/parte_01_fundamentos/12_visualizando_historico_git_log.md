# Tempo estimado de leitura

**12 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* Consultar o histórico de commits com `git log`.
* Entender as principais informações de um commit.
* Visualizar o histórico de forma resumida.
* Limitar a quantidade de commits exibidos.
* Filtrar commits por autor ou mensagem.
* Visualizar detalhes de um commit específico.
* Consultar as alterações registradas no histórico.

---

# Git e GitHub — Guia de Estudos

---

# Informações do capítulo

| Campo                   | Informação                             |
| ----------------------- | -------------------------------------- |
| **Capítulo**            | 12                                     |
| **Título**              | Visualizando o Histórico com `git log` |
| **Autor**               | Laerte Costa                           |
| **Sistema Operacional** | Debian GNU/Linux                       |
| **Terminal**            | Bash                                   |
| **Última atualização**  | Agosto de 2026                         |

---

# Objetivo deste capítulo

Aprender a utilizar o histórico do Git para consultar commits, encontrar informações sobre alterações e entender como o projeto evoluiu ao longo do tempo.

---

# Pré-requisitos

Recomenda-se ter concluído os capítulos anteriores, principalmente os capítulos sobre:

* `git commit`;
* `git status`;
* `git diff`;
* `git restore`.

---

# Conceito teórico

## O que é o histórico do Git?

Cada vez que um commit é criado, o Git registra uma nova versão do projeto.

Esses registros formam o **histórico do repositório**.

O histórico permite descobrir:

* quem realizou uma alteração;
* quando ela foi realizada;
* qual mensagem foi utilizada;
* qual commit contém determinada versão;
* quais alterações foram registradas.

Podemos imaginar o histórico como uma linha do tempo:

```text
Commit 1
   ↓
Commit 2
   ↓
Commit 3
   ↓
Commit 4
```

Cada commit representa um ponto registrado na evolução do projeto.

---

# O comando `git log`

O comando:

```bash
git log
```

é utilizado para consultar o histórico de commits.

Por padrão, os commits são apresentados do **mais recente para o mais antigo**.

---

# Visualizando o histórico

Execute:

```bash
git log
```

Um resultado poderá ser semelhante a:

```text
commit a84f91c2d8e7f6a5b4c3d2e1f0
Author: Laerte Costa <laerte@email.com>
Date:   Thu Jul 30 20:15:30 2026 -0300

    Adiciona documentação do capítulo 11
```

---

# Entendendo a saída

## `commit`

Exemplo:

```text
commit a84f91c2d8e7f6a5b4c3d2e1f0
```

Esse valor é o **hash do commit**.

O hash é um identificador usado pelo Git para identificar aquele commit.

Uma parte desse identificador também pode ser utilizada para fazer referência ao commit, desde que seja suficiente para diferenciá-lo dos demais.

---

## `Author`

Exemplo:

```text
Author: Laerte Costa <laerte@email.com>
```

Mostra quem realizou o commit.

Essas informações vêm da configuração do Git:

```bash
git config --global user.name
```

e:

```bash
git config --global user.email
```

---

## `Date`

Exemplo:

```text
Date: Thu Jul 30 20:15:30 2026 -0300
```

Mostra a data e o horário associados ao commit.

---

## Mensagem do commit

Exemplo:

```text
Adiciona documentação do capítulo 11
```

É a mensagem informada quando o commit foi criado:

```bash
git commit -m "Adiciona documentação do capítulo 11"
```

Uma mensagem clara facilita muito a leitura do histórico.

---

# Histórico resumido

Quando o projeto possui muitos commits, o `git log` pode apresentar bastante informação.

Para visualizar uma versão mais simples:

```bash
git log --oneline
```

Exemplo:

```text
a84f91c Adiciona documentação do capítulo 11
7c921aa Adiciona capítulo sobre git restore
3bd82ef Cria estrutura inicial do projeto
```

A opção:

```text
--oneline
```

significa:

> mostrar cada commit em uma única linha.

Normalmente serão exibidos:

* hash abreviado;
* mensagem do commit.

---

# Limitando a quantidade de commits

Podemos escolher quantos commits queremos visualizar.

Por exemplo:

```bash
git log -5
```

Nesse caso, serão exibidos os **5 commits mais recentes**.

Também podemos utilizar:

```bash
git log -3
```

para visualizar os três mais recentes.

---

# Visualizando estatísticas

O comando:

```bash
git log --stat
```

mostra um resumo das alterações registradas nos commits.

Pode apresentar informações como:

```text
3 files changed, 120 insertions(+), 5 deletions(-)
```

Significado:

* **files changed** → quantidade de arquivos alterados;
* **insertions** → quantidade de linhas adicionadas;
* **deletions** → quantidade de linhas removidas.

**stat** → *statistics* → estatísticas.

---

# Visualizando as alterações dos commits

Também podemos pedir ao Git para mostrar as diferenças registradas nos commits.

### Comando

```bash
git log -p
```

A opção:

```text
-p
```

vem de *patch* e faz o Git mostrar os detalhes das alterações registradas nos commits.

Isso pode gerar uma saída grande, principalmente em projetos com muitos commits.

---

# Filtrando por autor

Podemos pesquisar commits realizados por determinado autor.

### Comando

```bash
git log --author="Laerte"
```

O Git exibirá os commits que correspondem ao autor informado.

Essa opção é especialmente útil em projetos com várias pessoas trabalhando no mesmo repositório.

---

# Pesquisando pela mensagem do commit

Também podemos procurar uma palavra dentro das mensagens dos commits.

### Comando

```bash
git log --grep="capítulo"
```

O Git mostrará os commits cuja mensagem corresponde ao termo pesquisado.

Por exemplo, podemos pesquisar:

```bash
git log --grep="README"
```

para encontrar commits relacionados ao README.

---

# Visualizando um commit específico

Quando encontramos um commit interessante, podemos consultar seus detalhes utilizando:

```bash
git show a84f91c
```

O comando `git show` pode apresentar:

* identificação do commit;
* autor;
* data;
* mensagem;
* alterações registradas naquele commit.

---

# O que é `HEAD`?

Durante o estudo do Git, você encontrará frequentemente a palavra:

```text
HEAD
```

O `HEAD` representa a posição atual do Git no histórico.

De forma simples:

> **HEAD indica o commit que está sendo utilizado como referência na posição atual do repositório.**

Por exemplo:

```bash
git show HEAD
```

mostra informações sobre o commit apontado atualmente pelo `HEAD`.

Também podemos consultar o commit anterior:

```bash
git show HEAD~1
```

E dois commits anteriores:

```bash
git show HEAD~2
```

---

# Navegando pelo histórico

Quando o Git apresenta uma quantidade grande de informações, normalmente utiliza o paginador `less`.

Alguns comandos úteis:

```text
Espaço  → próxima página
b       → página anterior
/texto  → pesquisar
n       → próxima ocorrência
q       → sair
```

---

# Por que consultar o histórico?

O histórico é muito útil para entender o que aconteceu no projeto.

Imagine que você encontrou um problema e deseja descobrir quando determinada alteração foi feita.

Você pode utilizar:

```bash
git log
```

e:

```bash
git show
```

para investigar os commits.

Assim, o histórico funciona como uma espécie de **linha do tempo do projeto**.

---

# Boa prática: mensagens claras

Evite mensagens muito genéricas:

```text
alterações
```

ou:

```text
teste
```

Prefira mensagens que expliquem o que foi feito:

```text
Adiciona documentação do capítulo 12
```

ou:

```text
Corrige comando de instalação do Git
```

Uma mensagem clara facilita a consulta do histórico no futuro.

---

# Boa prática: commits organizados

Procure criar commits que representem alterações relacionadas.

Por exemplo:

```text
Adiciona capítulo sobre git diff
```

é melhor do que juntar várias alterações diferentes em um único commit sem uma descrição clara.

Commits organizados facilitam:

* consultar o histórico;
* encontrar problemas;
* entender alterações;
* recuperar versões anteriores.

---

# Exemplo de fluxo

Imagine que você terminou uma alteração no projeto.

Primeiro:

```bash
git status
```

Depois revise:

```bash
git diff
```

Prepare:

```bash
git add .
```

Revise novamente:

```bash
git diff --staged
```

Registre:

```bash
git commit -m "Atualiza documentação do projeto"
```

Depois consulte o histórico:

```bash
git log --oneline
```

O fluxo fica:

```text
Modificar
    ↓
git status
    ↓
git diff
    ↓
git add
    ↓
git diff --staged
    ↓
git commit
    ↓
git log
```

Esse é um dos fluxos mais importantes para quem está começando a utilizar Git.

---

# Comandos vistos neste capítulo

| Comando                     | Função                                        |
| --------------------------- | --------------------------------------------- |
| `git log`                   | Mostra o histórico de commits.                |
| `git log --oneline`         | Mostra o histórico de forma resumida.         |
| `git log -5`                | Mostra os 5 commits mais recentes.            |
| `git log --stat`            | Mostra estatísticas das alterações.           |
| `git log -p`                | Mostra as alterações registradas nos commits. |
| `git log --author="Laerte"` | Filtra commits por autor.                     |
| `git log --grep="palavra"`  | Pesquisa mensagens de commits.                |
| `git show <commit>`         | Mostra detalhes de um commit específico.      |
| `git show HEAD`             | Mostra o commit apontado pelo `HEAD`.         |

---

# O que foi aprendido

Ao concluir este capítulo, você é capaz de:

* ✅ Consultar o histórico com `git log`.
* ✅ Entender as principais informações de um commit.
* ✅ Utilizar `git log --oneline`.
* ✅ Limitar a quantidade de commits exibidos.
* ✅ Visualizar estatísticas com `git log --stat`.
* ✅ Consultar alterações com `git log -p`.
* ✅ Filtrar commits por autor.
* ✅ Pesquisar mensagens de commits.
* ✅ Consultar um commit específico com `git show`.
* ✅ Entender o conceito básico de `HEAD`.

---

# Resumo

O `git log` é uma das principais ferramentas para consultar a evolução de um projeto.

Com ele, podemos visualizar os commits realizados e encontrar informações importantes sobre as alterações.

Também podemos utilizar opções como:

```bash
git log --oneline
```

para uma visualização resumida,

```bash
git log --stat
```

para visualizar estatísticas,

e:

```bash
git show <commit>
```

para analisar um commit específico.

Entender o histórico é importante porque ele permite acompanhar o desenvolvimento do projeto e investigar alterações realizadas anteriormente.

---

# Próximo capítulo

## Capítulo 13 — Revisão da Parte 1 e Desafio Prático

No próximo capítulo você revisará os principais conceitos estudados até aqui e realizará um exercício prático utilizando o fluxo completo do Git:

```text
Criar
  ↓
Modificar
  ↓
Verificar
  ↓
Revisar
  ↓
Preparar
  ↓
Registrar
  ↓
Consultar histórico
  ↓
Restaurar quando necessário
```

Depois dessa revisão, você estará preparado para iniciar a **Parte 2 — Trabalhando com Branches**.

---

# 📚 Fonte de estudo

Este resumo foi elaborado a partir dos estudos e da prática do autor sobre **Git e GitHub**, utilizando os conteúdos da disciplina e materiais de estudo como referência.

**Observação:** este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo original das disciplinas e materiais utilizados como referência não deve ser reproduzido ou disponibilizado integralmente neste repositório.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

