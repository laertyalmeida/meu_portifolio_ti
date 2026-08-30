Processamento de Texto

No Linux, muitos comandos trabalham diretamente com texto. Isso permite filtrar, organizar e transformar informações rapidamente.

---

"sort" — Sort (Ordenar)

Organiza as linhas de um arquivo.

sort nomes.txt

Por padrão, ordena em ordem alfabética.

"-r" — Reverse (Inverso)

Inverte a ordem.

sort -r nomes.txt

---

"uniq" — Unique (Único)

Remove linhas repetidas que estejam uma ao lado da outra.

uniq nomes.txt

Para funcionar corretamente em muitos casos, primeiro usamos "sort":

sort nomes.txt | uniq

---

"cut" — Cut (Cortar)

Extrai partes de cada linha.

Exemplo:

cut -d: -f1 /etc/passwd

"-d" — Delimiter (Delimitador)

Define qual caractere separa os campos.

Aqui usamos:

:

"-f" — Field (Campo)

Define qual campo queremos mostrar.

-f1

→ primeiro campo.

---

"tr" — Translate (Traduzir)

Substitui ou transforma caracteres.

echo "linux" | tr 'a-z' 'A-Z'

Resultado:

LINUX

---

"sed" — Stream Editor (Editor de Fluxo)

Permite modificar texto enquanto ele passa pelo comando.

Exemplo:

sed 's/linux/Linux/' arquivo.txt

Nesse exemplo:

s → Substitute (Substituir)

O "sed" substitui a primeira ocorrência encontrada em cada linha.

---

"awk" — Linguagem de Processamento de Texto

O "awk" é usado para trabalhar com dados organizados em linhas e campos.

Exemplo:

awk '{print $1}' arquivo.txt

"print" — Print (Imprimir)

Mostra o conteúdo solicitado.

"$1" — Primeiro campo

Representa o primeiro campo da linha.

---

Exemplo com Pipe

Podemos combinar vários comandos:

cat nomes.txt | sort | uniq

Funcionamento:

cat
 ↓
mostra o arquivo
 ↓
sort
 ↓
ordena
 ↓
uniq
 ↓
remove repetições consecutivas

---

LPIC-1 — O que saber

- "sort" ordena linhas.
- "uniq" remove repetições consecutivas.
- "cut" extrai campos.
- "tr" transforma caracteres.
- "sed" modifica texto.
- "awk" trabalha com campos e texto.
- "|" permite combinar comandos.
- "-r" = Reverse (Inverso).
- "-d" = Delimiter (Delimitador).
- "-f" = Field (Campo).
- "s" no "sed" = Substitute (Substituir).

---

Resumo

sort → ordenar
uniq → remover repetições
cut  → cortar/extrair campos
tr   → transformar caracteres
sed  → modificar texto
awk  → trabalhar com campos

Principais opções

-r → Reverse (Inverso)
-d → Delimiter (Delimitador)
-f → Field (Campo)
