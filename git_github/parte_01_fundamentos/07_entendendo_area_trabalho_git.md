# Git e GitHub — Guia de Estudos

## Capítulo 07 — Entendendo as Áreas do Git

**Tempo estimado de leitura:** 12 minutos
**Nível:** Iniciante

---

## Neste capítulo você aprenderá

* Como o Git organiza as alterações.
* O que é a Área de Trabalho (*Working Tree*).
* O que é a Área de Preparação (*Staging Area*).
* O que é o Repositório (*Repository*).
* Como `git add` e `git commit` participam desse processo.

---

# Informações do capítulo

| Campo                   | Informação                 |
| ----------------------- | -------------------------- |
| **Capítulo**            | 07                         |
| **Título**              | Entendendo as Áreas do Git |
| **Autor**               | Laerte Costa               |
| **Sistema Operacional** | Debian GNU/Linux           |
| **Terminal**            | Bash                       |
| **Última atualização**  | Agosto de 2026             |

---

# Objetivo deste capítulo

Neste capítulo, você vai entender como o Git organiza as alterações feitas nos arquivos antes que elas sejam registradas no histórico do projeto.

Esse entendimento é importante para compreender melhor comandos como:

```bash
git status
git add
git commit
```

---

# Pré-requisitos

É recomendado ter concluído os capítulos anteriores, principalmente os capítulos sobre:

* criação de um repositório;
* criação de arquivos;
* `git status`;
* `git add`;
* `git commit`;
* `git log`.

---

# 1. Como o Git organiza as alterações?

Quando você cria ou modifica um arquivo, o Git não coloca essa alteração diretamente no histórico.

Antes de chegar ao histórico, a alteração passa por algumas etapas.

Podemos imaginar esse processo como três lugares diferentes:

```text
┌──────────────────────┐
│   Área de Trabalho   │
│    Working Tree      │
└──────────┬───────────┘
           │
        git add
           ↓
┌──────────────────────┐
│ Área de Preparação   │
│    Staging Area      │
└──────────┬───────────┘
           │
       git commit
           ↓
┌──────────────────────┐
│      Repositório     │
│      Repository      │
└──────────────────────┘
```

Cada área possui uma função diferente.

---

# 2. Área de Trabalho — Working Tree

A **Área de Trabalho** é o local onde você trabalha normalmente.

É nela que os arquivos do projeto ficam disponíveis para serem:

* criados;
* modificados;
* renomeados;
* removidos.

Por exemplo, imagine que você tenha:

```text
README.md
index.html
script.py
```

Se você abrir o `README.md` e adicionar algum texto, a alteração acontece primeiro na **Área de Trabalho**.

Nesse momento, ela ainda não foi preparada para um *commit*.

---

# 3. Verificando a Área de Trabalho

Podemos utilizar:

```bash
git status
```

O Git pode mostrar algo parecido com:

```text
Changes not staged for commit:
  modified: README.md
```

A expressão:

```text
Changes not staged for commit
```

significa que existe uma alteração, mas ela **ainda não foi adicionada à Área de Preparação**.

---

# 4. Área de Preparação — Staging Area

A **Área de Preparação**, também chamada de *Staging Area*, é uma etapa intermediária.

É nela que colocamos as alterações que queremos incluir no próximo *commit*.

Para adicionar um arquivo, usamos:

```bash
git add README.md
```

Depois disso, o `README.md` passa a fazer parte da Área de Preparação.

Podemos pensar assim:

```text
Área de Trabalho
      │
      │ git add
      ↓
Área de Preparação
```

---

# 5. O que o git add faz?

O comando:

```bash
git add README.md
```

informa ao Git:

> "Quero que a versão atual deste arquivo faça parte do próximo commit."

Por isso, o `git add` é uma etapa importante do fluxo de trabalho.

### Entendendo o comando

```text
git add README.md
│   │   │
│   │   └── arquivo que será preparado
│   └────── adiciona o arquivo à preparação
└────────── comando do Git
```

---

# 6. Conferindo a Área de Preparação

Depois de executar:

```bash
git add README.md
```

podemos verificar novamente:

```bash
git status
```

Agora o Git poderá mostrar:

```text
Changes to be committed:
  modified: README.md
```

A mensagem:

```text
Changes to be committed
```

significa que a alteração está **preparada para o próximo commit**.

---

# 7. Repositório — Repository

Depois de preparar as alterações, podemos registrá-las no histórico.

Para isso, usamos:

```bash
git commit -m "Atualiza README"
```

O `git commit` cria um novo registro no histórico do repositório utilizando as alterações que estão na Área de Preparação.

Podemos representar assim:

```text
Área de Preparação
        │
        │ git commit
        ↓
    Repositório
```

Depois do *commit*, essa alteração passa a fazer parte do histórico do projeto.

---

# 8. O que acontece com o arquivo?

Vamos acompanhar um exemplo simples.

Imagine que o `README.md` já esteja sendo acompanhado pelo Git.

Você modifica o arquivo:

```text
README.md
```

A alteração está na:

```text
Área de Trabalho
```

Depois você executa:

```bash
git add README.md
```

Agora a versão atual do arquivo está preparada:

```text
Área de Preparação
```

Depois você executa:

```bash
git commit -m "Atualiza README"
```

Agora a alteração foi registrada:

```text
Repositório
```

O fluxo fica assim:

```text
Modificar
   ↓
Working Tree
   ↓
git add
   ↓
Staging Area
   ↓
git commit
   ↓
Repository
```

---

# 9. Por que existe a Área de Preparação?

Essa é uma das partes mais importantes para entender o Git.

Imagine que você modificou cinco arquivos:

```text
README.md
index.html
script.py
config.txt
teste.py
```

Mas você deseja criar um *commit* contendo somente:

```text
README.md
script.py
```

Você pode preparar apenas esses arquivos:

```bash
git add README.md script.py
```

Depois:

```bash
git commit -m "Atualiza documentação e script"
```

Dessa forma, os outros arquivos não serão incluídos nesse *commit*.

A Área de Preparação permite ter esse controle.

---

# 10. Área de Trabalho × Área de Preparação

É importante entender a diferença entre essas duas áreas.

### Área de Trabalho

É onde você está trabalhando nos arquivos.

Exemplo:

```text
README.md foi modificado
```

Mas ainda não foi preparado.

### Área de Preparação

É onde ficam as alterações escolhidas para o próximo *commit*.

Exemplo:

```text
README.md está preparado
```

Podemos resumir:

```text
Área de Trabalho
    ↓
Alterações realizadas

Área de Preparação
    ↓
Alterações escolhidas para o commit
```

---

# 11. Área de Preparação × Repositório

Também existe uma diferença importante entre essas duas áreas.

### Área de Preparação

Contém alterações que **serão incluídas no próximo commit**.

### Repositório

Contém os *commits* que já foram registrados no histórico.

Podemos pensar assim:

```text
Staging Area
    ↓
"Ainda vou registrar"

Repository
    ↓
"Já registrei"
```

---

# 12. Exemplo completo

Vamos imaginar que você modificou o `README.md`.

### 1. Verificar o estado

```bash
git status
```

O Git identifica a alteração.

### 2. Preparar o arquivo

```bash
git add README.md
```

Agora a alteração está na *Staging Area*.

### 3. Conferir

```bash
git status
```

Deve aparecer algo semelhante a:

```text
Changes to be committed:
  modified: README.md
```

### 4. Criar o commit

```bash
git commit -m "Atualiza README"
```

### 5. Conferir novamente

```bash
git status
```

Se aparecer:

```text
nothing to commit, working tree clean
```

significa que não existem alterações pendentes.

---

# 13. O fluxo completo do Git

Podemos resumir todo o processo desta forma:

```text
┌──────────────────────────────┐
│       ÁREA DE TRABALHO       │
│         Working Tree         │
│                              │
│ Criar ou modificar arquivos  │
└──────────────┬───────────────┘
               │
               │ git add
               ↓
┌──────────────────────────────┐
│     ÁREA DE PREPARAÇÃO       │
│         Staging Area         │
│                              │
│ Alterações escolhidas        │
│ para o próximo commit        │
└──────────────┬───────────────┘
               │
               │ git commit
               ↓
┌──────────────────────────────┐
│         REPOSITÓRIO          │
│          Repository          │
│                              │
│ Histórico de commits         │
└──────────────────────────────┘
```

---

# 14. Comandos relacionados

| Comando                    | Função                                          |
| -------------------------- | ----------------------------------------------- |
| `git status`               | Mostra o estado atual do repositório.           |
| `git add arquivo`          | Coloca um arquivo na Área de Preparação.        |
| `git add .`                | Prepara as alterações do diretório atual.       |
| `git commit -m "mensagem"` | Registra as alterações preparadas no histórico. |
| `git log`                  | Mostra os commits registrados no histórico.     |

---

# Boas práticas

Ao trabalhar com Git:

* Use `git status` antes e depois de preparar alterações.
* Confira quais arquivos serão incluídos no *commit*.
* Evite usar `git add .` sem verificar antes o estado do repositório.
* Faça *commits* organizados.
* Use mensagens que expliquem claramente o que foi alterado.
* Entenda a diferença entre alteração na Área de Trabalho e alteração preparada.

---

# Resumo

O Git organiza o trabalho em três áreas principais:

```text
Área de Trabalho
       ↓
Staging Area
       ↓
Repositório
```

### Área de Trabalho

É onde os arquivos são criados e modificados.

### Área de Preparação

É onde colocamos as alterações que queremos incluir no próximo *commit*.

### Repositório

É onde ficam registrados os *commits* e o histórico do projeto.

Os principais comandos desse fluxo são:

```bash
git status
git add
git commit
```

Entender essas três áreas facilita muito o aprendizado dos próximos comandos do Git.

---

# O que você aprendeu

Ao concluir este capítulo, você consegue:

* ✅ Identificar as três principais áreas do Git.
* ✅ Entender a função da Área de Trabalho.
* ✅ Entender o que é a *Staging Area*.
* ✅ Entender o papel do Repositório.
* ✅ Saber o que acontece quando usamos `git add`.
* ✅ Saber o que acontece quando usamos `git commit`.
* ✅ Entender como uma alteração chega ao histórico do Git.

---

# Próximo capítulo

## Capítulo 08 — Comparando Alterações com `git diff`

No próximo capítulo, você aprenderá a utilizar o comando:

```bash
git diff
```

Esse comando permite visualizar as diferenças entre o conteúdo atual dos arquivos e o que foi registrado pelo Git.

---

# 📚 Fonte de estudo

Este resumo foi elaborado a partir dos estudos e da prática do autor sobre **Git e GitHub**, utilizando os conteúdos da disciplina e materiais de estudo como referência.

**Observação:** este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo original das disciplinas e materiais utilizados como referência não deve ser reproduzido ou disponibilizado integralmente neste repositório.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

