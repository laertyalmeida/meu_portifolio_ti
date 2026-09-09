# Comandos GNU/UNIX

## 12 — tar

`tar` — **Tape Archive** — Arquivo de Fita.

O `tar` é usado principalmente para **reunir vários arquivos e diretórios em um único arquivo**, chamado de **archive — arquivo de arquivamento**.

O `tar` também pode trabalhar junto com `gzip`, `bzip2` e `xz` para criar arquivos compactados.

---

## 1. Criar um arquivo `.tar`

Sintaxe:

    tar -cf arquivo.tar arquivos/

Exemplo:

    tar -cf documentos.tar documentos/

Significado:

    -c → create → criar
    -f → file → arquivo de saída

Resultado:

    documentos.tar

---

## 2. Listar o conteúdo

`-t` — **list — listar**.

    tar -tf documentos.tar

Mostra os arquivos armazenados sem extrair.

---

## 3. Extrair arquivos

`-x` — **extract — extrair**.

    tar -xf documentos.tar

Extrai o conteúdo no diretório atual.

Para extrair em outro diretório:

    tar -xf documentos.tar -C /tmp

`-C` — **change directory — mudar diretório**.

---

## 4. Criar `.tar.gz`

`-z` — usar **gzip**.

    tar -czf documentos.tar.gz documentos/

Opções:

    -c → create → criar
    -z → gzip → compressão gzip
    -f → file → arquivo

---

## 5. Extrair `.tar.gz`

    tar -xzf documentos.tar.gz

Ou:

    tar -xzf documentos.tar.gz -C /tmp

---

## 6. Criar `.tar.bz2`

`-j` — usar **bzip2**.

    tar -cjf documentos.tar.bz2 documentos/

---

## 7. Extrair `.tar.bz2`

    tar -xjf documentos.tar.bz2

---

## 8. Criar `.tar.xz`

`-J` — usar **xz**.

    tar -cJf documentos.tar.xz documentos/

---

## 9. Extrair `.tar.xz`

    tar -xJf documentos.tar.xz

---

## 10. Listar arquivos compactados

Podemos listar o conteúdo sem extrair.

Gzip:

    tar -tzf documentos.tar.gz

Bzip2:

    tar -tjf documentos.tar.bz2

XZ:

    tar -tJf documentos.tar.xz

---

## 11. Extrair apenas um arquivo

Imagine que o arquivo contenha:

    documentos/
    documentos/linux.txt
    documentos/redes.txt
    documentos/comandos.txt

Podemos extrair somente `linux.txt`:

    tar -xf documentos.tar documentos/linux.txt

Com arquivo `.tar.gz`:

    tar -xzf documentos.tar.gz documentos/linux.txt

---

## 12. Ver detalhes durante a operação

`-v` — **verbose — detalhado**.

    tar -cvf documentos.tar documentos/

Mostra os arquivos enquanto são adicionados.

Para extrair mostrando os arquivos:

    tar -xvf documentos.tar

---

## 13. Opções principais

| Opção | Inglês | Português |
|---|---|---|
| `-c` | create | criar |
| `-x` | extract | extrair |
| `-t` | list | listar |
| `-f` | file | especificar arquivo |
| `-v` | verbose | mostrar detalhes |
| `-z` | gzip | usar gzip |
| `-j` | bzip2 | usar bzip2 |
| `-J` | xz | usar xz |
| `-C` | change directory | mudar diretório |

---

## 14. `tar` não é apenas compressão

Essa diferença é muito importante:

    tar → arquiva/reúne arquivos
    gzip → comprime
    bzip2 → comprime
    xz → comprime

Por exemplo:

    tar -cf backup.tar documentos/

Cria um arquivo de arquivamento, **sem compressão**.

Já:

    tar -czf backup.tar.gz documentos/

Faz:

    tar + gzip

---

## 15. Backup com `tar`

Um exemplo comum:

    tar -czf backup.tar.gz /home/usuario/documentos/

Para restaurar:

    tar -xzf backup.tar.gz

---

## 16. Verificar o conteúdo antes de extrair

É uma boa prática listar primeiro:

    tar -tzf backup.tar.gz

Depois extrair:

    tar -xzf backup.tar.gz

Assim podemos verificar quais arquivos estão dentro do archive.

---

## Resumo LPIC-1

| Comando | Função |
|---|---|
| `tar -cf arquivo.tar dir/` | criar archive |
| `tar -tf arquivo.tar` | listar conteúdo |
| `tar -xf arquivo.tar` | extrair |
| `tar -czf arquivo.tar.gz dir/` | criar com gzip |
| `tar -xzf arquivo.tar.gz` | extrair gzip |
| `tar -cjf arquivo.tar.bz2 dir/` | criar com bzip2 |
| `tar -xjf arquivo.tar.bz2` | extrair bzip2 |
| `tar -cJf arquivo.tar.xz dir/` | criar com xz |
| `tar -xJf arquivo.tar.xz` | extrair xz |
| `tar -C` | definir diretório de destino |
| `tar -v` | mostrar detalhes |

**Memorize principalmente:**

    c → create   → criar
    x → extract  → extrair
    t → list     → listar
    f → file     → arquivo
    v → verbose  → detalhado

    z → gzip
    j → bzip2
    J → xz

**Combinações mais importantes:**

    tar -czf → criar .tar.gz
    tar -xzf → extrair .tar.gz

    tar -cjf → criar .tar.bz2
    tar -xjf → extrair .tar.bz2

    tar -cJf → criar .tar.xz
    tar -xJf → extrair .tar.xz

**Regra simples:**

    tar  → reúne
    gzip → comprime

    tar + gzip → .tar.gz

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
