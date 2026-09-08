# Usuários e Grupos

## 04 — useradd, usermod e userdel

## User Management — Gerenciamento de Usuários

Os principais comandos para administrar contas de usuários são:

| Comando | Inglês | Português |
|---|---|---|
| `useradd` | User Add | Adicionar Usuário |
| `usermod` | User Modify | Modificar Usuário |
| `userdel` | User Delete | Excluir Usuário |

---

# 1. useradd — User Add (Adicionar Usuário)

Cria uma nova conta de usuário.

    useradd usuario

Exemplo:

    sudo useradd laerte

O comando cria a conta, mas a configuração do diretório pessoal e outros itens pode depender das opções e da distribuição.

### Criar usuário com Home Directory

`-m` — create home directory (criar diretório pessoal)

    sudo useradd -m laerte

Normalmente será criado:

    /home/laerte

### Definir o Shell

`-s` — shell (shell de login)

    sudo useradd -m -s /bin/bash laerte

### Definir o grupo primário

`-g` — group (grupo primário)

    sudo useradd -m -g usuarios laerte

### Adicionar a grupos suplementares

`-G` — supplementary groups (grupos suplementares)

    sudo useradd -m -G sudo,dev laerte

---

# 2. Definir senha

Depois de criar o usuário:

    sudo passwd laerte

`passwd` — Password (Senha)

O sistema solicitará a nova senha.

---

# 3. usermod — User Modify (Modificar Usuário)

Altera características de uma conta existente.

### Alterar o Shell

    sudo usermod -s /bin/zsh laerte

`-s` — shell (shell de login)

### Alterar o diretório pessoal

`-d` — home directory (diretório pessoal)

    sudo usermod -d /home/novo laerte

Para mover também os arquivos existentes:

`-m` — move home (mover diretório pessoal)

    sudo usermod -d /home/novo -m laerte

---

## Adicionar usuário a um grupo

`-aG` — append + supplementary groups (adicionar aos grupos suplementares)

    sudo usermod -aG sudo laerte

`-a` — append (adicionar)

`-G` — supplementary groups (grupos suplementares)

### ⚠️ Atenção

Não use apenas:

    usermod -G grupo usuario

sem entender o efeito.

Ao definir `-G`, os grupos suplementares atuais podem ser substituídos.

Para **adicionar** um novo grupo mantendo os existentes, use:

    usermod -aG grupo usuario

---

# 4. Alterar o nome do usuário

`-l` — login (nome de login)

    sudo usermod -l novo_nome laerte

Isso altera o nome de login, mas não renomeia automaticamente o diretório pessoal.

---

# 5. userdel — User Delete (Excluir Usuário)

Remove uma conta de usuário.

    sudo userdel laerte

Por padrão, o diretório pessoal pode permanecer no sistema.

### Remover também o Home

`-r` — remove (remover arquivos relacionados)

    sudo userdel -r laerte

Isso remove a conta e o diretório pessoal, incluindo seu conteúdo.

⚠️ Use `-r` com cuidado.

---

# 6. Verificar o usuário

Depois de criar ou modificar uma conta:

    id laerte

Também podemos consultar:

    getent passwd laerte

E verificar os grupos:

    groups laerte

---

# 7. Arquivos importantes

Os comandos de gerenciamento de usuários trabalham com informações armazenadas em arquivos como:

    /etc/passwd
    /etc/shadow
    /etc/group

### `/etc/passwd`

Informações básicas da conta.

### `/etc/shadow`

Informações protegidas relacionadas às senhas.

### `/etc/group`

Informações dos grupos.

---

# 8. Exemplos completos

### Criar usuário

    sudo useradd -m -s /bin/bash laerte

### Definir senha

    sudo passwd laerte

### Adicionar ao grupo

    sudo usermod -aG sudo laerte

### Verificar

    id laerte

### Excluir

    sudo userdel -r laerte

---

# 9. LPIC-1 — O que lembrar

- `useradd` → cria usuários.
- `usermod` → modifica usuários.
- `userdel` → remove usuários.
- `-m` no `useradd` → cria Home Directory.
- `-s` → define o shell.
- `-g` → define o grupo primário.
- `-G` → define grupos suplementares.
- `-aG` → adiciona grupos suplementares sem substituir os atuais.
- `-d` → altera o diretório pessoal.
- `-l` → altera o nome de login.
- `userdel -r` → remove usuário e seu Home Directory.
- `passwd` → define/altera senha.
- `id` → verifica UID, GID e grupos.

### Resumo

    sudo useradd -m usuario

    sudo useradd -m -s /bin/bash usuario

    sudo passwd usuario

    sudo usermod -aG grupo usuario

    sudo usermod -s /bin/bash usuario

    sudo userdel usuario

    sudo userdel -r usuario

> **"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
