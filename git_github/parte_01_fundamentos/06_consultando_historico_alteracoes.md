# Tempo estimado de leitura

**8 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* Visualizar o histórico de commits.
* Entender as principais informações exibidas pelo Git.
* Consultar um histórico resumido.
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

# Pré-requisitos

Recomenda-se ter concluído os capítulos anteriores, principalmente o capítulo sobre criação de commits.

---

# Conceito teórico

## O que é o histórico de commits? (histórico de registros)

Sempre que um **commit** é realizado, o Git registra uma nova versão do projeto.

Essas versões formam um histórico que permite acompanhar a evolução do projeto ao longo do tempo.

Para consultar esse histórico, utiliza-se o comando `git log`.

---

# Visualizando o histórico

### Comando

```bash
git log
```

**log** → *registro*

Exemplo:

```text
commit 9c3f4d7b1b3d8f4d9f7b2c5e8a6d7f3c2a1b4e5
Author: Laerte Costa <laerte@email.com>
Date:   Wed Jul 22 20:15:30 2026 -0300

    Primeiro commit
```

Cada commit apresenta informações importantes sobre a alteração realizada.

---

# Entendendo a saída

O comando `git log` exibe, entre outras informações:

* **Commit:** identificador único da alteração.
* **Author:** nome e e-mail do autor.
* **Date:** data e hora do commit.
* **Mensagem:** descrição informada no momento do commit.

Essas informações ajudam a identificar quando uma alteração foi realizada e por quem.

---

# Histórico resumido

Caso deseje visualizar apenas uma linha para cada commit, utilize:

### Comando

```bash
git log --oneline
```

**oneline** → *uma linha* → *somente a mensagem do registro, o nome atribuido ao registro no momento do commit*

Exemplo:

```text
9c3f4d7 Primeiro commit
```

Essa opção facilita a visualização quando o projeto possui muitos commits, ele mostra uma lista decrescente por ordem de realização.

---

# Exibindo uma quantidade específica de commits

Também é possível limitar a quantidade de registros exibidos.

### Comando

```bash
git log -2
```

Exemplo:

```text
Exibe apenas os dois commits mais recentes.
```

Substitua o número `2` pela quantidade desejada.

---

* `git log` exibe o histórico de commits;
* cada commit possui um identificador único;
* `git log --oneline` mostra um histórico resumido;
* `git log -2` limita a quantidade de commits exibidos.

---

# Resumo

Neste capítulo você aprendeu a consultar o histórico do repositório utilizando o comando `git log`.

Também conheceu as principais informações exibidas em um commit e formas de visualizar o histórico de maneira resumida.

---

# Próximo capítulo

## 07 - Entendendo a Área de Trabalho do Git

No próximo capítulo você aprenderá como o Git organiza os arquivos entre a área de trabalho, a área de preparação (Staging Area) e o repositório.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

