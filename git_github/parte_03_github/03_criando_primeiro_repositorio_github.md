**Tempo estimado:** 20 minutos

**Nível:** Iniciante

# Capítulo 03 — Criando o Primeiro Repositório no GitHub

---

# Pré-requisitos

Antes de iniciar este capítulo é recomendado possuir uma conta no GitHub.

---

# Neste capítulo você aprenderá

* Como criar um repositório remoto.
* A diferença entre repositório local e remoto.
* Como definir o nome e a visibilidade do repositório.
* Quais opções selecionar durante a criação.

---

# O que é um repositório remoto?

Um **repositório remoto** é uma cópia do seu projeto armazenada em um servidor, permitindo que ele seja acessado pela internet.

Enquanto o repositório local fica no seu computador, o repositório remoto ficará hospedado no GitHub.

Neste curso, utilizaremos o GitHub para armazenar o projeto desenvolvido nas Partes 1 e 2.

---

# Criando um repositório

Após fazer login no GitHub:

1. Clique em **New** ou **New repository**.
2. Informe o nome do repositório.
3. Escolha a visibilidade.
4. Clique em **Create repository**.

---

# Configurações do repositório

## Repository name

Nome do repositório.

Exemplo:

```text
meu_portifolio_ti
```

Procure utilizar nomes curtos e descritivos.

---

## Description (Opcional)

Descrição breve do projeto.

Exemplo:

```text
Documentação dos meus estudos sobre Git, GitHub, Linux e Redes de Computadores.
```

---

## Public

Qualquer pessoa poderá visualizar o repositório.

Ideal para:

* portfólio;
* estudos;
* projetos Open Source.

---

## Private

Somente pessoas autorizadas poderão acessar o repositório.

Ideal para projetos pessoais ou privados.

---

## README

Para este projeto, **não marque** a opção de criar um README.

Seu repositório local já possui um README, e criaremos a conexão entre ele e o GitHub no próximo capítulo.

---

## .gitignore

Também **não selecione** um modelo de `.gitignore`.

Seu projeto já possui esse arquivo configurado.

---

## License

Neste momento, deixe a opção **None**.

Licenças serão estudadas posteriormente.

---

# Representação visual

Antes:

```text
Computador
    │
    ▼

Repositório Local
```

Depois:

```text
Computador
    │
    ├────────► GitHub
    │
    ▼
Repositório Local

Repositório Remoto
```

Neste momento, os dois repositórios existem, mas ainda **não estão conectados**.

---

# O que aconteceu internamente?

Ao clicar em **Create repository**, o GitHub cria um repositório remoto vazio.

Ele ainda não possui commits, arquivos ou histórico.

Nos próximos capítulos, utilizaremos o Git para conectar o repositório local a esse repositório remoto e enviar todo o histórico desenvolvido até agora.

---

# Atenção

Se o GitHub perguntar se deseja criar um README, um `.gitignore` ou uma licença, deixe essas opções desmarcadas para este projeto.

Isso evita conflitos durante a primeira sincronização com o repositório local.

---

# Resumo

Neste capítulo você aprendeu como criar um repositório remoto no GitHub e compreendeu a diferença entre um repositório local e um remoto. Também conheceu as principais opções de configuração disponíveis durante a criação e preparou o ambiente para conectar seu projeto local ao GitHub.

---

# Próximo capítulo

## Capítulo 04 — Conectando o Repositório Local ao GitHub

No próximo capítulo você aprenderá como utilizar o comando `git remote` para conectar o repositório criado no seu computador ao repositório remoto hospedado no GitHub.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

