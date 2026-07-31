# Tempo estimado de leitura

**8 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* Visualizar o histórico de commits.
* Entender as principais informações exibidas pelo Git.
* Consultar um histórico resumido.
* Limitar a quantidade de commits exibidos.
* Conhecer algumas opções do comando `git log`.

---

# Git e GitHub — Guia de Estudos

---

# Informações do capítulo

| Campo                   | Informação                            |
| ----------------------- | ------------------------------------- |
| **Capítulo**            | 06                                    |
| **Título**              | Consultando o Histórico de Alterações |
| **Autor**               | Laerte Costa                          |
| **Sistema Operacional** | Debian GNU/Linux                      |
| **Terminal**            | Bash                                  |
| **Última atualização**  | Julho de 2026                         |

---

# Objetivo deste capítulo

Aprender a consultar o histórico de alterações de um repositório Git e interpretar as principais informações registradas em cada commit.

---

# Pré-requisitos

Recomenda-se ter concluído os capítulos anteriores, principalmente o capítulo sobre criação de commits.

---

# Conceito teórico

## O que é o histórico de commits?

Sempre que um **commit** é realizado, o Git registra uma nova versão do projeto.

Essas versões formam um histórico que permite acompanhar toda a evolução do projeto ao longo do tempo.

Esse histórico pode ser consultado a qualquer momento utilizando o comando `git log`.

---

# Visualizando o histórico

### Comando

```bash
git log
```

### Explicação

O comando `git log` exibe todos os commits do repositório, do mais recente para o mais antigo.

**git** → *programa executado.*

**log** → *registro* → *histórico de registros realizados no repositório.*

Exemplo:

```text
commit 9c3f4d7b1b3d8f4d9f7b2c5e8a6d7f3c2a1b4e5
Author: Laerte Costa <laerte@email.com>
Date:   Wed Jul 22 20:15:30 2026 -0300

    Primeiro commit
```

---

# Entendendo a saída

Cada commit apresenta diversas informações importantes.

### Commit

Identificador único gerado pelo Git para cada registro realizado.

Nenhum commit possui o mesmo identificador.

### Author

Nome e endereço de e-mail do autor do commit.

Essas informações são obtidas da configuração realizada com `git config`.

### Date

Data e horário em que o commit foi realizado.

### Mensagem

Descrição informada pelo usuário no momento do commit.

Uma boa mensagem facilita a compreensão do histórico do projeto.

---

# Histórico resumido

Caso deseje visualizar apenas uma linha para cada commit, utilize:

### Comando

```bash
git log --oneline
```

### Explicação

A opção `--oneline` apresenta cada commit em apenas uma linha.

**oneline** → *uma linha.*

Exemplo:

```text
9c3f4d7 Primeiro commit
```

Essa opção facilita a leitura do histórico quando o projeto possui muitos commits.

---

# Exibindo uma quantidade específica de commits

Também é possível limitar a quantidade de registros exibidos.

### Comando

```bash
git log -2
```

### Explicação

O número informado após o comando define quantos commits serão exibidos.

No exemplo acima, apenas os dois commits mais recentes serão apresentados.

Você pode substituir o número `2` por qualquer outra quantidade desejada.

---

# Exibindo estatísticas dos commits

Caso deseje visualizar quais arquivos foram alterados em cada commit, utilize:

### Comando

```bash
git log --stat
```

### Explicação

Essa opção exibe um resumo mostrando:

- arquivos modificados;
- quantidade de linhas adicionadas;
- quantidade de linhas removidas.

É uma forma rápida de compreender o impacto de cada commit.

**stat** → *statistics* → *estatísticas.*

---

## Curiosidade

Cada commit recebe um identificador gerado por um algoritmo de criptografia chamado **SHA-1**.

Esse identificador é praticamente único, permitindo que o Git encontre qualquer versão do projeto com precisão.

---

# Resumo

Neste capítulo você aprendeu a consultar o histórico do repositório utilizando o comando `git log`.

Também conheceu as principais informações exibidas em um commit e diferentes formas de visualizar esse histórico.

---

# O que você aprendeu

Ao concluir este capítulo, você é capaz de:

- ✅ Visualizar o histórico de commits.
- ✅ Identificar as informações exibidas em cada commit.
- ✅ Utilizar o histórico resumido com `git log --oneline`.
- ✅ Limitar a quantidade de commits exibidos.
- ✅ Exibir estatísticas utilizando `git log --stat`.

---

# Próximo capítulo

## Capítulo 07 — Comparando Alterações com git diff

No próximo capítulo você aprenderá a utilizar o comando `git diff` para comparar alterações realizadas nos arquivos antes e depois dos commits.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**
