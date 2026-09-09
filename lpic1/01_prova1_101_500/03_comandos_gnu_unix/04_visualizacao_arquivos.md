# Comandos GNU/UNIX

## 04 — Visualização de Arquivos

Visualização de arquivos é saber **ler o conteúdo de um arquivo pelo terminal**, sem precisar abrir um editor.

---

### `cat` — Concatenate — concatenar/exibir

Mostra o conteúdo completo do arquivo.

    cat arquivo.txt

Também pode mostrar vários arquivos:

    cat arquivo1.txt arquivo2.txt

**Opções importantes:**

| Opção | Inglês | Português |
|---|---|---|
| `-n` | number | numerar as linhas |
| `-b` | number nonblank | numerar apenas linhas não vazias |
| `-A` | show all | mostrar caracteres especiais |

Exemplo:

    cat -n arquivo.txt

---

### `less` — menos

Permite visualizar arquivos grandes **página por página**.

    less arquivo.txt

Controles principais dentro do `less`:

| Tecla | Ação |
|---|---|
| `Space` | avançar uma página |
| `b` | voltar uma página |
| `↑` / `↓` | subir/descer |
| `/texto` | pesquisar |
| `n` | próximo resultado |
| `q` | sair |

**Muito importante para o LPIC-1:** `less` não carrega necessariamente todo o arquivo na tela de uma vez e é muito útil para arquivos grandes.

---

### `more` — mais

Também mostra o arquivo página por página.

    more arquivo.txt

É mais simples que `less`.

**Comparação:**

| Comando | Uso |
|---|---|
| `cat` | arquivo pequeno ou conteúdo completo |
| `less` | arquivos grandes e navegação |
| `more` | visualização página por página |

---

### `head` — cabeça/início

Mostra as **primeiras linhas** de um arquivo.

    head arquivo.txt

Por padrão, mostra **10 linhas**.

Mostrar uma quantidade específica:

    head -n 5 arquivo.txt

Ou:

    head -5 arquivo.txt

**Opção:**

| Opção | Inglês | Português |
|---|---|---|
| `-n` | number | quantidade de linhas |

---

### `tail` — cauda/final

Mostra as **últimas linhas** de um arquivo.

    tail arquivo.txt

Por padrão, mostra **10 linhas**.

Mostrar as últimas 5 linhas:

    tail -n 5 arquivo.txt

---

### `tail -f` — acompanhar arquivo em tempo real

Muito usado para acompanhar **logs**.

    tail -f /var/log/syslog

O terminal permanece mostrando novas linhas que forem adicionadas ao arquivo.

Para sair:

    Ctrl + C

`-f` — follow — acompanhar/seguir.

---

### Visualizando arquivos de configuração

Exemplo:

    cat /etc/hostname

    less /etc/passwd

    head /etc/passwd

    tail /etc/passwd

---

### `wc` — Word Count — contagem de palavras

Conta linhas, palavras e bytes/caracteres de um arquivo.

    wc arquivo.txt

Saída típica:

    20  50  350 arquivo.txt

Significa:

    20 → linhas
    50 → palavras
    350 → bytes

**Opções:**

| Opção | Inglês | Português |
|---|---|---|
| `-l` | lines | linhas |
| `-w` | words | palavras |
| `-c` | bytes | bytes |
| `-m` | characters | caracteres |

Exemplos:

    wc -l arquivo.txt

    wc -w arquivo.txt

    wc -c arquivo.txt

---

### `file` — arquivo/tipo do arquivo

Identifica o tipo do conteúdo de um arquivo.

    file arquivo.txt

Exemplo:

    file imagem.png

Pode informar que o arquivo é uma imagem PNG, texto, executável, arquivo compactado etc.

---

## Exemplo prático

Criar um arquivo:

    touch notas.txt

Adicionar conteúdo:

    echo "Linux é poderoso" > notas.txt

Visualizar:

    cat notas.txt

Ver apenas o início:

    head notas.txt

Ver o final:

    tail notas.txt

Contar linhas:

    wc -l notas.txt

Identificar o tipo:

    file notas.txt

---

## Resumo LPIC-1

| Comando | Função |
|---|---|
| `cat` | exibir conteúdo |
| `less` | visualizar página por página |
| `more` | visualizar página por página |
| `head` | mostrar início |
| `tail` | mostrar final |
| `tail -f` | acompanhar alterações em tempo real |
| `wc` | contar linhas, palavras e bytes |
| `file` | identificar o tipo do arquivo |

**Memorize principalmente:**

    cat    → conteúdo completo
    less   → navegar pelo arquivo
    head   → começo
    tail   → final
    tail -f → acompanhar em tempo real
    wc     → contar
    file   → identificar tipo

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
