# Tempo estimado de leitura

**8 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* Verificar se o Git já está instalado no Debian.
* Atualizar a lista de pacotes do Debian.
* Instalar o Git.
* Confirmar se a instalação foi realizada com sucesso.

---

# Git e GitHub — Guia de Estudos

---

# Informações do capítulo

| Campo                   | Informação                  |
| ----------------------- | --------------------------- |
| **Capítulo**            | 02                          |
| **Título**              | Instalação do Git no Debian |
| **Autor**               | Laerte Costa                |
| **Sistema Operacional** | Debian GNU/Linux            |
| **Terminal**            | Bash                        |
| **Última atualização**  | Julho de 2026               |

---

# Pré-requisitos

Recomenda-se ter concluído o capítulo anterior, no qual foram apresentados os conceitos de Git e controle de versão.

---

# Conceito teórico

## O que é instalar um programa?

Instalar um programa é o processo de copiar seus arquivos para o sistema operacional e realizar as configurações necessárias para que ele possa ser executado corretamente.

No Debian, esse processo normalmente é realizado utilizando o **APT)**, uma ferramenta do própro Debian para gerenciar pacotes (programas) da distribuição.
**apt - Advanced Package Tool** → *Ferramenta avançada de pacotes*

O APT localiza os pacotes nos repositórios oficiais, realiza o download dos arquivos necessários e executa a instalação automaticamente.

---

# Verificando se o Git já está instalado

Abra o terminal do Debian (**Ctrl + Alt + T**).

### Comando

```bash
git --version
```

Se o Git estiver instalado, será exibido um resultado semelhante a este:

```text
git version 2.39.5
```

Caso seja exibida uma mensagem informando que o comando não foi encontrado, ou não aparecer nada,  será necessário instalar o Git.

Outra forma de verificar consiste em consultar o pacote disponível no sistema.

### Comando

```bash
apt list git
```
Esse comando informa se o pacote existe nas listas de repositórios e indica se ele já está instalado no sistema.

**list** → *lista*
**git** → *pacote (programa) desejado*

Se o pacote já estiver instalado, será exibido no final da linha:

```text
[installed]
```
---

# Atualizando a lista de pacotes

Antes de instalar um programa, recomenda-se atualizar a lista de pacotes disponíveis nos repositórios.

### Comando

```bash
sudo apt update
```
Esse comando **não instala nem atualiza programas**.
Ele apenas atualiza a lista de pacotes disponíveis nos repositórios configurados no sistema.

**sudo** → *super user do* → *executar como superusuário do debian*
**update** → *atualizar* → *atualiza a lista de pacotes do repositório* → *atualiza os pacotes (programas) da lista para novas versões encontradas*
---

# Instalando o Git

### Comando

```bash
sudo apt install git
```

O APT fará o download do Git e realizará sua instalação automaticamente.
Durante a instalação poderá ser solicitada a senha do usuário administrador.

**install** → *instalar*

---

# Confirmando a instalação

Após a instalação, execute novamente o comando:

### Comando

```bash
git --version
```

Se uma versão for exibida, significa que o Git foi instalado corretamente.
Caso deseje saber onde o executável foi instalado, utilize o comando abaixo.

---

# Localizando o executável

### Comando

```bash
which git
```

Exemplo:

```text
/usr/bin/git
```

Esse comando mostra o caminho do executável utilizado quando você digita `git` no terminal.

**which** → *qual* → *em qual caminho (qual diretório - pasta) está o executável no sistema debian*

---

# Resumo do processo

```text
Verificar se o Git está instalado
              │
              ▼
 Atualizar a lista de pacotes
              │
              ▼
       Instalar o Git
              │
              ▼
 Confirmar a instalação
```

---

# O que foi aprendido

* o Debian utiliza o APT para instalar programas;
* `git --version` verifica se o Git está instalado;
* `apt list git` informa se o pacote está disponível e se já está instalado;
* `sudo apt update` atualiza a lista de pacotes dos repositórios;
* `sudo apt install git` instala o Git;
* `which git` informa o caminho do executável.

---

# Próximo capítulo

## 03 - Configuração da Identidade do Git

No próximo capítulo você aprenderá a configurar seu nome de usuário e endereço de e-mail, informações que o Git utiliza para identificar a autoria de cada commit realizado.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

