# Usuários e Grupos

## 05 — groupadd, groupmod e groupdel

### groupadd — Group Add — Adicionar Grupo

Cria um novo grupo no sistema.

    sudo groupadd developers

O grupo recebe um **GID — Group ID — ID do Grupo** automaticamente.

Definir um GID específico:

    sudo groupadd -g 1500 developers

| Opção | English | Português |
|---|---|---|
| `-g` | GID | Definir o ID do grupo |
| `-r` | System Group | Criar grupo do sistema |
| `-f` | Force | Não apresentar erro se o grupo já existir |

Verificar:

    getent group developers

---

### groupmod — Group Modify — Modificar Grupo

Altera as informações de um grupo existente.

### Alterar o nome

    sudo groupmod -n dev developers

Aqui:

    developers → dev

### Alterar o GID

    sudo groupmod -g 1600 dev

| Opção | English | Português |
|---|---|---|
| `-n` | New Name | Novo nome |
| `-g` | GID | Novo ID do grupo |
| `-o` | Non-Unique | Permitir GID não exclusivo |

> Alterar o GID não significa automaticamente alterar o GID armazenado nos arquivos que pertenciam ao grupo antigo.

---

### groupdel — Group Delete — Excluir Grupo

Remove um grupo do sistema.

    sudo groupdel developers

Verificar:

    getent group developers

Se o grupo não existir, o comando apresentará um erro.

> **Importante:** o `groupdel` remove o grupo, mas não remove os arquivos pertencentes a esse grupo.

---

## /etc/group

Os grupos locais são registrados em:

    /etc/group

Exemplo:

    developers:x:1500:laerte,joao

| Campo | Significado |
|---|---|
| `developers` | Group Name — Nome do grupo |
| `x` | Senha do grupo |
| `1500` | GID — ID do grupo |
| `laerte,joao` | Membros do grupo |

Consultar:

    cat /etc/group

Ou:

    getent group

---

## Verificando grupos e usuários

Ver grupos de um usuário:

    groups laerte

Ver UID, GID e grupos:

    id laerte

Ver informações do grupo:

    getent group developers

---

## Relação com usuários

Criar grupo:

    sudo groupadd developers

Adicionar usuário ao grupo:

    sudo usermod -aG developers laerte

Verificar:

    id laerte

Excluir grupo:

    sudo groupdel developers

---

## Resumo LPIC-1

| Comando | Função |
|---|---|
| `groupadd` | Criar grupo |
| `groupmod` | Modificar grupo |
| `groupdel` | Excluir grupo |
| `-g` | Definir/alterar GID |
| `-n` | Alterar nome do grupo |
| `-r` | Criar grupo do sistema |
| `/etc/group` | Arquivo de grupos |
| `getent group` | Consultar grupos |
| `id` | Consultar GID e grupos do usuário |
| `groups` | Mostrar grupos do usuário |

**Conhecimento só tem valor quando é compartilhado** - Laerte Costa
