grep — Global Regular Expression Print

grep — Procurar Texto

O "grep" é usado para procurar texto dentro de arquivos.

Exemplo:

grep "Linux" arquivo.txt

Significa:

grep
↓
procure "Linux"
↓
dentro de arquivo.txt

Se encontrar "Linux", o "grep" mostra a linha na tela.

---

Procurando uma palavra

Imagine o arquivo:

Linux é livre
Windows é um sistema
Linux usa comandos
macOS também é um sistema

Com:

grep "Linux" sistemas.txt

Resultado:

Linux é livre
Linux usa comandos

---

"-i" — Ignore Case (Ignorar Maiúsculas/Minúsculas)

Sem "-i", o "grep" diferencia:

Linux
linux
LINUX

Com:

grep -i "linux" arquivo.txt

ele encontra todas essas formas.

Flag

-i → Ignore Case (Ignorar Maiúsculas/Minúsculas)

---

"-v" — Invert Match (Inverter Correspondência)

Mostra as linhas que não possuem o texto procurado.

grep -v "Linux" arquivo.txt

Flag

-v → Invert Match (Inverter Correspondência)

---

"-n" — Line Number (Número da Linha)

Mostra o número da linha junto com o resultado.

grep -n "Linux" arquivo.txt

Resultado:

1:Linux é livre
3:Linux usa comandos

Flag

-n → Line Number (Número da Linha)

---

"-c" — Count (Contar)

Conta quantas linhas possuem o texto.

grep -c "Linux" arquivo.txt

Resultado:

2

Flag

-c → Count (Contar)

---

"-r" — Recursive (Recursivo)

Procura dentro de vários arquivos e subdiretórios.

grep -r "Linux" projeto/

Flag

-r → Recursive (Recursivo)

---

"-l" — Files with Match (Arquivos com Correspondência)

Mostra somente os nomes dos arquivos que possuem o texto.

grep -l "Linux" *.txt

Flag

-l → Files with Match (Arquivos com Correspondência)

---

"grep" com Pipe

O "grep" também pode receber a saída de outro comando.

ls | grep ".txt"

Funcionamento:

ls
↓
lista arquivos
↓
grep
↓
mostra os que possuem ".txt"

---

Principais flags para LPIC-1

-i → Ignore Case → ignorar maiúsculas/minúsculas
-v → Invert Match → inverter correspondência
-n → Line Number → número da linha
-c → Count → contar
-r → Recursive → recursivo
-l → Files with Match → arquivos com correspondência

---

Resumo

grep "Linux" arquivo.txt

→ procura "Linux".

grep -i "linux" arquivo.txt

→ ignora maiúsculas/minúsculas.

grep -v "Linux" arquivo.txt

→ mostra linhas que não possuem "Linux".

grep -n "Linux" arquivo.txt

→ mostra o número da linha.

grep -c "Linux" arquivo.txt

→ conta as linhas encontradas.

grep -r "Linux" projeto/

→ procura recursivamente.

grep -l "Linux" *.txt

→ mostra os arquivos que possuem "Linux".

Regra para memorizar

grep → procurar texto

-i → ignorar maiúsculas
-v → inverter
-n → número da linha
-c → contar
-r → recursivo
-l → nome dos arquivos
