# 01 — Dono e Grupo

## Ownership — Propriedade

No Linux, todo arquivo e diretório possui um **Owner (Dono)** e um **Group (Grupo)**.

    arquivo
       │
       ├── Owner → dono
       └── Group → grupo

Essas informações ajudam o Linux a decidir **quem pode acessar ou modificar** o arquivo.

---

## Owner — Dono

O **Owner (Dono)** é o usuário proprietário do arquivo ou diretório.

Exemplo:

    -rw-r--r-- 1 laerte usuarios arquivo.txt

    laerte → Owner (Dono)

---

## Group — Grupo

O **Group (Grupo)** é o grupo proprietário do arquivo ou diretório.

No exemplo:

    -rw-r--r-- 1 laerte usuarios arquivo.txt

    usuarios → Group (Grupo)

Um usuário pode pertencer a um ou vários grupos.

---

## Como visualizar dono e grupo

### ls -l — Long Listing (Listagem Longa)

    ls -l

Exemplo:

    -rw-r--r-- 1 laerte usuarios 1200 arquivo.txt

Os campos importantes são:

    laerte
       ↓
    Owner — Dono

    usuarios
       ↓
    Group — Grupo

---

## Alterar o dono

### chown — Change Owner (Alterar Dono)

    chown maria arquivo.txt

Altera o dono de `arquivo.txt` para `maria`.

### Alterar dono e grupo

    chown maria:usuarios arquivo.txt

    maria    → novo dono
    usuarios → novo grupo

---

## Alterar o grupo

### chgrp — Change Group (Alterar Grupo)

    chgrp desenvolvedores arquivo.txt

Altera o grupo proprietário para `desenvolvedores`.

Também podemos usar:

    chown :desenvolvedores arquivo.txt

---

## Diretórios

A propriedade também existe para diretórios.

    drwxr-xr-x 2 laerte usuarios documentos

    laerte   → dono
    usuarios → grupo

O dono e o grupo influenciam as permissões de acesso ao diretório.

---

## Dono × Grupo

| Termo | Inglês | Português |
|---|---|---|
| Owner | Owner | Dono |
| Group | Group | Grupo |
| Change Owner | Change Owner | Alterar dono |
| Change Group | Change Group | Alterar grupo |

### Comandos

| Comando | Tradução | Função |
|---|---|---|
| `ls -l` | Long Listing — Listagem Longa | Mostra dono e grupo |
| `chown` | Change Owner — Alterar Dono | Altera o proprietário |
| `chgrp` | Change Group — Alterar Grupo | Altera o grupo |

---

## LPIC-1 — O que saber

- Todo arquivo possui **Owner (Dono)** e **Group (Grupo)**.
- `ls -l` mostra o dono e o grupo.
- `chown` altera o dono.
- `chgrp` altera o grupo.
- `chown usuario:grupo arquivo` altera dono e grupo.
- As permissões são analisadas separadamente para:
  - **User/Owner** — usuário/dono
  - **Group** — grupo
  - **Others** — outros usuários.

---

## Resumo

    Arquivo
       │
       ├── Owner  → quem é o dono
       │
       └── Group  → grupo proprietário
       
    ls -l
       ↓
    visualizar

    chown
       ↓
    alterar dono

    chgrp
       ↓
    alterar grupo

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
