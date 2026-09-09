# Permissões e Propriedade

## 02 — Permissões rwx

### 1. O que são permissões?

**Permissions** — **Permissões**

As permissões determinam o que cada usuário pode fazer com um arquivo ou diretório.

As três permissões básicas são:

| Permissão | English | Português |
|---|---|---|
| `r` | Read | Ler |
| `w` | Write | Escrever |
| `x` | Execute | Executar |

---

### 2. As três classes

As permissões são aplicadas a:

| Classe | English | Português |
|---|---|---|
| `u` | User/Owner | Usuário/Dono |
| `g` | Group | Grupo |
| `o` | Others | Outros |

Exemplo:

    -rwxr-xr--

Separando:

    rwx | r-x | r--
     u  |  g  |  o

Interpretação:

    Dono   → rwx → ler, escrever e executar
    Grupo  → r-x → ler e executar
    Outros → r-- → somente ler

---

### 3. Permissão `r`

**Read** — **Leitura**

Para um arquivo:

    r → permite ler o conteúdo.

Exemplo:

    cat arquivo.txt

Sem `r`, o usuário não consegue ler o conteúdo normalmente.

Para um diretório:

    r → permite listar seus nomes.

Exemplo:

    ls diretorio

---

### 4. Permissão `w`

**Write** — **Escrita**

Para um arquivo:

    w → permite alterar o conteúdo.

Para um diretório:

    w → permite criar, remover e renomear entradas dentro dele, desde que as demais condições de acesso sejam atendidas.

---

### 5. Permissão `x`

**Execute** — **Execução**

Para um arquivo:

    x → permite executar o arquivo como programa/script, quando aplicável.

Para um diretório:

    x → permite acessar/atravessar o diretório.

Exemplo:

    cd diretorio

> Em diretórios, `x` não significa "executar o diretório". Significa poder atravessá-lo/acessá-lo.

---

### 6. Visualizar permissões

Use:

    ls -l

Exemplo:

    -rwxr-xr-- 1 laerte alunos 1200 script.sh

As permissões são:

    -rwxr-xr--

    -    → tipo
    rwx  → dono
    r-x  → grupo
    r--  → outros

---

### 7. Tipo de arquivo

O primeiro caractere não é uma permissão.

Exemplos:

    - → arquivo regular
    d → diretório
    l → link simbólico

Exemplo:

    drwxr-xr-x

O `d` indica que é um diretório.

---

### 8. Permissões numéricas

As permissões também podem ser representadas por números:

| Permissão | Valor |
|---|---:|
| `r` | 4 |
| `w` | 2 |
| `x` | 1 |
| `-` | 0 |

Somamos os valores:

    rwx = 4 + 2 + 1 = 7
    rw- = 4 + 2 + 0 = 6
    r-x = 4 + 0 + 1 = 5
    r-- = 4 + 0 + 0 = 4

---

### 9. Exemplo `755`

    755

Separando:

    7 | 5 | 5
    u | g | o

    7 → rwx
    5 → r-x
    5 → r-x

Resultado:

    rwxr-xr-x

Ou:

    Dono   → rwx
    Grupo  → r-x
    Outros → r-x

---

### 10. Exemplo `644`

    644

    6 → rw-
    4 → r--
    4 → r--

Resultado:

    rw-r--r--

Muito comum para arquivos de texto:

    Dono   → leitura + escrita
    Grupo  → leitura
    Outros → leitura

---

## Resumo LPIC-1

- `r` → **Read — Leitura** → valor `4`.
- `w` → **Write — Escrita** → valor `2`.
- `x` → **Execute — Execução** → valor `1`.
- `u` → dono.
- `g` → grupo.
- `o` → outros.
- `rwx` → `7`.
- `rw-` → `6`.
- `r-x` → `5`.
- `r--` → `4`.
- `ls -l` → visualizar permissões, dono e grupo.
- Em **arquivos**, `r/w/x` significam leitura/escrita/execução.
- Em **diretórios**, `r/w/x` têm significados relacionados à listagem, alteração das entradas e acesso/atravessamento.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
