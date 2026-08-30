Alias e Histórico

Alias — Apelido

Um Alias (Apelido) cria um nome curto para um comando.

Por exemplo:

alias ll='ls -l'

Agora podemos usar:

ll

Em vez de:

ls -l

---

"alias" — Alias (Apelido)

Para ver os aliases existentes:

alias

Para criar:

alias ll='ls -l'

Para remover:

unalias ll

"unalias" — Unalias (Remover Apelido)

Remove um alias.

---

Alias é permanente?

Normalmente, não.

Se você fechar o terminal, o alias pode desaparecer.

Para torná-lo permanente no Bash, podemos colocar o alias no arquivo:

~/.bashrc

---

History — Histórico

O shell mantém um History (Histórico) dos comandos que você executou.

"history" — History (Histórico)

history

Mostra comandos anteriores.

Exemplo:

100  ls
101  cd /etc
102  pwd
103  cat arquivo.txt

---

Executar novamente um comando

Podemos usar o número mostrado pelo "history":

!102

Isso executa novamente o comando número "102".

---

"!!" — Last Command (Último Comando)

Executa novamente o último comando.

!!

Um uso comum:

sudo !!

→ Executa novamente o último comando usando "sudo".

---

Procurar no histórico

No Bash, podemos usar:

Ctrl + R

"Ctrl + R" — Reverse Search (Busca Reversa)

Permite procurar um comando que você já executou.

Por exemplo, digite:

ssh

O Bash procura comandos anteriores que contenham "ssh".

---

"history -c"

"-c" — Clear (Limpar)

Limpa o histórico atual da sessão.

history -c

---

LPIC-1 — O que saber

- "alias" cria apelidos para comandos.
- "unalias" remove aliases.
- "history" mostra comandos anteriores.
- "!!" executa o último comando novamente.
- "!n" executa o comando de número "n" do histórico.
- "Ctrl + R" faz uma busca reversa no histórico.
- "~/.bashrc" pode conter aliases permanentes do Bash.
- "-c" = Clear (Limpar).

---

Resumo

alias     → criar apelido
unalias   → remover apelido
history   → histórico
!!        → último comando
!n        → comando número n
Ctrl + R  → procurar no histórico

Exemplo

alias ll='ls -l'

Depois:

ll

→ executa "ls -l".
