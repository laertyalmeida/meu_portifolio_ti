# Usuários e Grupos

## 02 — Grupos e GID

## Group — Grupo

Um **grupo** reúne usuários para facilitar o controle de acesso a arquivos, diretórios e recursos do sistema.

Cada grupo possui:

- **Group Name** — Nome do grupo
- **GID** — Group ID (ID do Grupo)

---

## 1. GID — Group ID

O **GID** é o número que identifica um grupo no Linux.

Exemplo:

    laerte:x:1000:

Nesse exemplo:

    Grupo → laerte
    GID   → 1000

Assim como acontece com usuários e UID, o Linux utiliza o **GID** internamente para identificar grupos.

---

## 2. Arquivo `/etc/group`

As informações dos grupos locais ficam normalmente em:

    /etc/group

Exemplo:

    desenvolvedores:x:1001:laerte,maria,joao

Os campos são separados por `:`.

### Estrutura

    grupo : senha : GID : usuários

Exemplo:

    desenvolvedores : x : 1001 : laerte,maria,joao

Nesse caso:

    Nome do grupo → desenvolvedores
    GID           → 1001
    Membros       → laerte, maria, joao

---

## 3. Grupo primário

**Primary Group — Grupo Primário**

Cada usuário possui um grupo primário.

Exemplo:

    uid=1000(laerte) gid=1000(laerte) groups=1000(laerte),27(sudo)

Nesse caso:

    GID primário → 1000
    Grupo        → laerte

O grupo primário é usado, por exemplo, como grupo padrão na criação de arquivos.

---

## 4. Grupos secundários

**Supplementary Groups — Grupos Suplementares**

Um usuário pode participar de vários grupos além do seu grupo primário.

Exemplo:

    groups=1000(laerte),27(sudo),1001(desenvolvedores)

Nesse caso, `laerte` pertence a:

    laerte
    sudo
    desenvolvedores

Os grupos suplementares permitem conceder acessos adicionais ao usuário.

---

## 5. Ver os grupos de um usuário

`groups` — Groups (Grupos)

    groups

Mostra os grupos do usuário atual.

Para outro usuário:

    groups laerte

---

## 6. Usar `id`

O comando `id` também mostra os grupos:

    id laerte

Exemplo:

    uid=1000(laerte)
    gid=1000(laerte)
    groups=1000(laerte),27(sudo),1001(desenvolvedores)

---

## 7. Criar um grupo

`groupadd` — Group Add (Adicionar Grupo)

    groupadd desenvolvedores

Cria o grupo `desenvolvedores`.

Para definir um GID:

    groupadd -g 1001 desenvolvedores

`-g` — GID (ID do Grupo)

---

## 8. Adicionar usuário a um grupo

`usermod` — User Modify (Modificar Usuário)

    usermod -aG desenvolvedores laerte

Opções:

    -a → append (adicionar)
    -G → supplementary groups (grupos suplementares)

### Atenção

O `-a` é importante quando queremos **adicionar** um grupo sem remover os grupos suplementares existentes.

---

## 9. Consultar um grupo

`getent` — Get Entries (Obter Entradas)

    getent group desenvolvedores

Exemplo:

    desenvolvedores:x:1001:laerte,maria

---

## 10. GID 0

O GID:

    0

é tradicionalmente associado ao grupo:

    root

Não confunda:

    UID 0 → root (usuário)
    GID 0 → root (grupo)

---

## 11. Grupos × Permissões

As permissões tradicionais possuem três categorias:

    User  | Group | Others
    Dono  | Grupo | Outros

Exemplo:

    -rwxr-x---

Nesse caso:

    Dono   → rwx
    Grupo  → r-x
    Outros → ---

O grupo proprietário pode determinar quais usuários terão as permissões do campo **Group**.

---

## 12. LPIC-1 — O que lembrar

- **GID** = Group ID (ID do Grupo).
- `/etc/group` → informações dos grupos.
- `groups` → mostra os grupos de um usuário.
- `id` → mostra UID, GID e grupos.
- `groupadd` → cria grupos.
- `usermod -aG` → adiciona usuário a grupo suplementar.
- Grupo primário → grupo principal do usuário.
- Grupos suplementares → grupos adicionais.
- **GID 0** → grupo `root`.
- `/etc/group` usa campos separados por `:`.
- O grupo participa diretamente do modelo tradicional de permissões `User | Group | Others`.

### Resumo

    groups
    groups usuario

    id usuario

    groupadd desenvolvedores

    usermod -aG desenvolvedores usuario

    getent group desenvolvedores

    UID 0 → root
    GID 0 → root

> **"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
