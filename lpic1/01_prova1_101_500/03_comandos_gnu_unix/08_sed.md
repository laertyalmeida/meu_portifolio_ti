# Comandos GNU/UNIX

## 08 — sed

`sed` — **Stream Editor** — Editor de Fluxo.

É usado para **ler, filtrar, substituir, remover e modificar texto** sem precisar abrir o arquivo em um editor interativo.

O `sed` normalmente recebe uma entrada, aplica uma regra e produz uma saída.

---

### Uso básico

    sed 's/Linux/GNU Linux/' arquivo.txt

Significa:

    s → substitute — substituir
    Linux → texto que será procurado
    GNU Linux → novo texto

Por padrão, o `sed` **não altera o arquivo original**. Ele mostra o resultado no terminal.

---

## `s` — Substitute — substituir

Sintaxe:

    sed 's/antigo/novo/' arquivo.txt

Exemplo:

    sed 's/Linux/Unix/' arquivo.txt

Substitui a **primeira ocorrência de cada linha**.

---

### `g` — Global — global/todas as ocorrências

Para substituir todas as ocorrências da linha:

    sed 's/Linux/Unix/g' arquivo.txt

Sem `g`:

    Linux Linux Linux

Pode resultar em:

    Unix Linux Linux

Com `g`:

    Unix Unix Unix

---

### `-i` — In-place — alterar no próprio arquivo

Para modificar o arquivo original:

    sed -i 's/Linux/Unix/g' arquivo.txt

**Cuidado:** `-i` altera o arquivo diretamente.

Uma forma mais segura é criar uma cópia de backup:

    sed -i.bak 's/Linux/Unix/g' arquivo.txt

Nesse caso, o `sed` cria:

    arquivo.txt
    arquivo.txt.bak

---

## `d` — Delete — excluir

Remove linhas da saída.

Remover a primeira linha:

    sed '1d' arquivo.txt

Remover a segunda linha:

    sed '2d' arquivo.txt

Remover da linha 2 até a 4:

    sed '2,4d' arquivo.txt

---

### Remover linhas vazias

    sed '/^$/d' arquivo.txt

Aqui:

    ^ → início da linha
    $ → fim da linha

`^$` representa uma linha vazia.

---

## `p` — Print — imprimir

O `sed` já imprime as linhas normalmente.

Para imprimir uma linha específica:

    sed -n '5p' arquivo.txt

`-n` — quiet/silent — não imprimir automaticamente.

Assim, apenas a linha selecionada será exibida.

---

### Imprimir um intervalo

    sed -n '5,10p' arquivo.txt

Mostra as linhas 5 até 10.

---

## `-n` — No automatic print — não imprimir automaticamente

Exemplo:

    sed -n '1,5p' arquivo.txt

Mostra somente as linhas 1 a 5.

Sem `-n`, o `sed` normalmente imprime também as linhas que não foram selecionadas.

---

## `a` — Append — adicionar depois

Adiciona texto **depois** de uma linha.

    sed '2a\Nova linha' arquivo.txt

Adiciona `Nova linha` depois da linha 2.

---

## `i` — Insert — inserir antes

Insere texto **antes** de uma linha.

    sed '2i\Nova linha' arquivo.txt

---

## `c` — Change — substituir uma linha

Substitui uma linha inteira.

    sed '2c\Nova linha' arquivo.txt

A linha 2 será substituída por `Nova linha`.

---

## `sed` com expressões regulares

O `sed` trabalha muito bem com **Regular Expressions (Regex) — Expressões Regulares**.

Exemplo:

    sed 's/^root/ROOT/' arquivo.txt

Procura `root` no início da linha e substitui por `ROOT`.

Outro exemplo:

    sed 's/bash$/BASH/' arquivo.txt

Procura `bash` no final da linha.

---

## Delimitadores

O `/` é normalmente usado na substituição:

    sed 's/antigo/novo/g' arquivo.txt

Mas podemos usar outro delimitador:

    sed 's#antigo#novo#g' arquivo.txt

Isso é útil quando o texto contém `/`, como caminhos:

    sed 's#/home/laerte#/home/usuario#g' arquivo.txt

---

## Exemplos práticos

Substituir uma palavra:

    sed 's/erro/ERROR/' log.txt

Substituir todas:

    sed 's/erro/ERROR/g' log.txt

Mostrar somente as linhas 10 a 20:

    sed -n '10,20p' log.txt

Remover linhas vazias:

    sed '/^$/d' arquivo.txt

Remover comentários iniciados por `#`:

    sed '/^#/d' arquivo.txt

Alterar o arquivo original:

    sed -i 's/antigo/novo/g' arquivo.txt

---

## Resumo LPIC-1

| Comando | Função |
|---|---|
| `sed 's/a/b/'` | substituir primeira ocorrência |
| `sed 's/a/b/g'` | substituir todas as ocorrências |
| `sed -i` | alterar o arquivo original |
| `sed '1d'` | remover a linha 1 |
| `sed '2,4d'` | remover linhas 2 a 4 |
| `sed -n '5p'` | mostrar a linha 5 |
| `sed -n '5,10p'` | mostrar linhas 5 a 10 |
| `sed '2a\texto'` | adicionar depois da linha 2 |
| `sed '2i\texto'` | inserir antes da linha 2 |
| `sed '2c\texto'` | substituir a linha 2 |

**Memorize principalmente:**

    sed → Stream Editor → Editor de Fluxo

    s → substitute → substituir
    d → delete → excluir
    p → print → imprimir
    a → append → adicionar depois
    i → insert → inserir antes
    c → change → alterar
    g → global → todas as ocorrências
    -n → não imprimir automaticamente
    -i → alterar o arquivo original

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
