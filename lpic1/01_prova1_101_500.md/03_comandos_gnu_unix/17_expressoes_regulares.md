Expressões Regulares

Regular Expression — Expressão Regular

Uma Regular Expression (Expressão Regular) é uma forma de procurar padrões em textos.

No LPIC-1, o mais importante é entender como usar padrões com o "grep".

---

"grep"

O "grep" procura texto dentro de arquivos.

grep "Linux" arquivo.txt

→ Mostra as linhas que contêm "Linux".

---

"^" — Start of Line (Início da Linha)

Procura um texto no início da linha.

grep "^Linux" arquivo.txt

Encontra:

Linux é um sistema operacional
Linux permite usar comandos

Mas não:

Eu uso Linux

---

"$" — End of Line (Fim da Linha)

Procura um texto no final da linha.

grep "Linux$" arquivo.txt

Encontra:

Eu estudo Linux
Eu uso Linux

---

"." — Any Character (Qualquer Caractere)

O ponto representa qualquer caractere.

grep "L.nux" arquivo.txt

Pode encontrar:

Linux
Lanux
Lenux

---

"*" — Zero or More (Zero ou Mais)

Indica que o caractere ou padrão anterior pode aparecer zero ou mais vezes.

grep "ab*c" arquivo.txt

Pode encontrar:

ac
abc
abbc
abbbc

---

"[]" — Character Set (Conjunto de Caracteres)

Define quais caracteres podem aparecer naquela posição.

grep "gr[ae]y" arquivo.txt

Pode encontrar:

gray
grey

---

"[^]" — Not These Characters (Exceto Estes Caracteres)

Dentro de "[]", o "^" no início significa que aqueles caracteres não devem aparecer.

grep "gr[^ae]y" arquivo.txt

---

"grep -E"

"-E" — Extended Regular Expression (Expressão Regular Estendida)

Permite usar recursos adicionais de expressões regulares.

grep -E "Linux|Unix" arquivo.txt

"|" — OR (OU)

Procura "Linux" ou "Unix".

---

Exemplo prático

Imagine:

Linux
Unix
Windows
Linux Mint

Com:

grep "^Linux" sistemas.txt

Resultado:

Linux
Linux Mint

O "^" diz:

"Linux precisa estar no início da linha"

---

LPIC-1 — O que saber

^       → início da linha
$       → fim da linha
.       → qualquer caractere
*       → zero ou mais
[]      → conjunto de caracteres
[^]     → exceto os caracteres
|       → OU

E:

-E → Extended Regular Expression

---

Resumo

grep
 ↓
procura padrões em texto

^     → início
$     → fim
.     → qualquer caractere
*     → zero ou mais
[]    → conjunto
[^]   → exceto
|     → OU

Exemplo para memorizar

grep -E "^Linux|Unix$" arquivo.txt

→ procura linhas que começam com "Linux" ou terminam com "Unix".
