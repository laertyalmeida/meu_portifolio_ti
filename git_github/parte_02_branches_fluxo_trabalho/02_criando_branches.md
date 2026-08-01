**Tempo estimado:** 20 minutos

**Nível:** Iniciante

---

# Pré-requisitos

Antes de iniciar este capítulo é recomendado compreender o conceito de Branch e o funcionamento do comando `git branch`.

---

# Neste capítulo você aprenderá

* Como criar uma nova Branch.
* A diferença entre `git branch` e `git switch -c`.
* Como verificar se uma Branch foi criada corretamente.
* Como o Git cria uma nova referência para o histórico.

---

# O que significa criar uma Branch?

Criar uma Branch significa criar uma nova linha de desenvolvimento dentro do repositório.

Inicialmente, a nova Branch aponta para o mesmo commit da Branch atual. Somente após novos commits seus históricos começam a ser diferentes.

Exemplo:

```text
main

A ─── B ─── C
```

Após criar uma Branch chamada `login`:

```text
main

A ─── B ─── C
             \
              login
```

Nesse momento, ambas apontam para o mesmo commit.

---

# Glossário

| Termo     | Tradução    | Significado                           |
| --------- | ----------- | ------------------------------------- |
| Create    | Criar       | Gerar uma nova referência             |
| Branch    | Ramificação | Linha independente de desenvolvimento |
| Switch    | Alternar    | Trocar de Branch                      |
| Reference | Referência  | Ponteiro para um commit               |

---

# Comando

Para criar uma nova Branch:

```bash
git branch nome-da-branch
```

---

# Significado do comando

## `git`

Sistema de controle de versão distribuído.

### `branch`

**Tradução:** Ramificação.

Cria uma nova Branch no repositório.

### `nome-da-branch`

Nome escolhido para a nova Branch.

Exemplo:

```bash
git branch login
```

---

# Resultado

O comando normalmente não apresenta nenhuma mensagem.

Para confirmar a criação da Branch, execute:

```bash
git branch
```

Resultado:

```text
* main
  login
```

---

# Explicação da saída

A Branch `login` foi criada com sucesso.

O símbolo `*` indica que você continua trabalhando na Branch `main`.

Criar uma Branch não significa mudar para ela.

---

# Criando e alternando para uma Branch

Na prática, normalmente queremos criar uma Branch e começar a utilizá-la imediatamente.

Para isso utilizamos:

```bash
git switch -c nome-da-branch
```

---

# Significado do comando

## `switch`

**Tradução:** Alternar.

Muda para outra Branch.

### `-c`

**Tradução:** Create (Criar).

Cria a Branch antes de realizar a troca.

### `nome-da-branch`

Nome da nova Branch.

Exemplo:

```bash
git switch -c login
```

---

# Resultado

```text
Switched to a new branch 'login'
```

---

# Explicação da saída

### `Switched`

O Git alterou a Branch atual.

### `to a new branch`

A Branch foi criada durante a execução do comando.

### `'login'`

Nome da nova Branch.

Agora execute:

```bash
git branch
```

Resultado:

```text
main
* login
```

Observe que agora o símbolo `*` aparece na Branch `login`.

---

# Comparação entre os comandos

| Comando              | Cria a Branch | Alterna para ela |
| -------------------- | :-----------: | :--------------: |
| `git branch nome`    |       ✅      |        ❌        |
| `git switch nome`    |       ❌      |        ✅        |
| `git switch -c nome` |       ✅      |        ✅        |

---

# O que aconteceu internamente?

Ao executar:

```bash
git branch login
```

o Git cria uma nova referência apontando para o commit atual.

Quando executamos:

```bash
git switch -c login
```

além de criar essa referência, o Git atualiza o `HEAD`, passando a apontar para a nova Branch.

Representação:

Antes:

```text
        HEAD
         │
         ▼

main

A ─── B ─── C
```

Depois:

```text
        HEAD
         │
         ▼

login

A ─── B ─── C
         │
       main
```

Os próximos commits serão registrados na Branch `login`.

---

# Resumo

Neste capítulo você aprendeu como criar novas Branches utilizando `git branch` e `git switch -c`. Também compreendeu a diferença entre criar uma Branch e criar uma Branch já alternando para ela, além de entender como o Git utiliza referências e o `HEAD` para controlar a linha de desenvolvimento ativa.

---

# Próximo capítulo

## Capítulo 03 — Alternando entre Branches

No próximo capítulo você aprenderá como mudar entre Branches existentes utilizando `git switch`, entenderá como o Git atualiza o `HEAD` e como os arquivos do projeto acompanham essa mudança.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

