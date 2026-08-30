Compactação e Arquivos

Archive — Arquivo/Arquivo de Pacote

Um Archive (Arquivo de pacote) reúne vários arquivos e diretórios em um único arquivo.

O comando mais importante para isso no Linux é o "tar".

---

"tar" — Tape Archive (Arquivo de Fita)

O "tar" junta vários arquivos em um único arquivo.

Por exemplo:

tar -cf backup.tar documentos/

Resultado:

documentos/
    ↓
backup.tar

"-c" — Create (Criar)

Cria um novo arquivo ".tar".

"-f" — File (Arquivo)

Indica o nome do arquivo que será criado ou usado.

---

Extrair um arquivo

tar -xf backup.tar

"-x" — Extract (Extrair)

Extrai o conteúdo do arquivo.

"-f" — File (Arquivo)

Indica qual arquivo será utilizado.

---

"tar.gz" — Arquivo compactado

O "tar" sozinho não comprime os arquivos.

Podemos combinar "tar" com gzip:

tar -czf backup.tar.gz documentos/

"-z" — Gzip

Usa o gzip para compactar.

Para extrair:

tar -xzf backup.tar.gz

---

"gzip" — GNU Zip (Compactação)

Compacta arquivos usando o formato gzip.

gzip arquivo.txt

Resultado:

arquivo.txt.gz

Para descompactar:

gunzip arquivo.txt.gz

"gunzip" — GNU Unzip (Descompactar)

Descompacta arquivos ".gz".

---

"bzip2"

Outro formato de compactação.

bzip2 arquivo.txt

Resultado:

arquivo.txt.bz2

Para descompactar:

bunzip2 arquivo.txt.bz2

---

"xz"

Outro formato de compactação bastante usado no Linux.

xz arquivo.txt

Resultado:

arquivo.txt.xz

Para descompactar:

unxz arquivo.txt.xz

---

"tar" + diferentes compactações

.tar      → apenas agrupamento
.tar.gz   → tar + gzip
.tar.bz2  → tar + bzip2
.tar.xz   → tar + xz

Exemplo:

tar -cJf backup.tar.xz documentos/

"-J" — XZ

Usa o XZ para compactar.

---

LPIC-1 — O que saber

- "tar" cria arquivos de pacote.
- "tar" não compacta sozinho.
- "gzip", "bzip2" e "xz" são ferramentas de compactação.
- ".tar.gz" = tar + gzip.
- ".tar.bz2" = tar + bzip2.
- ".tar.xz" = tar + xz.
- "-c" = Create (Criar).
- "-x" = Extract (Extrair).
- "-f" = File (Arquivo).
- "-z" = Gzip.
- "-J" = XZ.

---

Resumo

tar       → agrupar arquivos
gzip      → compactar
bzip2     → compactar
xz        → compactar

.tar      → arquivo tar
.tar.gz   → tar + gzip
.tar.bz2  → tar + bzip2
.tar.xz   → tar + xz

Comando para memorizar

tar -czf backup.tar.gz documentos/

-c → Create (Criar)
-z → Gzip
-f → File (Arquivo)
