# Instalação do Git no Debian

## Ambiente utilizado

**Sistema operacional:**

```text
Debian GNU/Linux
```

A instalação e os testes desta documentação foram realizados em um sistema Debian utilizando o terminal.

---

## O que é Git?

Git é um sistema de controle de versão distribuído.

Ele permite acompanhar alterações realizadas em arquivos e projetos, mantendo um histórico completo das modificações.

Com o Git é possível:

* controlar versões de arquivos;
* registrar alterações realizadas em um projeto;
* recuperar versões anteriores;
* criar branches para desenvolvimento paralelo (seria como um local individual de rascunhos antes de mandar para o projeto principal);
* trabalhar com projetos locais e remotos;
* integrar projetos com plataformas como o GitHub.

---

## Verificando se o Git já está instalado

Antes de instalar um pacote no Debian, é recomendável verificar se ele já está instalado no sistema.

Abra o terminal.

**Atalho:**

```text
Ctrl + Alt + T
```

**Comando:**

```bash
apt list git
```

### Explicação

`apt`

Gerenciador de pacotes do Debian.

`list`

Lista informações sobre um pacote.

`git`

Nome do pacote pesquisado.

Esse comando informa se o pacote **Git** está disponível e indica se ele já está instalado.

Caso esteja instalado, aparecerá ao final da linha:

```text
[installed]
```

ou

```text
[instalado]
```

dependendo do idioma do sistema.

Outra forma de verificar consiste em consultar diretamente a versão instalada.

**Comando:**

```bash
git --version
```

### Explicação

`--version`

Solicita ao programa que informe sua versão instalada.

**Exemplo de retorno:**

```text
git version 2.x.x
```

Caso nenhuma versão seja exibida, significa que o Git ainda não está instalado ou não está disponível no caminho de execução do sistema.

---

## Atualizando a lista de pacotes do Debian

Antes de instalar novos programas, é recomendado atualizar a lista de pacotes disponíveis nos repositórios.

**Comando:**

```bash
sudo apt update
```

### Explicação

`sudo`

Executa o comando com privilégios administrativos.

`apt`

Gerenciador de pacotes do Debian.

`update`

Atualiza a lista de pacotes disponíveis nos repositórios configurados.

Esse comando **não instala atualizações**. Ele apenas sincroniza a lista de pacotes disponíveis para que o sistema conheça as versões mais recentes.

---

## Instalando o Git no Debian

**Comando:**

```bash
sudo apt install git
```

### Explicação

`apt`

Gerenciador de pacotes do Debian.

`install`

Solicita a instalação de um pacote.

`git`

Nome do pacote que será instalado.

O gerenciador `apt` baixa o pacote dos repositórios configurados e realiza sua instalação automaticamente no sistema.

---

## Confirmando a instalação

Após concluir a instalação, confirme se o Git está disponível no sistema.

**Comando:**

```bash
git --version
```

**Exemplo de retorno:**

```text
git version 2.39.5
```

Se uma versão for exibida, significa que a instalação foi concluída com sucesso.

---

## Localizando o executável do Git

Em sistemas Linux é comum existirem diversos diretórios contendo programas executáveis.

O comando abaixo informa qual executável será utilizado quando o comando `git` for executado no terminal.

**Comando:**

```bash
which git
```

**Exemplo de retorno:**

```text
/usr/bin/git
```

Isso indica o caminho completo do executável utilizado pelo sistema.

---

## Resumo do processo

```text
Debian GNU/Linux
       │
       ▼
apt update
       │
       ▼
apt install git
       │
       ▼
Git instalado
       │
       ▼
git --version
       │
       ▼
Instalação confirmada
```

---

## O que foi aprendido

Ao final desta etapa foi possível compreender que:

* o Git é um sistema de controle de versão distribuído;
* o Debian utiliza o gerenciador de pacotes `apt` para instalar programas;
* `apt update` atualiza a lista de pacotes disponíveis;
* `apt install git` instala o Git;
* `git --version` confirma se o Git está instalado corretamente;
* `which git` informa o caminho do executável utilizado pelo sistema.

---

## Próxima etapa

Na próxima etapa será realizada a configuração da identidade do usuário utilizada pelo Git.

Os principais comandos serão:

```bash
git config --global user.name
git config --global user.email
```

Essas informações serão registradas automaticamente em cada commit realizado, permitindo identificar o autor de cada alteração.

