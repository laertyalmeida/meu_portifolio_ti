# 03 — chmod

## chmod — Change Mode (Alterar Permissões)

O comando `chmod` altera as **permissões** de arquivos e diretórios.

    chmod [opções] permissões arquivo

---

## 1. Forma simbólica

Usa letras para definir as permissões.

| Símbolo | Inglês | Português |
|---|---|---|
| `u` | user | usuário/dono |
| `g` | group | grupo |
| `o` | others | outros |
| `a` | all | todos |

### Operadores

| Operador | Inglês | Português |
|---|---|---|
| `+` | add | adicionar |
| `-` | remove | remover |
| `=` | assign | definir exatamente |

### Exemplos

    chmod u+x script.sh

Adiciona `x` — execute (execução) ao dono.

    chmod g-w arquivo.txt

Remove `w` — write (escrita) do grupo.

    chmod o-r arquivo.txt

Remove `r` — read (leitura) de outros.

    chmod a+x script.sh

Adiciona execução para todos.

---

## 2. Forma numérica

As permissões possuem valores:

| Permissão | Valor |
|---|---:|
| `r` — read (leitura) | 4 |
| `w` — write (escrita) | 2 |
| `x` — execute (execução) | 1 |

Somamos os valores:

    r = 4
    w = 2
    x = 1

### Exemplos

`7 = 4 + 2 + 1`

    rwx = 7

`6 = 4 + 2`

    rw- = 6

`5 = 4 + 1`

    r-x = 5

`4 = 4`

    r-- = 4

---

## 3. Exemplos práticos

    chmod 755 script.sh

Resultado:

    rwx r-x r-x
    7   5   5

**Dono:** leitura, escrita e execução  
**Grupo:** leitura e execução  
**Outros:** leitura e execução

---

    chmod 644 arquivo.txt

Resultado:

    rw- r-- r--
    6   4   4

**Dono:** leitura e escrita  
**Grupo:** somente leitura  
**Outros:** somente leitura

---

## 4. Alterar diretórios recursivamente

`-R` — recursive (recursivo)

    chmod -R 755 diretorio/

Aplica a alteração ao diretório e aos arquivos/subdiretórios dentro dele.

⚠️ Use `-R` com cuidado, pois pode alterar muitas permissões de uma só vez.

---

## 5. Verificar as permissões

    ls -l arquivo.txt

Exemplo:

    -rw-r--r-- 1 laerte users 120 arquivo.txt

As permissões são:

    rw- r-- r--
    │   │   └── Others — Outros
    │   └────── Group — Grupo
    └────────── User — Dono

---

## 6. LPIC-1 — O que lembrar

- `chmod` = alterar permissões.
- `u` = usuário/dono.
- `g` = grupo.
- `o` = outros.
- `a` = todos.
- `+` = adicionar.
- `-` = remover.
- `=` = definir.
- `r = 4`, `w = 2`, `x = 1`.
- `755` → `rwxr-xr-x`.
- `644` → `rw-r--r--`.
- `-R` = alteração recursiva.

### Resumo

    chmod 755 arquivo
    chmod 644 arquivo
    chmod u+x arquivo
    chmod g-w arquivo
    chmod o-r arquivo
    chmod -R 755 diretorio/

> **"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
