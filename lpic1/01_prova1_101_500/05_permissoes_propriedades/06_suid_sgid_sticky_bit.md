# Permissões e Propriedade

## 06 — SUID, SGID e Sticky Bit

### 1. O que são?

**Special Permissions** — **Permissões Especiais**

Além de `r`, `w` e `x`, o Linux possui três permissões especiais:

| Permissão | Nome em inglês | Português |
|---|---|---|
| SUID | Set User ID | Definir ID do Usuário |
| SGID | Set Group ID | Definir ID do Grupo |
| Sticky Bit | Sticky Bit | Bit de Proteção |

Elas são representadas por:

    SUID       → s
    SGID       → s
    Sticky Bit → t

---

### 2. SUID

**SUID** — *Set User ID* — **Definir ID do Usuário**

Quando aplicado a um arquivo executável, faz o programa ser executado com o **UID efetivo do proprietário do arquivo**.

Exemplo:

    -rwsr-xr-x

O `s` aparece no lugar do `x` do proprietário.

Exemplo clássico:

    ls -l /usr/bin/passwd

O `passwd` precisa realizar alterações relacionadas às informações de autenticação do sistema, mesmo quando executado por um usuário comum.

---

### 3. SGID em arquivos

**SGID** — *Set Group ID* — **Definir ID do Grupo**

Quando aplicado a um arquivo executável, faz o programa ser executado com o **GID efetivo do grupo proprietário**.

Exemplo:

    -rwxr-sr-x

O `s` aparece no lugar do `x` do grupo.

---

### 4. SGID em diretórios

Em um diretório, o SGID possui outro comportamento importante.

Arquivos e subdiretórios criados dentro dele herdam o **grupo do diretório**, em vez de necessariamente usar o grupo principal do usuário que criou o arquivo.

Exemplo:

    drwxrwsr-x

O `s` aparece no lugar do `x` do grupo.

Muito útil em diretórios compartilhados por uma equipe.

---

### 5. Sticky Bit

**Sticky Bit** — **Bit de Proteção**

É usado principalmente em diretórios compartilhados.

Quando aplicado, normalmente somente:

- o proprietário do arquivo;
- o proprietário do diretório;
- ou `root`;

pode remover ou renomear uma entrada dentro daquele diretório.

Exemplo clássico:

    ls -ld /tmp

Normalmente aparece algo semelhante a:

    drwxrwxrwt

O `t` no final indica **Sticky Bit**.

---

### 6. Representação simbólica

Exemplos:

    SUID:
    -rwsr-xr-x

    SGID:
    -rwxr-sr-x

    Sticky Bit:
    drwxrwxrwt

Quando o `s` ou `t` aparece em **maiúsculo**, significa que a permissão `x` correspondente não está definida.

Exemplos:

    SUID → -rwSr-xr-x
    SGID → -rwxr-Sr-x
    Sticky → drwxrwxrwT

---

### 7. Valores numéricos

As permissões especiais possuem valores próprios:

| Permissão | Valor |
|---|---:|
| SUID | `4000` |
| SGID | `2000` |
| Sticky Bit | `1000` |

Exemplo:

    chmod 4755 programa

Resultado:

    -rwsr-xr-x

    4 → SUID
    755 → permissões normais

---

### 8. Exemplos com `chmod`

Adicionar SUID:

    chmod u+s programa

Remover SUID:

    chmod u-s programa

Adicionar SGID:

    chmod g+s diretorio

Remover SGID:

    chmod g-s diretorio

Adicionar Sticky Bit:

    chmod +t diretorio

Remover Sticky Bit:

    chmod -t diretorio

---

### 9. Exemplo prático — diretório compartilhado

Criar:

    sudo mkdir /dados-compartilhados

Definir SGID:

    sudo chmod 2775 /dados-compartilhados

Resultado:

    drwxrwsr-x

Novos arquivos e diretórios criados ali herdarão o grupo do diretório.

---

### 10. Exemplo — Sticky Bit

Criar um diretório compartilhado:

    mkdir compartilhado

Aplicar Sticky Bit:

    chmod 1777 compartilhado

Resultado:

    drwxrwxrwt

Todos podem criar arquivos, mas um usuário não pode simplesmente remover ou renomear arquivos pertencentes a outro usuário.

---

### 11. Identificar permissões especiais

Use:

    ls -l

Exemplo:

    -rwsr-xr-x → SUID
    -rwxr-sr-x → SGID
    drwxrwxrwt → Sticky Bit

Também podemos usar:

    stat arquivo

**stat** — *Status* — **Informações detalhadas**

---

## Resumo LPIC-1

- **SUID** — *Set User ID* → execução com o UID efetivo do proprietário do programa.
- **SGID** — *Set Group ID* → execução com o GID efetivo do grupo do programa.
- **SGID em diretório** → arquivos e subdiretórios criados nele herdam o grupo do diretório.
- **Sticky Bit** → protege arquivos em diretórios compartilhados contra remoção/renomeação por usuários que não sejam seus proprietários.
- SUID → `4000`.
- SGID → `2000`.
- Sticky Bit → `1000`.
- `s` no lugar do `x` → SUID ou SGID.
- `t` no lugar do `x` → Sticky Bit.
- `chmod u+s` → adiciona SUID.
- `chmod g+s` → adiciona SGID.
- `chmod +t` → adiciona Sticky Bit.
- `/tmp` → exemplo clássico de diretório com Sticky Bit.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
