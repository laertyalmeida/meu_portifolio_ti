Expressões Regulares — Regular Expressions

As Expressões Regulares, também chamadas de Regex, são usadas para procurar padrões dentro de textos.

Elas são muito importantes no Linux e aparecem em ferramentas como:

- "grep"
- "sed"
- "awk"

A ideia principal é:

texto
 ↓
padrão
 ↓
encontrar o que corresponde

---

"Regex" — Regular Expression

Regular Expression → Expressão Regular

Uma expressão regular descreve um padrão de texto.

Por exemplo:

grep 'Linux' arquivo.txt

→ procura o texto Linux.

---

"." — Qualquer Caractere

O ponto "." representa qualquer caractere, normalmente exceto uma quebra de linha.

Exemplo:

grep 'c.sa' arquivo.txt

Pode encontrar:

casa
cosa
cisa

Porque:

c . s a
  ↑
qualquer caractere

---

"^" — Início da Linha

O símbolo "^" significa:

Início da linha

Exemplo:

grep '^Linux' arquivo.txt

→ encontra linhas que começam com "Linux".

Exemplo:

Linux é livre
Linux é poderoso
Eu estudo Linux

Resultado:

Linux é livre
Linux é poderoso

---

"$" — Final da Linha

O símbolo "$" significa:

Final da linha

Exemplo:

grep 'Linux$' arquivo.txt

→ encontra linhas que terminam com "Linux".

Exemplo:

Eu estudo Linux
Linux é livre
Hoje estudo Linux

Resultado:

Eu estudo Linux
Hoje estudo Linux

---

"[]" — Conjunto de Caracteres

Os colchetes "[]" representam um conjunto de caracteres possíveis.

Exemplo:

grep '[abc]' arquivo.txt

→ procura linhas que contenham:

a
b
ou
c

Outro exemplo:

grep '[0-9]' arquivo.txt

→ procura um dígito de 0 a 9.

---

"[^]" — Negação

Dentro de "[]", o símbolo "^" pode significar negação.

Exemplo:

grep '[^0-9]' arquivo.txt

→ procura um caractere que não seja um número.

⚠️ Atenção:

^Linux

→ início da linha.

[^0-9]

→ qualquer caractere que não seja de 0 a 9.

O significado depende da posição do "^".

---

"*" — Zero ou Mais

O "*" significa:

zero ou mais ocorrências do elemento anterior.

Exemplo:

grep 'ab*' arquivo.txt

Pode encontrar:

a
ab
abb
abbb

Porque o "b" pode aparecer:

0 vezes
1 vez
2 vezes
3 vezes
...

---

"?" — Zero ou Uma Ocorrência

O "?" significa:

zero ou uma ocorrência.

⚠️ Em ferramentas como "grep", seu uso depende do tipo de expressão regular utilizado. Para a LPIC-1, é importante reconhecer que existem diferenças entre BRE e ERE.

---

"+" — Uma ou Mais

O "+" significa:

uma ou mais ocorrências.

Exemplo com ERE:

grep -E 'ab+' arquivo.txt

Pode encontrar:

ab
abb
abbb

Mas não encontra apenas:

a

Porque é necessário ter pelo menos um "b".

---

"|" — OU

O símbolo "|" significa:

OU

Exemplo:

grep -E 'Linux|Unix' arquivo.txt

→ procura:

Linux
OU
Unix

---

Principais Metacaracteres

.      → qualquer caractere
^      → início da linha
$      → final da linha
[]     → conjunto de caracteres
[^]    → negação dentro de conjunto
*      → zero ou mais
+      → uma ou mais
?      → zero ou uma
|      → OU

---

🧠 Para a LPIC-1

Memorize principalmente:

^ → começo
$ → fim
. → qualquer caractere
[] → conjunto
* → zero ou mais
+ → uma ou mais
| → OU

Exemplos rápidos:

grep '^Linux' arquivo.txt

→ começa com Linux

grep 'Linux$' arquivo.txt

→ termina com Linux

grep '[0-9]' arquivo.txt

→ contém um número

grep -E 'Linux|Unix' arquivo.txt

→ contém Linux OU Unix

---

Regra para memorizar

Regex
 ↓
descreve um padrão
 ↓
a ferramenta procura esse padrão
 ↓
encontra o texto correspondente

📌 Resumo

Expressões regulares não procuram apenas palavras.

Elas permitem procurar padrões dentro de textos.

Por isso são muito usadas com:

grep
sed
awk
