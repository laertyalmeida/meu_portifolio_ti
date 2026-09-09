# Comandos GNU/UNIX

## 10 — Pipe e Redirecionamentos

**Pipe (|) — Canal** e **Redirection — Redirecionamento** permitem conectar comandos e controlar para onde a entrada e a saída de um comando serão enviadas.

São conceitos fundamentais do Linux e muito importantes para o LPIC-1.

---

## 1. Entrada e saída padrão

Todo processo possui, normalmente, três fluxos:

| Número | Nome | Português | Função |
|---|---|---|---|
| `0` | stdin | entrada padrão | recebe dados |
| `1` | stdout | saída padrão | mostra resultado |
| `2` | stderr | saída de erro | mostra erros |

Por padrão:

    stdin  → teclado
    stdout → terminal
    stderr → terminal

---

## 2. `>` — Redirecionamento de saída

Envia a saída para um arquivo.

    ls > arquivos.txt

Em vez de aparecer no terminal, o resultado será gravado em:

    arquivos.txt

**Importante:** `>` cria o arquivo ou **sobrescreve** seu conteúdo se ele já existir.

Exemplo:

    echo "Linux" > sistema.txt

Depois:

    cat sistema.txt

Resultado:

    Linux

---

## 3. `>>` — Append — adicionar

Adiciona a saída **no final do arquivo**, sem apagar o conteúdo existente.

    echo "GNU/Linux" >> sistema.txt

Agora o arquivo pode conter:

    Linux
    GNU/Linux

**Diferença:**

    >   → sobrescreve
    >>  → adiciona no final

---

## 4. `<` — Redirecionamento de entrada

Faz um comando receber a entrada de um arquivo.

    comando < arquivo.txt

Exemplo:

    wc -l < arquivo.txt

O `wc` recebe o conteúdo do arquivo através da entrada padrão.

---

## 5. `2>` — Redirecionar erros

O número `2` representa **stderr — saída de erro**.

    comando 2> erros.txt

Os erros serão enviados para `erros.txt`.

Exemplo:

    ls /diretorio_inexistente 2> erros.txt

O erro não será mostrado no terminal; será gravado no arquivo.

---

## 6. `2>>` — Adicionar erros

Adiciona os erros ao final do arquivo:

    comando 2>> erros.txt

---

## 7. `&>` — stdout + stderr

Redireciona **saída normal e erros** para o mesmo arquivo.

    comando &> resultado.txt

Assim:

    stdout → resultado.txt
    stderr → resultado.txt

---

## 8. `2>&1` — juntar stderr com stdout

`2>&1` significa:

    stderr → mesmo destino de stdout

Exemplo:

    comando > resultado.txt 2>&1

Resultado:

    stdout → resultado.txt
    stderr → resultado.txt

Essa forma é muito comum em scripts e administração Linux.

---

## 9. `|` — Pipe — canal

O pipe envia a **saída de um comando como entrada do próximo**.

    comando1 | comando2

Exemplo:

    ls | grep ".txt"

Fluxo:

    ls
      ↓
    stdout
      ↓
      |
      ↓
    grep
      ↓
    resultado

---

## 10. Vários pipes

Podemos conectar vários comandos.

    cat arquivo.txt | grep "Linux" | wc -l

Fluxo:

    cat
     ↓
    grep
     ↓
    wc

Nesse exemplo:

1. `cat` mostra o arquivo.
2. `grep` seleciona as linhas contendo `Linux`.
3. `wc -l` conta essas linhas.

---

## 11. Pipe com `grep`

Muito comum no Linux:

    ps aux | grep "bash"

O `ps` mostra os processos e o `grep` filtra aqueles que contêm `bash`.

Outro exemplo:

    ls -l /etc | grep ".conf"

Mostra apenas linhas relacionadas aos arquivos `.conf`.

---

## 12. Pipe com `head` e `tail`

Mostrar os primeiros resultados:

    ls -l | head

Mostrar os últimos:

    ls -l | tail

Mostrar apenas as primeiras 5 linhas:

    ls -l | head -n 5

---

## 13. `tee` — dividir a saída

`tee` recebe uma saída e a envia **para o terminal e para um arquivo ao mesmo tempo**.

    comando | tee arquivo.txt

Exemplo:

    ls -l | tee arquivos.txt

O resultado aparece no terminal e também é salvo em `arquivos.txt`.

Adicionar ao arquivo:

    comando | tee -a arquivo.txt

`-a` — append — adicionar.

---

## 14. `xargs` — argumentos a partir da entrada

`xargs` transforma dados recebidos pela entrada padrão em **argumentos para outro comando**.

Exemplo:

    echo "arquivo1 arquivo2" | xargs rm

É importante entender que `xargs` **não é um pipe**.

O pipe transporta dados:

    comando1 | comando2

O `xargs` utiliza esses dados para montar argumentos:

    comando | xargs outro_comando

---

## 15. Redirecionamento + Pipe

Podemos combinar os conceitos.

Exemplo:

    cat arquivo.txt | grep "Linux" > resultado.txt

Fluxo:

    arquivo.txt
         ↓
        cat
         ↓
        grep
         ↓
    resultado.txt

O resultado final do `grep` é salvo no arquivo.

---

## 16. ` /dev/null ` — dispositivo nulo

`/dev/null` — **Null Device — Dispositivo Nulo**.

Tudo que for enviado para ele é descartado.

Exemplo:

    comando > /dev/null

A saída normal será descartada.

Descartar erros:

    comando 2> /dev/null

Descartar saída e erros:

    comando > /dev/null 2>&1

Muito usado quando não queremos visualizar determinada saída.

---

## Resumo dos redirecionamentos

| Símbolo | Função |
|---|---|
| `>` | envia stdout e sobrescreve |
| `>>` | envia stdout e adiciona |
| `<` | recebe entrada de arquivo |
| `2>` | envia stderr para arquivo |
| `2>>` | adiciona stderr ao arquivo |
| `&>` | envia stdout + stderr |
| `2>&1` | envia stderr para o mesmo destino de stdout |
| `|` | envia stdout para stdin de outro comando |
| `tee` | envia saída para terminal e arquivo |
| `/dev/null` | descarta dados |

---

## Resumo LPIC-1

**Fluxos padrão:**

    0 → stdin  → entrada
    1 → stdout → saída normal
    2 → stderr → erro

**Redirecionamentos:**

    >       → sobrescrever arquivo
    >>      → adicionar ao arquivo
    <       → entrada a partir de arquivo
    2>      → redirecionar erros
    2>>     → adicionar erros
    2>&1    → juntar erro com saída
    &>      → saída + erro

**Pipe:**

    comando1 | comando2

    stdout do comando1
            ↓
          pipe
            ↓
    stdin do comando2

**Comandos importantes:**

    |       → conectar comandos
    tee     → salvar e mostrar saída
    xargs   → transformar entrada em argumentos
    /dev/null → descartar saída

**Memorize principalmente:**

    >   → sobrescreve
    >>  → adiciona
    |   → conecta comandos
    2>  → redireciona erros
    2>&1 → junta erros com a saída
    &>  → saída + erros
    <   → entrada
    /dev/null → descarta

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
