Proprietário e Grupo

No Linux, cada arquivo e diretório possui um Owner (Proprietário) e um Group (Grupo).

arquivo
   ├── proprietário
   └── grupo

---

Ver proprietário e grupo

Use:

ls -l

Exemplo:

-rw-r--r--  laerte  users  arquivo.txt

Nesse exemplo:

laerte → proprietário
users  → grupo

---

"chown" — Change Owner (Alterar Proprietário)

Altera o proprietário de um arquivo.

sudo chown joao arquivo.txt

Agora:

arquivo.txt → proprietário: joao

---

Alterar proprietário e grupo

Podemos alterar os dois ao mesmo tempo:

sudo chown joao:developers arquivo.txt

Resultado:

proprietário → joao
grupo        → developers

---

"chgrp" — Change Group (Alterar Grupo)

Altera somente o grupo.

sudo chgrp developers arquivo.txt

Agora:

grupo → developers

---

"-R" — Recursive (Recursivo)

Pode ser usado para alterar proprietário ou grupo de um diretório e todo o conteúdo.

sudo chown -R joao:developers projeto/

Isso altera:

projeto/
├── arquivo1
├── arquivo2
└── documentos/

e todo o conteúdo abaixo de "projeto/".

---

"id" — Identity (Identidade)

O comando "id" mostra informações sobre o usuário atual.

id

Pode mostrar:

uid=1000(laerte) gid=1000(laerte) groups=1000(laerte)

"uid" — User ID (ID do Usuário)

Identifica o usuário.

"gid" — Group ID (ID do Grupo)

Identifica o grupo principal.

---

"groups" — Groups (Grupos)

Mostra os grupos dos quais o usuário participa.

groups

---

LPIC-1 — O que saber

- Todo arquivo possui proprietário e grupo.
- "ls -l" mostra proprietário e grupo.
- "chown" altera o proprietário.
- "chgrp" altera o grupo.
- "chown usuário:grupo" altera os dois.
- "-R" aplica a alteração recursivamente.
- "id" mostra UID, GID e grupos.
- "groups" mostra os grupos do usuário.

---

Resumo

ls -l
 ↓
proprietário + grupo

chown usuario arquivo

→ altera o proprietário.

chown usuario:grupo arquivo

→ altera proprietário e grupo.

chgrp grupo arquivo

→ altera somente o grupo.

Principais opções

-R → Recursive (Recursivo)
