# Comandos GNU/UNIX

## 09 — awk

`awk` — **Aho, Weinberger and Kernighan** — ferramenta de processamento e análise de texto.

O `awk` é usado principalmente para **ler arquivos linha por linha, separar campos, filtrar informações e executar ações sobre os dados**.

É muito útil para trabalhar com arquivos organizados em colunas.

---

## Estrutura básica

Sintaxe:

    awk 'padrão { ação }' arquivo

Exemplo:

    awk '{print $1}' arquivo.txt

Significa:

    $1    → primeiro campo
    print → imprimir

Se o arquivo tiver:

    João 25 Linux
    Maria 30 Windows
    Pedro 22 Linux

O comando:

    awk '{print $1}' arquivo.txt

Produz:

    João
    Maria
    Pedro

---

## Campos

Por padrão, o `awk` considera espaços e tabulações como separadores de campos.

| Variável | Significado |
|---|---|
| `$0` | linha inteira |
| `$1` | primeiro campo |
| `$2` | segundo campo |
| `$3` | terceiro campo |
| `NF` | número de campos da linha |
| `NR` | número da linha atual |

Exemplo:

    awk '{print $1, $3}' arquivo.txt

Resultado:

    João Linux
    Maria Windows
    Pedro Linux

---

## `$0` — linha inteira

    awk '{print $0}' arquivo.txt

Mostra a linha completa.

Na prática, é semelhante a:

    cat arquivo.txt

---

## `NF` — Number of Fields — número de campos

    awk '{print NF}' arquivo.txt

Mostra quantos campos existem em cada linha.

Exemplo:

    João 25 Linux

Resultado:

    3

---

## `NR` — Number of Records — número do registro/linha

    awk '{print NR, $0}' arquivo.txt

Resultado:

    1 João 25 Linux
    2 Maria 30 Windows
    3 Pedro 22 Linux

`NR` aumenta a cada linha processada.

---

## Filtrando informações

Podemos usar condições.

Exemplo:

    awk '$3 == "Linux" {print $1}' arquivo.txt

Significa:

    $3 == "Linux" → terceiro campo é Linux
    print $1       → mostrar o primeiro campo

Resultado:

    João
    Pedro

---

## Operadores de comparação

| Operador | Significado |
|---|---|
| `==` | igual |
| `!=` | diferente |
| `>` | maior |
| `<` | menor |
| `>=` | maior ou igual |
| `<=` | menor ou igual |

Exemplo:

    awk '$2 > 25 {print $1}' arquivo.txt

Mostra os nomes cuja idade seja maior que 25.

---

## `-F` — Field Separator — separador de campos

Podemos definir qual caractere separa os campos.

Exemplo com `:`:

    awk -F: '{print $1}' /etc/passwd

O arquivo `/etc/passwd` utiliza `:` como separador.

Para mostrar usuário e shell:

    awk -F: '{print $1, $7}' /etc/passwd

Resultado semelhante a:

    root /bin/bash
    usuario /bin/bash

---

## Separador de saída

Podemos controlar como os campos serão exibidos usando `OFS`.

`OFS` — **Output Field Separator** — separador de campos de saída.

Exemplo:

    awk -F: 'BEGIN {OFS=" - "} {print $1, $7}' /etc/passwd

Saída:

    root - /bin/bash

---

## `BEGIN` — início

`BEGIN` executa uma ação **antes de o arquivo começar a ser processado**.

Exemplo:

    awk 'BEGIN {print "Usuários"} {print $1}' arquivo.txt

---

## `END` — fim

`END` executa uma ação **depois que todas as linhas foram processadas**.

Exemplo:

    awk '{total += $2} END {print total}' arquivo.txt

Nesse exemplo, o `awk` soma os valores do segundo campo.

---

## Variáveis

O `awk` permite criar variáveis.

Exemplo:

    awk '{total += $2} END {print "Total:", total}' arquivo.txt

Se os valores forem:

    João 10
    Maria 20
    Pedro 30

Resultado:

    Total: 60

---

## Expressões regulares

O `awk` também trabalha com **Regular Expressions (Regex) — Expressões Regulares**.

Exemplo:

    awk '/Linux/ {print $1}' arquivo.txt

Mostra o primeiro campo das linhas que contêm `Linux`.

Com expressão regular:

    awk '/^root/ {print $0}' /etc/passwd

Procura linhas que começam com `root`.

---

## `awk` com `|` — Pipe — canal

O `awk` pode receber a saída de outro comando.

Exemplo:

    ls -l | awk '{print $9}'

Aqui:

    ls -l → mostra os arquivos
    |     → envia a saída
    awk   → seleciona o campo desejado
    $9    → normalmente contém o nome do arquivo nessa saída

---

## `awk` × `grep` × `sed`

| Comando | Principal finalidade |
|---|---|
| `grep` | encontrar linhas |
| `sed` | substituir/modificar texto |
| `awk` | analisar campos e processar dados |

Exemplo:

    grep "Linux" arquivo.txt

→ encontra linhas contendo `Linux`.

    sed 's/Linux/Unix/g' arquivo.txt

→ substitui `Linux` por `Unix`.

    awk '{print $1}' arquivo.txt

→ extrai o primeiro campo.

---

## Exemplos práticos

Mostrar usuários do sistema:

    awk -F: '{print $1}' /etc/passwd

Mostrar usuário e shell:

    awk -F: '{print $1, $7}' /etc/passwd

Mostrar número das linhas:

    awk '{print NR, $0}' arquivo.txt

Mostrar apenas o segundo campo:

    awk '{print $2}' arquivo.txt

Mostrar linhas onde o terceiro campo é `Linux`:

    awk '$3 == "Linux" {print $0}' arquivo.txt

Somar valores do segundo campo:

    awk '{total += $2} END {print total}' arquivo.txt

---

## Resumo LPIC-1

| Elemento | Função |
|---|---|
| `awk` | processar e analisar texto |
| `$0` | linha inteira |
| `$1` | primeiro campo |
| `$2` | segundo campo |
| `$NF` | último campo |
| `NF` | número de campos |
| `NR` | número da linha |
| `-F` | definir separador de campos |
| `BEGIN` | executar antes do processamento |
| `END` | executar depois do processamento |
| `print` | imprimir |
| `OFS` | separador de campos de saída |
| `==` | igual |
| `!=` | diferente |
| `>` | maior |
| `<` | menor |

**Memorize principalmente:**

    awk '{print $1}' arquivo
    → mostrar o primeiro campo

    awk -F: '{print $1}' /etc/passwd
    → usar : como separador

    $0  → linha inteira
    $1  → primeiro campo
    $2  → segundo campo
    $NF → último campo
    NF  → quantidade de campos
    NR  → número da linha

    grep → encontrar
    sed  → modificar
    awk  → analisar/processar

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
