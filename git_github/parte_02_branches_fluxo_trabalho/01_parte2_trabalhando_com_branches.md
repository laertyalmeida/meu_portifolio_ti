# Tempo estimado de leitura

**15 minutos**

**Nível:** Iniciante

**Parte:** 2 — Trabalhando com Branches

---

# Continuação do capítulo

## Primeiro comando relacionado às Branches

Depois de compreender o conceito de Branch, chegou o momento de conhecer o primeiro comando utilizado para trabalhar com elas.

O comando é:

```bash
git branch
```

Quando executado sem opções, ele exibe todas as Branches existentes no repositório e identifica qual delas está ativa no momento.

Antes de executar o comando, vamos entender cada parte.

---

# Significado do comando

```bash
git branch
```

## `git`

**Tradução:** Git.

É o comando principal utilizado para executar funcionalidades do sistema de controle de versão Git.

Sempre que um comando começa com `git`, estamos informando ao sistema que desejamos utilizar algum recurso do Git.

---

## `branch`

**Tradução:** Ramificação ou galho.

No Git, `branch` é o subcomando responsável pelo gerenciamento das ramificações do projeto.

Ele pode ser utilizado para:

* listar Branches;
* criar novas Branches;
* renomear Branches;
* excluir Branches.

Neste momento, utilizaremos o comando apenas para listar as Branches existentes.

---

# Executando o comando

## Cenário

Você iniciou o trabalho em um projeto e deseja verificar quais Branches existem e em qual delas está trabalhando.

## Comando

```bash
git branch
```

---

# Resultado

Exemplo de saída:

```text
* main
```

---

# Explicação da saída

## `*`

O símbolo de asterisco indica a Branch atualmente ativa.

Isso significa que o Git está apontando o trabalho atual para essa Branch.

Todos os próximos commits serão registrados nela.

---

## `main`

Representa o nome da Branch ativa.

Neste exemplo, o usuário está trabalhando na Branch principal do projeto.

Em alguns repositórios mais antigos, esse nome pode aparecer como:

```text
master
```

---

# Outro exemplo

Após criar outras Branches, o resultado pode ser:

```text
correcao-login
* desenvolvimento
main
```

Explicação:

* `correcao-login` existe, mas não está ativa.
* `desenvolvimento` é a Branch atual.
* `main` continua existindo, porém não está selecionada.

O Git sempre exibirá apenas uma Branch marcada com o símbolo `*`.

---

# O que aconteceu internamente?

Ao executar:

```bash
git branch
```

o Git apenas consultou as referências existentes dentro do repositório.

Esse comando:

* não cria commits;
* não altera arquivos;
* não modifica o histórico;
* não altera nenhuma Branch.

Ele apenas apresenta informações armazenadas pelo Git.

Por isso, é um comando seguro e pode ser executado sempre que necessário.

---

# Exemplos práticos

## Exemplo 1

### Cenário

Antes de iniciar uma nova funcionalidade, você deseja confirmar se está trabalhando na Branch correta.

### Comando

```bash
git branch
```

### Resultado

```text
* main
```

### Explicação

O resultado informa que a Branch atual é `main`.

Caso você realize um commit agora, ele será registrado diretamente na Branch principal.

---

## Exemplo 2

### Cenário

Um projeto possui diferentes linhas de desenvolvimento e você deseja visualizar todas as Branches disponíveis.

### Comando

```bash
git branch
```

### Resultado

```text
feature-login
feature-dashboard
* desenvolvimento
main
```

### Explicação

O projeto possui quatro Branches.

A Branch ativa é:

```text
desenvolvimento
```

Os próximos commits serão registrados nela.

---

# Boas práticas

* Sempre verifique a Branch atual antes de iniciar uma tarefa.
* Utilize `git branch` para confirmar onde está trabalhando.
* Evite criar commits diretamente na Branch principal em projetos profissionais.
* Desenvolva novas funcionalidades em Branches separadas.

---

# Atenção

Um erro comum entre iniciantes é acreditar que:

```bash
git branch
```

cria uma nova Branch.

Isso não acontece.

Quando utilizado sem argumentos, o comando apenas lista as Branches existentes.

A criação de novas Branches será apresentada no próximo capítulo.

---

# Dicas

Antes de executar um commit importante, crie o hábito de verificar:

```bash
git branch
```

Esse pequeno cuidado evita registrar alterações na Branch errada.

---

# Curiosidade

Uma Branch não é uma cópia completa do projeto.

O Git trabalha com referências que apontam para commits existentes.

Por isso, criar uma nova Branch é uma operação rápida e eficiente, mesmo em projetos grandes.

---

# Laboratório guiado

## Objetivo

Identificar as Branches existentes em um repositório Git.

---

## Passo 1

Acesse um repositório Git.

```bash
cd meu_projeto
```

---

## Passo 2

Execute o comando:

```bash
git branch
```

---

## Passo 3

Observe:

* qual Branch possui o símbolo `*`;
* qual é o nome da Branch atual;
* quantas Branches existem no projeto.

---

# O que foi aprendido

Neste capítulo você aprendeu:

* o conceito de Branch;
* por que Branches são utilizadas;
* o funcionamento da Branch principal;
* o conceito de HEAD;
* como listar Branches com `git branch`;
* como interpretar a saída do terminal;
* boas práticas para trabalhar com Branches.

---

# Resumo

Neste capítulo você conheceu o conceito de Branch, uma das principais funcionalidades do Git para organização de projetos. Aprendeu que Branches permitem criar linhas independentes de desenvolvimento, possibilitando trabalhar em novas funcionalidades ou correções sem comprometer a versão principal.

Também aprendeu a utilizar o comando `git branch` para visualizar as Branches existentes, identificar a Branch atual e compreender como o Git organiza essas referências internamente.

---

# Próximo capítulo

## Capítulo 02 — Criando Branches

No próximo capítulo você aprenderá como criar novas Branches utilizando os comandos do Git.

Será apresentado o comando:

```bash
git branch nome-da-branch
```

e também:

```bash
git switch -c nome-da-branch
```

Você entenderá a diferença entre essas formas de criação, quando utilizar cada uma e como esse processo é aplicado no fluxo de trabalho profissional.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

