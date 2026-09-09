# Comandos GNU/UNIX

## 14 — Variáveis e PATH

**Variable — Variável**

Uma variável armazena um valor que pode ser usado pelo **Shell — Interpretador de Comandos**.

Exemplo:

    nome="Laerte"

Usar o valor:

    echo "$nome"

Resultado:

    Laerte

> Não coloque espaços ao redor do `=`.

---

## 1. Criar uma variável

    nome="Laerte"
    sistema="Linux"

Consultar:

    echo "$nome"
    echo "$sistema"

O `$` indica que queremos acessar o **valor da variável**.

---

## 2. Variáveis de ambiente

**Environment Variable — Variável de Ambiente**

É uma variável disponibilizada para processos executados pelo Shell.

Criar uma variável de ambiente:

    export NOME="Laerte"

Ver:

    echo "$NOME"

Consultar todas:

    env

ou:

    printenv

---

## 3. `export` — Exportar

`export` torna uma variável disponível para processos filhos do Shell.

Exemplo:

    nome="Laerte"
    export nome

Depois:

    bash

O novo Shell consegue acessar:

    echo "$nome"

Sem `export`, a variável normalmente fica disponível apenas no Shell atual.

---

## 4. Variáveis importantes

| Variável | English | Português |
|---|---|---|
| `$PATH` | Path | Caminho dos executáveis |
| `$HOME` | Home Directory | Diretório pessoal |
| `$USER` | User | Usuário atual |
| `$SHELL` | Shell | Shell padrão |
| `$PWD` | Present Working Directory | Diretório atual |
| `$OLDPWD` | Old Present Working Directory | Diretório anterior |
| `$LANG` | Language | Idioma/localização |
| `$TERM` | Terminal | Tipo de terminal |
| `$?` | Exit Status | Status de saída do último comando |
| `$$` | Process ID | PID do Shell atual |

Exemplos:

    echo "$HOME"
    echo "$USER"
    echo "$SHELL"
    echo "$PWD"

---

## 5. `PATH` — Caminho

**PATH — Path — Caminho**

`PATH` informa ao Shell **onde procurar pelos programas executáveis**.

Ver o PATH:

    echo "$PATH"

Exemplo:

    /usr/local/bin:/usr/bin:/bin

Os diretórios são separados por `:`.

O Shell procura os comandos nesses diretórios.

---

## 6. Como o PATH funciona

Quando você executa:

    ls

O Shell procura o executável `ls` nos diretórios definidos em `$PATH`.

Por exemplo:

    /usr/local/bin
    /usr/bin
    /bin

Quando encontra o programa, executa-o.

Por isso normalmente podemos usar:

    ls

em vez de:

    /usr/bin/ls

---

## 7. `which` — Qual / Localizar executável

Mostra qual executável será encontrado pelo PATH:

    which ls

Exemplo:

    /usr/bin/ls

Também pode ser usado:

    command -v ls

---

## 8. Adicionar um diretório ao PATH

Adicionar temporariamente:

    export PATH="$PATH:$HOME/bin"

Agora o Shell também procurará programas em:

    $HOME/bin

Verificar:

    echo "$PATH"

### Por que usar `$PATH`?

Porque queremos manter os diretórios que já estavam configurados.

Evite:

    export PATH="$HOME/bin"

Isso substitui o PATH anterior e pode fazer comandos comuns deixarem de funcionar.

---

## 9. PATH e diretório atual

Por segurança, o diretório atual `.` normalmente não está no PATH.

Para executar um programa que está no diretório atual:

    ./programa

`./` significa:

**current directory — diretório atual**

Exemplo:

    ./script.sh

Isso é diferente de:

    script.sh

O segundo depende de o diretório atual estar no `$PATH`.

---

## 10. Variáveis temporárias

Uma variável criada no Shell normalmente existe apenas durante aquela sessão.

Exemplo:

    mensagem="Olá"
    echo "$mensagem"

Ao fechar o Shell, a variável é perdida.

---

## 11. Variáveis permanentes

Para configurar variáveis automaticamente em novos Shells, podemos colocá-las em arquivos de inicialização.

Exemplo comum:

    ~/.bashrc

`~` — Home Directory — Diretório Pessoal.

Adicionar:

    export EDITOR="vim"

Depois recarregar:

    source ~/.bashrc

Ou:

    . ~/.bashrc

---

## 12. `unset` — Desdefinir / Remover variável

Remove uma variável:

    unset nome

Verificar:

    echo "$nome"

Se não existir, normalmente não haverá saída.

---

## 13. Aspas e variáveis

Com aspas:

    nome="Laerte Costa"
    echo "$nome"

O valor é tratado como uma unidade.

Sem aspas:

    echo $nome

O Shell pode realizar **Word Splitting — Divisão de Palavras**.

Regra prática:

    echo "$variavel"

Prefira colocar variáveis entre aspas quando estiver usando seus valores.

---

## 14. `env` — Environment — Ambiente

Mostra variáveis de ambiente:

    env

Também podemos procurar uma específica:

    env | grep PATH

---

## 15. `set` — Configurações do Shell

`set` pode mostrar variáveis, funções e configurações do Shell.

    set

Para estudar variáveis de ambiente, normalmente são mais úteis:

    env
    printenv
    echo "$VARIAVEL"

---

## Resumo LPIC-1

- **Variable — Variável** → armazena um valor.
- `$VAR` → acessa o valor de uma variável.
- `export` → transforma uma variável em variável de ambiente para processos filhos.
- `env` → mostra variáveis de ambiente.
- `printenv` → mostra variáveis de ambiente.
- `unset` → remove uma variável.
- `$HOME` → diretório pessoal.
- `$USER` → usuário atual.
- `$PWD` → diretório atual.
- `$SHELL` → Shell padrão.
- `$PATH` → lista de diretórios onde o Shell procura executáveis.
- Diretórios no `$PATH` são separados por `:`.
- `which comando` → mostra o executável encontrado.
- `command -v comando` → identifica como o comando será encontrado.
- `./programa` → executa um programa no diretório atual.
- `~/.bashrc` → arquivo comum para configurações do Bash.
- `source ~/.bashrc` → recarrega as configurações no Shell atual.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
