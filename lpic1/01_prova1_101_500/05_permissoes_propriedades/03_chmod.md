# Permissões e Propriedade

## 03 — chmod

### 1. O que é `chmod`

**chmod** — *Change Mode* — **Alterar Permissões**

É usado para alterar as permissões de arquivos e diretórios.

Sintaxe:

    chmod permissões arquivo

Exemplo:

    chmod 755 script.sh

---

### 2. Permissões numéricas

Os valores são:

| Permissão | English | Português | Valor |
|---|---|---|---:|
| `r` | Read | Leitura | 4 |
| `w` | Write | Escrita | 2 |
| `x` | Execute | Execução | 1 |

Somamos os valores:

    rwx = 4 + 2 + 1 = 7
    rw- = 4 + 2 + 0 = 6
    r-x = 4 + 0 + 1 = 5
    r-- = 4 + 0 + 0 = 4

---

### 3. Exemplos numéricos

    chmod 755 script.sh

Resultado:

    rwxr-xr-x

    Dono   → rwx
    Grupo  → r-x
    Outros → r-x

Outro exemplo:

    chmod 644 arquivo.txt

Resultado:

    rw-r--r--

    Dono   → rw-
    Grupo  → r--
    Outros → r--

---

### 4. Modo simbólico

Também podemos usar letras.

**u** — *User/Owner* — **Usuário/Dono**

**g** — *Group* — **Grupo**

**o** — *Others* — **Outros**

**a** — *All* — **Todos**

Operadores:

| Operador | English | Português |
|---|---|---|
| `+` | add | adicionar |
| `-` | remove | remover |
| `=` | assign | definir exatamente |

Exemplos:

    chmod u+x script.sh

Adiciona execução para o dono.

    chmod g+w arquivo.txt

Adiciona escrita para o grupo.

    chmod o-r arquivo.txt

Remove leitura de outros.

    chmod a+x script.sh

Adiciona execução para todos.

---

### 5. Definir permissões com `=`

Podemos definir exatamente as permissões:

    chmod u=rwx arquivo
    chmod g=rx arquivo
    chmod o=r arquivo

Também podemos fazer tudo de uma vez:

    chmod u=rwx,g=rx,o=r arquivo

Resultado:

    rwxr-xr--

---

### 6. Alterar permissões recursivamente

**`-R`** — *Recursive* — **Recursivo**

Aplica a alteração ao diretório e ao seu conteúdo.

    chmod -R 755 diretorio/

Exemplo:

    chmod -R 644 documentos/

> Cuidado com `-R`: aplicar a mesma permissão indiscriminadamente a todos os arquivos e diretórios pode causar problemas.

---

### 7. Verificar as permissões

Use:

    ls -l arquivo.txt

Exemplo:

    -rw-r--r-- 1 laerte alunos 1200 arquivo.txt

Depois:

    chmod 600 arquivo.txt

Verificando:

    ls -l arquivo.txt

Resultado esperado:

    -rw------- 1 laerte alunos 1200 arquivo.txt

---

### 8. `chmod` em diretórios

As permissões têm significado diferente em diretórios.

Exemplo:

    chmod 755 projetos/

Resultado:

    drwxr-xr-x

Interpretação:

    Dono   → rwx
    Grupo  → r-x
    Outros → r-x

Para um diretório:

    r → listar conteúdo
    w → criar, remover e renomear entradas
    x → acessar/atravessar

---

### 9. `chmod` com `sudo`

Se você não for o proprietário ou não tiver permissão suficiente:

    sudo chmod 644 arquivo.txt

O `sudo` executa o comando com privilégios administrativos, conforme a configuração do sistema.

---

## Resumo LPIC-1

- `chmod` → **Change Mode — Alterar Permissões**.
- Altera permissões de arquivos e diretórios.
- `r = 4` → leitura.
- `w = 2` → escrita.
- `x = 1` → execução.
- `u` → dono.
- `g` → grupo.
- `o` → outros.
- `a` → todos.
- `+` → adiciona.
- `-` → remove.
- `=` → define.
- `-R` → recursivo.
- `chmod 755 arquivo` → `rwxr-xr-x`.
- `chmod 644 arquivo` → `rw-r--r--`.
- `chmod u+x arquivo` → adiciona execução ao dono.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
