# 05 — umask

## umask — User File-Creation Mask (Máscara de Criação de Arquivos)

O `umask` define **quais permissões serão retiradas** das permissões padrão ao criar novos arquivos e diretórios.

Ele **não adiciona permissões**; ele funciona como uma máscara que bloqueia permissões.

---

## 1. Ver a umask atual

    umask

Exemplo:

    0022

O primeiro `0` representa permissões especiais; os três últimos dígitos correspondem a:

    Dono | Grupo | Outros
      0  |  2   |   2

---

## 2. Como funciona

As permissões máximas usadas como base normalmente são:

**Arquivos:**

    666 → rw-rw-rw-

**Diretórios:**

    777 → rwxrwxrwx

A `umask` remove permissões dessa base.

### Exemplo: umask 022

Arquivo:

    666
    022
    ---
    644

Resultado:

    rw-r--r--

Diretório:

    777
    022
    ---
    755

Resultado:

    rwxr-xr-x

> A operação é conceitualmente uma **máscara de bits**, não uma simples subtração decimal.

---

## 3. Valores comuns

| umask | Arquivo criado | Diretório criado |
|---:|---|---|
| `000` | `666` → `rw-rw-rw-` | `777` → `rwxrwxrwx` |
| `022` | `644` → `rw-r--r--` | `755` → `rwxr-xr-x` |
| `027` | `640` → `rw-r-----` | `750` → `rwxr-x---` |
| `077` | `600` → `rw-------` | `700` → `rwx------` |

---

## 4. Definir uma umask

    umask 022

A partir daí, novos arquivos e diretórios criados pelo processo/shell usarão essa máscara.

Para conferir:

    umask

---

## 5. Forma simbólica

Também é possível usar:

    umask -S

Exemplo:

    u=rwx,g=rx,o=rx

`-S` — symbolic (simbólico)

Mostra a máscara em formato legível.

---

## 6. Ponto importante para a prova

### Arquivos × Diretórios

Não confunda:

    Arquivos      → base 666
    Diretórios    → base 777

Arquivos normalmente **não recebem `x` automaticamente** na criação.

Por isso, com:

    umask 022

temos:

    Arquivo     → 644
    Diretório   → 755

---

## 7. LPIC-1 — O que lembrar

- `umask` = User File-Creation Mask (Máscara de Criação de Arquivos).
- Controla permissões de **novos** arquivos e diretórios.
- `umask` → mostra a máscara atual.
- `umask 022` → define a máscara.
- `umask -S` → mostra em formato simbólico.
- Arquivos usam `666` como base.
- Diretórios usam `777` como base.
- `022` → arquivos `644`, diretórios `755`.
- `077` → arquivos `600`, diretórios `700`.

### Resumo

    umask
    umask -S
    umask 022

**Base:**

    Arquivo    666
    Diretório  777

**Com umask 022:**

    Arquivo    644
    Diretório  755

> **"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
