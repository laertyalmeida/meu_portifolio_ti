sed — Stream Editor

"sed" — Stream Editor (Editor de Fluxo)

O "sed" é usado para procurar, substituir, apagar e mostrar partes de texto.

Ele normalmente recebe um texto, faz uma alteração e mostra o resultado.

---

"s" — Substitute (Substituir)

A operação mais importante para a LPIC-1 é a substituição.

sed 's/Linux/Unix/' arquivo.txt

Significa:

s
↓
Substitute → Substituir

Linux
↓
Unix

---

Exemplo

Arquivo:

Linux é livre
Eu estudo Linux
Linux é poderoso

Com:

sed 's/Linux/Unix/' arquivo.txt

Resultado:

Unix é livre
Eu estudo Unix
Unix é poderoso

⚠️ Por padrão, o "sed" substitui apenas a primeira ocorrência de cada linha.

---

"g" — Global (Todas as Ocorrências)

Para substituir todas as ocorrências da linha:

sed 's/Linux/Unix/g' arquivo.txt

"g" — Global (Global/Todas)

Exemplo:

Linux Linux Linux

Resultado:

Unix Unix Unix

---

"-i" — In-Place (No Próprio Arquivo)

Normalmente, o "sed" mostra o resultado na tela e não altera o arquivo original.

Para alterar o arquivo:

sed -i 's/Linux/Unix/g' arquivo.txt

"-i" — In-Place (No Próprio Arquivo)

→ modifica o próprio "arquivo.txt".

---

"d" — Delete (Apagar)

Podemos apagar linhas.

sed '2d' arquivo.txt

"d" — Delete (Apagar)

→ apaga a linha 2 da saída.

Por padrão, o arquivo original não é alterado.

---

"$" — Last Line (Última Linha)

Podemos usar "$" para representar a última linha.

sed '$d' arquivo.txt

→ não mostra a última linha.

---

"p" — Print (Mostrar)

Podemos pedir para o "sed" mostrar uma linha.

sed -n '2p' arquivo.txt

"-n" — No Automatic Print (Não Mostrar Automaticamente)

Sem "-n", o "sed" normalmente mostra todas as linhas.

Com:

sed -n '2p' arquivo.txt

mostramos somente a linha 2.

"p" — Print (Mostrar)

p → Print → Mostrar

---

Intervalo de linhas

Podemos trabalhar com várias linhas.

sed -n '2,5p' arquivo.txt

→ mostra as linhas 2 até 5.

2 → início
5 → fim
p → mostrar

---

"sed" + Expressões Regulares

O "sed" também pode usar padrões.

sed -n '/Linux/p' arquivo.txt

→ mostra somente as linhas que contêm "Linux".

---

Principais comandos

s → Substitute → Substituir
d → Delete → Apagar
p → Print → Mostrar

Principais flags

-i → In-Place → Alterar o próprio arquivo
-n → No Automatic Print → Não mostrar automaticamente
g  → Global → Todas as ocorrências

---

🧠 Para a LPIC-1

Memorize este formato:

sed 's/ANTIGO/NOVO/' arquivo.txt

s      → substituir
ANTIGO → texto encontrado
NOVO   → texto novo

Para substituir todas:

sed 's/ANTIGO/NOVO/g' arquivo.txt

Para alterar o arquivo:

sed -i 's/ANTIGO/NOVO/g' arquivo.txt

Para mostrar somente uma linha:

sed -n '5p' arquivo.txt

Para apagar uma linha da saída:

sed '5d' arquivo.txt

Regra para memorizar

sed
↓
texto entra
↓
sed faz a operação
↓
resultado sai

O "sed" é principalmente uma ferramenta para fazer alterações rápidas em textos.
