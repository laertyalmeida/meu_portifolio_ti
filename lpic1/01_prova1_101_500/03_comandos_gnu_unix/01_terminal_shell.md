Terminal e Shell

Terminal — Terminal

O Terminal é o programa que permite interagir com o Linux através de comandos de texto.

Exemplo:

ls

Você digita o comando → o Linux executa → o resultado aparece no terminal.

---

Shell — Interpretador de Comandos

O Shell é o programa que recebe o comando que você digitou e pede ao sistema para executá-lo.

Você
 ↓
Terminal
 ↓
Shell
 ↓
Kernel
 ↓
Hardware

O terminal é a interface. O shell é quem interpreta os comandos.

---

Bash — Bourne Again Shell

Bash é um dos shells mais utilizados no Linux.

Para saber qual shell está sendo usado:

echo $SHELL

Normalmente o resultado será algo como:

/bin/bash

---

"echo" — Echo (Exibir)

Mostra um texto ou o valor de uma variável.

echo "Olá Linux"

Também podemos mostrar uma variável:

echo $SHELL

---

SHELL — Shell Atual

A variável "$SHELL" normalmente indica o shell definido para o usuário.

echo $SHELL

---

"command" — Command (Comando)

Podemos usar "command" para verificar se um comando está disponível.

command -v ls

"-v" — Verbose/Version (Informação)

No "command", "-v" mostra como o comando seria encontrado pelo shell.

Exemplo:

/usr/bin/ls

---

Terminal x Shell

É importante não confundir:

Terminal
→ onde você digita

Shell
→ interpreta o que você digita

Bash
→ um tipo de Shell

---

LPIC-1 — O que saber

- Terminal é a interface para trabalhar com comandos.
- Shell interpreta e executa os comandos.
- Bash é um shell muito usado no Linux.
- "$SHELL" indica o shell definido para o usuário.
- "echo" exibe informações.
- "command -v" pode mostrar onde um comando é encontrado.

---

Resumo

Terminal
   ↓
Shell
   ↓
Comando
   ↓
Kernel
   ↓
Sistema

echo $SHELL

→ mostra o shell definido para o usuário.

Terminal ≠ Shell

Terminal é onde você trabalha.
Shell é quem interpreta seus comandos.
