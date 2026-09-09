# Comandos GNU/UNIX

## 13 — Links

**Link — Link / Ligação**

Um **link** permite acessar um arquivo ou diretório por outro caminho.

No Linux existem dois tipos principais:

| Tipo | Nome em inglês | Funcionamento |
|---|---|---|
| **Hard Link** | Hard Link — Link Físico | Aponta para o mesmo inode do arquivo |
| **Symbolic Link** | Symbolic Link — Link Simbólico | Aponta para o caminho de outro arquivo |

---

### 1. Hard Link — Link Físico

Um **Hard Link** é outro nome para o mesmo arquivo.

Os dois nomes apontam para o **mesmo inode** e compartilham os mesmos dados.

Criar:

    ln arquivo.txt copia.txt

Verificar:

    ls -li

Exemplo:

    123456 -rw-r--r-- 2 usuario usuario 100 arquivo.txt
    123456 -rw-r--r-- 2 usuario usuario 100 copia.txt

O mesmo número de inode indica que são Hard Links do mesmo arquivo.

### Características

- Compartilha o mesmo inode.
- Compartilha os mesmos dados.
- Alterar um altera o conteúdo visto pelo outro.
- Remover um nome não remove os dados enquanto existir outro Hard Link.
- Normalmente não pode apontar para diretórios.
- Não pode atravessar sistemas de arquivos diferentes.

---

### 2. Symbolic Link — Link Simbólico

Um **Symbolic Link** é um arquivo especial que aponta para outro caminho.

Criar:

    ln -s arquivo.txt atalho.txt

Verificar:

    ls -l

Resultado semelhante a:

    atalho.txt -> arquivo.txt

### Características

- Possui inode próprio.
- Guarda o caminho do destino.
- Pode apontar para arquivos ou diretórios.
- Pode atravessar sistemas de arquivos diferentes.
- Pode ficar quebrado se o destino for removido ou movido.

---

## 3. `ln` — Link — criar links

Sintaxe:

    ln [opção] origem destino

### Criar Hard Link

    ln arquivo.txt copia.txt

### Criar Symbolic Link

    ln -s arquivo.txt atalho.txt

### Opções importantes

| Opção | English | Português |
|---|---|---|
| `-s` | symbolic | simbólico |
| `-f` | force | forçar |
| `-i` | interactive | perguntar antes |
| `-v` | verbose | mostrar o que está sendo feito |

Exemplo:

    ln -sv arquivo.txt atalho.txt

---

## 4. Verificar links

### `ls -l`

    ls -l atalho.txt

Exemplo:

    lrwxrwxrwx 1 usuario usuario 11 set 8 20:00 atalho.txt -> arquivo.txt

O primeiro caractere `l` indica **Symbolic Link — Link Simbólico**.

---

### `ls -i`

    ls -i arquivo.txt copia.txt

Mostra o **inode**.

Se os números forem iguais:

    123456 arquivo.txt
    123456 copia.txt

São Hard Links.

---

### `readlink`

**readlink — ler o destino de um link**

    readlink atalho.txt

Resultado:

    arquivo.txt

Para obter o caminho completo:

    readlink -f atalho.txt

`-f` — canonicalize/follow — resolver o caminho completo seguindo os links.

---

## 5. Remover um link

Use:

    rm atalho.txt

Ao remover um **Symbolic Link**, o arquivo original não é removido.

Para um Hard Link:

    rm copia.txt

O arquivo continuará existindo se ainda houver outro nome apontando para o mesmo inode.

---

## 6. Hard Link × Symbolic Link

| Característica | Hard Link | Symbolic Link |
|---|---|---|
| Mesmo inode? | Sim | Não |
| Aponta para | Inode | Caminho |
| Pode apontar para diretório? | Normalmente não | Sim |
| Pode cruzar sistemas de arquivos? | Não | Sim |
| Quebra se destino for removido? | Não | Sim |
| Criado com | `ln` | `ln -s` |

### Visualização

    arquivo.txt
        │
        └── mesmo inode
              ├── arquivo.txt
              └── copia.txt

Symbolic Link:

    atalho.txt ──────> arquivo.txt

---

## 7. Exemplo prático

Criar arquivo:

    echo "Linux" > arquivo.txt

Criar Hard Link:

    ln arquivo.txt hard.txt

Criar Symbolic Link:

    ln -s arquivo.txt simbolico.txt

Verificar:

    ls -li

Testar:

    cat arquivo.txt
    cat hard.txt
    cat simbolico.txt

Os três exibem:

    Linux

---

## 8. Inode — Inode / Estrutura do Arquivo

O **inode** guarda informações sobre o arquivo, como:

- permissões;
- proprietário;
- grupo;
- tamanho;
- timestamps;
- localização dos dados;
- quantidade de Hard Links.

O nome do arquivo não fica armazenado no inode.

Por isso, vários nomes podem apontar para o mesmo inode através de **Hard Links**.

---

## Resumo LPIC-1

- `ln arquivo link` → cria **Hard Link**.
- `ln -s arquivo link` → cria **Symbolic Link**.
- Hard Link → mesmo inode.
- Symbolic Link → aponta para um caminho.
- `ls -i` → mostra o inode.
- `ls -l` → mostra detalhes e o destino de links simbólicos.
- `readlink` → mostra para onde um link aponta.
- Hard Link não atravessa sistemas de arquivos.
- Symbolic Link pode apontar para diretórios e atravessar sistemas de arquivos.
- Remover um Symbolic Link não remove o arquivo original.
- Um arquivo só deixa de existir quando não há mais referências válidas a seus dados.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
