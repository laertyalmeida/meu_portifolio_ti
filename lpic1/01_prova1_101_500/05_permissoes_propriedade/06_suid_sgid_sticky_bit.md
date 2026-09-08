# 06 — SUID, SGID e Sticky Bit

## Special Permissions — Permissões Especiais

Além de `rwx`, o Linux possui três permissões especiais:

| Permissão | Nome em inglês | Português | Valor |
|---|---|---|---:|
| SUID | Set User ID | Definir ID do Usuário | 4 |
| SGID | Set Group ID | Definir ID do Grupo | 2 |
| Sticky Bit | Sticky Bit | Bit de Proteção | 1 |

Essas permissões são representadas pelos valores **4, 2 e 1** na primeira posição da notação numérica.

---

# 1. SUID — Set User ID

O **SUID** faz um programa ser executado com as permissões do **dono do arquivo**, e não necessariamente com as permissões do usuário que o executou.

Exemplo:

    -rwsr-xr-x

O `s` aparece no lugar do `x` do **dono**.

### Valor numérico

    SUID = 4

Exemplo:

    chmod 4755 programa

    4 → SUID
    7 → rwx do dono
    5 → r-x do grupo
    5 → r-x de outros

### Atenção

SUID é especialmente relevante para **arquivos executáveis**.

---

# 2. SGID — Set Group ID

O **SGID** possui dois comportamentos importantes.

### Em arquivos executáveis

O programa pode ser executado com as permissões do **grupo proprietário** do arquivo.

Exemplo:

    -rwxr-sr-x

O `s` aparece no lugar do `x` do **grupo**.

### Em diretórios

Arquivos e subdiretórios criados dentro do diretório herdam o **grupo proprietário** do diretório.

Isso é muito útil para diretórios compartilhados por uma equipe.

### Valor numérico

    SGID = 2

Exemplo:

    chmod 2775 projeto/

---

# 3. Sticky Bit

O Sticky Bit é usado principalmente em **diretórios compartilhados**.

Ele impede que um usuário remova ou renomeie arquivos pertencentes a outro usuário, mesmo que o diretório permita escrita.

Exemplo clássico:

    /tmp

Permissão típica:

    drwxrwxrwt

O `t` aparece no lugar do `x` de **outros**.

### Valor numérico

    Sticky Bit = 1

Exemplo:

    chmod 1777 compartilhado/

---

# 4. Como identificar

Use:

    ls -l

### SUID

    -rwsr-xr-x

`s` no campo do **dono**.

### SGID

    -rwxr-sr-x

`s` no campo do **grupo**.

### Sticky Bit

    drwxrwxrwt

`t` no campo de **outros**.

---

# 5. `s` e `t` maiúsculos

Também podem aparecer letras maiúsculas:

    S
    T

Isso acontece quando a permissão especial está definida, mas o `x` correspondente **não** está.

Exemplo:

    -rwSr--r--

SUID definido, mas sem `x` para o dono.

    drwxrwxrwT

Sticky Bit definido, mas sem `x` para outros.

---

# 6. Notação numérica

As quatro posições podem representar:

    SUID | Dono | Grupo | Outros
      4  |  7   |  5    |   5

Exemplo:

    chmod 4755 programa

Resultado:

    -rwsr-xr-x

Outro exemplo:

    chmod 2775 projeto/

Resultado:

    drwxrwsr-x

Outro:

    chmod 1777 compartilhado/

Resultado:

    drwxrwxrwt

---

# 7. Comparação rápida

| Permissão | Onde aparece | Função principal |
|---|---|---|
| SUID | Dono | Executa com identidade do dono |
| SGID | Grupo | Executa com grupo do arquivo; em diretórios, mantém o grupo |
| Sticky Bit | Outros | Protege arquivos em diretórios compartilhados |

### Valores

    SUID       = 4
    SGID       = 2
    Sticky Bit = 1

---

# 8. LPIC-1 — O que lembrar

- `s` no campo do **dono** → SUID.
- `s` no campo do **grupo** → SGID.
- `t` no campo de **outros** → Sticky Bit.
- SUID = `4`.
- SGID = `2`.
- Sticky Bit = `1`.
- SGID em diretórios faz novos arquivos herdarem o **grupo** do diretório.
- Sticky Bit é comum em `/tmp`.
- `ls -l` mostra as permissões especiais.
- `chmod 4755` → SUID.
- `chmod 2775` → SGID.
- `chmod 1777` → Sticky Bit.

### Resumo

    SUID       → 4 → dono
    SGID       → 2 → grupo
    Sticky Bit → 1 → outros

    chmod 4755 programa
    chmod 2775 projeto/
    chmod 1777 compartilhado/

> **"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
