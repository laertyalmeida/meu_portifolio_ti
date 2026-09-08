# Usuários e Grupos

## 03 — /etc/passwd e /etc/shadow

## `/etc/passwd` — Password File (Arquivo de Senhas)

O `/etc/passwd` armazena informações básicas sobre as contas de usuários.

    cat /etc/passwd

Exemplo:

    laerte:x:1000:1000:Laerte:/home/laerte:/bin/bash

Os campos são separados por `:`.

### Estrutura

    usuário : senha : UID : GID : GECOS : home : shell

| Campo | Inglês | Português |
|---|---|---|
| 1 | Username | Nome do usuário |
| 2 | Password | Senha |
| 3 | UID | ID do Usuário |
| 4 | GID | ID do Grupo |
| 5 | GECOS | Informações do usuário |
| 6 | Home Directory | Diretório pessoal |
| 7 | Login Shell | Shell de login |

### Exemplo interpretado

    laerte:x:1000:1000:Laerte:/home/laerte:/bin/bash

    Usuário → laerte
    Senha   → x
    UID     → 1000
    GID     → 1000
    GECOS   → Laerte
    Home    → /home/laerte
    Shell   → /bin/bash

---

# `/etc/shadow` — Shadow Password File (Arquivo de Senhas Sombreadas)

O `/etc/shadow` armazena informações protegidas relacionadas às senhas das contas.

    sudo cat /etc/shadow

Exemplo simplificado:

    laerte:$y$...:20400:0:99999:7:::

O arquivo normalmente possui permissões muito mais restritas que `/etc/passwd`.

---

## 1. Estrutura do `/etc/shadow`

Os campos são separados por `:`.

    usuário : senha : último_mudança : mínimo : máximo : aviso : inatividade : expiração : reservado

| Campo | Significado |
|---|---|
| 1 | Nome do usuário |
| 2 | Hash da senha |
| 3 | Data da última alteração |
| 4 | Dias mínimos para trocar a senha |
| 5 | Dias máximos para trocar a senha |
| 6 | Dias de aviso antes da expiração |
| 7 | Dias de inatividade após expiração |
| 8 | Data de expiração da conta |
| 9 | Campo reservado |

---

## 2. Hash da senha

O segundo campo contém o **password hash — hash da senha**.

Exemplo:

    $y$...

Não é a senha em texto puro.

O prefixo do hash pode indicar o algoritmo utilizado.

Exemplos encontrados em sistemas Linux:

    $1$  → MD5
    $5$  → SHA-256
    $6$  → SHA-512
    $y$  → yescrypt

O algoritmo disponível depende da configuração e da distribuição Linux.

---

## 3. Senha bloqueada

Um prefixo especial no campo da senha pode indicar que a autenticação por senha está bloqueada.

Exemplo:

    !

ou:

    *

Isso não significa necessariamente que a conta inteira esteja bloqueada; significa que aquele valor não funciona como uma senha válida para autenticação.

---

## 4. Por que existem dois arquivos?

Historicamente, colocar o hash da senha em `/etc/passwd` permitiria que qualquer usuário com acesso de leitura ao arquivo obtivesse o hash.

Por isso, sistemas modernos normalmente mantêm:

    /etc/passwd
        ↓
    informações públicas da conta

    /etc/shadow
        ↓
    informações protegidas da autenticação

O `/etc/passwd` normalmente pode ser lido por usuários comuns, enquanto o `/etc/shadow` possui acesso restrito.

---

## 5. Comandos importantes

### Consultar usuário

    getent passwd laerte

### Consultar grupo

    getent group laerte

### Consultar informações de senha

    sudo getent shadow laerte

### Alterar senha

`passwd` — Password (Senha)

    passwd

Para outro usuário, normalmente com privilégios administrativos:

    sudo passwd laerte

---

## 6. `passwd` × `/etc/shadow`

Não edite `/etc/shadow` manualmente para alterar senhas.

Use:

    passwd

O comando atualiza as informações necessárias de forma apropriada.

---

## 7. LPIC-1 — O que lembrar

### `/etc/passwd`

    usuário:x:UID:GID:GECOS:home:shell

- Informações básicas das contas.
- `UID` → ID do usuário.
- `GID` → grupo primário.
- `/home/usuario` → diretório pessoal.
- `/bin/bash` → shell de login.
- `x` no campo da senha normalmente indica que o hash está no `/etc/shadow`.

### `/etc/shadow`

- Armazena informações protegidas de autenticação.
- Contém o **hash da senha**.
- Também contém informações de validade e expiração da senha.
- Possui permissões de acesso restritas.
- Campos separados por `:`.

### Resumo

    /etc/passwd → informações da conta

    /etc/shadow → informações protegidas da senha

    cat /etc/passwd
    getent passwd usuario

    sudo cat /etc/shadow
    sudo getent shadow usuario

    passwd
    sudo passwd usuario

> **"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
