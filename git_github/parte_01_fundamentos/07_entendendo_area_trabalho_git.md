# Tempo estimado de leitura

**12 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* Como o Git organiza as alterações.
* O que é a Área de Trabalho (Working Tree).
* O que é a Área de Preparação (Staging Area).
* O que é o Repositório (Repository).
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

# Pré-requisitos

Recomenda-se ter concluído os capítulos anteriores.

---

# Conceito teórico

## Como o Git organiza um projeto?

Ao contrário do que muitos imaginam, o Git não grava imediatamente todas as alterações realizadas em um arquivo.

Antes que uma alteração seja registrada definitivamente, ela passa por algumas etapas.

Esse processo permite selecionar exatamente quais alterações farão parte de um commit.

---

# As três áreas do Git

O Git organiza o trabalho em três áreas principais:

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

# Área de Trabalho (Working Tree)

É onde os arquivos são criados, modificados, renomeados ou removidos.

Sempre que você altera um arquivo, essa alteração acontece primeiro na Área de Trabalho.

Nesse momento, o Git ainda não registrou nenhuma mudança.

---

# Área de Preparação (Staging Area)

A Área de Preparação funciona como uma etapa intermediária.

Quando você executa:

### Comando

```bash
git add README.md
```

**add** → *adicionar* 

o Git copia a versão atual do arquivo para a Área de Preparação.

Isso significa que esse arquivo está pronto para fazer parte do próximo commit.

---

# Repositório (Repository)

Quando você executa:

### Comando

```bash
git commit -m "Mensagem do commit"
```

o Git registra definitivamente todas as alterações que estavam na Área de Preparação.

Esse registro passa a fazer parte do histórico do projeto.

---

# Fluxo de trabalho

O fluxo básico do Git é:

```text
Criar ou modificar um arquivo
              │
              ▼
      Área de Trabalho
              │
       git add (adicionando)
              │
              ▼
     Área de Preparação
              │
      git commit (registrando)
              │
              ▼
        Repositório
```

---

# Exemplo prático

Imagine que você alterou o arquivo `README.md`.

Ao executar:

```bash
git status
```

o Git informa que existe uma alteração na Área de Trabalho.

Depois:

```bash
git add README.md
```

essa alteração é enviada para a Área de Preparação.

Por fim:

```bash
git commit -m "Atualiza README"
```

a alteração passa a fazer parte do histórico do projeto.

---

# Por que existe a Área de Preparação?

A Área de Preparação permite escolher exatamente quais alterações serão registradas.

Imagine que você modificou cinco arquivos, mas deseja registrar apenas dois.

Basta adicionar somente esses dois arquivos com `git add`.

Assim, o commit conterá apenas as alterações desejadas.

Essa é uma das principais vantagens do Git.

---

# O que foi aprendido

* o Git organiza as alterações em três áreas;
* a Área de Trabalho contém os arquivos modificados;
* `git add` envia arquivos para a Área de Preparação;
* `git commit` registra as alterações no repositório;
* `git status` ajuda a acompanhar esse processo.

---

# Resumo

Neste capítulo você aprendeu como o Git organiza as alterações antes de registrá-las.

Compreender esse fluxo facilita o entendimento dos próximos comandos e torna o uso do Git muito mais natural.

---

# Próximo capítulo

## 08 - Comparando Alterações com git diff

No próximo capítulo você aprenderá a visualizar exatamente quais linhas foram adicionadas, removidas ou modificadas antes de criar um commit.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

