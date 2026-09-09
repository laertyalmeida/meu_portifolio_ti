# Comandos GNU/UNIX

## 15 — Histórico e Aliases

**History — Histórico**

O histórico guarda comandos executados anteriormente no Shell.

**Alias — Apelido**

Um alias cria um nome curto para um comando ou conjunto de opções.

---

## 1. `history` — History — Histórico

Mostrar os comandos anteriores:

    history

Exemplo:

    101  pwd
    102  ls -la
    103  cd /etc
    104  grep root passwd

O número identifica a posição do comando no histórico.

---

## 2. Executar um comando pelo número

Use `!` seguido do número:

    !102

Isso executa novamente:

    ls -la

---

## 3. `!!` — Último comando

Executa novamente o último comando:

    !!

Exemplo:

    apt update

Se for necessário repetir:

    !!

O Shell executará novamente `apt update`.

---

## 4. `!texto` — Comando que começa com texto

Executa o comando mais recente que começa com determinado texto:

    !ls

Se o último comando iniciado por `ls` foi:

    ls -la /etc

`!ls` executará esse comando novamente.

---

## 5. `!$` — Último argumento

`!$` representa o último argumento do comando anterior.

Exemplo:

    cat arquivo.txt

Depois:

    nano !$

O Shell interpreta como:

    nano arquivo.txt

---

## 6. Teclas úteis

| Tecla | English | Português |
|---|---|---|
| `↑` | Up Arrow | Comando anterior |
| `↓` | Down Arrow | Próximo comando |
| `Ctrl+R` | Reverse Search | Busca reversa |
| `Ctrl+C` | Interrupt | Interromper comando |
| `Ctrl+L` | Clear Screen | Limpar tela |

### `Ctrl+R`

Permite procurar comandos anteriores:

    (reverse-i-search)`grep':

O Shell procura comandos que contenham `grep`.

Pressione `Ctrl+R` novamente para procurar ocorrências anteriores.

---

## 7. `history -c` — Clear — Limpar

Limpa o histórico da sessão atual:

    history -c

> O comportamento do arquivo de histórico pode depender da configuração do Shell.

---

## 8. Arquivo do histórico do Bash

No Bash, o histórico normalmente é armazenado em:

    ~/.bash_history

`~` — Home Directory — Diretório Pessoal.

Visualizar:

    cat ~/.bash_history

ou:

    less ~/.bash_history

---

# Aliases

## 9. `alias` — Alias — Apelido

Um alias cria um nome alternativo para um comando.

Exemplo:

    alias ll='ls -la'

Agora:

    ll

equivale a:

    ls -la

---

## 10. Ver aliases

Mostrar todos:

    alias

Ver um específico:

    alias ll

Exemplo:

    alias ll='ls -la'

---

## 11. Criar aliases úteis

    alias ll='ls -lh'
    alias la='ls -la'
    alias cls='clear'

Agora:

    ll

executa:

    ls -lh

---

## 12. Alias com segurança

Um alias comum:

    alias rm='rm -i'

`-i` — interactive — interativo.

Antes de remover um arquivo, o Shell pergunta:

    rm: remove regular file 'arquivo.txt'?

Isso ajuda a evitar exclusões acidentais.

---

## 13. Remover um alias

Use:

    unalias ll

Verificar:

    alias ll

Se não existir, o alias foi removido.

---

## 14. Alias temporário × permanente

Criado diretamente no terminal:

    alias ll='ls -la'

Normalmente vale apenas para aquela sessão do Shell.

Para carregar automaticamente no Bash, coloque o alias em:

    ~/.bashrc

Exemplo:

    alias ll='ls -la'
    alias la='ls -la'
    alias rm='rm -i'

Depois recarregue:

    source ~/.bashrc

---

## 15. Ignorar um alias

Se existir:

    alias rm='rm -i'

Podemos executar o comando original usando:

    \rm arquivo.txt

A barra invertida `\` impede a expansão do alias naquele comando.

Também podemos usar:

    command rm arquivo.txt

`command` solicita ao Shell que execute o comando sem utilizar um alias com esse nome.

---

## 16. Histórico + Aliases

Exemplo:

    alias ll='ls -la'

Executando:

    ll

O Bash registra o comando digitado no histórico conforme sua configuração.

Podemos verificar com:

    history

---

## Resumo LPIC-1

- `history` → mostra o histórico de comandos.
- `!n` → executa o comando de número `n`.
- `!!` → executa novamente o último comando.
- `!texto` → executa o último comando iniciado com `texto`.
- `!$` → representa o último argumento do comando anterior.
- `Ctrl+R` → pesquisa comandos anteriores.
- `~/.bash_history` → arquivo comum de histórico do Bash.
- `history -c` → limpa o histórico da sessão.
- `alias` → mostra ou cria apelidos para comandos.
- `alias ll='ls -la'` → cria o alias `ll`.
- `unalias ll` → remove o alias.
- `~/.bashrc` → arquivo comum para aliases permanentes no Bash.
- `source ~/.bashrc` → recarrega o arquivo.
- `\comando` → evita a expansão de um alias naquele comando.
- `command comando` → executa o comando sem usar um alias com esse nome.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
