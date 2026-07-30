# Tempo estimado de leitura

**8 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* Verificar se o Git já está instalado no Debian.
* Atualizar a lista de pacotes do Debian.
* Instalar o Git utilizando o APT.
* Confirmar se a instalação foi realizada com sucesso.
* Localizar o executável do Git no sistema.

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

# Objetivo deste capítulo

Aprender a verificar se o Git já está instalado no Debian, instalar a ferramenta utilizando o APT e confirmar que a instalação foi realizada corretamente.

---

# Pré-requisitos

Recomenda-se ter concluído o capítulo anterior, no qual foram apresentados os conceitos de Git e controle de versão.

---

# Conceito teórico

## O que é instalar um programa?

Instalar um programa é o processo de copiar seus arquivos para o sistema operacional e realizar as configurações necessárias para que ele possa ser executado corretamente.

No Debian, esse processo normalmente é realizado utilizando o **APT**, o gerenciador de pacotes da distribuição.

**APT** → *Advanced Package Tool* → *Ferramenta Avançada de Pacotes*

O APT é responsável por localizar programas nos repositórios oficiais, realizar o download dos arquivos necessários, instalar, atualizar e remover pacotes de forma automática.

---

# Verificando se o Git já está instalado

Antes de instalar qualquer programa, é uma boa prática verificar se ele já está presente no sistema. Isso evita instalações desnecessárias e permite conhecer a versão atualmente instalada.

### Comando

```bash
git --version
```

### Explicação

Esse comando exibe a versão instalada do Git.

Se o Git estiver instalado, será exibido um resultado semelhante a este:

```text
git version 2.39.5
```

Caso seja exibida uma mensagem informando que o comando não foi encontrado, será necessário instalar o Git.

> **Boa prática**
>
> Sempre confirme a instalação utilizando `git --version`. Assim você garante que o Git foi instalado corretamente e identifica rapidamente a versão disponível no sistema.

---

Outra forma de verificar consiste em consultar as informações do pacote disponível nos repositórios.

### Comando

```bash
apt list git
```

### Explicação

Esse comando consulta as informações do pacote **git** disponíveis nos repositórios e informa se ele já está instalado no sistema.

**list** → *listar*

**git** → *nome do pacote desejado*

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

### Explicação

Esse comando **não instala nem atualiza programas**.

Ele apenas atualiza a lista de pacotes disponíveis nos repositórios configurados no sistema, permitindo que o APT conheça as versões mais recentes disponíveis.

**sudo** → *Super User Do* → *executa o comando com privilégios administrativos.*

**update** → *atualizar* → *atualiza a lista de pacotes disponíveis nos repositórios.*

> **Observação**
>
> A atualização dos programas instalados é realizada com outros comandos, como `apt upgrade`, que será estudado posteriormente.

---

# Instalando o Git

### Comando

```bash
sudo apt install git
```

### Explicação

O APT localizará o pacote Git nos repositórios configurados, fará o download dos arquivos necessários e realizará a instalação automaticamente.

Durante a instalação poderá ser solicitada a senha do usuário administrador.

**install** → *instalar*

---

# Confirmando a instalação

Após a instalação, execute novamente o comando:

### Comando

```bash
git --version
```

### Explicação

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

### Explicação

Sempre que você executa um comando no terminal, o sistema procura seu executável nos diretórios configurados na variável de ambiente **PATH**.

O comando `which` informa exatamente qual executável será utilizado.

**which** → *qual* → *informa o caminho do executável utilizado pelo sistema.*

---

## Curiosidade

Os repositórios oficiais do Debian priorizam estabilidade e segurança. Por isso, nem sempre disponibilizam a versão mais recente dos programas, mas sim versões amplamente testadas e confiáveis.

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
              │
              ▼
 Localizar o executável (opcional)
```

---

# O que você aprendeu

Ao concluir este capítulo, você é capaz de:

- ✅ Verificar se o Git já está instalado.
- ✅ Atualizar a lista de pacotes do Debian.
- ✅ Instalar o Git utilizando o APT.
- ✅ Confirmar se a instalação foi concluída com sucesso.
- ✅ Localizar o executável do Git no sistema.

---

# Próximo capítulo

## Capítulo 03 — Configuração da Identidade do Git

No próximo capítulo você aprenderá a configurar seu nome de usuário e endereço de e-mail, informações que o Git utiliza para identificar a autoria de cada commit realizado.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**
