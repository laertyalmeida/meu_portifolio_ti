Localização de Comandos

Quando digitamos um comando, o Shell (Interpretador de Comandos) precisa descobrir onde o programa está.

Para isso, ele usa principalmente o "PATH".

---

"PATH" — Path (Caminho)

"PATH" é uma variável que contém os diretórios onde o shell procura programas.

echo $PATH

Exemplo:

/usr/local/bin:/usr/bin:/bin

O ":" separa os diretórios.

---

"which" — Which (Qual)

Mostra qual executável será encontrado no "PATH".

which ls

Resultado comum:

/usr/bin/ls

---

"type" — Type (Tipo)

Mostra como o shell interpreta um comando.

type ls

Também é importante para descobrir aliases e comandos internos.

type cd

Pode mostrar:

cd is a shell builtin

Isso significa:

builtin → comando interno do shell

---

"command -v"

Também podemos descobrir como um comando é localizado:

command -v ls

"-v" — Verbose (Informação)

Mostra como o comando seria encontrado pelo shell.

---

"whereis" — Where Is (Onde Está)

Procura o programa e arquivos relacionados, como documentação.

whereis ls

Pode mostrar caminhos como:

/usr/bin/ls
/usr/share/man/man1/ls.1.gz

---

Comando interno x programa externo

Nem todo comando é um arquivo executável.

Builtin — Comando Interno

Faz parte do próprio shell.

Exemplo:

type cd

External Command — Comando Externo

É um programa localizado no sistema.

Exemplo:

type ls

---

Como o shell procura?

Quando digitamos:

ls

De forma simplificada:

ls
 ↓
Shell verifica o comando
 ↓
Procura no PATH
 ↓
/usr/bin/ls
 ↓
Executa

Se o comando não for encontrado:

command not found

---

LPIC-1 — O que saber

- "PATH" contém diretórios onde o shell procura comandos.
- "which" mostra o executável encontrado.
- "type" mostra o tipo do comando.
- "command -v" mostra como o shell encontra o comando.
- "whereis" procura programa e arquivos relacionados.
- "cd" normalmente é um builtin do shell.
- "ls" normalmente é um programa externo.
- ":" separa os diretórios do "PATH".

---

Resumo

PATH
 ↓
diretórios de programas

which       → caminho do executável
type        → tipo do comando
command -v  → como o shell encontra
whereis     → programa + arquivos relacionados

Para memorizar

Builtin → dentro do Shell
Externo → programa no sistema
