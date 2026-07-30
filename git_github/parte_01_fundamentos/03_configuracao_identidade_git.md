# Tempo estimado de leitura

**8 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* Configurar seu nome no Git.
* Configurar seu e-mail no Git.
* Verificar as configurações realizadas.
* Descobrir onde essas informações são armazenadas.
* Entender a diferença entre configurações globais e locais.

---

# Git e GitHub — Guia de Estudos

---

# Informações do capítulo

| Campo                   | Informação                        |
| ----------------------- | --------------------------------- |
| **Capítulo**            | 03                                |
| **Título**              | Configuração da Identidade do Git |
| **Autor**               | Laerte Costa                      |
| **Sistema Operacional** | Debian GNU/Linux                  |
| **Terminal**            | Bash                              |
| **Última atualização**  | Julho de 2026                     |

---

# Objetivo deste capítulo

Aprender a configurar sua identidade no Git, compreender por que essas informações são necessárias e verificar onde elas ficam armazenadas no sistema.

---

# Pré-requisitos

Recomenda-se ter concluído o capítulo anterior, no qual foi realizada a instalação do Git.

---

# Conceito teórico

## O que é a identidade do Git?

Sempre que um **commit** é realizado, o Git registra quem foi o autor daquela alteração.

Para isso, é necessário configurar duas informações:

- nome do usuário;
- endereço de e-mail.

Esses dados passam a identificar a autoria de todos os commits realizados.

**commit** → *comprometer* → *assumir um compromisso* → *registro permanente de uma alteração no histórico do projeto.*

> **Observação**
>
> O nome e o e-mail configurados no Git não precisam, obrigatoriamente, ser os mesmos utilizados em sua conta do GitHub. Entretanto, utilizar o mesmo e-mail facilita a associação dos commits ao seu perfil.

---

# Configurando o nome do usuário

### Comando

```bash
git config --global user.name "Seu Nome"
```

Exemplo:

```bash
git config --global user.name "Laerte Costa"
```

### Explicação

Esse comando configura o nome que será utilizado para identificar a autoria dos seus commits.

**git** → *programa executado.*

**config** → *configurar.*

**--global** → *aplica a configuração para todos os repositórios do usuário.*

**user.name** → *nome do autor dos commits.*

---

# Configurando o e-mail

### Comando

```bash
git config --global user.email "seuemail@email.com"
```

Exemplo:

```bash
git config --global user.email "laerte@email.com"
```

### Explicação

Esse comando configura o endereço de e-mail associado aos seus commits.

**user.email** → *endereço de e-mail do autor dos commits.*

---

## O que significa a opção `--global`?

Ao utilizar a opção `--global`, a configuração será válida para todos os repositórios Git criados ou utilizados por esse usuário no computador.

Caso essa opção não seja utilizada, a configuração será aplicada apenas ao repositório atual.

Essa diferença será estudada com mais detalhes em capítulos futuros.

---

# Verificando as configurações

Após realizar as configurações, é recomendável verificar se elas foram gravadas corretamente.

Consultar o nome configurado:

### Comando

```bash
git config --global user.name
```

Consultar o e-mail configurado:

### Comando

```bash
git config --global user.email
```

Consultar todas as configurações do Git:

### Comando

```bash
git config --list
```

### Explicação

O comando `git config --list` exibe todas as configurações atualmente utilizadas pelo Git.

**list** → *listar* → *exibir todas as configurações disponíveis.*

---

# Onde essas informações são armazenadas?

Ao utilizar a opção `--global`, o Git salva essas configurações no arquivo:

```text
~/.gitconfig
```

Para visualizar o conteúdo do arquivo `.gitconfig`, utilize o comando abaixo.

### Comando

```bash
cat ~/.gitconfig
```

### Explicação

O comando `cat` exibe o conteúdo de um ou mais arquivos diretamente no terminal.

Nesse exemplo, ele mostra o conteúdo do arquivo `.gitconfig`, permitindo verificar as configurações globais do Git.

Exemplo:

```text
[user]
    name = Laerte Costa
    email = laerte@email.com
```

Se essas informações forem exibidas, significa que a configuração foi realizada com sucesso.

**cat** → *concatenate* → *concatenar* → *originalmente criado para unir (concatenar) o conteúdo de arquivos, mas é amplamente utilizado para exibir o conteúdo de arquivos no terminal.*

**~** → *representa o diretório pessoal (home) do usuário.*

**/** → *separa diretórios no sistema Linux.*

**~/** → *diretório pessoal do usuário atual.*

**.gitconfig** → *o ponto (.) no início do nome indica que o arquivo é oculto no Linux.*

---

## Curiosidade

O arquivo `.gitconfig` é um arquivo de texto simples.

Isso significa que ele pode ser visualizado ou editado utilizando qualquer editor de texto, como `nano`, `vim` ou `gedit`.

---

# Resumo

Neste capítulo você configurou sua identidade no Git.

A partir de agora, todos os commits realizados serão identificados pelo nome e endereço de e-mail configurados.

Você também aprendeu onde essas informações ficam armazenadas e como consultá-las sempre que necessário.

---

# O que você aprendeu

Ao concluir este capítulo, você é capaz de:

- ✅ Configurar o nome do usuário.
- ✅ Configurar o endereço de e-mail.
- ✅ Verificar as configurações realizadas.
- ✅ Entender a função da opção `--global`.
- ✅ Localizar o arquivo `.gitconfig`.

---

# Próximo capítulo

## Capítulo 04 — Criando o Primeiro Repositório Git

No próximo capítulo você aprenderá como criar seu primeiro repositório utilizando o comando `git init` e dará os primeiros passos no controle de versão.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**
