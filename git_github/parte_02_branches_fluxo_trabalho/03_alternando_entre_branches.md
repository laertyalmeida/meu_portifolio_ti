**Tempo estimado:** 20 minutos

**Nível:** Iniciante

---

# Pré-requisitos

Antes de iniciar este capítulo é recomendado compreender como criar Branches e o funcionamento do comando `git switch -c`.

---

# Neste capítulo você aprenderá

* Como alternar entre Branches existentes.
* O comando `git switch`.
* Como verificar a Branch atual.
* O que acontece com os arquivos ao trocar de Branch.
* Como o `HEAD` é atualizado.

---

# O que significa alternar de Branch?

Alternar de Branch significa informar ao Git que você deseja mudar a linha de desenvolvimento atual.

Ao realizar essa troca, o Git passa a considerar outra Branch como ativa, e todos os próximos commits serão registrados nela.

Exemplo:

```text
main

A ─── B ─── C
             \
              D ─── E
                 login
```

Você está trabalhando na Branch `main` e deseja continuar o desenvolvimento da funcionalidade de login. Em vez de criar uma nova Branch, basta alternar para a Branch `login`.

---

# Representação visual

Antes da troca:

```text
        HEAD
         │
         ▼

main

A ─── B ─── C

login

A ─── B ─── C ─── D ─── E
```

Depois da troca:

```text
               HEAD
                │
                ▼

main

A ─── B ─── C

login

A ─── B ─── C ─── D ─── E
```

O histórico não é alterado. Apenas o `HEAD` passa a apontar para outra Branch.

---

# Glossário

| Termo          | Tradução     | Significado                                       |
| -------------- | ------------ | ------------------------------------------------- |
| Switch         | Alternar     | Trocar para outra Branch                          |
| HEAD           | Cabeça       | Ponteiro para a Branch atual                      |
| Current Branch | Branch atual | Branch onde os próximos commits serão registrados |
| Reference      | Referência   | Ponteiro para um commit                           |

---

# Comando

Para alternar entre Branches existentes:

```bash
git switch nome-da-branch
```

---

# Significado do comando

## `git`

Sistema de controle de versão distribuído.

### `switch`

**Tradução:** Alternar.

Troca da Branch atual para outra Branch já existente.

### `nome-da-branch`

Nome da Branch para a qual deseja mudar.

Exemplo:

```bash
git switch login
```

---

# Resultado

Após executar o comando, o Git exibirá uma mensagem semelhante a:

```text
Switched to branch 'login'
```

---

# Explicação da saída

### `Switched`

Indica que o Git realizou a troca de Branch.

### `to branch`

Informa que a alteração ocorreu para uma Branch já existente.

### `'login'`

Nome da Branch que passou a ser a Branch ativa.

Para confirmar a alteração, execute:

```bash
git branch
```

Resultado:

```text
main
* login
```

O símbolo `*` indica a Branch atualmente ativa.

---

# O que aconteceu internamente?

Ao executar:

```bash
git switch login
```

o Git realiza as seguintes operações:

1. Localiza a Branch informada.
2. Atualiza o ponteiro `HEAD`.
3. Atualiza os arquivos do diretório de trabalho para refletirem o último commit dessa Branch.
4. Mantém o histórico do repositório inalterado.

Nenhum commit é criado durante essa operação.

---

# Atenção

Caso a Branch informada não exista, o Git exibirá uma mensagem semelhante a:

```text
fatal: invalid reference: login
```

Isso significa que a Branch não foi encontrada.

Para visualizar as Branches disponíveis, utilize:

```bash
git branch
```

---

# Resumo

Neste capítulo você aprendeu como alternar entre Branches utilizando `git switch`, compreendeu como identificar a Branch ativa, interpretou a saída do comando e entendeu que o Git apenas atualiza o `HEAD` e o diretório de trabalho, sem criar novos commits ou modificar o histórico.

---

# Próximo capítulo

## Capítulo 04 — Trabalhando em Branches

No próximo capítulo você aprenderá como realizar alterações dentro de uma Branch, criar commits independentes e entender como cada Branch mantém seu próprio histórico até o momento da integração com outras Branches.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

