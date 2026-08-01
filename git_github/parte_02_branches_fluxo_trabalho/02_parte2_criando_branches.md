# Capítulo 02 — Criando Branches (Parte 2)

---

# Segundo comando: criar e alternar para uma Branch

No desenvolvimento diário, normalmente queremos criar uma nova Branch e começar a trabalhar nela imediatamente.

Para isso, utilizamos:

```bash
git switch -c nome-da-branch
```

Esse comando realiza duas ações:

1. Cria uma nova Branch.
2. Alterna automaticamente para ela.

---

# Significado do comando

## `git`

**Tradução:** Git.

É o comando principal utilizado para executar funcionalidades do sistema de controle de versão Git.

---

## `switch`

**Tradução:** Alternar ou trocar.

No Git, o subcomando `switch` é utilizado para mudar a Branch atual.

Ele substituiu, em muitos casos, o uso do comando antigo:

```bash
git checkout
```

O objetivo do `switch` é deixar mais claro quando estamos apenas trocando entre Branches.

---

## `-c`

**Tradução:** Create (Criar).

A flag `-c` informa ao Git que uma nova Branch deve ser criada antes da troca.

Sem essa opção, o comando `git switch` apenas tentaria mudar para uma Branch que já existe.

Exemplo:

```bash
git switch desenvolvimento
```

Significa:

"Altere para a Branch chamada desenvolvimento."

Já:

```bash
git switch -c desenvolvimento
```

Significa:

"Crie a Branch desenvolvimento e altere para ela."

---

## `nome-da-branch`

É o nome escolhido para a nova Branch.

Exemplos:

```bash
git switch -c tela_login
```

Cria:

```text
tela_login
```

e muda automaticamente para ela.

# Resultado

O Git apresenta:

```text
Switched to a new branch 'login'
```
---

# Explicação da saída

## `Switched`

Tradução:

> Alterado / Mudado

Indica que o Git realizou uma troca de Branch.

---

## `to a new branch`

Tradução:

> Para uma nova Branch

Informa que a Branch não existia anteriormente e foi criada durante o comando.

---

## `'tela_login'`

Representa o nome da nova Branch criada.

---

# Verificando a Branch atual

```bash
git branch
```

Resultado:

```text
main
* tela_login
```

Explicação:

* `main` continua existindo.
* `tela_login` foi criada.
* O símbolo `*` indica que agora estamos trabalhando nela.

---

# Comparação entre os comandos

| Comando              | Cria Branch | Muda para Branch |
| -------------------- | ----------- | ---------------- |
| `git branch nome`    | ✅ Sim      | ❌ Não           |
| `git switch nome`    | ❌ Não      | ✅ Sim           |
| `git switch -c nome` | ✅ Sim      | ✅ Sim           |

---

# O que aconteceu internamente?

Ao executar:

```bash
git switch -c tela_login
```
o Git realiza algumas etapas:

1. Verifica qual é o commit atual.
2. Cria uma nova referência chamada `tela_login`.
3. Faz essa referência apontar para o commit atual.
4. Atualiza o HEAD.
5. Move o usuário para a nova Branch.

Antes:

```text
HEAD
 |
main

A ─── B ─── C
```

Depois:

```text
        HEAD
         |
       tela_login

A ─── B ─── C
         |
        main
```

Agora os próximos commits serão registrados na Branch `tela_login`.

O desenvolvimento pode continuar sem alterar a Branch principal.

---

# Boas práticas

## Utilize nomes descritivos

Bons exemplos:

```text
feature-login
correcao-pagamento
melhoria-dashboard
documentacao-git
```

Evite:

```text
teste
nova
abc
branch1
```

---

## Utilize padrões de nomenclatura

Em equipes profissionais é comum utilizar prefixos:

```text
feature/
bugfix/
hotfix/
docs/
```

Exemplos:

```text
feature/login
bugfix/erro-calculo
docs/manual-git
```

Isso facilita identificar o objetivo da Branch.

---

# Atenção

Um erro comum é tentar criar uma Branch que já existe.

Exemplo:

```bash
git switch -c feature/login
```

Resultado:

```text
fatal: a branch named 'feature/login' already exists
```

Significado:

O Git informou que essa Branch já foi criada.

Solução:

Visualizar as Branches:

```bash
git branch
```

Depois alternar:

```bash
git switch feature/login
```

---

# Dicas

Antes de criar uma nova Branch, verifique o estado atual do projeto:

```bash
git status
```

e a Branch atual:

```bash
git branch
```

Isso ajuda a evitar criar uma nova linha de desenvolvimento a partir de um local incorreto.

---

# O que foi aprendido

Neste capítulo você aprendeu:

* como criar novas Branches;
* diferença entre `git branch` e `git switch -c`;
* como criar e alternar para uma Branch;
* significado da flag `-c`;
* como o Git cria referências internamente;
* boas práticas de nomenclatura;
* como evitar erros comuns.

---

# Resumo

Neste capítulo você aprendeu como criar novas Branches no Git e compreendeu que existem diferentes formas de realizar essa tarefa.

O comando `git branch nome-da-branch` permite criar uma nova Branch sem alterar a Branch atual.

Já o comando `git switch -c nome-da-branch` cria uma nova Branch e automaticamente muda para ela, sendo uma das formas mais utilizadas atualmente no desenvolvimento profissional.

---

# Próximo capítulo

## Capítulo 03 — Alternando entre Branches

No próximo capítulo você aprenderá como navegar entre diferentes Branches utilizando os comandos do Git.

Será apresentado como:

* mudar de uma Branch para outra;
* entender o funcionamento do HEAD durante a troca;
* retornar para a Branch principal;
* verificar a Branch atual;
* evitar problemas ao alternar entre ambientes de desenvolvimento.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**
