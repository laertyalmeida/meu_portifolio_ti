# Comandos GNU/UNIX

## 05 — Busca de Arquivos

No Linux, podemos procurar arquivos e diretórios pelo **nome**, **localização**, **tipo**, **tamanho**, **data** e outros critérios.

---

### `find` — Find — encontrar

É o principal comando para busca de arquivos e diretórios.

Sintaxe:

    find [localização] [critério]

Buscar pelo nome:

    find /home -name "arquivo.txt"

Buscar no diretório atual:

    find . -name "arquivo.txt"

`-name` — name — nome, diferencia maiúsculas de minúsculas.

Para ignorar diferença entre maiúsculas e minúsculas:

    find . -iname "arquivo.txt"

`-iname` — insensitive name — nome sem diferenciar maiúsculas/minúsculas.

---

### Buscar por tipo

`-type` — type — tipo.

Principais tipos:

| Tipo | Significado |
|---|---|
| `f` | file — arquivo comum |
| `d` | directory — diretório |
| `l` | link — link simbólico |

Exemplos:

    find /home -type f

    find /home -type d

    find /home -type l

---

### Buscar pelo tamanho

`-size` — size — tamanho.

Exemplo:

    find /home -type f -size +100M

Procura arquivos maiores que 100 MB.

Outros exemplos:

    find . -size +1G
    find . -size -10M

`+` — maior que  
`-` — menor que

---

### Buscar por usuário

`-user` — user — usuário/dono.

    find /home -user laerte

Busca arquivos pertencentes ao usuário informado.

---

### Buscar por grupo

`-group` — group — grupo.

    find /home -group alunos

---

### Buscar por data

`-mtime` — modification time — tempo desde a última modificação.

Exemplo:

    find . -mtime -1

Arquivos modificados nas últimas 24 horas.

    find . -mtime +7

Arquivos modificados há mais de 7 dias.

---

### `locate` — Locate — localizar

Procura arquivos usando uma **base de dados** previamente criada.

    locate arquivo.txt

É normalmente mais rápido que `find`, mas a base pode não estar atualizada.

Atualizar a base:

    sudo updatedb

---

### `which` — Which — qual/localização do comando

Mostra onde está o executável de um comando encontrado no `PATH`.

    which bash

    which ls

Exemplo:

    which python3

Pode retornar algo como:

    /usr/bin/python3

---

### `whereis` — Where Is — onde está

Procura informações relacionadas a um comando, como:

- executável;
- páginas de manual;
- código-fonte, quando disponível.

Exemplo:

    whereis bash

---

### `find` com ação

O `find` também pode executar uma ação sobre os resultados.

`-exec` — execute — executar.

Exemplo:

    find . -name "*.tmp" -exec rm {} \;

Significado:

    find        → procurar
    -name       → pelo nome
    "*.tmp"     → arquivos .tmp
    -exec       → executar comando
    rm          → remover
    {}          → arquivo encontrado
    \;          → fim do comando

**Cuidado:** comandos com `rm` podem apagar arquivos permanentemente.

---

## `find` × `locate`

| Comando | Característica |
|---|---|
| `find` | pesquisa diretamente no sistema de arquivos |
| `locate` | pesquisa em uma base de dados |
| `which` | encontra executáveis no `PATH` |
| `whereis` | procura executável, manuais e outros arquivos relacionados |

---

## Exemplos práticos

Buscar todos os arquivos `.conf`:

    find /etc -type f -name "*.conf"

Buscar diretórios chamados `backup`:

    find /home -type d -name "backup"

Buscar arquivos maiores que 500 MB:

    find /home -type f -size +500M

Buscar arquivos modificados nas últimas 24 horas:

    find /home -type f -mtime -1

Localizar o executável do Bash:

    which bash

Localizar informações sobre o Bash:

    whereis bash

---

## Resumo LPIC-1

| Comando/opção | Função |
|---|---|
| `find` | procurar arquivos e diretórios |
| `-name` | buscar pelo nome |
| `-iname` | buscar pelo nome ignorando maiúsculas/minúsculas |
| `-type` | buscar pelo tipo |
| `-size` | buscar pelo tamanho |
| `-user` | buscar pelo proprietário |
| `-group` | buscar pelo grupo |
| `-mtime` | buscar pela data de modificação |
| `-exec` | executar comando sobre resultados |
| `locate` | procurar usando uma base de dados |
| `updatedb` | atualizar a base do `locate` |
| `which` | localizar executável no `PATH` |
| `whereis` | localizar arquivos relacionados a um comando |

**Memorize principalmente:**

    find   → busca completa e flexível
    locate → busca rápida pela base de dados
    which  → onde está o comando
    whereis → onde estão os arquivos relacionados ao comando

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
