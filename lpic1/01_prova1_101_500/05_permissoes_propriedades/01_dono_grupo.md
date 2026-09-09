# Permissões e Propriedade

## 01 — Dono e Grupo

### 1. Dono — Owner

**Owner** — **Dono/Proprietário**

Todo arquivo ou diretório no Linux possui um usuário como proprietário.

Para visualizar:

    ls -l

Exemplo:

    -rw-r--r-- 1 laerte alunos 1200 arquivo.txt

Nesse exemplo:

    laerte → Owner — Dono
    alunos → Group — Grupo

---

### 2. Grupo — Group

**Group** — **Grupo**

Além do dono, cada arquivo possui um grupo associado.

O grupo permite que vários usuários compartilhem permissões sobre o mesmo arquivo ou diretório.

Exemplo:

    -rw-r--r-- 1 laerte alunos 1200 arquivo.txt

    Dono  → laerte
    Grupo → alunos

---

### 3. Visualizar dono e grupo

Use:

    ls -l arquivo.txt

Exemplo:

    -rw-r--r-- 1 laerte alunos 1200 arquivo.txt

Podemos interpretar:

| Parte | Significado |
|---|---|
| `-` | tipo: arquivo regular |
| `rw-r--r--` | permissões |
| `1` | número de hard links |
| `laerte` | dono |
| `alunos` | grupo |
| `1200` | tamanho |
| `arquivo.txt` | nome |

---

### 4. `whoami`

**whoami** — **Quem sou eu**

Mostra o usuário atualmente utilizado:

    whoami

Exemplo:

    laerte

---

### 5. `id`

**id** — **Identificação do usuário**

Mostra informações do usuário, incluindo:

- UID
- GID
- Grupos

Exemplo:

    id

Saída:

    uid=1000(laerte) gid=1000(laerte) groups=1000(laerte),100(users)

**UID** — *User ID* — **ID do Usuário**

**GID** — *Group ID* — **ID do Grupo**

---

### 6. Alterar o dono

**chown** — *Change Owner* — **Alterar Dono**

Sintaxe:

    sudo chown usuário arquivo

Exemplo:

    sudo chown joao arquivo.txt

Alterar dono e grupo:

    sudo chown joao:alunos arquivo.txt

---

### 7. Alterar somente o grupo

**chgrp** — *Change Group* — **Alterar Grupo**

Exemplo:

    sudo chgrp alunos arquivo.txt

---

### 8. Diretórios

O dono e o grupo também pertencem aos diretórios.

Exemplo:

    drwxr-xr-x 2 laerte alunos 4096 projetos

    laerte  → dono
    alunos  → grupo
    projetos → diretório

---

### 9. Dono × Grupo × Outros

As permissões do Linux são organizadas em três classes:

| Classe | English | Português |
|---|---|---|
| `u` | user/owner | usuário/dono |
| `g` | group | grupo |
| `o` | others | outros usuários |
| `a` | all | todos |

Exemplo:

    -rwxr-x---

    u → rwx
    g → r-x
    o → ---

Isso significa:

    Dono   → leitura, escrita e execução
    Grupo  → leitura e execução
    Outros → nenhuma permissão

---

## Resumo LPIC-1

- Todo arquivo possui **dono** e **grupo**.
- `ls -l` → mostra dono, grupo e permissões.
- `whoami` → mostra o usuário atual.
- `id` → mostra UID, GID e grupos.
- `chown` → altera o dono.
- `chgrp` → altera o grupo.
- `u` → usuário/dono.
- `g` → grupo.
- `o` → outros.
- `a` → todos.
- **Owner** → dono do arquivo.
- **Group** → grupo associado ao arquivo.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
