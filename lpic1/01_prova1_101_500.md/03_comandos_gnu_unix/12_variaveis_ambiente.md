Variáveis de Ambiente

Variable — Variável

Uma Variable (Variável) é um nome que guarda um valor.

No shell, podemos criar e consultar variáveis.

nome="Linux"

Para mostrar:

echo $nome

Resultado:

Linux

---

Environment Variable — Variável de Ambiente

Uma Environment Variable (Variável de Ambiente) é uma variável que pode ser usada por programas executados pelo shell.

Exemplos importantes:

PATH
HOME
SHELL
USER

---

"echo" — Echo (Exibir)

Mostra o valor de uma variável.

echo $HOME

Exemplo:

/home/laerte

---

"HOME" — Diretório Pessoal

A variável "HOME" indica o diretório pessoal do usuário.

echo $HOME

Resultado típico:

/home/usuario

---

"USER" — Usuário

Mostra o nome do usuário atual.

echo $USER

---

"SHELL" — Shell

Indica o shell definido para o usuário.

echo $SHELL

Resultado comum:

/bin/bash

---

"PATH" — Path (Caminho)

Define os diretórios onde o shell procura programas.

echo $PATH

Os diretórios são separados por:

:

Exemplo:

/usr/local/bin:/usr/bin:/bin

---

"export" — Export (Exportar)

Torna uma variável disponível para programas executados a partir daquele shell.

export NOME="Linux"

Agora programas iniciados por esse shell podem receber a variável "NOME".

---

Variável local x variável exportada

nome="Linux"

→ variável do shell atual.

export nome="Linux"

→ variável exportada para processos filhos.

---

Remover uma variável

"unset" — Unset (Desdefinir/Remover)

Remove uma variável do shell.

unset nome

---

LPIC-1 — O que saber

- Variável guarda um valor.
- Variáveis de ambiente podem ser usadas por programas.
- "$HOME" indica o diretório pessoal.
- "$USER" indica o usuário atual.
- "$SHELL" indica o shell.
- "$PATH" indica onde o shell procura programas.
- "export" disponibiliza uma variável para processos filhos.
- "unset" remove uma variável.

---

Resumo

HOME  → diretório pessoal
USER  → usuário atual
SHELL → shell
PATH  → caminhos dos programas

echo $HOME

→ mostra o diretório pessoal.

export NOME="Linux"

→ exporta a variável.

unset NOME

→ remove a variável.
