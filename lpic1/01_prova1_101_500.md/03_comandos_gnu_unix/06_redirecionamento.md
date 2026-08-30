Redirecionamento

Redirect — Redirecionar

No Linux, podemos enviar a saída de um comando para um arquivo, em vez de mostrar tudo na tela.

Os símbolos mais importantes são:

>     → substituir o conteúdo
>>    → adicionar ao final
<     → usar arquivo como entrada
|     → enviar saída para outro comando

---

">" — Output Redirection (Redirecionamento de Saída)

Envia a saída para um arquivo.

ls > arquivos.txt

Se "arquivos.txt" existir, seu conteúdo será substituído.

---

">>" — Append (Adicionar)

Adiciona a saída ao final do arquivo.

ls >> arquivos.txt

O conteúdo anterior é mantido.

---

"<" — Input Redirection (Redirecionamento de Entrada)

Usa um arquivo como entrada para um comando.

wc -l < arquivo.txt

Nesse caso, o "wc" recebe o conteúdo do arquivo como entrada.

---

"|" — Pipe (Canal)

Envia a saída de um comando diretamente para outro comando.

ls | grep ".txt"

Funcionamento:

ls
 ↓
lista de arquivos
 ↓
grep
 ↓
somente arquivos contendo ".txt"

O pipe é extremamente importante no Linux.

---

"stdout" — Standard Output (Saída Padrão)

É o local normal onde um programa envia seus resultados.

Normalmente:

stdout → tela

Podemos redirecionar:

ls > arquivos.txt

---

"stderr" — Standard Error (Erro Padrão)

É o canal usado para mensagens de erro.

Normalmente:

stderr → tela

Podemos redirecionar erros:

comando 2> erros.txt

"2>" — Redirecionar stderr

O número "2" representa o stderr.

---

"stdin" — Standard Input (Entrada Padrão)

É de onde o programa recebe dados.

Normalmente:

stdin → teclado

O número usado para "stdin" é:

0

Os três canais padrão:

0 → stdin  → entrada
1 → stdout → saída
2 → stderr → erro

---

Redirecionar saída e erro

Podemos enviar a saída e os erros para o mesmo arquivo:

comando > resultado.txt 2>&1

"2>&1"

Significa:

2 → stderr
1 → stdout

2>&1
↓
envie stderr para o mesmo lugar do stdout

---

LPIC-1 — O que saber

- ">" substitui o conteúdo do arquivo.
- ">>" adiciona ao final.
- "<" redireciona entrada.
- "|" conecta comandos.
- "stdin" = entrada padrão.
- "stdout" = saída padrão.
- "stderr" = erro padrão.
- "0" = stdin.
- "1" = stdout.
- "2" = stderr.
- "2>&1" envia stderr para o mesmo destino de stdout.

---

Resumo

0 → stdin  → entrada
1 → stdout → saída
2 → stderr → erro

>   → substituir
>>  → adicionar
<   → entrada
|   → pipe

Exemplo

ls /etc | grep ".conf" > arquivos.txt

ls
 ↓
lista /etc
 ↓
grep
 ↓
filtra ".conf"
 ↓
>
 ↓
arquivos.txt
