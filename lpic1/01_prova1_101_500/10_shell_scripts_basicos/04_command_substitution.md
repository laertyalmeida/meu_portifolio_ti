# 10 — Shell e Scripts Básicos
## 04 — Command Substitution

### Command Substitution — Substituição de comandos

**Command Substitution** permite executar um comando e usar seu resultado dentro de outro comando.

A forma recomendada é:

    $(comando)

---

## 1. Exemplo básico

    echo "Hoje é $(date)"

O Bash:

1. executa `date`;
2. pega o resultado;
3. coloca o resultado dentro do `echo`.

---

## 2. Armazenar o resultado

    data=$(date)

    echo "$data"

A variável recebe a saída do comando.

---

## 3. Usando comandos

Exemplo:

    arquivos=$(ls)

    echo "$arquivos"

Outro exemplo:

    diretorio=$(pwd)

    echo "$diretorio"

---

## 4. Forma antiga

Também existe a sintaxe:

    `comando`

Exemplo:

    data=`date`

Funciona, mas a forma moderna e recomendada é:

    data=$(date)

---

## 5. Combinando com variáveis

    usuario=$(whoami)

    echo "Usuário: $usuario"

Resultado semelhante a:

    Usuário: laerte

---

## 🎯 Para a LPIC-1

**Command Substitution — Substituição de comandos**

    $(comando)

→ executa o comando e substitui pela saída.

Forma antiga:

    `comando`

Prefira:

    $(comando)

### Exemplo

    kernel=$(uname -r)

    echo "$kernel"

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
