# 10 — Shell e Scripts Básicos
## 06 — Wildcards

### Wildcards — Caracteres coringa

**Wildcards** são caracteres usados pelo Bash para representar padrões de nomes de arquivos e diretórios.

Os principais são:

| Wildcard | Significado |
|---|---|
| `*` | Qualquer quantidade de caracteres |
| `?` | Exatamente um caractere |
| `[ ]` | Um caractere entre as opções |

---

## 1. Asterisco `*`

Representa qualquer quantidade de caracteres.

Listar todos os arquivos `.txt`:

    ls *.txt

Exemplos encontrados:

    notas.txt
    estudo.txt
    comandos.txt

Outro exemplo:

    ls arquivo*

Pode encontrar:

    arquivo.txt
    arquivo.md
    arquivo1

---

## 2. Interrogação `?`

Representa **um único caractere**.

    ls arquivo?.txt

Pode encontrar:

    arquivo1.txt
    arquivo2.txt

Mas não:

    arquivo10.txt

---

## 3. Colchetes `[ ]`

Representam uma opção entre os caracteres indicados.

    ls arquivo[123].txt

Pode encontrar:

    arquivo1.txt
    arquivo2.txt
    arquivo3.txt

---

## 4. Faixa de caracteres

Podemos usar `-` para indicar uma faixa.

    ls arquivo[1-5].txt

Encontra:

    arquivo1.txt
    arquivo2.txt
    arquivo3.txt
    arquivo4.txt
    arquivo5.txt

---

## 5. Combinação

Os padrões podem ser combinados.

    ls *.log

→ todos os arquivos terminados em `.log`.

    ls backup?.tar

→ `backup` + um caractere + `.tar`.

    ls [a-c]*

→ nomes começando com `a`, `b` ou `c`.

---

## 🎯 Para a LPIC-1

    *       → qualquer quantidade
    ?       → um caractere
    [abc]   → a, b ou c
    [0-9]   → números de 0 a 9

Exemplo:

    rm *.tmp

→ remove arquivos que correspondem ao padrão `*.tmp`.

**Wildcards são expandidos pelo Bash antes do comando ser executado.**

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
