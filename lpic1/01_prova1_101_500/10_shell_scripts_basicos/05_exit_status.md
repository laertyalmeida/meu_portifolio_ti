# 10 — Shell e Scripts Básicos
## 05 — Exit Status

### Exit Status — Status de saída

Todo comando executado no Bash retorna um número chamado **Exit Status — Status de saída**.

Esse valor indica se o comando foi executado com sucesso ou se ocorreu algum problema.

---

## 1. Ver o Exit Status

Use:

    echo $?

Exemplo:

    ls /home

    echo $?

Se funcionar:

    0

---

## 2. Código 0

**0 → sucesso**

Exemplo:

    mkdir teste

    echo $?

Resultado:

    0

---

## 3. Código diferente de 0

Um valor diferente de `0` normalmente indica erro ou alguma condição diferente de sucesso.

Exemplo:

    ls /diretorio-inexistente

    echo $?

Resultado semelhante a:

    2

O código exato depende do comando.

---

## 4. Exit Status em Scripts

Um script também pode retornar um status.

Use:

    exit 0

Indica sucesso.

Para indicar erro:

    exit 1

---

## 5. Verificar sucesso ou erro

O Exit Status pode ser usado em condições:

    comando

    if [ $? -eq 0 ]; then
        echo "Sucesso"
    else
        echo "Erro"
    fi

**-eq — equal (igual)**

---

## 6. Status do último comando

O `$?` sempre representa o status do **último comando executado**.

Exemplo:

    ls

    echo $?

Depois de executar outro comando:

    pwd

    echo $?

O `$?` agora corresponde ao `pwd`.

---

## 🎯 Para a LPIC-1

    0
    ↓
    sucesso

    != 0
    ↓
    erro/condição diferente de sucesso

Consultar:

    echo $?

Definir em um script:

    exit 0
    exit 1

**`$?` → Exit Status do último comando.**

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
