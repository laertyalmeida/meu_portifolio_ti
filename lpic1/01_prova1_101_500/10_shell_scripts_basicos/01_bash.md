# 10 — Shell e Scripts Básicos

## 01 — Bash

**Bash — Bourne Again Shell — Shell Bourne Novamente**

O **Bash** é um dos principais Shells usados no Linux.

Ele interpreta comandos digitados pelo usuário e também pode executar **scripts**.

### 1. O que é Shell?

**Shell — Interpretador de Comandos**

É o programa que recebe comandos e solicita sua execução ao sistema.

Fluxo simplificado:

    Usuário → Bash → Kernel → Hardware

Exemplo:

    $ ls

O Bash interpreta `ls` e executa o programa.

---

### 2. Verificar o Shell

    echo $SHELL

Exemplo:

    /bin/bash

Também é possível verificar o processo atual:

    echo $$

- `$$` — Process ID — ID do Processo atual do Shell.

---

### 3. Iniciar e sair do Bash

Iniciar uma nova sessão:

    bash

Sair da sessão atual:

    exit

---

### 4. Bash interativo

**Interactive Shell — Shell Interativo**

É quando o usuário executa comandos diretamente no terminal:

    pwd
    ls
    cd /tmp
    echo "Olá"

O Bash interpreta cada comando e mostra o resultado.

---

### 5. Bash Script

**Bash Script — Script Bash**

É um arquivo contendo comandos que serão executados pelo Bash.

Exemplo:

    #!/bin/bash

    echo "Olá"
    pwd
    ls

A primeira linha é:

**Shebang — Linha do Interpretador**

    #!/bin/bash

Ela indica que o script deve ser interpretado pelo Bash.

---

### 6. Executar um script

Podemos executar diretamente pelo Bash:

    bash script.sh

Ou tornar o arquivo executável:

    chmod +x script.sh
    ./script.sh

- `chmod` — Change Mode — Alterar Permissões.
- `+x` — Add Execute — Adicionar Execução.
- `./` — Current Directory — Diretório Atual.

---

### 7. Comandos internos e externos

**Builtin — Comando Interno**

Faz parte do próprio Bash.

Exemplos:

    cd
    export
    alias
    history

**External Command — Comando Externo**

É um programa separado executado pelo Bash.

Exemplos:

    ls
    grep
    cat
    awk

Para verificar:

    type cd
    type ls

Exemplo:

    cd is a shell builtin
    ls is /usr/bin/ls

---

### 8. Arquivos importantes

**`~/.bashrc` — Bash Run Commands — Configurações do Bash**

Normalmente contém configurações da sessão interativa.

Exemplo:

    alias ll='ls -la'

Aplicar as alterações:

    source ~/.bashrc

**`~/.bash_profile` — Bash Profile — Perfil do Bash**

Pode conter configurações executadas durante o login, dependendo da configuração do sistema.

---

### 9. Comandos essenciais

| Comando | English | Português |
|---|---|---|
| `bash` | Bourne Again Shell | Iniciar Bash |
| `echo` | Display Text | Exibir Texto |
| `type` | Identify Command | Identificar Comando |
| `source` | Read and Execute | Ler e Executar |
| `export` | Export Variable | Exportar Variável |
| `alias` | Create Alias | Criar Apelido |
| `history` | Command History | Histórico de Comandos |
| `exit` | Exit Shell | Sair do Shell |

---

## Resumo LPIC-1

- **Bash** é um Shell utilizado para interpretar comandos.
- Também executa **Bash Scripts**.
- `echo $SHELL` mostra o Shell definido.
- `$$` representa o PID do Shell atual.
- `bash` inicia uma nova sessão.
- `exit` encerra a sessão.
- `type` identifica comandos internos e externos.
- `#!/bin/bash` define o Bash como interpretador.
- `chmod +x` adiciona permissão de execução.
- `./script.sh` executa um script diretamente.
- `~/.bashrc` contém configurações comuns do Bash.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
