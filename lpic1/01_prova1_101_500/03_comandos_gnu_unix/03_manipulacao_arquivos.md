# Comandos GNU/UNIX

## 03 — Manipulação de Arquivos

### File Manipulation — Manipulação de Arquivos

No Linux, os principais comandos para criar, copiar, mover, renomear e remover arquivos e diretórios são:

    touch
    cp
    mv
    rm
    mkdir
    rmdir

---

## touch — Tocar/Criar Arquivo

**touch — Tocar** cria um arquivo vazio quando ele não existe.

    touch arquivo.txt

Também pode atualizar a data e hora de modificação de um arquivo existente.

---

## mkdir — Make Directory — Criar Diretório

Cria um diretório.

    mkdir documentos

Criar vários diretórios:

    mkdir fotos vídeos projetos

### `-p` — parents — diretórios pais

Cria toda a estrutura necessária:

    mkdir -p projetos/linux/comandos

Resultado:

    projetos/
    └── linux/
        └── comandos/

---

## cp — Copy — Copiar

Copia arquivos ou diretórios.

### Copiar arquivo

    cp arquivo.txt backup.txt

### Copiar para outro diretório

    cp arquivo.txt documentos/

### `-r` — recursive — recursivo

Copia diretórios e seu conteúdo:

    cp -r documentos backup/

### `-i` — interactive — interativo

Pergunta antes de sobrescrever:

    cp -i arquivo.txt documentos/

### `-v` — verbose — detalhado

Mostra o que está sendo copiado:

    cp -v arquivo.txt documentos/

---

## mv — Move — Mover

Move ou renomeia arquivos e diretórios.

### Mover

    mv arquivo.txt documentos/

### Renomear

    mv antigo.txt novo.txt

O mesmo comando realiza as duas operações porque, no Linux, renomear significa alterar o nome dentro do mesmo sistema de arquivos.

### `-i` — interactive — interativo

    mv -i arquivo.txt documentos/

Pergunta antes de sobrescrever.

### `-v` — verbose — detalhado

    mv -v arquivo.txt documentos/

---

## rm — Remove — Remover

Remove arquivos.

    rm arquivo.txt

### `-i` — interactive — interativo

    rm -i arquivo.txt

Pede confirmação antes de remover.

### `-r` — recursive — recursivo

Remove diretórios e seu conteúdo:

    rm -r documentos/

### `-f` — force — forçar

Não pede confirmação e ignora arquivos inexistentes:

    rm -f arquivo.txt

**Cuidado:** `rm` normalmente não envia arquivos para uma lixeira. A remoção pode ser permanente.

---

## rmdir — Remove Directory — Remover Diretório

Remove um diretório **vazio**.

    rmdir documentos

Se o diretório possuir arquivos, o `rmdir` não o removerá.

Para diretórios com conteúdo:

    rm -r documentos/

---

## Arquivos Ocultos

No Linux, arquivos cujo nome começa com `.` são normalmente considerados ocultos.

Exemplo:

    .bashrc
    .profile
    .config/

Listar incluindo arquivos ocultos:

    ls -a

- `-a` — all — todos

---

## Wildcards — Caracteres Coringa

Os curingas podem ser usados para manipular vários arquivos.

### `*` — qualquer quantidade de caracteres

    cp *.txt backup/

### `?` — exatamente um caractere

    mv arquivo?.txt documentos/

### `[ ]` — conjunto de caracteres

    rm arquivo[1-3].txt

O shell expande esses padrões antes de executar o comando.

---

## Opções importantes

| Opção | Inglês | Português |
|---|---|---|
| `-a` | all | todos |
| `-f` | force | forçar |
| `-i` | interactive | interativo |
| `-p` | parents | diretórios pais |
| `-r` | recursive | recursivo |
| `-v` | verbose | detalhado |

---

## Exemplo prático

Criar estrutura:

    mkdir -p projeto/documentos

Criar arquivo:

    touch projeto/documentos/arquivo.txt

Copiar:

    cp projeto/documentos/arquivo.txt backup.txt

Renomear:

    mv backup.txt copia.txt

Remover:

    rm copia.txt

---

## Resumo LPIC-1

- `touch` = criar arquivo vazio ou atualizar timestamps.
- `mkdir` = criar diretório.
- `mkdir -p` = criar diretórios pais necessários.
- `cp` = copiar.
- `cp -r` = copiar diretórios recursivamente.
- `mv` = mover ou renomear.
- `rm` = remover arquivos.
- `rm -r` = remover diretório e conteúdo recursivamente.
- `rm -f` = forçar remoção.
- `rmdir` = remover diretório vazio.
- `ls -a` = mostrar arquivos ocultos.
- `*` = qualquer quantidade de caracteres.
- `?` = exatamente um caractere.
- `[ ]` = conjunto de caracteres.
- **Recursive — Recursivo** = executar a operação também dentro dos subdiretórios.
- `rm` não utiliza uma lixeira por padrão.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
