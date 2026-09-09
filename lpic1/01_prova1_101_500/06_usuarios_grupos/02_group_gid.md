# Usuários e Grupos

## 02 — Group e GID

### Group — Grupo

Um **Group (Grupo)** reúne usuários que podem compartilhar permissões de acesso a arquivos e diretórios.

Cada grupo possui um número de identificação chamado **GID**.

### GID — Group ID — ID do Grupo

O **GID** é o número usado pelo Linux para identificar um grupo.

Exemplo:

    developers:x:1001:laerte,joao

| Campo | Significado |
|---|---|
| `developers` | Nome do grupo |
| `x` | Senha do grupo armazenada separadamente |
| `1001` | GID — ID do grupo |
| `laerte,joao` | Usuários membros |

O arquivo que armazena os grupos é:

    /etc/group

---

## Grupo primário e grupos secundários

Um usuário pode pertencer a vários grupos.

### Primary Group — Grupo Primário

É o grupo principal associado ao usuário.

Pode ser consultado com:

    id usuario

Exemplo:

    uid=1000(laerte) gid=1000(laerte) groups=1000(laerte),27(sudo),1001(developers)

Neste exemplo:

- `gid=1000(laerte)` → grupo primário.
- `groups=...` → grupos aos quais o usuário pertence.

### Supplementary Groups — Grupos Secundários

São os grupos adicionais do usuário.

No exemplo:

    groups=1000(laerte),27(sudo),1001(developers)

Além do grupo primário, o usuário pertence a:

- `sudo`
- `developers`

---

## Comandos importantes

### id — Identity — Identidade

Mostra UID, GID e grupos do usuário.

    id
    id laerte

### groups — Groups — Grupos

Mostra os grupos de um usuário.

    groups
    groups laerte

### getent — Get Entries — Obter Entradas

Consulta informações das bases configuradas pelo sistema.

    getent group
    getent group developers

É útil porque pode consultar grupos locais e também outras fontes configuradas no sistema.

---

## /etc/group

Estrutura:

    grupo:x:GID:membros

Exemplo:

    developers:x:1001:laerte,joao

O arquivo pode ser consultado com:

    cat /etc/group

Ou:

    getent group

---

## GID e permissões

Arquivos e diretórios possuem:

- **UID** → dono.
- **GID** → grupo associado.

Exemplo:

    -rw-r----- 1 laerte developers 1200 arquivo.txt

Aqui:

- `laerte` → Owner — Dono.
- `developers` → Group — Grupo.
- `rw-` → permissões do dono.
- `r--` → permissões do grupo.
- `---` → permissões dos outros.

Assim, o grupo pode controlar o acesso compartilhado ao arquivo.

---

## Resumo LPIC-1

| Conceito | Significado |
|---|---|
| Group | Grupo |
| GID | Group ID — ID do Grupo |
| Primary Group | Grupo Primário |
| Supplementary Groups | Grupos Secundários |
| `/etc/group` | Arquivo de grupos |
| `id` | Mostra UID, GID e grupos |
| `groups` | Mostra grupos do usuário |
| `getent group` | Consulta grupos |

**Conhecimento só tem valor quando é compartilhado** - Laerte Costa
