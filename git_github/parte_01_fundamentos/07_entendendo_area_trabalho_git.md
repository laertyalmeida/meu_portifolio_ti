# Tempo estimado de leitura

**12 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* Como o Git organiza as alterações.
* O que é a Área de Trabalho (*Working Tree*).
* O que é a Área de Preparação (*Staging Area*).
* O que é o Repositório (*Repository*).
* Como os comandos `git add` e `git commit` atuam nesse processo.

---

# Git e GitHub — Guia de Estudos

---

# Informações do capítulo

| Campo                   | Informação                           |
| ----------------------- | ------------------------------------ |
| **Capítulo**            | 07                                   |
| **Título**              | Entendendo a Área de Trabalho do Git |
| **Autor**               | Laerte Costa                         |
| **Sistema Operacional** | Debian GNU/Linux                     |
| **Terminal**            | Bash                                 |
| **Última atualização**  | Julho de 2026                        |

---

# Objetivo deste capítulo

Compreender como o Git organiza as alterações realizadas nos arquivos antes de registrá-las definitivamente no histórico do projeto.

---

# Pré-requisitos

Recomenda-se ter concluído os capítulos anteriores.

---

# Conceito teórico

## Como o Git organiza um projeto?

Ao contrário do que muitos imaginam, o Git **não grava imediatamente** todas as alterações realizadas em um arquivo.

Antes que uma alteração seja registrada definitivamente, ela passa por etapas intermediárias.

Esse processo permite selecionar exatamente quais alterações farão parte do próximo commit.

---

# As três áreas do Git

O Git organiza o trabalho em três áreas principais.

```text
Área de Trabalho
        │
        ▼
Área de Preparação
        │
        ▼
Repositório
```

Cada uma possui uma função específica.

---

# Área de Trabalho (*Working Tree*)

A Área de Trabalho é onde os arquivos são criados, modificados, renomeados ou removidos.

Sempre que você altera um arquivo, essa alteração acontece primeiro nessa área.

Nesse momento, o Git ainda não registrou nenhuma mudança.

---

# Área de Preparação (*Staging Area*)

A Área de Preparação funciona como uma etapa intermediária entre os arquivos e o histórico do projeto.

Quando você executa:

### Comando

```bash
git add README.md
```

### Explicação

O comando `git add` copia a versão atual do arquivo para a Área de Preparação.

Isso significa que esse arquivo está pronto para fazer parte do próximo commit.

**git** → *programa executado.*

**add** → *adicionar.*

**README.md** → *arquivo que será preparado para o próximo commit.*

---

# Repositório (*Repository*)

Quando você executa:

### Comando

```bash
git commit -m "Mensagem do commit"
```

### Explicação

O comando `git commit` registra definitivamente todas as alterações que estavam na Área de Preparação.

A partir desse momento, elas passam a fazer parte do histórico do projeto.

**commit** → *registro permanente das alterações.*

**-m** → *message* → *mensagem do commit.*

---

# Fluxo de trabalho

O fluxo básico do Git pode ser representado da seguinte forma:

```text
Criar ou modificar um arquivo
              │
              ▼
      Área de Trabalho
              │
       git add
(adiciona à Área de Preparação)
              │
              ▼
     Área de Preparação
              │
      git commit
(registra no histórico)
              │
              ▼
        Repositório
```

---

# Exemplo prático

Imagine que você alterou o arquivo `README.md`.

Primeiro, execute:

```bash
git status
```

O Git informará que existe uma alteração na Área de Trabalho.

Depois execute:

```bash
git add README.md
```

Agora essa alteração foi enviada para a Área de Preparação.

Por fim:

```bash
git commit -m "Atualiza README"
```

A alteração passa a fazer parte do histórico permanente do projeto.

---

# Por que existe a Área de Preparação?

A Área de Preparação permite escolher exatamente quais alterações serão registradas.

Imagine que você modificou cinco arquivos, mas deseja registrar apenas dois.

Basta adicionar somente esses dois arquivos utilizando `git add`.

Assim, o commit conterá apenas as alterações desejadas.

Esse é um dos recursos mais importantes do Git.

---

## Curiosidade

Muitos sistemas de controle de versão registram todas as alterações diretamente.

O Git utiliza uma Área de Preparação justamente para oferecer maior controle sobre o conteúdo de cada commit.

---

# Resumo

Neste capítulo você aprendeu como o Git organiza as alterações antes de registrá-las definitivamente.

Compreender esse fluxo facilita o entendimento dos próximos comandos e torna o uso do Git muito mais intuitivo.

---

# O que você aprendeu

Ao concluir este capítulo, você é capaz de:

- ✅ Identificar as três áreas do Git.
- ✅ Compreender a função da Área de Trabalho.
- ✅ Entender o papel da Área de Preparação.
- ✅ Saber quando um arquivo passa a fazer parte do histórico.
- ✅ Relacionar os comandos `git add` e `git commit` com cada etapa do processo.

---

# Próximo capítulo

## Capítulo 08 — Comparando Alterações com `git diff`

No próximo capítulo você aprenderá a visualizar exatamente quais linhas foram adicionadas, removidas ou modificadas antes de criar um commit.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**
