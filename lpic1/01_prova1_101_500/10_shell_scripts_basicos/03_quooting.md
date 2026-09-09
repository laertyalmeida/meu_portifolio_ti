# 10 — Shell e Scripts Básicos

## 03 — Quoting

**Quoting — Uso de Aspas**

No Bash, **Quoting** é o uso de aspas para controlar como o Shell interpreta caracteres especiais, espaços e variáveis.

Os três principais tipos são:

- `' '` — Single Quotes — Aspas Simples
- `" "` — Double Quotes — Aspas Duplas
- `\` — Backslash — Barra Invertida

---

### 1. Single Quotes — Aspas Simples

Tudo dentro de `' '` é tratado literalmente.

Exemplo:

    nome="Laerte"
    echo 'Olá $nome'

Resultado:

    Olá $nome

A variável **não é expandida**.

Também preserva caracteres especiais:

    echo '$HOME'
    echo '*'
    echo '$(date)'

---

### 2. Double Quotes — Aspas Duplas

Dentro de `" "` o Bash ainda interpreta algumas expansões.

Exemplo:

    nome="Laerte"
    echo "Olá $nome"

Resultado:

    Olá Laerte

Também funciona com:

    echo "Diretório: $HOME"
    echo "Usuário: $USER"
    echo "Status: $?"

As aspas duplas protegem espaços e outros caracteres, mas permitem expansão de:

- `$variavel` — Variável
- `$(comando)` — Substituição de Comando
- `` `comando` `` — Substituição de Comando antiga
- `$((expressão))` — Expansão Aritmética

---

### 3. Backslash — Barra Invertida

A `\` faz com que o próximo caractere perca seu significado especial.

Exemplo:

    echo \$HOME

Resultado:

    $HOME

Sem a `\`:

    echo $HOME

O Bash substituirá `$HOME` pelo valor da variável.

---

### 4. Espaços

Sem aspas, espaços podem separar argumentos.

Exemplo:

    nome="Laerte Costa"

    echo $nome

O Bash interpreta como dois argumentos:

    Laerte
    Costa

Com aspas:

    echo "$nome"

O valor é tratado como um único argumento:

    Laerte Costa

**Regra prática:** use `"$variavel"` quando quiser preservar espaços no valor.

---

### 5. Diferença principal

| Forma | Expande variável? | Protege espaços? |
|---|---:|---:|
| `'texto'` | Não | Sim |
| `"texto"` | Sim | Sim |
| `\texto` | Caractere seguinte | Depende |

Exemplo:

    nome="Laerte"

    echo '$nome'
    echo "$nome"
    echo \$nome

Resultado:

    $nome
    Laerte
    $nome

---

### 6. Quoting com comandos

**Command Substitution — Substituição de Comando**

Permite colocar o resultado de um comando dentro de outro comando.

Forma recomendada:

    echo "Hoje é $(date)"

O Bash executa `date` e coloca o resultado no texto.

Também existe a forma antiga:

    echo "Hoje é `date`"

Prefira:

    $(date)

---

### 7. Quoting e caminhos

Aspas são importantes quando um arquivo ou diretório possui espaços.

Exemplo:

    arquivo="meu arquivo.txt"

Correto:

    cat "$arquivo"

Sem aspas:

    cat $arquivo

O Bash pode interpretar como dois argumentos:

    meu
    arquivo.txt

---

### 8. Quoting em scripts

Boa prática:

    arquivo="/home/laerte/meus arquivos/teste.txt"

    cat "$arquivo"

Isso torna o script mais seguro contra problemas causados por espaços e outros caracteres especiais.

---

## Resumo LPIC-1

- **Quoting** controla como o Bash interpreta caracteres.
- `'texto'` — Aspas simples: preservam o conteúdo literalmente.
- `"texto"` — Aspas duplas: permitem expansão de variáveis e comandos.
- `\` — Barra invertida: protege o caractere seguinte.
- `"$(comando)"` permite usar o resultado de um comando.
- Aspas duplas preservam espaços dentro de variáveis.
- `"$variavel"` é uma prática importante em scripts.
- Aspas simples não expandem `$variavel`.
- Aspas duplas expandem `$variavel`.
- `\` pode impedir a expansão de caracteres especiais.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
