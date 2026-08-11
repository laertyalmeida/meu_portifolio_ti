# Git e GitHub — Guia de Estudos

## Capítulo 05 — Primeiras Alterações em um Repositório Git

**Tempo estimado de leitura:** 12 minutos
**Nível:** Iniciante

---

## Neste capítulo você aprenderá

* Criar o primeiro arquivo do projeto.
* Verificar o estado do repositório.
* Adicionar arquivos à área de preparação (*Staging Area*).
* Criar o primeiro *commit*.
* Entender o fluxo básico de trabalho do Git.

---

# Informações do capítulo

| Campo                   | Informação                                 |
| ----------------------- | ------------------------------------------ |
| **Capítulo**            | 05                                         |
| **Título**              | Primeiras Alterações em um Repositório Git |
| **Autor**               | Laerte Costa                               |
| **Sistema Operacional** | Debian GNU/Linux                           |
| **Terminal**            | Bash                                       |
| **Última atualização**  | Agosto de 2026                             |

---

# Objetivo deste capítulo

Neste capítulo, você vai praticar o fluxo básico de trabalho do Git.

Vamos criar um arquivo dentro do projeto, verificar o estado do repositório, preparar o arquivo para ser salvo no histórico e, por fim, criar o primeiro *commit*.

Esse processo será repetido várias vezes durante o uso do Git.

---

# Pré-requisitos

É recomendado ter concluído os capítulos anteriores, principalmente os capítulos sobre:

* instalação do Git;
* configuração da identidade do Git;
* criação de um repositório.

---

# 1. Como o Git acompanha as alterações?

Depois que um repositório é criado, o Git **não salva automaticamente todas as alterações**.

É necessário informar ao Git quais arquivos devem fazer parte do próximo registro.

O fluxo básico é:

```text
Criar ou modificar um arquivo
            ↓
      git status
            ↓
        git add
            ↓
      git commit
            ↓
  Alteração registrada
```

Vamos entender cada etapa na prática.

---

# 2. Criando o primeiro arquivo

Primeiro, entre no diretório do projeto.

Dentro dele, vamos criar um arquivo chamado `README.md`.

### Comando

```bash
touch README.md
```

### O que esse comando faz?

O `touch` pode ser usado para:

* criar um arquivo vazio, caso ele não exista;
* atualizar a data e a hora de um arquivo que já existe.

Neste exemplo, como o arquivo ainda não existe, ele será criado.

### Entendendo o nome do arquivo

**README** significa *Read Me*, que pode ser entendido como **"Leia-me"**.

Esse tipo de arquivo normalmente contém informações importantes sobre um projeto, como:

* descrição;
* instruções;
* documentação;
* organização do projeto.

O `.md` significa **Markdown**, um formato muito utilizado para criar documentação.

> **Resumo**
>
> `touch README.md` → cria um arquivo chamado `README.md`.

---

# 3. Verificando o estado do repositório

Depois de criar o arquivo, vamos verificar o que o Git identificou.

### Comando

```bash
git status
```

O `git status` mostra a situação atual do repositório.

Um resultado parecido com este pode aparecer:

```text
On branch master

No commits yet

Untracked files:
  README.md
```

A parte mais importante neste momento é:

```text
Untracked files:
```

Isso significa que o Git encontrou um arquivo novo, mas ainda **não está acompanhando esse arquivo**.

### O que significa `untracked`?

`Untracked` significa **não rastreado**.

Ou seja, o arquivo existe na pasta do projeto, mas ainda não foi informado ao Git que ele deve fazer parte do próximo registro.

---

# 4. Adicionando o arquivo à área de preparação

Agora vamos informar ao Git que o arquivo deve fazer parte do próximo *commit*.

### Comando

```bash
git add README.md
```

O comando `git add` coloca o arquivo na **área de preparação**, também chamada de *Staging Area*.

Podemos pensar nessa área como uma espécie de **lista de arquivos que serão incluídos no próximo commit**.

### Entendendo o comando

```text
git add README.md
│   │   │
│   │   └── arquivo que será preparado
│   └────── adiciona o arquivo à preparação
└────────── comando do Git
```

> **Resumo**
>
> `git add README.md` → prepara o arquivo para o próximo *commit*.

---

# 5. Adicionando vários arquivos

Também podemos adicionar vários arquivos de uma só vez.

Uma forma bastante utilizada é:

### Comando

```bash
git add .
```

O ponto (`.`) representa o **diretório atual**.

Dessa forma, o Git adiciona as alterações encontradas no diretório atual à área de preparação.

> **Boa prática**
>
> Antes de usar `git add .`, é importante executar:
>
> ```bash
> git status
> ```
>
> Assim você consegue verificar quais arquivos foram modificados ou criados e evita preparar arquivos que não deveriam fazer parte do *commit*.

---

# 6. Verificando novamente

Depois de executar:

```bash
git add README.md
```

verifique novamente o estado do repositório:

```bash
git status
```

Agora deverá aparecer algo parecido com:

```text
Changes to be committed:
  new file: README.md
```

A mensagem:

```text
Changes to be committed
```

significa que existem alterações **preparadas para serem registradas**.

E:

```text
new file: README.md
```

indica que o `README.md` é um novo arquivo que fará parte do próximo *commit*.

---

# 7. Criando o primeiro commit

Agora que o arquivo está preparado, podemos criar o primeiro registro no histórico.

### Comando

```bash
git commit -m "Primeiro commit"
```

### O que é um commit?

Um *commit* é um registro das alterações realizadas no projeto.

Cada *commit* recebe uma mensagem para ajudar a identificar o que foi alterado.

A opção `-m` permite escrever essa mensagem diretamente no comando.

### Entendendo o comando

```text
git commit -m "Primeiro commit"
│   │      │
│   │      └── mensagem do commit
│   └───────── cria um registro no histórico
└───────────── comando do Git
```

Uma saída parecida com esta poderá aparecer:

```text
[master (root-commit) abc1234] Primeiro commit
 1 file changed
 create mode 100644 README.md
```

O texto e os números podem ser diferentes no seu computador.

O importante é entender que o Git registrou o primeiro *commit*.

---

# 8. Verificando o repositório depois do commit

Depois de criar o *commit*, execute novamente:

```bash
git status
```

O resultado esperado será parecido com:

```text
On branch master

nothing to commit, working tree clean
```

Isso significa que não existem alterações pendentes para serem registradas.

### Entendendo a mensagem

**nothing to commit**

Significa:

> Não há alterações para registrar.

**working tree clean**

Significa:

> A área de trabalho está limpa.

Em outras palavras, tudo que estava preparado foi registrado no último *commit*.

---

# 9. Entendendo o fluxo básico do Git

Agora podemos visualizar o processo completo:

```text
┌──────────────────────────────┐
│ Criar ou modificar arquivo   │
└──────────────┬───────────────┘
               ↓
        ┌─────────────┐
        │ git status  │
        └──────┬──────┘
               ↓
     ┌──────────────────┐
     │     git add      │
     │                  │
     │ Área de preparo  │
     └────────┬─────────┘
              ↓
     ┌──────────────────┐
     │    git commit    │
     └────────┬─────────┘
              ↓
     ┌──────────────────┐
     │ Histórico do Git │
     └──────────────────┘
```

Esse fluxo será usado diversas vezes durante o trabalho com Git.

---

# 10. A importância da Staging Area

A **Staging Area** é a área de preparação do Git.

Ela permite escolher quais alterações serão incluídas no próximo *commit*.

Por exemplo, imagine que você tenha três arquivos:

```text
README.md
config.txt
teste.py
```

Você pode preparar apenas:

```bash
git add README.md
```

Nesse caso, somente o `README.md` ficará preparado para o próximo *commit*.

Isso permite ter mais controle sobre o histórico do projeto.

---

# 11. Exemplo completo

Veja novamente todo o processo:

### 1. Criar o arquivo

```bash
touch README.md
```

### 2. Verificar o estado

```bash
git status
```

### 3. Adicionar o arquivo

```bash
git add README.md
```

### 4. Verificar novamente

```bash
git status
```

### 5. Criar o commit

```bash
git commit -m "Primeiro commit"
```

### 6. Conferir o estado final

```bash
git status
```

Se aparecer:

```text
nothing to commit, working tree clean
```

significa que o repositório está sem alterações pendentes.

---

# Boas práticas

Ao trabalhar com Git, procure desenvolver alguns hábitos:

* Use `git status` com frequência.
* Confira os arquivos antes de executar `git add .`.
* Crie mensagens de *commit* que expliquem o que foi alterado.
* Evite mensagens muito genéricas, como `coisas`, `teste` ou `alterações`.
* Faça *commits* pequenos e organizados.
* Não tenha medo de consultar `git status`; ele é um dos comandos mais úteis para entender o que está acontecendo.

---

# Resumo

Neste capítulo, você aprendeu a realizar o fluxo básico de trabalho do Git.

O processo pode ser resumido em:

```text
Criar ou modificar
        ↓
   git status
        ↓
     git add
        ↓
   git commit
        ↓
Alteração registrada
```

Você também aprendeu que o Git possui uma **área de preparação**, chamada *Staging Area*, que permite escolher quais alterações serão incluídas em cada *commit*.

---

# O que você aprendeu

Ao concluir este capítulo, você consegue:

* ✅ Criar arquivos usando `touch`.
* ✅ Verificar o estado do repositório usando `git status`.
* ✅ Identificar arquivos não rastreados (*untracked*).
* ✅ Adicionar arquivos à *Staging Area* usando `git add`.
* ✅ Criar um *commit* usando `git commit`.
* ✅ Entender o fluxo básico de trabalho do Git.
* ✅ Verificar se o repositório está limpo após um *commit*.

---

# Próximo capítulo

## Capítulo 06 — Consultando o Histórico de Alterações

No próximo capítulo, você aprenderá a consultar o histórico do repositório usando o comando:

```bash
git log
```

Com ele, será possível visualizar os *commits* realizados e entender melhor como o Git registra a evolução do projeto.

---

# 📚 Fonte de estudo

Este resumo foi elaborado a partir dos estudos e da prática do autor sobre **Git e GitHub**, utilizando os conteúdos da disciplina e materiais de estudo como referência.

**Observação:** este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo original das disciplinas e materiais utilizados como referência não deve ser reproduzido ou disponibilizado integralmente neste repositório.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

