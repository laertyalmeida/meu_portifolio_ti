# Usuários e Grupos

## 01 — Usuário e UID

### 1. Usuário — User

**User** — **Usuário**

No Linux, um usuário é uma identidade utilizada para acessar o sistema e executar processos.

Cada usuário possui uma identificação numérica chamada **UID**.

---

### 2. UID

**UID** — *User ID* — **ID do Usuário**

É o número que identifica um usuário no sistema.

Exemplo:

    id laerte

Saída:

    uid=1000(laerte) gid=1000(laerte) groups=1000(laerte)

Neste exemplo:

    UID → 1000
    Usuário → laerte

O Linux utiliza principalmente o UID para identificar o usuário internamente.

---

### 3. Usuário comum × root

O usuário administrador é:

    root

O `root` normalmente possui:

    UID = 0

Usuários comuns geralmente recebem UIDs a partir de uma faixa definida pela distribuição.

Exemplo:

    laerte → UID 1000
    joao   → UID 1001
    maria  → UID 1002

A faixa exata pode variar conforme a distribuição e sua configuração.

---

### 4. Consultar informações do usuário

**`id`** — **Identificação**

    id

Mostra informações do usuário atual.

Para um usuário específico:

    id joao

Exemplo:

    uid=1001(joao) gid=1001(joao) groups=1001(joao),100(users)

---

### 5. `whoami`

**whoami** — **Quem sou eu**

Mostra o nome do usuário atualmente efetivo:

    whoami

Exemplo:

    laerte

Diferença:

    whoami → mostra o nome do usuário
    id      → mostra UID, GID e grupos

---

### 6. `/etc/passwd`

**`/etc/passwd`** — **Arquivo de informações dos usuários**

Contém informações básicas das contas locais.

Exemplo de entrada:

    laerte:x:1000:1000:Laerte Costa:/home/laerte:/bin/bash

Os campos são separados por `:`.

Estrutura:

    usuário:senha:GID:UID:descrição:home:shell

Na prática, o campo da senha normalmente contém `x`, indicando que o hash da senha está armazenado em `/etc/shadow`.

---

### 7. Informações importantes do `/etc/passwd`

Exemplo:

    laerte:x:1000:1000:Laerte Costa:/home/laerte:/bin/bash

| Campo | Conteúdo | Significado |
|---|---|---|
| 1 | `laerte` | nome do usuário |
| 2 | `x` | senha armazenada em `/etc/shadow` |
| 3 | `1000` | UID |
| 4 | `1000` | GID principal |
| 5 | `Laerte Costa` | descrição/comentário |
| 6 | `/home/laerte` | diretório pessoal |
| 7 | `/bin/bash` | shell padrão |

---

### 8. Usuário e arquivos

O Linux associa arquivos a um UID e a um GID.

Exemplo:

    ls -l arquivo.txt

Saída:

    -rw-r--r-- 1 laerte desenvolvimento 1200 arquivo.txt

Aqui:

    laerte          → dono
    desenvolvimento → grupo

Internamente, o sistema utiliza os identificadores numéricos correspondentes.

---

### 9. Diretório pessoal

**Home Directory** — **Diretório Pessoal**

Normalmente fica em:

    /home/usuário

Exemplo:

    /home/laerte

A variável:

    $HOME

indica o diretório pessoal do usuário atual.

---

## Resumo LPIC-1

- **User** → usuário.
- **UID** — *User ID* → ID numérico do usuário.
- `root` → usuário administrativo, normalmente UID `0`.
- `id` → mostra UID, GID e grupos.
- `whoami` → mostra o usuário efetivo atual.
- `/etc/passwd` → contém informações básicas das contas.
- `/etc/shadow` → armazena informações protegidas relacionadas às senhas.
- `/home/usuário` → diretório pessoal de usuários comuns.
- `$HOME` → caminho do diretório pessoal atual.
- Arquivos possuem um **dono (UID)** e um **grupo (GID)**.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
