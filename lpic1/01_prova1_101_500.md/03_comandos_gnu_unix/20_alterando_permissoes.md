Alterando Permissões

"chmod" — Change Mode (Alterar Permissões)

O "chmod" altera as permissões de arquivos e diretórios.

Existem duas formas principais:

Modo numérico
Modo simbólico

---

Modo Numérico

Usamos números para representar as permissões:

r = 4
w = 2
x = 1

Exemplo:

chmod 755 script.sh

Resultado:

rwxr-xr-x

7 → rwx → proprietário
5 → r-x → grupo
5 → r-x → outros

---

Modo Simbólico

Podemos alterar permissões usando letras.

Os grupos são:

u → User (Usuário/Proprietário)
g → Group (Grupo)
o → Others (Outros)
a → All (Todos)

As permissões:

r → Read (Ler)
w → Write (Escrever)
x → Execute (Executar)

---

"+" — Add (Adicionar)

Adiciona uma permissão.

chmod u+x script.sh

Tradução:

u → User (Usuário)
+ → adicionar
x → Execute (Executar)

→ Adiciona permissão de execução ao proprietário.

---

"-" — Remove (Remover)

Remove uma permissão.

chmod o-w arquivo.txt

→ Remove a permissão de escrita dos outros usuários.

---

"=" — Set (Definir)

Define exatamente as permissões indicadas.

chmod g=rx arquivo.txt

→ O grupo fica somente com:

r-x

---

Vários grupos

Podemos alterar mais de um grupo:

chmod ug+x script.sh

→ Adiciona execução ao proprietário e ao grupo.

Também:

chmod a+r arquivo.txt

→ Adiciona leitura para todos.

---

"-R" — Recursive (Recursivo)

Aplica a alteração ao diretório e ao conteúdo dentro dele.

chmod -R 755 documentos/

Cuidado: usar "-R" sem entender o conteúdo pode alterar muitas permissões de uma vez.

---

Exemplos

Dar execução ao proprietário:

chmod u+x script.sh

Remover escrita dos outros:

chmod o-w arquivo.txt

Dar leitura para todos:

chmod a+r arquivo.txt

Definir permissões do grupo:

chmod g=rx arquivo.txt

---

LPIC-1 — O que saber

Grupos

u → User (Usuário)
g → Group (Grupo)
o → Others (Outros)
a → All (Todos)

Permissões

r → Read (Ler)
w → Write (Escrever)
x → Execute (Executar)

Operadores

+ → adicionar
- → remover
= → definir

Opção

-R → Recursive (Recursivo)

---

Resumo

chmod u+x arquivo
      │ │
      │ └── Execute
      └──── User

chmod 755 arquivo

→ Define:

rwx r-x r-x

Regra simples:

u → usuário
g → grupo
o → outros
a → todos

+ → adicionar
- → remover
= → definir
