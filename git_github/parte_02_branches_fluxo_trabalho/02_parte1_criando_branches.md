**20 minutos**

**Nível:** Iniciante

**Capítulo:** 02 — Criando Branches

---

# Pré-requisitos

Antes de iniciar este capítulo é recomendado compreender os capítulos anteriores.

---

# Neste capítulo você aprenderá

* Como criar uma nova Branch.
* O comando `git branch <nome-da-branch>`.
* O comando `git switch -c <nome-da-branch>`.
* A diferença entre criar uma Branch e trocar para ela.
* Como o Git cria uma nova referência.
* Como verificar se uma Branch foi criada corretamente.
* Boas práticas para nomear Branches.

---

Imagine uma equipe desenvolvendo um sistema.

A versão principal do projeto está funcionando na Branch:

```text
main
```

Um desenvolvedor recebe a tarefa de criar uma nova tela de login.

Outro desenvolvedor precisa corrigir um erro no sistema.

Um terceiro precisa testar uma nova configuração.

Se todos trabalharem diretamente na Branch principal, qualquer alteração poderá afetar o projeto funcionando.

A solução é criar Branches separadas.

Exemplo:

```text
main

A ─── B ─── C


tela_login

A ─── B ─── C ─── D ─── E


correcao_bug

A ─── B ─── C ─── F
```

Cada tarefa possui seu próprio espaço de desenvolvimento.

---

# Conceito teórico

## O que significa criar uma Branch?

Criar uma Branch significa criar uma nova referência dentro do histórico do Git.

Essa nova Branch inicialmente aponta para o mesmo commit onde ela foi criada.

Ela não copia todos os arquivos do projeto.

Ela apenas cria uma nova "linha de desenvolvimento" que poderá receber novos commits.

---

# Exemplo visual

Imagine o seguinte histórico:

```text
main

A ─── B ─── C
```

O commit atual (ou último commit)  é:

```text
C
```

Agora criamos uma nova Branch chamada:

```text
tela_login
```

O resultado será:

```text
main
 │
 A ─── B ─── C
              │
              tela_login
```

Neste momento:

* `main` continua apontando para o commit C;
* `login` também aponta para o commit C;
* nenhuma alteração foi criada ainda.

**As duas Branches estão no mesmo ponto do histórico.**

---

# Atenção

Criar uma Branch **não significa automaticamente começar a trabalhar nela**.

Quando executamos:

```bash
git branch tela_login
```

o Git cria a Branch:

```text
tela_login
```

mas permanece na Branch atual.

Exemplo:

Antes:

```text
* main
```

Depois:

```text
* main
  tela_login
```

A Branch foi criada, mas você continua na `main`.

Para trocar para ela, utilizaremos outro comando que veremos neste capítulo.

---

# Glossário

| Termo     | Tradução         | Significado no Git                              |
| --------- | ---------------- | ----------------------------------------------- |
| Create    | Criar            | Gerar uma nova referência                       |
| Branch    | Ramificação      | Linha independente de desenvolvimento           |
| Switch    | Alternar         | Mudar para outra Branch                         |
| Checkout  | Verificar/Trocar | Comando antigo para alternar referências        |
| Reference | Referência       | Ponteiro que aponta para um commit              |
| Pointer   | Ponteiro         | Referência para localização dentro do histórico |

---

# Primeiro comando: criar uma Branch

O primeiro comando para criação de Branches é:

```bash
git branch nome-da-branch
```

Agora vamos entender cada parte.

---

# Significado do comando

```bash
git branch nome-da-branch
```

## `git`

Tradução:

> Git

Significado:

Executa comandos do sistema de controle de versão Git.

---

## `branch`

Tradução:

> Ramificação

Significado:

Manipula Branches dentro do repositório.

Neste caso específico, será utilizado para criar uma nova Branch.

---

## `nome-da-branch`

Representa o nome que será dado para a nova Branch.

Exemplos:

```bash
git branch tela_login
```

Cria uma Branch chamada:

```text
tela_login
```

Outro exemplo:

```bash
git branch correcao_bug
```

Cria uma Branch chamada:

```text
correcao_bug
```

---

## Importante!

* `main` continua sendo a Branch atual;
* `tela_login e correcao_bug `foram criadas;
* o símbolo `*` mostra onde estamos trabalhando.

---

(Continua na Parte 2: `git switch -c`, diferença entre criar e mudar de Branch, boas práticas, laboratório e fechamento do capítulo.)

