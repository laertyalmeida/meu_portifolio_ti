## Tempo estimado de leitura

**25 minutos**

**Nível:** Intermediário

# Capítulo 14 – Trabalhando com Tags no Git

---

# Neste capítulo você aprenderá

- O que são tags no Git.
- Quando utilizar uma tag.
- A diferença entre tags leves (*lightweight*) e anotadas (*annotated*).
- Como criar, listar e remover tags.
- Como enviar tags para o GitHub.
- Boas práticas para versionamento.

---

# Objetivo

Durante o desenvolvimento de um projeto, chega um momento em que desejamos marcar uma versão importante do código.

Pode ser a primeira versão funcional, uma versão estável ou um lançamento para produção.

O Git permite fazer isso utilizando **tags**, que funcionam como marcadores permanentes apontando para um commit específico.

Neste capítulo aprenderemos como criar e administrar tags.

---

# O que é uma Tag?

Uma **tag** é um marcador que identifica um commit específico.

Diferentemente das branches, as tags normalmente **não continuam evoluindo**.

Elas servem para registrar versões importantes do projeto.

Exemplo:

```text
v1.0.0
v1.1.0
v2.0.0
```

Esses nomes representam versões do software.

---

# Quando utilizar uma Tag?

As tags são normalmente utilizadas para:

- registrar uma versão estável;
- identificar uma entrega ao cliente;
- marcar uma versão utilizada em produção;
- facilitar o retorno a versões anteriores;
- organizar o histórico do projeto.

---

# Tipos de Tags

O Git possui dois tipos principais de tags.

## Lightweight Tag

É uma tag simples.

Ela apenas aponta para um commit.

Não armazena informações adicionais.

---

## Annotated Tag

É a forma mais utilizada.

Além de apontar para o commit, ela registra:

- autor;
- data;
- mensagem;
- identificação da versão.

É recomendada para projetos reais.

---

# Criando uma Tag Anotada

```bash
git tag -a v1.0.0 -m "Primeira versão estável"
```

---

# Entendendo o comando

```bash
git tag -a v1.0.0 -m "Primeira versão estável"
```

---

## git

Sistema de controle de versões.

---

## tag

Manipula as tags do projeto.

---

## -a

Significa:

> **Annotated**

Cria uma tag anotada.

---

## v1.0.0

É o nome da versão.

A letra **v** significa **Version (Versão)**.

---

## -m

Significa:

> **Message**

Permite adicionar uma descrição da versão criada.

---

# Listando as Tags

Para visualizar todas as tags existentes:

```bash
git tag
```

Exemplo:

```text
v1.0.0
v1.1.0
v2.0.0
```

---

# Visualizando informações de uma Tag

Para consultar os detalhes de uma tag:

```bash
git show v1.0.0
```

Exemplo de saída:

```text
tag v1.0.0

Primeira versão estável

commit 3b9b8c...
Author: Laerte Costa
Date: ...
```

Serão exibidas informações da tag e do commit associado.

---

# Criando uma Tag em um Commit Específico

Também é possível marcar um commit antigo.

```bash
git tag -a v0.9.0 <hash_do_commit> -m "Versão Beta"
```

Exemplo:

```bash
git tag -a v0.9.0 a3f81d2 -m "Versão Beta"
```

Assim, a tag será criada apontando para aquele commit específico.

---

# Enviando uma Tag para o GitHub

Depois de criar a tag localmente, envie-a para o servidor.

```bash
git push origin v1.0.0
```

---

# Entendendo o comando

```bash
git push origin v1.0.0
```

## push

Envia a tag para o repositório remoto.

---

## origin

Representa o repositório hospedado no GitHub.

---

## v1.0.0

É a tag que será enviada.

---

# Enviando Todas as Tags

Caso existam várias tags:

```bash
git push origin --tags
```

O Git enviará todas as tags locais que ainda não existem no servidor.

---

# Removendo uma Tag Local

```bash
git tag -d v1.0.0
```

---

# Entendendo o comando

```bash
git tag -d v1.0.0
```

## -d

Significa:

> **Delete**

Remove a tag da máquina local.

---

# Removendo uma Tag Remota

Para excluir a tag do GitHub:

```bash
git push origin --delete v1.0.0
```

A tag será removida apenas do repositório remoto.

---

# Fluxo completo

Na prática, o processo fica assim:

```bash
git tag -a v1.0.0 -m "Primeira versão estável"
git tag
git show v1.0.0
git push origin v1.0.0
```

---

# Versionamento Semântico

Uma convenção muito utilizada é o **Versionamento Semântico (Semantic Versioning)**.

Exemplos:

```text
v1.0.0
```

- Primeiro número → Mudanças grandes (Major)
- Segundo número → Novas funcionalidades (Minor)
- Terceiro número → Correções (Patch)

Exemplo:

```text
v2.4.7
```

Significa:

- Versão principal 2
- Quarta atualização de funcionalidades
- Sétima correção

---

# Integração com o Projeto Linux

As tags são utilizadas em praticamente todos os projetos Open Source.

No **Projeto Linux**, elas serão importantes para identificar versões estáveis de scripts, configurações, laboratórios e automações, permitindo recuperar facilmente qualquer versão anterior do projeto.

---

# Boas práticas

- Utilize sempre tags anotadas (`-a`).
- Nomeie as versões de forma padronizada.
- Utilize o Versionamento Semântico.
- Crie tags apenas para versões importantes.
- Evite remover tags já utilizadas por outros colaboradores.

---

# Resumo

Neste capítulo você aprendeu:

- o que são tags;
- quando utilizá-las;
- como criar tags anotadas;
- como listar e visualizar tags;
- como enviar tags ao GitHub;
- como remover tags;
- como utilizar o Versionamento Semântico.

Agora você consegue identificar versões importantes do seu projeto de forma organizada e profissional.

---

# O que foi realizado na prática

Durante este capítulo foram realizadas as seguintes atividades:

- ✔ Criação de uma tag anotada.
- ✔ Listagem das tags existentes.
- ✔ Consulta das informações de uma tag.
- ✔ Envio de uma tag para o GitHub.
- ✔ Remoção de uma tag local.
- ✔ Remoção de uma tag remota.

---

# Próximo capítulo

## Capítulo 15 – Criando Releases no GitHub

No próximo capítulo você aprenderá como transformar uma **tag** em uma **Release** no GitHub, adicionando título, descrição, notas da versão e disponibilizando uma versão oficial do projeto para download.
