# Comandos GNU/UNIX

## 11 — Compressão

**Compression — Compressão** é o processo de reduzir o tamanho de arquivos para economizar espaço e facilitar transferências.

No Linux, os principais comandos de compressão cobrados no LPIC-1 são:

    gzip
    bzip2
    xz

Também é importante conhecer:

    gunzip
    bunzip2
    unxz

---

## 1. `gzip` — GNU Zip — compressão

Comprime arquivos usando o formato **Gzip**.

    gzip arquivo.txt

O arquivo original normalmente é substituído por:

    arquivo.txt.gz

Para descomprimir:

    gunzip arquivo.txt.gz

Ou:

    gzip -d arquivo.txt.gz

`-d` — decompress — descomprimir.

---

### `gzip -k` — Keep — manter

Mantém o arquivo original:

    gzip -k arquivo.txt

Resultado:

    arquivo.txt
    arquivo.txt.gz

---

### `gzip -l` — List — listar

Mostra informações sobre o arquivo comprimido:

    gzip -l arquivo.txt.gz

---

### `gzip -c` — Standard Output — saída padrão

Envia o resultado comprimido para a saída padrão.

    gzip -c arquivo.txt > arquivo.txt.gz

Isso permite controlar o arquivo de saída usando `>`.

---

## 2. `bzip2` — Bzip2

Outra ferramenta tradicional de compressão.

    bzip2 arquivo.txt

Produz:

    arquivo.txt.bz2

Descomprimir:

    bunzip2 arquivo.txt.bz2

Ou:

    bzip2 -d arquivo.txt.bz2

---

### `bzip2 -k` — Keep — manter

    bzip2 -k arquivo.txt

Mantém o arquivo original.

---

## 3. `xz` — XZ

Ferramenta de compressão muito utilizada em distribuições Linux e pacotes de código-fonte.

    xz arquivo.txt

Produz:

    arquivo.txt.xz

Descomprimir:

    unxz arquivo.txt.xz

Ou:

    xz -d arquivo.txt.xz

---

### `xz -k` — Keep — manter

    xz -k arquivo.txt

Mantém o arquivo original.

---

## 4. Comparação

| Ferramenta | Extensão | Descompressão |
|---|---|---|
| `gzip` | `.gz` | `gunzip` / `gzip -d` |
| `bzip2` | `.bz2` | `bunzip2` / `bzip2 -d` |
| `xz` | `.xz` | `unxz` / `xz -d` |

---

## 5. Compressão não é arquivamento

**Compression — Compressão** reduz o tamanho.

**Archiving — Arquivamento** reúne vários arquivos em um único arquivo.

Por exemplo:

    gzip arquivo.txt

Comprime um arquivo.

Já:

    tar -cf arquivos.tar arquivo1.txt arquivo2.txt

Reúne vários arquivos em um único arquivo `.tar`, mas não necessariamente os comprime.

Por isso é comum combinar:

    tar + gzip
    tar + bzip2
    tar + xz

Exemplos:

    arquivo.tar.gz
    arquivo.tar.bz2
    arquivo.tar.xz

---

## 6. `zcat` — Zipped Cat — exibir arquivo gzip

Permite visualizar um arquivo `.gz` sem descompactá-lo primeiro.

    zcat arquivo.txt.gz

Também existem:

    bzcat arquivo.txt.bz2

    xzcat arquivo.txt.xz

Eles permitem visualizar o conteúdo comprimido diretamente.

---

## 7. Compressão pela entrada e saída padrão

Podemos combinar compressão com redirecionamentos.

Exemplo:

    gzip -c arquivo.txt > arquivo.txt.gz

Para descomprimir e salvar:

    gzip -dc arquivo.txt.gz > arquivo.txt

Aqui:

    -d → decompress → descomprimir
    -c → stdout → enviar para a saída padrão

---

## 8. Verificar o tipo do arquivo

Podemos usar `file`:

    file arquivo.txt.gz

    file arquivo.txt.bz2

    file arquivo.txt.xz

O `file` identifica o formato do conteúdo.

---

## 9. Compressão e `tar`

Um dos usos mais importantes no Linux é combinar `tar` com compressão.

### Gzip

    tar -czf backup.tar.gz documentos/

`-z` — gzip — usar compressão gzip.

### Bzip2

    tar -cjf backup.tar.bz2 documentos/

`-j` — bzip2 — usar compressão bzip2.

### XZ

    tar -cJf backup.tar.xz documentos/

`-J` — xz — usar compressão xz.

O estudo detalhado do `tar` será feito na próxima página.

---

## Resumo LPIC-1

| Comando | Função |
|---|---|
| `gzip` | comprimir com gzip |
| `gunzip` | descomprimir `.gz` |
| `bzip2` | comprimir com bzip2 |
| `bunzip2` | descomprimir `.bz2` |
| `xz` | comprimir com xz |
| `unxz` | descomprimir `.xz` |
| `zcat` | visualizar `.gz` |
| `bzcat` | visualizar `.bz2` |
| `xzcat` | visualizar `.xz` |
| `gzip -d` | descomprimir gzip |
| `bzip2 -d` | descomprimir bzip2 |
| `xz -d` | descomprimir xz |

**Opções importantes:**

    -d → decompress → descomprimir
    -k → keep → manter original
    -c → stdout → saída padrão

**Extensões:**

    .gz    → gzip
    .bz2   → bzip2
    .xz    → xz
    .tar   → arquivamento
    .tar.gz  → tar + gzip
    .tar.bz2 → tar + bzip2
    .tar.xz  → tar + xz

**Memorize:**

    gzip  → .gz
    bzip2 → .bz2
    xz    → .xz

    Compressão ≠ arquivamento

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
