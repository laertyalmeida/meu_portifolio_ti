Variables and PATH — Variáveis e PATH

Variable — Variável

Uma variável guarda uma informação que pode ser usada pelos comandos e programas.

Para visualizar uma variável:

echo $HOME

O "$" significa:

$ → usar o valor da variável

---

Variáveis importantes

"HOME" — Home Directory (Diretório Pessoal)

Mostra o diretório pessoal do usuário.

echo $HOME

Exemplo:

/home/joao

---

"USER" — User (Usuário)

Mostra o nome do usuário atual.

echo $USER

---

"SHELL" — Shell (Interpretador de Comandos)

Mostra o shell utilizado.

echo $SHELL

Exemplo:

/bin/bash

---

"PATH" — Path (Caminho)

O "PATH" contém os diretórios onde o shell procura os programas.

echo $PATH

Exemplo:

/usr/local/bin:/usr/bin:/bin

Os diretórios são separados por:

: → dois-pontos

---

Como o PATH funciona?

Quando você digita:

ls

o shell procura o programa nos diretórios definidos no "PATH".

ls
 ↓
PATH
 ↓
/usr/local/bin
 ↓
/usr/bin
 ↓
/bin
 ↓
encontra ls

---

Criando uma variável

NOME="Linux"

Agora:

echo $NOME

Resultado:

Linux

⚠️ Não coloque espaços ao criar a variável:

NOME="Linux"

correto.

NOME = "Linux"

incorreto.

---

"export" — Exportar

Para disponibilizar uma variável para programas iniciados pelo shell:

export NOME="Linux"

Agora a variável é uma Environment Variable (Variável de Ambiente).

---

"unset" — Remover Variável

Remove uma variável:

unset NOME

Depois:

echo $NOME

não mostrará mais o valor.

---

Alterando o PATH

Podemos adicionar um diretório ao "PATH":

export PATH="$PATH:/home/joao/bin"

Aqui:

$PATH
↓
mantém o PATH atual

:
↓
separa os diretórios

/home/joao/bin
↓
novo diretório

---

"env" — Environment (Ambiente)

Mostra as variáveis de ambiente:

env

Também podemos procurar uma variável:

env | grep HOME

---

"printenv" — Print Environment (Mostrar Ambiente)

Mostra variáveis de ambiente.

printenv HOME

Resultado:

/home/joao

---

🧠 Para a LPIC-1

Memorize estas:

HOME   → diretório pessoal
USER   → usuário atual
SHELL  → shell utilizado
PATH   → onde procurar programas

Comandos:

echo     → mostrar valor
export   → exportar variável
unset    → remover variável
env      → mostrar ambiente
printenv → mostrar variável de ambiente

---

Regra simples

VARIAVEL="valor"

→ cria uma variável.

echo $VARIAVEL

→ mostra seu valor.

export VARIAVEL="valor"

→ exporta para o ambiente.

unset VARIAVEL

→ remove a variável.

E lembre:

PATH
↓
lista de diretórios
↓
onde o shell procura programas
