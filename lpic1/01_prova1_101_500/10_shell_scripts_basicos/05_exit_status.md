# 10 — Shell e Scripts Básicos

## 05 — Exit Status

**Exit Status — Status de Saída**

O **Exit Status** é o código retornado por um comando quando ele termina.

Ele informa ao Bash se o comando foi executado com sucesso ou se ocorreu algum problema.

---

### 1. Código 0

Por convenção:

    0 = sucesso

Exemplo:

    ls
    echo $?

Se `ls` for executado corretamente:

    0

---

### 2. Código diferente de 0

Um valor diferente de `0` normalmente indica erro ou alguma condição diferente de sucesso.

Exemplo:

    ls /diretorio-inexistente
    echo $?

Resultado:

    2

O número exato depende do comando.

**Importante:** qualquer valor diferente de `0` indica que o comando não terminou com status de sucesso.

---

### 3. `$?`

`$?` é uma variável especial do Bash.

**`$?` — Exit Status — Status de Saída**

Ela contém o status de saída do **último comando executado**.

Exemplo:

    pwd
    echo $?

Depois de outro comando:

    ls
    echo $?

O valor de `$?` será atualizado.

---

### 4. Verificar sucesso ou erro

Podemos usar o status em um script:

    ls /tmp

    if [ $? -eq 0 ]; then
        echo "Comando executado com sucesso"
    else
        echo "Erro na execução"
    fi

- `-eq` — Equal — Igual.

Uma forma melhor é testar o comando diretamente:

    if ls /tmp; then
        echo "Sucesso"
    else
        echo "Erro"
    fi

---

### 5. `exit`

**exit — Exit Shell/Script — Encerrar Shell/Script**

Podemos definir o status de saída de um script:

    exit 0

Indica sucesso.

Exemplo:

    echo "Tudo certo"
    exit 0

Ou:

    exit 1

Indica uma condição de erro.

---

### 6. Exemplo de script

    #!/bin/bash

    arquivo="/tmp/teste.txt"

    if [ -f "$arquivo" ]; then
        echo "Arquivo encontrado"
        exit 0
    else
        echo "Arquivo não encontrado"
        exit 1
    fi

- `-f` — Regular File — Arquivo regular.
- `0` — sucesso.
- `1` — erro/condição definida pelo script.

---

### 7. Status de comandos encadeados

O status pode controlar a execução de outros comandos.

**`&&` — AND — E**

Executa o segundo comando somente se o primeiro tiver status `0`.

    mkdir teste && echo "Diretório criado"

**`||` — OR — OU**

Executa o segundo comando se o primeiro tiver status diferente de `0`.

    mkdir teste || echo "Erro ao criar diretório"

---

### 8. `true` e `false`

O Bash possui comandos simples para representar sucesso e falha.

    true
    echo $?

Resultado:

    0

E:

    false
    echo $?

Resultado:

    1

Eles são úteis em testes e scripts.

---

### 9. `return` × `exit`

**`exit` — Encerrar**

Encerra o Shell ou o script atual.

    exit 1

**`return` — Retornar**

Retorna um status de uma função ou de um script que foi carregado com `source`.

Exemplo:

    minha_funcao() {
        return 1
    }

    minha_funcao
    echo $?

Resultado:

    1

---

## Resumo LPIC-1

- **Exit Status** informa como um comando terminou.
- `0` normalmente significa **sucesso**.
- Valor diferente de `0` normalmente indica **erro ou outra condição**.
- `$?` mostra o status do último comando.
- `exit 0` encerra com sucesso.
- `exit 1` encerra com status `1`.
- `&&` executa o próximo comando somente se o anterior tiver sucesso.
- `||` executa o próximo comando se o anterior falhar.
- `true` retorna `0`.
- `false` retorna `1`.
- `exit` encerra o script/Shell.
- `return` retorna um status de uma função.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
