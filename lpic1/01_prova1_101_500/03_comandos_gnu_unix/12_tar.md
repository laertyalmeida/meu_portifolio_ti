tar — Tape Archive

O que é "tar"?

O "tar" é usado para juntar vários arquivos e diretórios em um único arquivo.

vários arquivos
      ↓
     tar
      ↓
arquivo.tar

O "tar" sozinho não comprime. Ele apenas agrupa.

---

Criar um arquivo ".tar"

tar -cf arquivos.tar documentos/

Flags

-c → Create → Criar
-f → File → Arquivo

Significa:

-c → criar um arquivo tar
-f → definir o nome do arquivo

---

Listar o conteúdo

Use:

tar -tf arquivos.tar

Flags

-t → List → Listar
-f → File → Arquivo

Mostra os arquivos dentro do ".tar" sem extrair.

---

Extrair

tar -xf arquivos.tar

Flags

-x → Extract → Extrair
-f → File → Arquivo

---

Criar e comprimir com gzip

tar -czf backup.tar.gz documentos/

Flags

-c → Create → Criar
-z → Gzip → Usar gzip
-f → File → Arquivo

Resultado:

backup.tar.gz

---

Extrair ".tar.gz"

tar -xzf backup.tar.gz

Flags

-x → Extract → Extrair
-z → Gzip → Usar gzip
-f → File → Arquivo

---

bzip2

Criar:

tar -cjf backup.tar.bz2 documentos/

Flag

-j → bzip2 → Usar bzip2

Extrair:

tar -xjf backup.tar.bz2

---

xz

Criar:

tar -cJf backup.tar.xz documentos/

Flag

-J → xz → Usar xz

Extrair:

tar -xJf backup.tar.xz

---

"tar" e seus formatos

.tar
↓
apenas agrupamento

.tar.gz
↓
tar + gzip

.tar.bz2
↓
tar + bzip2

.tar.xz
↓
tar + xz

---

Ver o conteúdo sem extrair

tar -tf backup.tar.gz

→ mostra o conteúdo.

Isso é útil quando queremos saber o que existe dentro do arquivo antes de extrair.

---

"-v" — Verbose (Detalhado)

Mostra os arquivos sendo processados.

tar -cvf arquivos.tar documentos/

Flag

-v → Verbose → Mostrar detalhes

---

🧠 Para a LPIC-1

As flags mais importantes:

-c → Create → Criar
-x → Extract → Extrair
-t → List → Listar
-f → File → Arquivo
-v → Verbose → Detalhado
-z → gzip
-j → bzip2
-J → xz

Decore estes três:

tar -czf backup.tar.gz pasta/

→ criar ".tar.gz"

tar -xzf backup.tar.gz

→ extrair ".tar.gz"

tar -tzf backup.tar.gz

→ listar conteúdo do ".tar.gz"

---

Regra simples

-c → criar
-x → extrair
-t → listar

-z → gzip
-j → bzip2
-J → xz

-f → arquivo
-v → detalhes

Pense assim:

tar
 ↓
junta arquivos

gzip / bzip2 / xz
 ↓
comprime
