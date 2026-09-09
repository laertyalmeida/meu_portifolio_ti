# Comandos GNU/UNIX

## 06 — grep

`grep` — **Global Regular Expression Print** — localizar e exibir linhas que correspondem a um padrão.

É um dos comandos mais importantes do Linux para **pesquisar texto dentro de arquivos e saídas de comandos**.

---

### Uso básico

Pesquisar uma palavra:

    grep "Linux" arquivo.txt

O `grep` mostra as linhas que contêm `Linux`.

Pesquisar em vários arquivos:

    grep "Linux" arquivo1.txt arquivo2.txt

---

### Opções principais

| Opção | Inglês | Português |
|---|---|---|
| `-i` | ignore case | ignorar maiúsculas/minúsculas |
| `-v` | invert match | mostrar linhas que **não** correspondem |
| `-n` | line number | mostrar número da linha |
| `-r` | recursive | pesquisar recursivamente |
| `-l` | files with matches | mostrar apenas nomes dos arquivos encontrados |
| `-c` | count | contar ocorrências/linhas correspondentes |
| `-w` | word | procurar palavra inteira |
| `-E` | extended regexp | usar expressões regulares estendidas |
| `-A` | after context | mostrar linhas depois da correspondência |
| `-B` | before context | mostrar linhas antes da correspondência |
| `-C` | context | mostrar linhas antes e depois |

---

### `-i` — Ignore Case — ignorar maiúsculas/minúsculas

    grep -i "linux" arquivo.txt

Encontra:

    Linux
    linux
    LINUX
    LiNuX

---

### `-n` — Line Number — número da linha

    grep -n "Linux" arquivo.txt

Mostra a linha onde o texto foi encontrado.

---

### `-v` — Invert Match — inverter correspondência

Mostra as linhas que **não contêm** o padrão.

    grep -v "Linux" arquivo.txt

---

### `-w` — Word — palavra inteira

    grep -w "root" arquivo.txt

Procura `root` como palavra inteira, evitando correspondências como:

    root
    root123
    myroot

---

### `-r` — Recursive — recursivo

Pesquisa dentro de diretórios e seus subdiretórios.

    grep -r "Linux" /etc

Muito útil para procurar uma configuração em vários arquivos.

---

### `-l` — Files with Matches — arquivos com correspondência

Mostra somente os nomes dos arquivos que contêm o padrão.

    grep -l "Linux" *.txt

---

### `-c` — Count — contar

Conta quantas linhas correspondem ao padrão.

    grep -c "Linux" arquivo.txt

---

### `-E` — Extended Regular Expression — expressão regular estendida

Permite utilizar recursos de **expressões regulares estendidas**.

    grep -E "Linux|Unix" arquivo.txt

Procura `Linux` **ou** `Unix`.

Também pode ser usado como:

    egrep "Linux|Unix" arquivo.txt

Para LPIC-1, prefira conhecer `grep -E`.

---

### `grep` com `|` — Pipe — canal

O `grep` é frequentemente usado com **pipes** para pesquisar a saída de outro comando.

    ps aux | grep "bash"

Aqui:

    ps aux → mostra processos
    |      → envia a saída para o próximo comando
    grep   → procura "bash"

Outro exemplo:

    ls -l /etc | grep "conf"

---

### `grep` com expressões regulares

O `grep` pode procurar padrões, não apenas palavras.

Exemplo:

    grep "^root" /etc/passwd

`^` — início da linha.

Procura linhas que começam com `root`.

Outro exemplo:

    grep "bash$" /etc/passwd

`$` — fim da linha.

Procura linhas que terminam com `bash`.

---

### `grep` e arquivos de configuração

Exemplo:

    grep "PermitRootLogin" /etc/ssh/sshd_config

Podemos ignorar linhas comentadas:

    grep -v "^#" /etc/ssh/sshd_config

E também ignorar linhas vazias:

    grep -v "^#" /etc/ssh/sshd_config | grep -v "^$"

---

### `grep` com contexto

Mostrar 2 linhas depois:

    grep -A 2 "Linux" arquivo.txt

Mostrar 2 linhas antes:

    grep -B 2 "Linux" arquivo.txt

Mostrar 2 linhas antes e depois:

    grep -C 2 "Linux" arquivo.txt

---

## Exemplos práticos

Pesquisar usuários:

    grep "root" /etc/passwd

Pesquisar sem diferenciar maiúsculas/minúsculas:

    grep -i "error" log.txt

Mostrar números das linhas:

    grep -n "error" log.txt

Pesquisar recursivamente:

    grep -r "localhost" /etc

Pesquisar palavra inteira:

    grep -w "root" arquivo.txt

Pesquisar duas possibilidades:

    grep -E "Linux|Unix" arquivo.txt

Pesquisar na saída de um comando:

    ps aux | grep "bash"

---

## Resumo LPIC-1

| Comando | Função |
|---|---|
| `grep "texto" arquivo` | procurar texto |
| `grep -i` | ignorar maiúsculas/minúsculas |
| `grep -v` | inverter a busca |
| `grep -n` | mostrar número da linha |
| `grep -r` | pesquisar recursivamente |
| `grep -l` | mostrar nomes dos arquivos |
| `grep -c` | contar correspondências |
| `grep -w` | procurar palavra inteira |
| `grep -E` | usar expressões regulares estendidas |
| `grep -A` | mostrar linhas depois |
| `grep -B` | mostrar linhas antes |
| `grep -C` | mostrar contexto |
| `\|` | enviar saída para outro comando |

**Memorize principalmente:**

    grep      → pesquisar texto
    grep -i   → ignorar maiúsculas/minúsculas
    grep -n   → mostrar número da linha
    grep -v   → mostrar o que NÃO corresponde
    grep -r   → pesquisar recursivamente
    grep -w   → palavra inteira
    grep -E   → expressão regular estendida

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
