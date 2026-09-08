# 10 — Shell e Scripts Básicos
## 01 — Bash

### O que é Bash?

**Bash — Bourne Again SHell (Shell Bourne Novamente)**

O Bash é um **shell**, ou seja, um programa que permite ao usuário interagir com o Linux por meio de comandos.

Exemplo:

    ls
    cd /home
    mkdir projetos

O Bash recebe o comando, interpreta e solicita ao sistema que o execute.

---

# 1. Shell x Terminal

Esses conceitos são diferentes.

### Terminal

**Terminal — Terminal**

É o programa/interface onde você digita comandos.

Exemplos:

    GNOME Terminal
    Konsole
    xterm

### Shell

**Shell — Interpretador de comandos**

É o programa que interpreta os comandos.

Exemplos:

    bash
    sh
    zsh
    fish

Uma forma simples de lembrar:

    Terminal → onde você digita
    Shell    → quem interpreta

---

# 2. Ver o Shell atual

Use:

    echo $SHELL

**echo** → exibir

**$SHELL** → variável que normalmente indica o shell de login configurado para o usuário.

Para descobrir o processo do shell atualmente em execução:

    ps -p $$ -o comm=

Aqui:

**$$** → PID do shell atual.

---

# 3. Iniciar o Bash

Digite:

    bash

Isso inicia uma nova sessão do Bash dentro do shell atual.

Para sair:

    exit

---

# 4. Bash como Shell de Login

O Bash pode ser configurado como shell de login de um usuário.

Essa informação aparece em:

    /etc/passwd

Exemplo:

    laerte:x:1000:1000:Laerte:/home/laerte:/bin/bash

O último campo indica o shell de login:

    /bin/bash

---

# 5. Comandos internos e externos

O Bash possui comandos que são **builtins**.

**Builtin — Comando interno**

São comandos executados pelo próprio Bash.

Exemplos:

    cd
    echo
    export
    alias
    history
    pwd
    read

Existem também programas externos.

Exemplos:

    ls
    cat
    grep
    mkdir
    cp
    mv

---

# 6. Descobrir onde está um comando

### type

    type cd

Resultado semelhante a:

    cd is a shell builtin

Para um comando externo:

    type ls

Pode mostrar:

    ls is aliased to ...
    
ou:

    ls is /usr/bin/ls

---

### command -v

**command -v — verificar localização/tipo do comando**

    command -v ls

Exemplo:

    /usr/bin/ls

---

# 7. PATH

**PATH — Caminho de pesquisa**

É uma variável que informa ao shell onde procurar programas executáveis.

Ver:

    echo $PATH

Exemplo:

    /usr/local/bin:/usr/bin:/bin

Os diretórios são separados por:

    :

Quando você executa:

    ls

o Bash procura o programa nos diretórios definidos pelo `PATH`.

---

# 8. Executar um programa pelo caminho

Podemos informar o caminho completo:

    /usr/bin/ls

Ou, no diretório atual:

    ./script.sh

**./** → diretório atual.

⚠️ Por segurança, o diretório atual normalmente não faz parte do `PATH`.

---

# 9. Variáveis no Bash

Criar uma variável:

    nome="Laerte"

⚠️ Não coloque espaços ao redor do `=`.

Correto:

    nome="Laerte"

Incorreto:

    nome = "Laerte"

Ler a variável:

    echo "$nome"

---

# 10. Variáveis de ambiente

Uma variável pode ser exportada para os processos filhos:

    export nome="Laerte"

Ver:

    echo "$nome"

Ou:

    printenv nome

**printenv** → exibir variáveis de ambiente.

---

# 11. Variáveis especiais

O Bash possui variáveis especiais.

| Variável | Significado |
|---|---|
| `$0` | Nome do script/comando |
| `$1` | Primeiro argumento |
| `$2` | Segundo argumento |
| `$#` | Quantidade de argumentos |
| `$@` | Todos os argumentos |
| `$?` | Status do último comando |
| `$$` | PID do shell atual |
| `$!` | PID do último processo em background |

Essas variáveis são muito importantes em scripts.

---

# 12. Status de saída

Todo comando normalmente termina com um **exit status**.

Ver o status do último comando:

    echo $?

Normalmente:

    0 → sucesso
    diferente de 0 → erro ou condição diferente de sucesso

Exemplo:

    ls /etc

    echo $?

Se o comando funcionar, normalmente será:

    0

---

# 13. Histórico

O Bash mantém um histórico dos comandos executados.

Ver:

    history

Executar novamente um comando pelo número:

    !123

Executar o comando anterior:

    !!

Também podemos usar:

    ↑

para navegar pelos comandos anteriores.

---

# 14. Alias

**Alias — Apelido**

Permite criar um nome alternativo para um comando.

Exemplo:

    alias ll='ls -l'

Agora:

    ll

executa:

    ls -l

Ver aliases:

    alias

Remover:

    unalias ll

---

# 15. Redirecionamento

O Bash permite redirecionar entrada e saída.

### Saída

    ls > arquivos.txt

**>** → redirecionar saída e substituir o arquivo.

### Acrescentar

    ls >> arquivos.txt

**>>** → acrescentar ao final.

### Erros

    comando 2> erro.txt

**2>** → redirecionar stderr (saída de erro).

### Saída + erro

Uma forma comum:

    comando > saida.txt 2>&1

→ saída normal e erros vão para o mesmo arquivo.

---

# 16. Pipe

**Pipe — Tubo**

O símbolo:

    |

envia a saída de um comando para a entrada de outro.

Exemplo:

    ls /etc | grep ssh

Interpretação:

    ls /etc
       ↓
    saída
       ↓
    grep ssh

O resultado será filtrado pelo `grep`.

---

# 17. Quoting — Aspas

As aspas são muito importantes no Bash.

### Aspas simples

    'texto'

Preservam o conteúdo literalmente.

Exemplo:

    echo '$HOME'

Resultado:

    $HOME

---

### Aspas duplas

    "texto"

Permitem expansão de variáveis.

Exemplo:

    echo "$HOME"

Resultado semelhante a:

    /home/laerte

---

### Escape

A barra invertida:

    \

pode impedir a interpretação de um caractere especial.

Exemplo:

    echo "\$HOME"

Resultado:

    $HOME

---

# 18. Comandos úteis do Bash

| Comando | Função |
|---|---|
| `pwd` | Mostrar diretório atual |
| `cd` | Mudar diretório |
| `echo` | Exibir texto/variáveis |
| `type` | Identificar tipo/localização do comando |
| `command -v` | Localizar/verificar comando |
| `history` | Mostrar histórico |
| `alias` | Mostrar/criar aliases |
| `export` | Exportar variável |
| `read` | Ler entrada |
| `exit` | Encerrar shell/script |

---

# 🎯 LPIC-1 — O que memorizar

### Bash

**Bash — Bourne Again SHell**

→ Shell muito utilizado no Linux.

### Conceitos fundamentais

    Shell
    ↓
    interpreta comandos

    PATH
    ↓
    procura executáveis

    $?
    ↓
    status do último comando

    $$
    ↓
    PID do shell atual

    $1, $2...
    ↓
    argumentos

    $#
    ↓
    quantidade de argumentos

    $@
    ↓
    argumentos recebidos

    |
    ↓
    pipe

    >
    ↓
    sobrescrever saída

    >>
    ↓
    acrescentar saída

    2>
    ↓
    redirecionar erros

---

## 🧠 Pegadinhas LPIC-1

**`$SHELL`** geralmente indica o shell de login configurado, não necessariamente o shell atualmente em execução.

**`$?`** deve ser consultado logo após o comando que você deseja verificar.

**`>`** substitui o conteúdo do arquivo.

**`>>`** acrescenta ao arquivo.

**`$0`** não é o primeiro argumento; normalmente representa o nome do script ou comando.

**`$1`** é o primeiro argumento.

**`$#`** é a quantidade de argumentos.

**`$@`** representa os argumentos posicionais.

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
