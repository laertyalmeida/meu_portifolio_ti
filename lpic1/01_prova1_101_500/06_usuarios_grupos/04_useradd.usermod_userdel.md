# Usuários e Grupos

## 04 — useradd, usermod e userdel

### useradd — User Add — Adicionar Usuário

Cria uma nova conta de usuário.

    sudo useradd laerte

Criar usuário com diretório pessoal e shell:

    sudo useradd -m -s /bin/bash laerte

| Opção | English | Português |
|---|---|---|
| `-m` | Create Home | Criar diretório pessoal |
| `-d` | Home Directory | Definir diretório pessoal |
| `-s` | Shell | Definir shell de login |
| `-u` | User ID | Definir UID |
| `-g` | Group | Definir grupo primário |
| `-G` | Supplementary Groups | Definir grupos secundários |
| `-c` | Comment | Definir comentário |
| `-r` | System Account | Criar conta do sistema |

Exemplo:

    sudo useradd -m -s /bin/bash -G sudo laerte

---

### passwd — Password — Senha

`useradd` cria a conta, mas o usuário pode precisar de uma senha.

    sudo passwd laerte

---

## usermod — User Modify — Modificar Usuário

Altera as características de uma conta existente.

### Alterar shell

    sudo usermod -s /bin/zsh laerte

### Alterar diretório pessoal

    sudo usermod -d /home/novo_laerte laerte

Para mover também os arquivos existentes:

    sudo usermod -d /home/novo_laerte -m laerte

### Alterar grupo primário

    sudo usermod -g developers laerte

### Adicionar grupos secundários

    sudo usermod -aG docker laerte

| Opção | English | Português |
|---|---|---|
| `-a` | Append | Adicionar sem remover os grupos atuais |
| `-G` | Supplementary Groups | Definir grupos secundários |
| `-g` | Primary Group | Definir grupo primário |
| `-d` | Home Directory | Alterar diretório pessoal |
| `-m` | Move Home | Mover o conteúdo para o novo diretório |
| `-s` | Shell | Alterar shell |
| `-u` | User ID | Alterar UID |
| `-l` | Login | Alterar nome de login |
| `-L` | Lock | Bloquear conta |
| `-U` | Unlock | Desbloquear conta |

### Atenção ao `-aG`

Use:

    sudo usermod -aG docker laerte

O `-a` significa **Append — Adicionar**.

Sem `-a`:

    sudo usermod -G docker laerte

os grupos secundários anteriores podem ser substituídos pelo novo conjunto informado.

---

## userdel — User Delete — Excluir Usuário

Remove uma conta de usuário.

    sudo userdel laerte

### Remover também o diretório pessoal

    sudo userdel -r laerte

| Opção | English | Português |
|---|---|---|
| `-r` | Remove Home | Remover diretório pessoal e arquivos associados |

> **Cuidado:** `userdel -r` pode remover permanentemente os arquivos do diretório pessoal.

---

## Verificando as alterações

Consultar a conta:

    id laerte

Consultar grupos:

    groups laerte

Consultar a entrada no `/etc/passwd`:

    getent passwd laerte

Consultar o grupo:

    getent group developers

---

## Fluxo básico

Criar:

    sudo useradd -m -s /bin/bash laerte

Definir senha:

    sudo passwd laerte

Adicionar grupo:

    sudo usermod -aG developers laerte

Verificar:

    id laerte

Excluir:

    sudo userdel -r laerte

---

## Resumo LPIC-1

| Comando | Função |
|---|---|
| `useradd` | Criar usuário |
| `usermod` | Modificar usuário |
| `userdel` | Excluir usuário |
| `passwd` | Definir/alterar senha |
| `-m` | Criar/mover Home |
| `-s` | Definir shell |
| `-g` | Grupo primário |
| `-G` | Grupos secundários |
| `-aG` | Adicionar aos grupos sem remover os atuais |
| `-r` | Remover Home ao excluir |

**Conhecimento só tem valor quando é compartilhado** - Laerte Costa
