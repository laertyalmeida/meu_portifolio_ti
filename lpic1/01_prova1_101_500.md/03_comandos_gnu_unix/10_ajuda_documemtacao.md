Ajuda e Documentação

No Linux, você não precisa decorar todos os comandos. O próprio sistema possui ferramentas para consultar como os comandos funcionam.

---

"man" — Manual (Manual)

O "man" mostra o manual de um comando.

man ls

Você verá informações como:

- O que o comando faz.
- Como usar.
- Opções disponíveis.
- Exemplos e detalhes.

Para sair:

q

"q" — Quit (Sair)

---

"--help" — Help (Ajuda)

Muitos comandos possuem a opção "--help".

ls --help

Mostra uma explicação rápida das opções do comando.

É útil quando você quer uma consulta rápida, sem abrir o manual completo.

---

"info" — Information (Informação)

O "info" fornece documentação de vários programas GNU.

info ls

---

"apropos" — Aproximadamente / Relacionado

Procura páginas do manual relacionadas a uma palavra ou assunto.

apropos network

Pode encontrar comandos relacionados a network (rede).

---

"whatis" — What Is (O que é)

Mostra uma descrição curta de um comando.

whatis ls

Exemplo:

ls - list directory contents

---

"type" — Type (Tipo)

Mostra como o shell interpreta um comando.

type ls

Pode informar que "ls" é um programa ou outro tipo de comando.

Também podemos verificar:

type cd

Isso é importante porque "cd" normalmente é um builtin (comando interno) do shell.

---

"which" — Which (Qual)

Mostra o caminho de um executável encontrado no "PATH".

which ls

Resultado típico:

/usr/bin/ls

---

"PATH" — Path (Caminho)

"PATH" é uma variável que contém os diretórios onde o shell procura programas.

echo $PATH

Exemplo:

/usr/local/bin:/usr/bin:/bin

Quando você digita:

ls

o shell procura o programa nos diretórios do "PATH".

---

LPIC-1 — O que saber

- "man" → manual completo.
- "--help" → ajuda rápida.
- "info" → documentação GNU.
- "apropos" → procura assuntos nos manuais.
- "whatis" → descrição curta.
- "type" → mostra o tipo de comando.
- "which" → mostra o caminho de um executável.
- "PATH" → diretórios onde o shell procura programas.
- "q" = Quit (Sair).

---

Resumo

man       → manual
--help    → ajuda rápida
info      → documentação
apropos   → procurar assunto
whatis    → descrição curta
type      → tipo do comando
which     → caminho do programa
PATH      → onde procurar programas

Para memorizar

man comando

→ Manual completo.

comando --help

→ Ajuda rápida.
