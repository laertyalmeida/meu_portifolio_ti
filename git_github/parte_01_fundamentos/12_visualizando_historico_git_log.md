# Tempo estimado de leitura

**12 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* O que é o comando `git log`.
* Consultar o histórico de commits.
* Entender as informações exibidas pelo Git.
* Utilizar opções para melhorar a visualização do histórico.
* Encontrar informações importantes sobre alterações realizadas no projeto.

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
| **Última atualização**  | Julho de 2026                          |

---

# Pré-requisitos

Recomenda-se ter concluído os capítulos anteriores.

---

# Conceito teórico

## O que é o histórico do Git?

Uma das principais características do Git é registrar todas as alterações importantes realizadas em um projeto.

Cada vez que um commit é criado, o Git armazena informações como:

* quem realizou a alteração;
* quando ela aconteceu;
* qual mensagem foi registrada;
* quais arquivos foram modificados.

Esse conjunto de registros forma o histórico do projeto.

O histórico permite acompanhar a evolução dos arquivos e recuperar informações importantes sobre o desenvolvimento.

---

# O que é o `git log`?

O comando:

```bash
git log
```

permite visualizar o histórico de commits de um repositório.

Ele apresenta os registros realizados desde o commit mais recente até os commits mais antigos.

---

# Visualizando o histórico

Execute:

### Comando

```bash
git log
```

Exemplo:

```text
commit a84f91c2d8e7f6a5b4
Author: Laerte Costa
Date:   Jul 30 2026

    Adiciona documentação do capítulo 11
```

---

# Entendendo a saída do `git log`

## Commit

Exemplo:

```text
commit a84f91c2d8e7f6a5b4
```

Representa o identificador único do commit.

Esse código é chamado de **hash**.

O Git utiliza esse identificador para localizar exatamente uma versão registrada do projeto.

---

## Author

Exemplo:

```text
Author: Laerte Costa
```

Mostra o autor responsável pelo commit.

Essa informação é definida através da configuração:

```bash
git config --global user.name
```

e:

```bash
git config --global user.email
```

---

## Date

Exemplo:

```text
Date: Jul 30 2026
```

Mostra quando o commit foi criado.

---

## Mensagem do commit

Exemplo:

```text
Adiciona documentação do capítulo 11
```

É a mensagem informada no momento da criação do commit:

```bash
git commit -m "mensagem"
```

Mensagens claras ajudam a entender a evolução do projeto.

---

# Navegando pelo histórico

Assim como no `git diff`, o Git utiliza o paginador `less`.

Comandos:

```text
Espaço → próxima página

b → página anterior

/texto → pesquisar

n → próxima ocorrência

q → sair
```

---

# Visualização resumida

O histórico completo pode apresentar muitas informações.

Para visualizar apenas uma linha por commit:

### Comando

```bash
git log --oneline
```

Exemplo:

```text
a84f91c Adiciona documentação do capítulo 11
7c921aa Adiciona capítulo sobre git restore
3bd82ef Cria estrutura inicial do projeto
```

---

# Entendendo o `--oneline`

**oneline** → uma linha

Essa opção apresenta uma versão resumida do histórico mostrando:

* hash reduzido do commit;
* mensagem do commit.

É muito utilizada para consultar rapidamente a evolução do projeto.

---

# Exibindo arquivos alterados

Para visualizar um resumo das alterações realizadas em cada commit:

### Comando

```bash
git log --stat
```

Exemplo:

```text
3 files changed, 120 insertions(+), 5 deletions(-)
```

Mostra:

* quantidade de arquivos modificados;
* linhas adicionadas;
* linhas removidas.

---

# Mostrando as alterações de cada commit

Para visualizar exatamente quais alterações foram realizadas em cada commit:

### Comando

```bash
git log -p
```

A opção:

```text
-p
```

vem de:

```text
patch
```

e apresenta as diferenças (*diff*) registradas nos commits.

---

# Limitando a quantidade de commits

Para mostrar apenas os últimos commits:

### Comando

```bash
git log -5
```

Nesse exemplo:

```text
-5
```

significa:

mostrar os últimos 5 commits.

---

# Filtrando commits por autor

É possível pesquisar commits realizados por determinado autor.

### Comando

```bash
git log --author="Laerte"
```

O Git exibirá apenas commits relacionados ao autor informado.

---

# Pesquisando mensagens de commits

Para procurar uma palavra dentro das mensagens:

### Comando

```bash
git log --grep="capítulo"
```

O Git exibirá somente commits que possuem a palavra pesquisada na mensagem.

---

# Consultando um commit específico

Cada commit possui um identificador único.

Para visualizar detalhes de um commit:

### Comando

```bash
git show a84f91c
```

O comando:

```text
git show
```

apresenta:

* autor;
* data;
* mensagem;
* arquivos modificados;
* diferenças realizadas.

---

# Boa prática

## Utilize mensagens claras nos commits

Evite:

```text
alterações
```

Prefira:

```text
Adiciona documentação do capítulo 12
```

Mensagens bem escritas facilitam localizar mudanças no futuro.

---

## Consulte o histórico antes de alterar arquivos importantes

O histórico funciona como uma linha do tempo do projeto.

Ele permite entender:

* quando uma alteração foi realizada;
* quem realizou;
* qual era o objetivo da mudança.

---

## Crie commits organizados

Commits pequenos e bem definidos facilitam:

* encontrar problemas;
* entender mudanças;
* recuperar versões anteriores.

---

# O que foi aprendido

* `git log` exibe o histórico de commits;
* cada commit possui um identificador único (*hash*);
* mensagens de commit ajudam a compreender alterações;
* `--oneline` apresenta uma visão resumida;
* `git show` permite analisar um commit específico;
* o histórico ajuda a acompanhar a evolução do projeto.

---

# Resumo

Neste capítulo você aprendeu a consultar o histórico do Git utilizando o comando `git log`.

Também aprendeu diferentes formas de visualizar commits, encontrar informações específicas e utilizar o histórico como uma ferramenta de organização e segurança.

O histórico do Git não serve apenas para consultar informações, mas também para compreender a evolução de um projeto e tomar decisões com mais segurança.

---

# Próximo capítulo

## 13 - Revisão da Parte 1 e Desafio Prático

No próximo capítulo você revisará os principais conceitos aprendidos até aqui e realizará um desafio prático utilizando o fluxo completo do Git:

```text
Criar
 ↓
Modificar
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

Esse exercício ajudará a consolidar o aprendizado antes de iniciar a Parte 2, onde serão apresentados conceitos mais avançados como branches e desenvolvimento paralelo.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

