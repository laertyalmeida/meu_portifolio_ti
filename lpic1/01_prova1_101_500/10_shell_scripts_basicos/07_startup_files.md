# 10.07 — Startup Files — Arquivos de Inicialização

## O que são?

**Startup Files — Arquivos de inicialização** são arquivos que o **Shell** lê automaticamente ao iniciar uma sessão.

Eles são usados para configurar:

- Variáveis
- PATH
- Aliases
- Funções
- Opções do Shell
- Configurações do usuário

---

## Arquivos principais

| Arquivo | Função |
|---|---|
| `/etc/profile` | Configuração global para shells de login |
| `~/.bash_profile` | Configuração do usuário para Bash de login |
| `~/.bash_login` | Alternativa ao `.bash_profile` |
| `~/.profile` | Alternativa ao `.bash_profile` |
| `~/.bashrc` | Configuração do Bash interativo |

> `~` representa o **Home Directory — Diretório pessoal** do usuário.

---

## Login Shell — Shell de Login

Ao iniciar um **Login Shell — Shell de login**, o Bash procura, nesta ordem:

    ~/.bash_profile
    ~/.bash_login
    ~/.profile

Ele utiliza o **primeiro arquivo existente e legível**.

Exemplo:

    ~/.bash_profile

Pode conter:

    export PATH="$PATH:$HOME/bin"

---

## Interactive Shell — Shell Interativo

Para um Bash interativo que não é de login, normalmente é utilizado:

    ~/.bashrc

Exemplo:

    alias ll='ls -lah'

Depois:

    source ~/.bashrc

O `source` — **carregar/executar no shell atual** — aplica as alterações sem abrir outro shell.

---

## `/etc/profile`

É uma configuração **global** para usuários.

Exemplo:

    /etc/profile

Alterações nesse arquivo podem afetar vários usuários.

---

## `.bash_profile` e `.bashrc`

É comum o `.bash_profile` carregar o `.bashrc`:

    if [ -f ~/.bashrc ]; then
        . ~/.bashrc
    fi

Assim, configurações como aliases e funções do `.bashrc` também ficam disponíveis em uma sessão de login.

---

## Como verificar

Ver o Shell padrão:

    echo $SHELL

Ver arquivos ocultos no Home:

    ls -la ~

Ver o conteúdo:

    cat ~/.bashrc

    cat ~/.bash_profile

---

## Resumo LPIC-1

- `/etc/profile` → configuração global de login.
- `~/.bash_profile` → configuração individual de login.
- `~/.bash_login` → alternativa ao `.bash_profile`.
- `~/.profile` → alternativa ao `.bash_profile`.
- `~/.bashrc` → configuração do Bash interativo.
- `source ~/.bashrc` → recarrega o arquivo no shell atual.
- Arquivos iniciados por `.` são **hidden files — arquivos ocultos**.

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
