Pipes e Redirecionamentos

Pipe — Canal

O "|" pega a saída de um comando e envia para outro comando.

ls | grep ".txt"

Funcionamento:

ls
↓
lista arquivos
↓
|
↓
grep
↓
mostra os arquivos .txt

"|" — Pipe (Canal)

É muito usado para combinar comandos.

---

">" — Output Redirection (Redirecionamento de Saída)

Envia a saída para um arquivo.

ls > arquivos.txt

Se "arquivos.txt" já existir, seu conteúdo será substituído.

comando
↓
>
↓
arquivo

---

">>" — Append (Adicionar)

Adiciona a saída ao final do arquivo.

ls >> arquivos.txt

O conteúdo anterior é mantido.

>  → substituir
>> → adicionar

---

"<" — Input Redirection (Redirecionamento de Entrada)

Faz um comando receber a entrada de um arquivo.

sort < nomes.txt

Significa:

nomes.txt
↓
entrada
↓
sort

"<" — Input (Entrada)

---

"2>" — Error Redirection (Redirecionamento de Erro)

Redireciona mensagens de erro.

comando 2> erros.txt

O erro será enviado para:

erros.txt

O número "2" representa:

2 → stderr → Standard Error → Erro padrão

---

"2>>" — Append Error (Adicionar Erros)

Adiciona os erros ao final do arquivo.

comando 2>> erros.txt

---

"&>" — Output and Error (Saída e Erro)

Redireciona saída normal e erro para o mesmo arquivo.

comando &> resultado.txt

---

"2>&1" — Error to Output (Erro para Saída)

Faz o erro ("2") ser enviado para o mesmo destino da saída ("1").

comando > resultado.txt 2>&1

Aqui:

1 → stdout → Standard Output → Saída padrão
2 → stderr → Standard Error → Erro padrão

Resultado:

saída normal ──┐
               ├──> resultado.txt
erro ──────────┘

---

Standard Streams — Fluxos Padrão

Todo programa normalmente trabalha com três fluxos:

0 → stdin  → Standard Input  → Entrada
1 → stdout → Standard Output → Saída
2 → stderr → Standard Error  → Erro

Para memorizar:

0 → entrada
1 → saída
2 → erro

---

Combinando Pipe e Redirecionamento

Podemos combinar os dois:

ps aux | grep "sshd" > processos.txt

Funcionamento:

ps aux
↓
Pipe
↓
grep "sshd"
↓
>
↓
processos.txt

Primeiro o "grep" filtra o resultado.

Depois ">" salva o resultado no arquivo.

---

Principais símbolos

|    → Pipe → Canal
>    → Output Redirection → Redirecionar saída
>>   → Append → Adicionar
<    → Input Redirection → Redirecionar entrada
2>   → Error Redirection → Redirecionar erro
2>>  → Append Error → Adicionar erro
&>   → Output and Error → Saída e erro
2>&1 → Error to Output → Erro para saída

---

🧠 Para a LPIC-1

Se aparecer:

comando1 | comando2

pense:

"A saída do comando 1 entra no comando 2."

Se aparecer:

comando > arquivo

pense:

"Salvar/substituir a saída no arquivo."

Se aparecer:

comando >> arquivo

pense:

"Adicionar a saída no final do arquivo."

Se aparecer:

comando 2> erro.txt

pense:

"Enviar os erros para o arquivo."

Regra para memorizar

|   → conecta comandos
>   → substitui
>>  → adiciona
<   → recebe entrada
2>  → erro
