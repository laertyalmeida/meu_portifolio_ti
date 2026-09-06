History and Aliases — Histórico e Aliases

History — Histórico

O shell guarda os comandos que você executou.

Para visualizar:

history

Resultado parecido com:

100  ls
101  cd /home
102  pwd
103  grep Linux arquivo.txt

O número identifica cada comando.

---

"!!" — Last Command (Último Comando)

Executa novamente o último comando.

!!

Se o último comando foi:

ls

então:

!!

executa "ls" novamente.

---

"!n" — Command Number (Número do Comando)

Executa um comando específico pelo número.

!102

→ executa o comando número "102".

---

"Ctrl + R" — Reverse Search (Pesquisa Reversa)

Pressione:

Ctrl + R

e digite parte de um comando anterior.

Exemplo:

Ctrl + R
grep

O shell procura comandos anteriores que contenham "grep".

É muito útil quando você não lembra exatamente o comando.

---

Alias — Atalho de Comando

Um Alias (Atalho) cria um nome mais curto para um comando.

Exemplo:

alias ll='ls -l'

Agora:

ll

é equivalente a:

ls -l

---

"alias" — Mostrar Aliases

Para ver os aliases existentes:

alias

Para consultar um específico:

alias ll

---

"unalias" — Remover Alias

Para remover um alias:

unalias ll

"unalias"

un → remover
alias → atalho

---

Alias Temporário

Se você executar:

alias ll='ls -l'

o alias normalmente existe somente naquela sessão do shell.

Ao fechar o terminal, ele pode desaparecer.

---

Alias Permanente

Para manter o alias no Bash, normalmente colocamos a configuração em:

~/.bashrc

Exemplo:

alias ll='ls -l'

Depois podemos carregar novamente:

source ~/.bashrc

"source" — Carregar (Executar no Shell Atual)

O "source" faz o shell ler novamente o arquivo.

---

🧠 Para a LPIC-1

Memorize:

history
→ mostrar histórico

!!
→ repetir último comando

!n
→ executar comando pelo número

Ctrl + R
→ procurar no histórico

alias
→ criar/mostrar atalhos

unalias
→ remover atalho

~/.bashrc
→ configurações do Bash do usuário

source
→ carregar novamente a configuração

---

Exemplo completo

Criar um alias:

alias ll='ls -l'

Usar:

ll

Remover:

unalias ll

Tornar permanente:

echo "alias ll='ls -l'" >> ~/.bashrc

Carregar:

source ~/.bashrc

---

Regra simples

history
↓
lembrar comandos

alias
↓
criar atalhos

unalias
↓
remover atalhos

.bashrc
↓
guardar configurações do Bash
