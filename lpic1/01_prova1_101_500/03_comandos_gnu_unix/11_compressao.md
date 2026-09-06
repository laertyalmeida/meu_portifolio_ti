Compression — Compressão

O que é compressão?

Compression (Compressão) reduz o tamanho de um arquivo.

Exemplo:

arquivo grande
     ↓
compressão
     ↓
arquivo menor

Isso ajuda a economizar espaço e facilita o envio de arquivos.

---

"gzip" — GNU Zip

O "gzip" é uma ferramenta muito comum no Linux.

gzip arquivo.txt

O arquivo passa a ser:

arquivo.txt.gz

Por padrão, o "gzip" remove o arquivo original depois de comprimi-lo.

---

"gunzip" — GNU Unzip

Usado para descomprimir arquivos ".gz".

gunzip arquivo.txt.gz

Resultado:

arquivo.txt

---

"gzip -d"

Também podemos descomprimir usando:

gzip -d arquivo.txt.gz

"-d" — Decompress (Descomprimir)

-d → Decompress → Descomprimir

---

"gzip -k"

Mantém o arquivo original.

gzip -k arquivo.txt

"-k" — Keep (Manter)

-k → Keep → Manter

Resultado:

arquivo.txt
arquivo.txt.gz

---

bzip2

O "bzip2" também comprime arquivos.

bzip2 arquivo.txt

Resultado:

arquivo.txt.bz2

Para descomprimir:

bunzip2 arquivo.txt.bz2

Ou:

bzip2 -d arquivo.txt.bz2

"-d" — Decompress (Descomprimir)

---

xz

O "xz" é outra ferramenta de compressão.

xz arquivo.txt

Resultado:

arquivo.txt.xz

Para descomprimir:

unxz arquivo.txt.xz

Ou:

xz -d arquivo.txt.xz

"-d" — Decompress (Descomprimir)

---

Comparando

gzip  → .gz
bzip2 → .bz2
xz    → .xz

Para descomprimir:

gunzip → .gz
bunzip2 → .bz2
unxz   → .xz

---

"tar" não é compressão

Essa diferença é muito importante.

O "tar" serve principalmente para agrupar vários arquivos em um único arquivo.

tar -cf arquivos.tar arquivos/

vários arquivos
      ↓
     tar
      ↓
arquivos.tar

O ".tar" sozinho não significa que o arquivo está comprimido.

---

"tar" + "gzip"

Podemos agrupar e comprimir:

tar -czf backup.tar.gz arquivos/

Flags

-c → Create → Criar
-z → Gzip → Usar gzip
-f → File → Arquivo de saída

Resultado:

backup.tar.gz

---

"tar" + "bzip2"

tar -cjf backup.tar.bz2 arquivos/

Flag

-j → bzip2 → Usar bzip2

---

"tar" + "xz"

tar -cJf backup.tar.xz arquivos/

Flag

-J → xz → Usar xz

---

🧠 Para a LPIC-1

Memorize:

gzip  → .gz
bzip2 → .bz2
xz    → .xz
tar   → agrupar arquivos

Flags do "tar"

-c → Create → Criar
-x → Extract → Extrair
-z → gzip
-j → bzip2
-J → xz
-f → File → Arquivo

Exemplos

tar -czf backup.tar.gz pasta/

→ cria um ".tar.gz".

tar -xzf backup.tar.gz

→ extrai um ".tar.gz".

tar -cJf backup.tar.xz pasta/

→ cria um ".tar.xz".

tar -xJf backup.tar.xz

→ extrai um ".tar.xz".

---

Regra simples

tar
↓
agrupa

gzip / bzip2 / xz
↓
comprimem

Portanto:

.tar
→ agrupado

.tar.gz
→ agrupado + gzip

.tar.bz2
→ agrupado + bzip2

.tar.xz
→ agrupado + xz
