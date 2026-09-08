# Usuários e Grupos

## 08 — /etc/skel e Home

## `/etc/skel` — Skeleton Directory (Diretório Modelo)

O `/etc/skel` contém arquivos e diretórios **modelo** usados na criação de novos usuários.

Quando um usuário é criado com um **Home Directory**, o conteúdo de `/etc/skel` pode ser copiado para o novo diretório pessoal.

Exemplo:

    /etc/skel
    ├── .bash_logout
    ├── .bashrc
    └── .profile

Ao criar:

    sudo useradd -m laerte

Pode resultar em:

    /home/laerte/
    ├── .bash_logout
    ├── .bashrc
    └── .profile

O conteúdo exato depende da distribuição e da configuração do sistema.

---

# 1. Ver o conteúdo do `/etc/skel`

    ls -la /etc/skel

`-l` — long (listagem detalhada)

`-a` — all (mostrar arquivos ocultos)

---

# 2. Personalizar o `/etc/skel`

Um administrador pode colocar arquivos no `/etc/skel` para que novos usuários recebam uma configuração inicial.

Exemplo:

    sudo cp arquivo.txt /etc/skel/

Depois, novos usuários criados com Home poderão receber esse arquivo.

⚠️ Alterar `/etc/skel` normalmente afeta **novos usuários**. Isso não atualiza automaticamente os Homes dos usuários existentes.

---

# Home Directory — Diretório Pessoal

O **Home Directory** é o diretório pessoal de cada usuário.

Normalmente fica em:

    /home/usuario

Exemplo:

    /home/laerte

É onde ficam arquivos pessoais e configurações do usuário.

---

# 3. Variável `$HOME`

A variável:

    $HOME

indica o diretório pessoal do usuário atual.

Ver:

    echo $HOME

Exemplo:

    /home/laerte

---

# 4. Atalho `~`

O caractere:

    ~

representa o **Home Directory** do usuário atual.

Exemplo:

    cd ~

É equivalente a:

    cd "$HOME"

Para listar:

    ls -la ~

---

# 5. Home do usuário root

O usuário `root` normalmente possui um Home diferente:

    /root

Enquanto usuários comuns normalmente utilizam:

    /home/usuario

Exemplo:

    root    → /root
    laerte  → /home/laerte

---

# 6. Definir o Home ao criar usuário

`-d` — home directory (diretório pessoal)

    sudo useradd -d /home/laerte -m laerte

`-m` — create home directory (criar diretório pessoal)

O `-d` define o caminho e o `-m` solicita a criação do diretório.

---

# 7. Alterar o Home de um usuário

Use:

    sudo usermod -d /home/novo -m laerte

`-d` — home directory (diretório pessoal)

`-m` — move home (mover diretório pessoal)

O `-m` move o conteúdo existente para o novo diretório.

---

# 8. Ver o Home configurado

Podemos consultar:

    getent passwd laerte

Exemplo:

    laerte:x:1000:1000:Laerte:/home/laerte:/bin/bash

O campo:

    /home/laerte

é o Home Directory.

Também podemos usar:

    echo $HOME

quando estamos na sessão do próprio usuário.

---

# 9. `/etc/skel` × `/home`

| Local | Função |
|---|---|
| `/etc/skel` | Modelo para novos usuários |
| `/home/usuario` | Diretório pessoal do usuário |
| `/root` | Diretório pessoal do root |
| `$HOME` | Variável que aponta para o Home |
| `~` | Atalho para o Home |

### Fluxo simplificado

    /etc/skel
         │
         │ criação do usuário
         ▼
    /home/usuario
         │
         ├── arquivos pessoais
         ├── configurações
         └── arquivos ocultos

---

# 10. Arquivos ocultos

Arquivos que começam com `.` são normalmente considerados **hidden files — arquivos ocultos**.

Exemplos:

    .bashrc
    .profile
    .bash_logout

Para visualizá-los:

    ls -la

`-a` — all (todos)

---

# 11. LPIC-1 — O que lembrar

- `/etc/skel` = Skeleton Directory (Diretório Modelo).
- Serve como modelo para novos usuários.
- `useradd -m` cria o Home Directory quando solicitado.
- Home de usuários comuns normalmente fica em `/home/usuario`.
- Home do `root` normalmente é `/root`.
- `$HOME` aponta para o Home do usuário atual.
- `~` representa o Home do usuário.
- `usermod -d` altera o caminho do Home.
- `usermod -d ... -m` altera e move o Home.
- Arquivos como `.bashrc` são arquivos ocultos.
- Alterações em `/etc/skel` normalmente afetam novos usuários, não os já existentes.

### Resumo

    ls -la /etc/skel

    sudo useradd -m usuario

    echo $HOME

    cd ~

    sudo usermod -d /home/novo -m usuario

    getent passwd usuario

> **"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
