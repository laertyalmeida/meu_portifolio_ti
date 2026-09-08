# 10 — Shell e Scripts Básicos
## 03 — Quoting

### Quoting — Uso de aspas

**Quoting** controla como o Bash interpreta caracteres especiais e variáveis.

Os principais tipos são:

- `' '` — aspas simples
- `" "` — aspas duplas
- `\` — escape

---

## 1. Aspas simples

**Single Quotes — Aspas simples**

Tudo dentro das aspas é tratado literalmente.

    nome="Laerte"
    echo '$nome'

Resultado:

    $nome

A variável **não é expandida**.

---

## 2. Aspas duplas

**Double Quotes — Aspas duplas**

Permitem a expansão de variáveis.

    nome="Laerte"
    echo "$nome"

Resultado:

    Laerte

Também preservam espaços:

    nome="Laerte Costa"
    echo "$nome"

---

## 3. Escape

**Escape Character — Caractere de escape**

A barra invertida `\` faz o Bash tratar o próximo caractere de forma literal.

Exemplo:

    echo "\$HOME"

Resultado:

    $HOME

Sem o escape:

    echo "$HOME"

O Bash expande o valor da variável.

---

## 4. Diferença principal

| Forma | Expande variável? |
|---|---|
| `'texto'` | Não |
| `"texto"` | Sim |
| `\` | Escapa o próximo caractere |

---

## 5. Exemplo prático

    nome="Linux"

    echo 'Sistema: $nome'
    echo "Sistema: $nome"

Resultado:

    Sistema: $nome
    Sistema: Linux

---

## 🎯 Para a LPIC-1

    '...'  → literal
    "..."  → permite expansão
    \      → escapa caractere

**Aspas simples** → não expandem variáveis.

**Aspas duplas** → expandem variáveis.

**Backslash (`\`)** → impede a interpretação do próximo caractere.

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa** 
