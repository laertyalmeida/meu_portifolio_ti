# Comandos GNU/UNIX

## 02 — Navegação no Sistema

### Navigation — Navegação

**Navigation — Navegação** é o uso de comandos para percorrer diretórios, descobrir onde você está e acessar arquivos no sistema Linux.

A estrutura básica começa na:

    /
    ├── home
    ├── etc
    ├── var
    ├── usr
    └── tmp

- `/` — root — raiz do sistema
- `/home` — diretórios pessoais
- `/etc` — arquivos de configuração
- `/var` — dados variáveis
- `/usr` — programas e recursos do sistema
- `/tmp` — arquivos temporários

---

## pwd — Print Working Directory — Mostrar Diretório de Trabalho

    pwd

Mostra o diretório atual.

Exemplo:

    /home/laerte

---

## ls — List — Listar

    ls

Lista arquivos e diretórios do local atual.

### Opções importantes

    ls -l

- `-l` — long — formato detalhado

    ls -a

- `-a` — all — todos, incluindo arquivos ocultos

    ls -la

- `-l` — long — detalhado
- `-a` — all — todos

    ls -lh

- `-h` — human-readable — formato legível para humanos

---

## cd — Change Directory — Mudar de Diretório

Usado para entrar em outro diretório.

    cd /home

Voltar para o diretório pessoal:

    cd ~

- `~` — home — diretório pessoal do usuário

Voltar ao diretório anterior:

    cd -

Subir um nível:

    cd ..

- `..` — parent directory — diretório pai

Ir para a raiz:

    cd /

- `/` — root — raiz

---

## Caminho Absoluto

### Absolute Path — Caminho Absoluto

Começa na raiz `/`.

Exemplo:

    cd /home/laerte/documentos

O caminho é independente do diretório atual.

---

## Caminho Relativo

### Relative Path — Caminho Relativo

É interpretado a partir do diretório atual.

Exemplo:

    cd documentos

Se estiver em:

    /home/laerte

o comando leva para:

    /home/laerte/documentos

---

## `.` e `..`

### `.` — Current Directory — Diretório Atual

    ls .

Lista o diretório atual.

### `..` — Parent Directory — Diretório Pai

    ls ..

Lista o diretório acima do atual.

Exemplo:

    /home/laerte/documentos

    cd ..

Resultado:

    /home/laerte

---

## `~` — Home Directory — Diretório Pessoal

O caractere `~` representa o diretório pessoal do usuário.

Exemplo:

    cd ~

ou:

    cd /home/laerte

Os dois podem levar ao mesmo local quando `/home/laerte` é o diretório pessoal do usuário.

Ver:

    echo $HOME

- `$HOME` — variável que contém o diretório pessoal.

---

## Comandos úteis para navegação

### tree — Árvore

    tree

Mostra diretórios em formato de árvore, quando o comando está instalado.

Exemplo:

    .
    ├── documentos
    ├── imagens
    └── projetos

---

### file — Arquivo

    file arquivo.txt

Identifica o tipo do arquivo.

---

### realpath — Caminho Real

    realpath arquivo.txt

Mostra o caminho absoluto do arquivo.

---

## Tab — Autocompletar

A tecla `Tab` completa nomes de arquivos e diretórios.

Exemplo:

    cd Doc<Tab>

Pode completar para:

    cd Documentos/

Isso reduz erros de digitação e torna a navegação mais rápida.

---

## Atalhos de navegação

| Comando | Função |
|---|---|
| `pwd` | Mostrar diretório atual |
| `ls` | Listar conteúdo |
| `ls -la` | Listar tudo em formato detalhado |
| `cd /` | Ir para a raiz |
| `cd ~` | Ir para o diretório pessoal |
| `cd ..` | Subir um nível |
| `cd -` | Voltar ao diretório anterior |
| `tree` | Mostrar estrutura em árvore |
| `realpath` | Mostrar caminho absoluto |

---

## Resumo LPIC-1

- **Navigation — Navegação** = movimentação entre diretórios.
- `pwd` = mostra onde você está.
- `ls` = lista arquivos e diretórios.
- `cd` = muda de diretório.
- `/` = raiz do sistema.
- `~` = diretório pessoal.
- `.` = diretório atual.
- `..` = diretório pai.
- `cd -` = volta ao diretório anterior.
- **Absolute Path — Caminho Absoluto** começa em `/`.
- **Relative Path — Caminho Relativo** depende do diretório atual.
- `Tab` = autocompletar.
- `tree` = visualizar estrutura em árvore.
- `realpath` = mostrar caminho absoluto.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
