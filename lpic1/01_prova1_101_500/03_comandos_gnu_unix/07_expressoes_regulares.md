# Comandos GNU/UNIX

## 07 — Expressões Regulares

**Regular Expressions (Regex) — Expressões Regulares** são padrões usados para **encontrar, filtrar e manipular textos**.

No LPIC-1, são especialmente importantes com `grep`, `grep -E`, `sed` e `awk`.

---

### Caracteres básicos

| Regex | Significado | Exemplo |
|---|---|---|
| `.` | qualquer caractere | `a.c` → `abc`, `a1c` |
| `^` | início da linha | `^root` |
| `$` | fim da linha | `bash$` |
| `*` | zero ou mais ocorrências | `ab*` |
| `[ ]` | conjunto de caracteres | `[abc]` |
| `[^ ]` | qualquer caractere exceto os indicados | `[^0-9]` |

---

### `.` — qualquer caractere

O ponto representa **um caractere qualquer**.

    grep "c.t" arquivo.txt

Pode encontrar:

    cat
    cot
    c1t

---

### `^` — início da linha

    grep "^root" /etc/passwd

Procura linhas que começam com `root`.

Exemplo:

    root:x:0:0:root:/root:/bin/bash

---

### `$` — fim da linha

    grep "bash$" /etc/passwd

Procura linhas que terminam com `bash`.

---

### `*` — zero ou mais ocorrências

    grep "ab*c" arquivo.txt

Pode encontrar:

    ac
    abc
    abbc
    abbbc

O `*` modifica o caractere ou expressão imediatamente anterior.

---

### `[ ]` — conjunto de caracteres

Permite escolher um caractere entre várias possibilidades.

    grep "[abc]" arquivo.txt

Encontra linhas que possuem `a`, `b` ou `c`.

Também podemos usar intervalos:

    grep "[0-9]" arquivo.txt

Procura qualquer número de `0` a `9`.

Outros exemplos:

    [a-z]    → letras minúsculas
    [A-Z]    → letras maiúsculas
    [0-9]    → números

---

### `[^ ]` — negação

Dentro de `[ ]`, o `^` no início significa **exceto**.

    grep "[^0-9]" arquivo.txt

Procura caracteres que **não sejam números**.

---

## Expressões regulares estendidas

Com `grep -E`, podemos utilizar operadores adicionais.

### `+` — uma ou mais ocorrências

    grep -E "ab+c" arquivo.txt

Encontra:

    abc
    abbc
    abbbc

Mas não encontra:

    ac

---

### `?` — zero ou uma ocorrência

    grep -E "colou?r" arquivo.txt

Pode encontrar:

    color
    colour

---

### `|` — OR — ou

Permite procurar uma alternativa ou outra.

    grep -E "Linux|Unix" arquivo.txt

Encontra linhas contendo:

    Linux

ou:

    Unix

---

### `( )` — agrupamento

Agrupa partes de uma expressão.

    grep -E "(Linux|Unix) OS" arquivo.txt

Procura:

    Linux OS
    Unix OS

---

### `{ }` — quantidade específica

Define quantas vezes uma expressão deve aparecer.

    grep -E "[0-9]{3}" arquivo.txt

Procura exatamente **3 números consecutivos**.

Exemplo:

    123

Também podemos definir intervalo:

    grep -E "[0-9]{2,4}" arquivo.txt

Procura de **2 a 4 números consecutivos**.

---

## Classes de caracteres

O `grep -E` também pode trabalhar com classes POSIX.

| Classe | Significado |
|---|---|
| `[[:digit:]]` | dígitos |
| `[[:alpha:]]` | letras |
| `[[:alnum:]]` | letras e números |
| `[[:lower:]]` | letras minúsculas |
| `[[:upper:]]` | letras maiúsculas |
| `[[:space:]]` | espaços |
| `[[:blank:]]` | espaço e tabulação |

Exemplo:

    grep -E "[[:digit:]]" arquivo.txt

Procura linhas contendo números.

---

## Exemplos práticos

Linhas que começam com `root`:

    grep "^root" /etc/passwd

Linhas que terminam com `bash`:

    grep "bash$" /etc/passwd

Linhas contendo números:

    grep -E "[0-9]" arquivo.txt

Linhas contendo exatamente três números consecutivos:

    grep -E "[0-9]{3}" arquivo.txt

Procurar `Linux` ou `Unix`:

    grep -E "Linux|Unix" arquivo.txt

Procurar uma palavra começando com `lin`:

    grep -E "^lin" arquivo.txt

---

## `grep` × `grep -E`

| Comando | Uso |
|---|---|
| `grep` | Expressões regulares básicas (BRE) |
| `grep -E` | Expressões regulares estendidas (ERE) |

**Importante:**

    grep -E

é a forma moderna de utilizar **Extended Regular Expressions (ERE) — Expressões Regulares Estendidas**.

---

## Resumo LPIC-1

| Símbolo | Significado |
|---|---|
| `.` | qualquer caractere |
| `^` | início da linha |
| `$` | fim da linha |
| `*` | zero ou mais |
| `+` | uma ou mais |
| `?` | zero ou uma |
| `[abc]` | a, b ou c |
| `[^abc]` | qualquer caractere, exceto a, b ou c |
| `[0-9]` | qualquer número de 0 a 9 |
| `{n}` | exatamente n ocorrências |
| `{n,m}` | de n até m ocorrências |
| `|` | ou |
| `( )` | agrupamento |

**Memorize principalmente:**

    ^      → início
    $      → fim
    .      → qualquer caractere
    *      → zero ou mais
    +      → uma ou mais
    ?      → zero ou uma
    [ ]    → conjunto
    { }    → quantidade
    |      → ou
    ( )    → agrupamento

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
