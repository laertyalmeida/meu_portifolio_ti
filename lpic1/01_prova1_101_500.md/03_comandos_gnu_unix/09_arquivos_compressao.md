Arquivos e Compressão

"gzip" — GNU Zip (Compactação)

O "gzip" compacta arquivos individualmente.

gzip arquivo.txt

Resultado:

arquivo.txt.gz

Para descompactar:

gunzip arquivo.txt.gz

---

"bzip2" — Burrows-Wheeler Zip 2

O "bzip2" também compacta arquivos.

bzip2 arquivo.txt

Resultado:

arquivo.txt.bz2

Para descompactar:

bunzip2 arquivo.txt.bz2

---

"xz" — XZ

O "xz" é outro formato de compressão bastante usado no Linux.

xz arquivo.txt

Resultado:

arquivo.txt.xz

Para descompactar:

unxz arquivo.txt.xz

---

"tar" + Compressão

O "tar" pode trabalhar junto com ferramentas de compressão.

Gzip

tar -czf backup.tar.gz documentos/

- "-c" — Create (Criar)
- "-z" — Gzip
- "-f" — File (Arquivo)

Bzip2

tar -cjf backup.tar.bz2 documentos/

- "-c" — Create (Criar)
- "-j" — Bzip2
- "-f" — File (Arquivo)

XZ

tar -cJf backup.tar.xz documentos/

- "-c" — Create (Criar)
- "-J" — XZ
- "-f" — File (Arquivo)

---

"zip" — Zip (Compactar)

O "zip" cria arquivos no formato ".zip".

zip backup.zip arquivo.txt

Para incluir um diretório:

zip -r backup.zip documentos/

"-r" — Recursive (Recursivo)

Inclui o diretório e todo o seu conteúdo.

Para extrair:

unzip backup.zip

---

Diferença importante

tar
 ↓
agrupa arquivos

gzip / bzip2 / xz
 ↓
compactam dados

zip
 ↓
agrupa + compacta

Por isso:

.tar.gz

significa:

tar + gzip

---

LPIC-1 — O que saber

- "gzip" usa ".gz".
- "bzip2" usa ".bz2".
- "xz" usa ".xz".
- "zip" usa ".zip".
- "tar" agrupa arquivos.
- "gunzip", "bunzip2" e "unxz" descompactam.
- "unzip" extrai arquivos ".zip".
- "-r" = Recursive (Recursivo).
- "-j" = Bzip2.
- "-J" = XZ.

---

Resumo

.gz    → gzip
.bz2   → bzip2
.xz    → xz
.zip   → zip

tar -czf → tar + gzip
tar -cjf → tar + bzip2
tar -cJf → tar + xz
