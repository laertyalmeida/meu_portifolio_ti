Busca de Arquivos

No Linux, existem comandos para encontrar arquivos e localizar informações dentro deles.

---

"find" — Find (Encontrar)

Procura arquivos e diretórios.

Exemplo:

find /home -name "arquivo.txt"

Procura por "arquivo.txt" dentro de "/home".

"-name" — Name (Nome)

Procura pelo nome do arquivo.

find /home -name "*.txt"

→ Procura arquivos que terminam com ".txt".

---

"locate" — Locate (Localizar)

Também procura arquivos, mas utiliza um banco de dados com os caminhos dos arquivos.

locate arquivo.txt

É normalmente mais rápido que "find", mas o banco de dados pode não estar atualizado.

"updatedb" — Update Database (Atualizar Banco de Dados)

Atualiza o banco usado pelo "locate".

sudo updatedb

---

"which" — Which (Qual)

Mostra onde está o programa que será executado pelo shell.

which ls

Exemplo:

/usr/bin/ls

---

"whereis" — Where Is (Onde Está)

Procura a localização do programa, documentação e código-fonte quando disponível.

whereis ls

---

"grep" — Global Regular Expression Print

Procura texto dentro de arquivos.

grep "Linux" arquivo.txt

→ Mostra as linhas que contêm "Linux".

"-i" — Ignore Case (Ignorar Maiúsculas/Minúsculas)

grep -i "linux" arquivo.txt

Encontra:

Linux
linux
LINUX

"-r" — Recursive (Recursivo)

Procura dentro de diretórios e seus subdiretórios.

grep -r "Linux" documentos/

"-n" — Number (Número)

Mostra o número da linha encontrada.

grep -n "Linux" arquivo.txt

---

"find" x "grep"

Não confunda:

find
 ↓
Procura arquivos

grep
 ↓
Procura texto dentro de arquivos

Exemplo:

find /home -name "*.txt"

→ Encontra arquivos ".txt".

grep "Linux" arquivo.txt

→ Encontra "Linux" dentro do arquivo.

---

LPIC-1 — O que saber

- "find" procura arquivos e diretórios.
- "locate" procura usando um banco de dados.
- "updatedb" atualiza o banco do "locate".
- "which" mostra onde um comando está.
- "whereis" procura programa e arquivos relacionados.
- "grep" procura texto.
- "-name" = Name (Nome).
- "-i" = Ignore Case (Ignorar maiúsculas/minúsculas).
- "-r" = Recursive (Recursivo).
- "-n" = Number (Número da linha).

---

Resumo

find    → procurar arquivos
locate  → procurar arquivos pelo banco
which   → localização do comando
whereis → programa + arquivos relacionados
grep    → procurar texto

Principais opções

-name → Name (Nome)
-i    → Ignore Case (Ignorar maiúsculas/minúsculas)
-r    → Recursive (Recursivo)
-n    → Number (Número da linha)
