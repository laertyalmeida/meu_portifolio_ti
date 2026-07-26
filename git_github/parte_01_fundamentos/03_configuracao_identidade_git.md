# Tempo estimado de leitura

**8 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* Configurar seu nome no Git.
* Configurar seu e-mail no Git.
* Verificar as configurações realizadas.
* Descobrir onde essas informações são armazenadas.

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

# Pré-requisitos

Recomenda-se ter concluído o capítulo anterior, no qual foi realizada a instalação do Git.

---

# Conceito teórico

## O que é a identidade do Git?

Sempre que um **commit** é realizado, o Git registra quem fez aquela alteração.

**commit** → *comprometer* → *um compromisso registrado* → *registro*

Para isso, é necessário configurar duas informações:

* nome do usuário;
* endereço de e-mail.

Esses dados passam a identificar a autoria dos seus commits.

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

Esse nome e e-mail serão registrados em todos os commits.

**git** → *programa executado*
**config** → *configuração*
**--global** → *global, para todos os registros*
**user.name** → *nome do usuário*
**user.email** → *email do usuário*
---

# Verificando as configurações

Consultar o nome configurado:

### Comando

```bash
git config --global user.name
```

Consulta o nome configurado:

### Comando

```bash
git config --global user.email
```
Consulta o email configurado:


### Comando

```bash
git config --list
```

Exibe todas as configurações atualmente utilizadas pelo Git.

---

# Onde essas informações são armazenadas?

Ao utilizar a opção `--global`, o Git salva essas configurações no arquivo:

```text
~/.gitconfig
```

Para visualizar seu conteúdo:

### Comando

```bash
cat ~/.gitconfig
```

Exemplo:

```text
[user]
    name = Laerte Costa
    email = laerte@email.com
```

Se essas informações forem exibidas, a configuração foi realizada com sucesso.

**~** →  *sinal "til" ~ no debian informa que o ambiente de trabalho sendo utilizado é o usuário local*
**/** → *sinal "barra" / depois do nome no debian, informa que é um diretório*
**~/** → *diretório do usuário local*
**cat** → *concatenate* → *concatenar* → *visualizar o conteúdo do arquivo*
**.** → *o "ponto" . no debian antes do arquivo, indica que o arquivo está oculto*

---

# O que foi aprendido

* o Git registra o autor de cada commit;
* `git config --global user.name` configura o nome do usuário;
* `git config --global user.email` configura o e-mail do usuário;
* `git config --list` exibe as configurações do Git;
* `cat ~/.gitconfig` permite visualizar onde essas configurações são armazenadas.

---

# Resumo

Neste capítulo você configurou sua identidade no Git.

A partir de agora, seus commits serão identificados pelo nome e endereço de e-mail configurados.

---

# Próximo capítulo

## 04 - Criando o Primeiro Repositório Git

No próximo capítulo você aprenderá como criar seu primeiro repositório utilizando o comando `git init` e dará os primeiros passos no controle de versão.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

