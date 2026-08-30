Localização de Arquivos

No Linux, existem várias formas de encontrar arquivos.

Os comandos mais importantes para o LPIC-1 são:

find
locate

---

"find" — Find (Encontrar)

Procura arquivos diretamente no sistema de arquivos.

Exemplo:

find /home -name "arquivo.txt"

Tradução:

/home → onde procurar
-name → Name (Nome)
"arquivo.txt" → nome procurado

---

"-name" — Name (Nome)

Procura pelo nome exato, respeitando maiúsculas e minúsculas.

find /home -name "documento.txt"

---

"-iname" — Ignore Case Name (Nome sem Diferenciar Maiúsculas)

Não diferencia maiúsculas e minúsculas.

find /home -iname "documento.txt"

Pode encontrar:

documento.txt
Documento.txt
DOCUMENTO.TXT

---

"-type" — Type (Tipo)

Permite procurar pelo tipo do arquivo.

"f" — File (Arquivo)

find /home -type f

→ Procura arquivos comuns.

"d" — Directory (Diretório)

find /home -type d

→ Procura diretórios.

---

Procurar por tamanho

"-size" — Size (Tamanho)

find /home -size +100M

→ Procura arquivos maiores que 100 MB.

---

"locate" — Locate (Localizar)

O "locate" procura arquivos usando uma base de dados.

locate arquivo.txt

Ele costuma ser mais rápido que "find", porque não precisa percorrer o sistema inteiro naquele momento.

---

"updatedb" — Update Database (Atualizar Banco de Dados)

Atualiza a base usada pelo "locate".

sudo updatedb

Depois:

locate arquivo.txt

---

"find" x "locate"

find
↓
procura diretamente no sistema
↓
mais flexível

locate
↓
consulta uma base de dados
↓
normalmente mais rápido

Uma consequência importante:

O "locate" pode não encontrar um arquivo criado recentemente se a base ainda não tiver sido atualizada.

---

Exemplos

Procurar um arquivo:

find /etc -name "passwd"

Procurar diretórios:

find /var -type d

Procurar arquivos:

find /home -type f

Procurar sem diferenciar maiúsculas:

find /home -iname "*.txt"

---

LPIC-1 — O que saber

- "find" procura diretamente no sistema de arquivos.
- "locate" consulta uma base de dados.
- "updatedb" atualiza essa base.
- "-name" = Name (Nome).
- "-iname" = Ignore Case Name (Nome sem diferenciar maiúsculas).
- "-type" = Type (Tipo).
- "f" = File (Arquivo).
- "d" = Directory (Diretório).
- "-size" = Size (Tamanho).

---

Resumo

find
→ procura diretamente

locate
→ procura na base de dados

updatedb
→ atualiza a base

Para memorizar

find /home -name "arquivo.txt"

→ procura pelo nome.

find /home -type f

→ procura arquivos.

find /home -type d

→ procura diretórios.

locate arquivo.txt

→ procura rapidamente na base de dados.
