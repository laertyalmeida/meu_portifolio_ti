# Tempo estimado de leitura

**8 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* Configurar seu nome no Git.
* Configurar seu e-mail no Git.
* Verificar as configurações realizadas.
* Descobrir onde o Git armazena essas informações.
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
| **Última atualização**  | Agosto de 2026                    |

---

# Objetivo deste capítulo

Aprender a configurar seu nome e seu e-mail no Git e entender como essas informações são utilizadas para identificar quem realizou cada alteração no projeto.

Também vamos verificar onde o Git armazena essas configurações.

---

# Pré-requisitos

É recomendado ter concluído o capítulo anterior, onde foi realizada a instalação do Git no Debian.

---

# Conceito teórico

## Por que precisamos configurar o Git?

Quando fazemos uma alteração em um projeto e registramos essa alteração com um **commit**, o Git precisa saber quem realizou aquele registro.

Para isso, configuramos:

* **nome do usuário**;
* **endereço de e-mail**.

Essas informações ficam associadas aos commits realizados pelo usuário.

### O que é um commit?

De forma simples, podemos entender o **commit** como um registro de uma alteração realizada no projeto.

Ele permite consultar posteriormente:

* quem realizou a alteração;
* quando ela foi realizada;
* o que foi registrado naquele momento.

> **Observação**
>
> O nome e o e-mail configurados no Git não precisam obrigatoriamente ser os mesmos utilizados na conta do GitHub.
>
> Porém, quando o e-mail utilizado no Git corresponde a um e-mail reconhecido pela conta do GitHub, os commits podem ser associados ao perfil.

---

# Configurando o nome

Para configurar o nome que será utilizado nos commits, usamos:

### Comando

```bash
git config --global user.name "Seu Nome"
```

### Exemplo

```bash
git config --global user.name "Laerte Costa"
```

### Entendendo o comando

**git** → executa o programa Git.

**config** → indica que queremos configurar alguma informação do Git.

**--global** → aplica a configuração para o usuário em todos os repositórios Git daquele computador.

**user.name** → define o nome do autor dos commits.

**"Laerte Costa"** → nome que será registrado como autor.

---

# Configurando o e-mail

Agora vamos configurar o endereço de e-mail.

### Comando

```bash
git config --global user.email "seuemail@email.com"
```

### Exemplo

```bash
git config --global user.email "laerte@email.com"
```

### Entendendo o comando

**user.email** → define o endereço de e-mail que será associado aos commits.

Assim como o nome, essa configuração será utilizada nos repositórios Git do usuário quando usamos a opção `--global`.

---

# O que significa `--global`?

A opção `--global` indica que a configuração será feita para o usuário atual do computador.

Por exemplo:

```bash
git config --global user.name "Laerte Costa"
```

Essa configuração poderá ser utilizada em todos os repositórios Git desse usuário.

Existe também a possibilidade de configurar informações específicas para apenas um repositório.

Por exemplo:

```bash
git config user.name "Outro Nome"
```

Nesse caso, a configuração será aplicada somente ao repositório atual.

> **Importante**
>
> Neste momento, o mais importante é entender que:
>
> **`--global` → configuração geral do usuário.**
>
> **Sem `--global` → configuração específica do repositório atual.**
>
> A configuração local será estudada com mais detalhes posteriormente.

---

# Verificando as configurações

Depois de configurar o nome e o e-mail, podemos verificar se tudo foi registrado corretamente.

## Verificando o nome

### Comando

```bash
git config --global user.name
```

Resultado esperado:

```text
Laerte Costa
```

---

## Verificando o e-mail

### Comando

```bash
git config --global user.email
```

Resultado esperado:

```text
laerte@email.com
```

---

## Listando as configurações

Também podemos pedir ao Git para mostrar várias configurações de uma vez.

### Comando

```bash
git config --list
```

Esse comando apresenta as configurações que o Git está utilizando.

Entre elas, podemos encontrar:

```text
user.name=Laerte Costa
user.email=laerte@email.com
```

**--list** → solicita ao Git que liste as configurações.

> **Dica**
>
> Durante os estudos, esse comando é útil para verificar rapidamente se uma configuração foi registrada.

---

# Onde o Git armazena essas informações?

Quando usamos `--global`, as configurações do usuário ficam armazenadas no arquivo:

```text
~/.gitconfig
```

Podemos visualizar esse arquivo diretamente pelo terminal.

### Comando

```bash
cat ~/.gitconfig
```

### Exemplo de resultado

```text
[user]
    name = Laerte Costa
    email = laerte@email.com
```

Se o nome e o e-mail aparecerem dessa forma, significa que as configurações foram gravadas no arquivo de configuração global.

---

# Entendendo `~/.gitconfig`

Vamos dividir o caminho para entender melhor:

```text
~/.gitconfig
```

**`~`** → representa o diretório pessoal do usuário, também chamado de **home**.

**`/`** → separa os diretórios e arquivos no Linux.

**`.gitconfig`** → arquivo utilizado pelo Git para armazenar configurações globais.

O ponto (`.`) no início do nome indica que o arquivo é **oculto** no Linux.

Portanto:

```text
~/.gitconfig
```

significa:

> Arquivo `.gitconfig` localizado dentro do diretório pessoal do usuário.

---

# Curiosidade

O arquivo `.gitconfig` é um arquivo de texto simples.

Por isso, ele pode ser visualizado utilizando comandos do terminal ou aberto com um editor de texto.

Por exemplo:

```bash
nano ~/.gitconfig
```

ou:

```bash
vim ~/.gitconfig
```

No entanto, normalmente não é necessário editar esse arquivo manualmente.

É mais seguro utilizar os próprios comandos do Git para realizar as configurações.

---

# Boas práticas

Ao configurar o Git, algumas práticas são importantes:

* Confira se o nome foi digitado corretamente.
* Confira se o e-mail está correto.
* Evite utilizar um e-mail que você não pretende associar aos seus commits.
* Depois de configurar, use `git config --list` para verificar as informações.
* Prefira utilizar os comandos do Git para alterar suas configurações.

---

# Resumo

Neste capítulo, configuramos a identidade do Git.

Aprendemos que o Git utiliza um **nome** e um **e-mail** para identificar o autor dos commits.

Também aprendemos que:

```bash
--global
```

faz com que a configuração seja aplicada ao usuário em seus repositórios Git.

As configurações globais ficam armazenadas em:

```text
~/.gitconfig
```

E podemos consultá-las utilizando comandos como:

```bash
git config --global user.name
```

```bash
git config --global user.email
```

e:

```bash
git config --list
```

---

# O que você aprendeu

Ao concluir este capítulo, você sabe:

* ✅ Configurar o nome do usuário no Git.
* ✅ Configurar o endereço de e-mail.
* ✅ Verificar as configurações.
* ✅ Entender o significado de `--global`.
* ✅ Diferenciar configurações globais e locais.
* ✅ Localizar o arquivo `.gitconfig`.
* ✅ Visualizar as configurações pelo terminal.

---

# Próximo capítulo

## Capítulo 04 — Criando o Primeiro Repositório Git

No próximo capítulo, vamos criar nosso primeiro repositório Git utilizando o comando:

```bash
git init
```

A partir daí, começaremos a trabalhar na prática com o controle de versão.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

