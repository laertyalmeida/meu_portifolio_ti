awk — Processamento de Texto

"awk" — Processamento de Texto por Campos

O "awk" é usado principalmente para ler texto dividido em campos e trabalhar com esses campos.

Ele é muito útil para arquivos organizados em colunas.

---

Exemplo

Imagine um arquivo:

joao 25 brasil
maria 30 portugal
carlos 22 brasil

Cada espaço separa um campo.

joao    25    brasil
  $1     $2      $3

No "awk":

$1 → primeiro campo
$2 → segundo campo
$3 → terceiro campo

---

Mostrar um campo

awk '{print $1}' pessoas.txt

"print" — Print (Mostrar)

Resultado:

joao
maria
carlos

Para mostrar o segundo campo:

awk '{print $2}' pessoas.txt

Resultado:

25
30
22

---

Mostrar vários campos

awk '{print $1, $3}' pessoas.txt

Resultado:

joao brasil
maria portugal
carlos brasil

---

"$0" — Whole Line (Linha Inteira)

O "$0" representa a linha inteira.

awk '{print $0}' pessoas.txt

Resultado:

joao 25 brasil
maria 30 portugal
carlos 22 brasil

---

"-F" — Field Separator (Separador de Campos)

Por padrão, o "awk" considera espaços como separadores.

Podemos escolher outro separador.

Imagine:

joao:25:brasil
maria:30:portugal

Podemos usar:

awk -F ':' '{print $1}' pessoas.txt

"-F"

-F → Field Separator → Separador de Campos

O ":" será usado para separar os campos.

---

"NF" — Number of Fields (Número de Campos)

"NF" informa quantos campos existem na linha.

awk '{print NF}' pessoas.txt

Se a linha tiver:

joao 25 brasil

o resultado será:

3

---

"NR" — Number of Records (Número do Registro/Linha)

"NR" mostra o número da linha que o "awk" está processando.

awk '{print NR, $1}' pessoas.txt

Resultado:

1 joao
2 maria
3 carlos

---

Condições

O "awk" também pode filtrar informações.

Exemplo:

awk '$2 > 25 {print $1}' pessoas.txt

Significa:

$2 > 25
↓
segundo campo maior que 25
↓
mostrar $1

Resultado:

maria

---

"BEGIN" e "END"

"BEGIN" — Antes (Antes de processar)

Executa antes de ler as linhas.

awk 'BEGIN {print "Pessoas"}' pessoas.txt

"END" — Depois (Depois de processar)

Executa depois de terminar.

awk 'END {print "Fim"}' pessoas.txt

Para a LPIC-1, é importante reconhecer esses dois.

---

Principais elementos

$0  → Whole Line → Linha inteira
$1  → primeiro campo
$2  → segundo campo
$3  → terceiro campo
NF  → Number of Fields → Número de campos
NR  → Number of Records → Número da linha

Principais flags

-F → Field Separator → Separador de Campos

---

🧠 Para a LPIC-1

Memorize:

awk '{print $1}' arquivo.txt

→ mostra o primeiro campo.

awk '{print $2}' arquivo.txt

→ mostra o segundo campo.

awk '{print $1, $3}' arquivo.txt

→ mostra o primeiro e o terceiro.

awk -F ':' '{print $1}' arquivo.txt

→ usa ":" como separador.

---

Regra simples

awk
 ↓
lê a linha
 ↓
separa em campos
 ↓
escolhe o que queremos
 ↓
mostra ou processa

Pense no "awk" como uma ferramenta para trabalhar com "colunas" de texto.
