Mini Simulado — Comandos GNU e Unix

Nível: LPIC-1 — Exam 101
Questões: 10
Objetivo: testar se você realmente entendeu o conteúdo.

«Tente responder primeiro. O gabarito está no final.»

---

1. Redirecionamento

Você quer adicionar a saída de um comando ao final de um arquivo, sem apagar o conteúdo existente.

Qual operador usar?

A) ">"
B) ">>"
C) "<"
D) "|"

---

2. "grep"

Qual comando mostra somente as linhas que começam com "Linux"?

A)

grep "Linux$" arquivo.txt

B)

grep "^Linux" arquivo.txt

C)

grep "*Linux" arquivo.txt

D)

grep "[Linux]" arquivo.txt

---

3. "tar"

Qual comando cria um arquivo "backup.tar.gz" usando Gzip?

A)

tar -xzf backup.tar.gz

B)

tar -czf backup.tar.gz projeto/

C)

tar -xJf backup.tar.gz

D)

gzip backup.tar.gz

---

4. Permissões

Qual comando dá permissão de execução somente ao proprietário?

A)

chmod u+x script.sh

B)

chmod g+x script.sh

C)

chmod o+x script.sh

D)

chmod a+x script.sh

---

5. Proprietário

Qual comando altera o proprietário de "arquivo.txt" para "joao"?

A)

chgrp joao arquivo.txt

B)

chmod joao arquivo.txt

C)

chown joao arquivo.txt

D)

owner joao arquivo.txt

---

6. Link

Qual comando cria um Symbolic Link — Link Simbólico?

A)

ln arquivo.txt copia.txt

B)

ln -s arquivo.txt atalho.txt

C)

cp -l arquivo.txt atalho.txt

D)

link -s arquivo.txt

---

7. Processos

Qual comando mostra processos em execução?

A) "jobs"
B) "ps"
C) "grep"
D) "find"

---

8. Sinais

Você tentou:

kill 1234

Qual sinal é enviado por padrão?

A) "SIGKILL"
B) "SIGSTOP"
C) "SIGTERM"
D) "SIGINT"

---

9. Localização

Qual comando utiliza uma base de dados para localizar arquivos?

A) "find"
B) "locate"
C) "which"
D) "type"

---

10. Segundo plano

Você executou:

sleep 100

O processo está no primeiro plano.

Qual combinação suspende o processo e depois permite colocá-lo em segundo plano?

A)

Ctrl + C
bg

B)

Ctrl + Z
bg

C)

Ctrl + D
fg

D)

Ctrl + R
jobs

---

📝 Gabarito

<details>
<summary>Mostrar respostas</summary>Questão| Resposta
1| B
2| B
3| B
4| A
5| C
6| B
7| B
8| C
9| B
10| B

Pontuação

10/10 → Excelente
8–9   → Muito bom
6–7   → Revise alguns pontos
0–5   → Faça uma revisão do livro

</details>---

🎯 O que este simulado avaliou

☑ Redirecionamento
☑ grep e expressões regulares
☑ tar + gzip
☑ chmod
☑ chown
☑ Links
☑ Processos
☑ Sinais
☑ find / locate
☑ Jobs em segundo plano

Livro 03 concluído.
