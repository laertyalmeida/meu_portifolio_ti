Exercícios — Comandos GNU e Unix

Tente responder sem consultar as páginas anteriores.

1. Redirecionamento

O que acontece?

ls > arquivos.txt

A) Adiciona ao arquivo
B) Substitui o conteúdo
C) Apaga o arquivo
D) Executa o arquivo

---

2. Pipe

O que faz?

ls | grep ".txt"

A) Procura arquivos ".txt" no disco
B) Mostra somente a saída do "ls" que contém ".txt"
C) Cria arquivos ".txt"
D) Compacta arquivos

---

3. Permissões

O que significa?

755

A) "rwxrwxrwx"
B) "rw-r--r--"
C) "rwxr-xr-x"
D) "r--r--r--"

---

4. Processos

O que significa?

kill 1234

A) Apaga o arquivo 1234
B) Envia um sinal para o processo PID 1234
C) Reinicia o computador
D) Cria o processo 1234

---

5. Sinais

Qual sinal representa SIGKILL — Encerramento Forçado?

A) "1"
B) "2"
C) "9"
D) "15"

---

6. Links

Qual comando cria um Symbolic Link — Link Simbólico?

A)

ln arquivo.txt copia.txt

B)

ln -s arquivo.txt atalho.txt

C)

cp -s arquivo.txt atalho.txt

D)

link arquivo.txt

---

7. Localização

Qual comando procura diretamente no sistema de arquivos?

A) "locate"
B) "find"
C) "which"
D) "whereis"

---

8. Compactação

O que significa:

backup.tar.gz

A) Apenas gzip
B) Apenas tar
C) tar + gzip
D) zip + gzip

---

9. Variáveis

O que mostra?

echo $HOME

A) O diretório pessoal
B) O usuário atual
C) O grupo atual
D) O diretório "/tmp"

---

10. Segundo plano

O que faz?

sleep 60 &

A) Executa em primeiro plano
B) Executa em segundo plano
C) Encerra o processo
D) Suspende o processo

---

🎯 Desafio prático

Imagine que existe:

projeto/
├── script.sh
├── notas.txt
└── backup/

Você precisa:

1. Dar permissão de execução para o proprietário de "script.sh".
2. Procurar todos os arquivos ".txt" dentro de "projeto".
3. Criar um arquivo "backup.tar.gz" contendo "projeto".
4. Executar "sleep 100" em segundo plano.
5. Verificar as tarefas em segundo plano.

Escreva os 5 comandos.

---

Gabarito

<details>
<summary>Mostrar respostas</summary>1.

B — ">" substitui o conteúdo.

2.

B — envia a saída do "ls" para o "grep".

3.

C — "rwxr-xr-x".

4.

B — envia um sinal para o PID 1234.

5.

C — "SIGKILL = 9".

6.

B — "ln -s".

7.

B — "find".

8.

C — "tar + gzip".

9.

A — mostra o diretório pessoal.

10.

B — executa em segundo plano.

Desafio

chmod u+x projeto/script.sh

find projeto -name "*.txt"

tar -czf backup.tar.gz projeto/

sleep 100 &

jobs

</details>---

Resultado

9–10 → Excelente
7–8  → Muito bom
5–6  → Revise alguns pontos
0–4  → Recomendo revisar o livro

Objetivo: entender o comando, não apenas decorar.
