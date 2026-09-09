# 10 — Shell e Scripts Básicos

## 07 — Startup Files

**Startup Files — Arquivos de Inicialização**

São arquivos que o Bash lê automaticamente durante a inicialização de uma sessão.

Eles são usados para configurar:

- variáveis;
- `PATH`;
- aliases;
- funções;
- opções do Shell;
- configurações do ambiente.

---

### 1. Principais Startup Files

| Arquivo | English | Português | Uso |
|---|---|---|---|
| `~/.bash_profile` | Bash Profile | Perfil do Bash | Login Shell |
| `~/.bash_login` | Bash Login | Login do Bash | Alternativa ao `.bash_profile` |
| `~/.profile` | User Profile | Perfil do Usuário | Perfil de login genérico |
| `~/.bashrc` | Bash Run Commands | Configurações do Bash | Shell interativo |
| `/etc/profile` | System Profile | Perfil do Sistema | Configuração global de login |
| `/etc/bash.bashrc` | System Bash RC | Configuração global do Bash | Shell interativo, em sistemas que usam esse arquivo |

---

### 2. Login Shell

**Login Shell — Shell de Login**

É um Bash iniciado como uma sessão de login.

Por exemplo, uma sessão iniciada após autenticação no sistema.

Um Bash de login procura, normalmente, nesta ordem:

    ~/.bash_profile
    ~/.bash_login
    ~/.profile

Ele utiliza o **primeiro arquivo existente e legível** dessa lista.

---

### 3. `.bash_profile`

**`~/.bash_profile` — Bash Profile — Perfil do Bash**

É um arquivo de configuração do usuário para **Login Shells**.

Um uso comum é carregar o `.bashrc`:

    if [ -f ~/.bashrc ]; then
        . ~/.bashrc
    fi

- `-f` — Regular File — Verifica se é um arquivo regular.
- `.` — Source — Carrega e executa o arquivo.

Assim, as configurações interativas do `.bashrc` também ficam disponíveis no login.

---

### 4. `.bash_login`

**`~/.bash_login` — Bash Login — Login do Bash**

É uma alternativa ao `.bash_profile`.

Se `~/.bash_profile` não existir, o Bash procura:

    ~/.bash_login

Se também não existir, procura:

    ~/.profile

---

### 5. `.profile`

**`~/.profile` — User Profile — Perfil do Usuário**

É um arquivo de configuração de login mais genérico.

Pode ser utilizado quando não existe:

    ~/.bash_profile

nem:

    ~/.bash_login

Não é exclusivo do Bash.

---

### 6. `.bashrc`

**`~/.bashrc` — Bash Run Commands — Configurações do Bash**

É normalmente utilizado para **Shells interativos que não são de login**.

É comum colocar nele:

    alias ll='ls -la'

    export PATH="$PATH:$HOME/bin"

    export EDITOR=vim

Para aplicar alterações sem abrir outro Shell:

    source ~/.bashrc

Ou:

    . ~/.bashrc

---

### 7. Arquivos globais

Os arquivos abaixo ficam disponíveis para configurações do sistema:

    /etc/profile
    /etc/bash.bashrc

`/etc/bash.bashrc` é comum em algumas distribuições, mas o nome/localização dos arquivos globais pode variar entre distribuições.

---

### 8. Startup Files × tipo de Shell

| Shell | Arquivos principais |
|---|---|
| Login Bash | `/etc/profile` → `~/.bash_profile` ou `~/.bash_login` ou `~/.profile` |
| Interativo não-login | `~/.bashrc` |
| Não interativo | normalmente não lê `.bashrc` automaticamente |

Para um script Bash:

    #!/bin/bash

    echo "Executando script"

Não devemos assumir que `~/.bashrc` será carregado automaticamente.

---

### 9. Verificar se o arquivo existe

    ls -la ~/.bashrc
    ls -la ~/.bash_profile
    ls -la ~/.bash_login
    ls -la ~/.profile

- `-a` — All — Incluir arquivos ocultos.
- `-l` — Long — Formato detalhado.

Os arquivos começam com `.` e, por isso, são **arquivos ocultos**.

---

### 10. `source`

**source — Read and Execute — Ler e Executar**

Carrega um arquivo no **Shell atual**.

Exemplo:

    source ~/.bashrc

Ou:

    . ~/.bashrc

Isso é diferente de:

    bash ~/.bashrc

Com `source`, as variáveis, aliases e funções definidas permanecem no Shell atual.

---

## Resumo LPIC-1

- **Startup Files** configuram o Bash durante sua inicialização.
- `~/.bash_profile` é usado principalmente para **Login Shell**.
- `~/.bash_login` é uma alternativa ao `.bash_profile`.
- `~/.profile` é um perfil de login mais genérico.
- `~/.bashrc` é usado normalmente por **Shells interativos não-login**.
- `/etc/profile` fornece configuração global para login.
- `/etc/bash.bashrc` fornece configuração global do Bash em sistemas que utilizam esse arquivo.
- O Bash procura `.bash_profile`, depois `.bash_login`, depois `.profile`.
- `source ~/.bashrc` recarrega o arquivo no Shell atual.
- `.bashrc` é muito usado para aliases, variáveis e `PATH`.
- Scripts não devem depender automaticamente do `.bashrc`.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
