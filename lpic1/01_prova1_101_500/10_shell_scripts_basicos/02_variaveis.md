# 10 — Shell e Scripts Básicos
## 02 — Variáveis

### Variable — Variável

Uma variável armazena um valor que pode ser utilizado pelo Shell.

Exemplo:

    nome="Laerte"

Consultar:

    echo "$nome"

Resultado:

    Laerte

---

## Criando variáveis

A sintaxe é:

    variável=valor

Exemplo:

    idade=30

⚠️ Não coloque espaços ao redor do `=`.

Correto:

    nome="Laerte"

Incorreto:

    nome = "Laerte"

---

## Variáveis de ambiente

**Environment Variable — Variável de ambiente**

É uma variável disponibilizada para processos filhos.

Criar e exportar:

    export NOME="Laerte"

Ver:

    echo "$NOME"

Também podemos usar:

    printenv NOME

---

## Variáveis importantes

| Variável | Função |
|---|---|
| `$HOME` | Diretório pessoal |
| `$USER` | Usuário atual |
| `$SHELL` | Shell configurado |
| `$PATH` | Caminhos dos executáveis |
| `$PWD` | Diretório atual |
| `$OLDPWD` | Diretório anterior |
| `$?` | Status do último comando |
| `$$` | PID do shell atual |

Exemplo:

    echo "$HOME"
    echo "$USER"
    echo "$PATH"

---

## Exibir variáveis

**echo — exibir**

    echo "$HOME"

**printenv — exibir variáveis de ambiente**

    printenv

Para uma variável específica:

    printenv HOME

---

## unset

**unset — remover variável**

    nome="Laerte"

    unset nome

Depois:

    echo "$nome"

A variável não terá mais o valor definido.

---

## Variáveis somente para o comando

Podemos definir uma variável apenas para a execução de um comando:

    NOME="Laerte" comando

Essa variável fica disponível para esse processo.

---

## Export

**export — exportar**

Permite que uma variável seja herdada por processos filhos.

Exemplo:

    nome="Laerte"

    export nome

Ou diretamente:

    export nome="Laerte"

---

## Variáveis em Scripts

Exemplo:

    nome="$1"
    echo "Olá, $nome"

Se o script for executado:

    ./script.sh Laerte

O `$1` receberá:

    Laerte

---

## Aspas e variáveis

### Aspas duplas

Permitem expansão:

    nome="Laerte"
    echo "Olá, $nome"

Resultado:

    Olá, Laerte

### Aspas simples

Não expandem variáveis:

    echo 'Olá, $nome'

Resultado:

    Olá, $nome

---

## 🎯 Para a LPIC-1

**Criar:**

    nome="Laerte"

**Usar:**

    echo "$nome"

**Exportar:**

    export nome

**Remover:**

    unset nome

**Ver ambiente:**

    printenv

**Variáveis especiais:**

    $?
    $$
    $1
    $#
    $@

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
