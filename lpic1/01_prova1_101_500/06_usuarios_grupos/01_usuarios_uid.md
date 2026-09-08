# Usuários e Grupos

## 01 — Usuários e UID

## User — Usuário

No Linux, cada usuário possui uma **identidade** usada pelo sistema para controlar acesso a arquivos, processos e recursos.

Cada usuário possui:

- **Username** — Nome de usuário
- **UID** — User ID (ID do Usuário)
- **GID** — Group ID (ID do Grupo)
- **Home Directory** — Diretório pessoal
- **Shell** — Interpretador de comandos

---

## 1. UID — User ID

O **UID** é um número que identifica um usuário para o sistema.

Exemplo:

    laerte:x:1000:1000:Laerte:/home/laerte:/bin/bash

Nesse exemplo:

    Usuário → laerte
    UID     → 1000
    GID     → 1000
    Home    → /home/laerte
    Shell   → /bin/bash

O Linux trabalha internamente com o **UID**, não apenas com o nome do usuário.

---

## 2. Ver o usuário atual

`whoami` — Who Am I (Quem Sou Eu)

    whoami

Exemplo:

    laerte

---

## 3. Ver UID e GID

`id` — Identity (Identidade)

    id

Exemplo:

    uid=1000(laerte) gid=1000(laerte) groups=1000(laerte),27(sudo)

Para consultar um usuário específico:

    id laerte

---

## 4. Arquivo `/etc/passwd`

O arquivo:

    /etc/passwd

Armazena informações básicas dos usuários locais.

Exemplo:

    laerte:x:1000:1000:Laerte:/home/laerte:/bin/bash

Os campos são separados por `:`.

### Estrutura

    usuário : senha : UID : GID : descrição : home : shell

Exemplo:

    laerte : x : 1000 : 1000 : Laerte : /home/laerte : /bin/bash

### Importante

O `x` normalmente indica que o **hash da senha** não está armazenado diretamente nesse arquivo.

Em sistemas Linux modernos, as senhas ficam normalmente em:

    /etc/shadow

---

## 5. Usuários do sistema

Além dos usuários comuns, existem **System Users — Usuários do Sistema**.

Eles são usados por serviços e processos.

Exemplos comuns:

    root
    daemon
    www-data
    nobody

Os intervalos de UID podem variar conforme a distribuição e sua configuração.

---

## 6. UID 0

O UID:

    0

pertence ao usuário:

    root

`root` — Superuser (Superusuário)

O `root` possui privilégios administrativos muito elevados no sistema.

---

## 7. Consultar `/etc/passwd`

Podemos usar:

    cat /etc/passwd

Ou pesquisar um usuário:

    grep '^laerte:' /etc/passwd

---

## 8. Comandos importantes

### `whoami`

    whoami

Mostra o usuário atualmente efetivo.

### `id`

    id
    id usuario

Mostra UID, GID e grupos.

### `getent`

`getent` — Get Entries (Obter Entradas)

    getent passwd laerte

Consulta a base de usuários configurada no sistema, que pode incluir fontes locais ou serviços de diretório.

---

## 9. LPIC-1 — O que lembrar

- **UID** = User ID (ID do Usuário).
- Cada usuário possui um UID.
- **UID 0** → `root`.
- `whoami` → mostra o usuário efetivo atual.
- `id` → mostra UID, GID e grupos.
- `/etc/passwd` → informações básicas dos usuários.
- `/etc/shadow` → informações protegidas relacionadas às senhas.
- Os campos de `/etc/passwd` são separados por `:`.
- `getent passwd` → consulta a base de usuários do sistema.

### Resumo

    whoami
    id
    id usuario
    getent passwd usuario

    /etc/passwd
    /etc/shadow

    UID 0 → root

> **"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
