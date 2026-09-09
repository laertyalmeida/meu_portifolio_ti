# 10 — Shell e Scripts Básicos

## 04 — Command Substitution

**Command Substitution — Substituição de Comando**

É o recurso do Bash que permite **executar um comando e usar o resultado dele dentro de outro comando**.

A forma recomendada é:

    $(comando)

---

### 1. Exemplo básico

    echo "Hoje é $(date)"

O Bash:

1. executa `date`;
2. pega o resultado;
3. coloca o resultado dentro do `echo`.

Exemplo de resultado:

    Hoje é Wed Sep 9 12:00:00 BRT 2026

---

### 2. Armazenar o resultado

Podemos guardar o resultado em uma variável:

    data=$(date)

    echo "$data"

Outro exemplo:

    usuario=$(whoami)

    echo "Usuário: $usuario"

---

### 3. Usar comandos dentro de comandos

Exemplo:

    echo "Estou em $(pwd)"

Resultado:

    Estou em /home/laerte

Outro exemplo:

    echo "Arquivos: $(ls)"

---

### 4. Forma antiga

O Bash também possui uma sintaxe antiga:

    `comando`

Exemplo:

    data=`date`

Ela funciona, mas é menos recomendada.

Prefira:

    data=$(date)

### Por quê?

`$(...)` é mais fácil de ler e permite aninhar comandos.

Exemplo:

    echo "$(date +%Y)"

---

### 5. Command Substitution aninhado

**Nested Command Substitution — Substituição de Comando Aninhada**

Podemos colocar uma substituição dentro de outra:

    echo "$(basename "$(pwd)")"

Aqui:

- `pwd` — mostra o diretório atual;
- `basename` — obtém o último componente do caminho;
- `$(...)` — substitui cada resultado.

---

### 6. Usar em condições e scripts

Exemplo:

    arquivos=$(ls | wc -l)

    echo "Quantidade de linhas: $arquivos"

Outro exemplo:

    diretorio=$(pwd)

    if [ "$diretorio" = "/home/laerte" ]; then
        echo "Diretório correto"
    fi

---

### 7. Diferença entre `$(...)` e variável

    nome="Laerte"

Aqui `nome` recebe um **valor definido diretamente**.

Já:

    usuario=$(whoami)

`usuario` recebe o **resultado de um comando**.

---

### 8. Command Substitution remove quebras de linha

Quando o resultado de um comando é colocado em `$(...)`, as **quebras de linha finais** são removidas.

Exemplo:

    resultado=$(printf "A\nB\n")

O valor armazenado será equivalente a:

    A
    B

As quebras de linha internas são preservadas.

---

### 9. Command Substitution × Quoting

É possível combinar substituição de comando com aspas:

    echo "$(date)"

As aspas preservam o resultado como um único argumento.

Também podemos fazer:

    arquivo="$(pwd)/teste.txt"

E depois:

    cat "$arquivo"

Essa combinação é muito comum em scripts Bash.

---

## Resumo LPIC-1

- **Command Substitution** executa um comando e utiliza seu resultado.
- Sintaxe recomendada: `$(comando)`.
- Sintaxe antiga: `` `comando` ``.
- `$(...)` é mais legível e permite aninhamento.
- O resultado pode ser armazenado em uma variável:
  `resultado=$(comando)`.
- Pode ser usado dentro de `echo`, variáveis, condições e outros comandos.
- `"$(comando)"` mantém o resultado como um único argumento.
- Quebras de linha finais do resultado são removidas.
- É muito utilizado em **Bash Scripts**.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
