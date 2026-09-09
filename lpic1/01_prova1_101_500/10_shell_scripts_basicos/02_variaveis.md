# 10 — Shell e Scripts Básicos

## 02 — Variáveis

**Variable — Variável**

Uma variável no Bash é um nome que armazena um valor para ser usado posteriormente.

Exemplo:

    nome="Laerte"
    echo "$nome"

Resultado:

    Laerte

---

### 1. Criar uma variável

Sintaxe:

    nome="valor"

Exemplo:

    usuario="laerte"
    idade=30

**Importante:** não coloque espaços ao redor do `=`.

Correto:

    nome="Laerte"

Incorreto:

    nome = "Laerte"

---

### 2. Usar uma variável

Para acessar o valor, usamos `$`:

    nome="Laerte"
    echo "$nome"

Também podemos usar:

    echo "${nome}"

As chaves ajudam a separar o nome da variável de outros caracteres.

Exemplo:

    nome="Laerte"
    echo "${nome}Costa"

Resultado:

    LaerteCosta

---

### 3. Variáveis de ambiente

**Environment Variable — Variável de Ambiente**

São variáveis disponibilizadas para processos executados pelo Shell.

Exemplos comuns:

    $HOME
    $USER
    $SHELL
    $PATH
    $PWD

Consultar:

    echo "$HOME"
    echo "$USER"
    echo "$SHELL"
    echo "$PATH"

---

### 4. Variáveis locais

Uma variável criada normalmente no Bash é, por padrão, uma variável local daquele Shell.

Exemplo:

    nome="Laerte"

Um programa iniciado a partir desse Shell não recebe automaticamente essa variável.

Para disponibilizá-la aos processos filhos, usamos `export`.

---

### 5. export

**export — Exportar**

Torna uma variável disponível para processos filhos.

Exemplo:

    nome="Laerte"
    export nome

Ou diretamente:

    export nome="Laerte"

Verificar:

    export -p

- `-p` — Print — Exibir variáveis exportadas.

---

### 6. Variáveis especiais

O Bash possui variáveis especiais:

| Variável | Significado |
|---|---|
| `$0` | Nome do script/comando |
| `$1` | Primeiro argumento |
| `$2` | Segundo argumento |
| `$#` | Quantidade de argumentos |
| `$?` | Status de saída do último comando |
| `$$` | PID do Shell atual |
| `$!` | PID do último processo executado em background |
| `$HOME` | Diretório pessoal |
| `$USER` | Usuário atual |
| `$PWD` | Diretório atual |
| `$OLDPWD` | Diretório anterior |
| `$PATH` | Caminhos para procurar comandos |

---

### 7. Status de saída — `$?`

**Exit Status — Status de Saída**

Todo comando termina com um código.

Normalmente:

    0 = sucesso
    diferente de 0 = erro ou outra condição

Exemplo:

    ls
    echo "$?"

Se `ls` funcionar, normalmente:

    0

Outro exemplo:

    comando_inexistente
    echo "$?"

O valor será diferente de `0`.

---

### 8. Variáveis somente leitura

**readonly — Somente Leitura**

Impede que uma variável seja alterada normalmente.

Exemplo:

    readonly sistema="Linux"

Consultar:

    readonly

---

### 9. Remover uma variável

**unset — Remover Variável**

Exemplo:

    nome="Laerte"
    unset nome

Depois:

    echo "$nome"

A variável não terá mais seu valor definido.

---

### 10. Regras para nomes

Um nome de variável pode conter:

- letras;
- números;
- `_` — underscore — sublinhado.

Não deve começar com número.

Correto:

    nome="Laerte"
    usuario_atual="laerte"
    arquivo1="teste"

Incorreto:

    1nome="Laerte"

Bash diferencia maiúsculas e minúsculas:

    nome="Laerte"
    Nome="Linux"

São duas variáveis diferentes.

---

### 11. Aspas e variáveis

**Double Quotes — Aspas Duplas**

Permitem a expansão de variáveis:

    nome="Laerte"
    echo "Olá, $nome"

Resultado:

    Olá, Laerte

**Single Quotes — Aspas Simples**

Impedem a expansão:

    echo 'Olá, $nome'

Resultado:

    Olá, $nome

---

## Resumo LPIC-1

- Variáveis armazenam valores no Bash.
- Criar: `nome="valor"`.
- Acessar: `$nome`.
- `${nome}` delimita o nome da variável.
- `export` disponibiliza a variável para processos filhos.
- `unset` remove uma variável.
- `readonly` cria uma variável somente leitura.
- `$?` mostra o status do último comando.
- `$0`, `$1`, `$2` representam o script e seus argumentos.
- `$#` mostra a quantidade de argumentos.
- `$$` mostra o PID do Shell atual.
- `$HOME`, `$USER`, `$PATH` e `$PWD` são variáveis comuns de ambiente.
- Aspas duplas permitem expansão de variáveis.
- Aspas simples impedem expansão de variáveis.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
