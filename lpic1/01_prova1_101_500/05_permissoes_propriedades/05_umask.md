# Permissões e Propriedade

## 05 — umask

### 1. O que é `umask`

**umask** — *User File-Creation Mask* — **Máscara de Criação de Arquivos**

Define quais permissões serão **removidas por padrão** quando novos arquivos e diretórios forem criados.

Ver a `umask` atual:

    umask

Exemplo:

    0022

---

### 2. Permissões padrão

O Linux parte de permissões máximas diferentes para arquivos e diretórios:

**Arquivos:**

    666 → rw-rw-rw-

**Diretórios:**

    777 → rwxrwxrwx

A `umask` remove permissões desses valores.

---

### 3. Exemplo com `umask 022`

Imagine:

    umask 022

Para um arquivo:

    666
  - 022
  -----
    644

Resultado:

    rw-r--r--

Para um diretório:

    777
  - 022
  -----
    755

Resultado:

    rwxr-xr-x

Portanto:

    umask 022

Normalmente resulta em:

    Arquivo    → 644
    Diretório  → 755

---

### 4. Exemplo com `umask 077`

Agora:

    umask 077

Arquivo:

    666
  - 077
  -----
    600

Resultado:

    rw-------

Diretório:

    777
  - 077
  -----
    700

Resultado:

    rwx------

Isso deixa os novos arquivos e diretórios acessíveis somente pelo proprietário.

---

### 5. `umask` não adiciona permissões

A `umask` funciona como uma **máscara de remoção**.

Exemplo:

    umask 027

Não significa:

    "dar 027"

Significa:

    "retirar as permissões indicadas pela máscara"

---

### 6. Alterar a `umask`

Para alterar temporariamente na sessão atual:

    umask 022

Verificar:

    umask

Outra possibilidade:

    umask 077

A alteração normalmente permanece válida para os processos iniciados a partir daquela sessão, conforme o ambiente do shell.

---

### 7. Testando na prática

Verifique:

    umask

Crie um arquivo:

    touch arquivo.txt

Veja:

    ls -l arquivo.txt

Crie um diretório:

    mkdir teste

Veja:

    ls -ld teste

Com `umask 022`, normalmente:

    -rw-r--r-- arquivo.txt
    drwxr-xr-x teste

---

### 8. Arquivos × Diretórios

| Tipo | Base | Com `umask 022` |
|---|---:|---:|
| Arquivo | `666` | `644` |
| Diretório | `777` | `755` |

Arquivos começam em `666` porque normalmente **não recebem `x` automaticamente**.

Diretórios começam em `777` porque precisam do `x` para serem acessados/atravessados.

---

### 9. Onde configurar

A `umask` pode ser definida em arquivos de inicialização do shell ou de configuração do ambiente.

Exemplo:

    umask 022

Pode aparecer em arquivos como:

    ~/.profile
    ~/.bashrc

A localização exata depende da forma como a sessão é iniciada e da configuração da distribuição.

---

## Resumo LPIC-1

- `umask` → **User File-Creation Mask — Máscara de Criação de Arquivos**.
- Define permissões que serão **removidas** dos novos arquivos e diretórios.
- Arquivos → base `666`.
- Diretórios → base `777`.
- `umask 022` → arquivos `644` e diretórios `755`.
- `umask 077` → arquivos `600` e diretórios `700`.
- Arquivos novos normalmente não recebem `x` automaticamente.
- `umask` não concede permissões; ela **restringe as permissões padrão**.
- `umask` sem argumento → mostra a máscara atual.
- `umask 022` → altera a máscara da sessão.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
