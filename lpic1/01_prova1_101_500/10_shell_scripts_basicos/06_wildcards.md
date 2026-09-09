# 10 — Shell e Scripts Básicos

## 06 — Wildcards

**Wildcard — Coringa**

Wildcards são caracteres especiais usados pelo Bash para representar **padrões de nomes de arquivos e diretórios**.

Eles são muito usados com comandos como:

    ls
    cp
    mv
    rm

Os principais são:

| Wildcard | English | Português | Significado |
|---|---|---|---|
| `*` | Asterisk | Asterisco | Zero ou mais caracteres |
| `?` | Question Mark | Ponto de Interrogação | Exatamente um caractere |
| `[...]` | Character Class | Classe de Caracteres | Um caractere dentro da lista |
| `[!...]` | Negated Character Class | Classe Negada | Um caractere que não esteja na lista |

---

### 1. `*` — Asterisk

Representa **zero ou mais caracteres**.

Exemplo:

    ls *.txt

Encontra arquivos como:

    arquivo.txt
    teste.txt
    documento.txt

Também pode aparecer no início:

    ls *.conf

Ou no meio:

    ls arquivo*.txt

Pode encontrar:

    arquivo.txt
    arquivo1.txt
    arquivo-backup.txt

---

### 2. `?` — Question Mark

Representa **exatamente um caractere**.

Exemplo:

    ls arquivo?.txt

Pode encontrar:

    arquivo1.txt
    arquivo2.txt

Mas não:

    arquivo10.txt

Porque `??` seria necessário para representar dois caracteres:

    ls arquivo??.txt

---

### 3. `[...]` — Character Class

Representa **um único caractere escolhido entre os caracteres especificados**.

Exemplo:

    ls arquivo[123].txt

Pode encontrar:

    arquivo1.txt
    arquivo2.txt
    arquivo3.txt

Mas não:

    arquivo4.txt

Também podemos usar intervalos:

    ls arquivo[1-5].txt

Encontra:

    arquivo1.txt
    arquivo2.txt
    arquivo3.txt
    arquivo4.txt
    arquivo5.txt

---

### 4. `[!...]` — Negated Character Class

Representa um caractere que **não esteja** na lista.

Exemplo:

    ls arquivo[!0-9].txt

Procura nomes em que o caractere naquela posição não seja um número.

Em Bash também é comum:

    [^...]

O significado de negação em padrões de nome pode variar conforme o contexto; no Bash, `[!...]` é a forma tradicional e clara para negação.

---

### 5. Diferença entre `*` e `?`

Imagine:

    arquivo1.txt
    arquivo12.txt
    arquivo123.txt

Com:

    ls arquivo?.txt

Somente:

    arquivo1.txt

Com:

    ls arquivo*.txt

Os três podem ser encontrados.

**`?` = um caractere**

**`*` = zero ou mais caracteres**

---

### 6. Wildcards não são Regex

**Filename Expansion — Expansão de Nomes de Arquivos**

Wildcards são usados pelo Shell para encontrar nomes de arquivos.

Exemplo:

    ls *.log

Já **Regex — Regular Expression — Expressão Regular** é usada para encontrar padrões dentro de textos.

Exemplo:

    grep '^root' /etc/passwd

Não confunda:

    *.txt

com:

    .*\.txt$

São mecanismos diferentes.

---

### 7. `*` não inclui arquivos ocultos normalmente

Arquivos ocultos começam com `.`.

Exemplo:

    .bashrc
    .profile
    .config

O comando:

    ls *

normalmente não inclui esses arquivos.

Para listar arquivos ocultos:

    ls -a

- `-a` — All — Todos, incluindo ocultos.

Para usar um padrão específico para ocultos:

    ls .*

**Cuidado:** `.*` também pode corresponder a `.` e `..` em determinados contextos/comandos. Por isso, não use padrões amplos com `rm` sem entender exatamente o que será expandido.

---

### 8. Expansão acontece antes do comando

Quando você executa:

    ls *.txt

O Bash primeiro expande `*.txt` para os arquivos correspondentes.

Por exemplo:

    ls arquivo1.txt arquivo2.txt arquivo3.txt

Depois o `ls` recebe esses nomes.

Isso significa que o `*` é interpretado pelo **Shell**, não pelo `ls`.

---

### 9. Verificar a expansão

Podemos usar `echo`:

    echo *.txt

Se existirem:

    teste.txt
    arquivo.txt

O resultado será:

    teste.txt arquivo.txt

O Bash fez a expansão antes de executar o `echo`.

---

## Resumo LPIC-1

- **Wildcard** = caractere coringa usado para padrões de nomes.
- `*` = zero ou mais caracteres.
- `?` = exatamente um caractere.
- `[abc]` = um caractere entre `a`, `b` ou `c`.
- `[1-5]` = um caractere entre `1` e `5`.
- `[!0-9]` = um caractere que não seja de `0` a `9`.
- Arquivos ocultos não são incluídos normalmente por `*`.
- Wildcards são diferentes de **Regex**.
- O Bash faz a expansão do padrão antes de executar o comando.
- `echo *.txt` é uma forma simples de visualizar a expansão.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
