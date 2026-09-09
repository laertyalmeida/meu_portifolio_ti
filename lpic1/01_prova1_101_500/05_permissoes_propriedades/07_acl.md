# Permissões e Propriedade

## 07 — ACL

### 1. O que é ACL?

**ACL** — *Access Control List* — **Lista de Controle de Acesso**

Permite definir permissões mais específicas do que as permissões tradicionais de:

    Dono → Grupo → Outros

Com ACL, podemos dar permissões diferentes para usuários e grupos específicos.

Exemplo:

    arquivo.txt
    Dono  → laerte
    Grupo → desenvolvimento

Podemos permitir que outro usuário, como `joao`, também tenha acesso sem precisar mudar o dono ou o grupo principal.

---

### 2. Comandos principais

| Comando | English | Português |
|---|---|---|
| `getfacl` | Get File Access Control List | Obter ACL do arquivo |
| `setfacl` | Set File Access Control List | Definir ACL do arquivo |

---

### 3. Ver ACL

Use:

    getfacl arquivo.txt

Exemplo:

    # file: arquivo.txt
    # owner: laerte
    # group: desenvolvimento
    user::rw-
    user:joao:r--
    group::r--
    mask::r--
    other::---

Interpretação:

    user::rw-           → permissões do dono
    user:joao:r--       → permissões específicas para joao
    group::r--          → permissões do grupo
    mask::r--           → limite das permissões ACL
    other::---          → permissões dos outros

---

### 4. Adicionar ACL para um usuário

**setfacl** — *Set File Access Control List* — **Definir Lista de Controle de Acesso**

Sintaxe:

    setfacl -m u:usuário:permissões arquivo

**`-m`** — *modify* — **modificar**

Exemplo:

    setfacl -m u:joao:r-- arquivo.txt

Agora `joao` possui:

    r-- → leitura

---

### 5. Adicionar ACL para um grupo

Sintaxe:

    setfacl -m g:grupo:permissões arquivo

Exemplo:

    setfacl -m g:desenvolvimento:rw arquivo.txt

O grupo `desenvolvimento` recebe:

    rw- → leitura e escrita

---

### 6. Remover ACL

Para remover a ACL específica de um usuário:

    setfacl -x u:joao arquivo.txt

**`-x`** — *remove* — **remover entrada**

Para remover a ACL de um grupo:

    setfacl -x g:desenvolvimento arquivo.txt

---

### 7. Remover todas as ACLs

**`-b`** — *remove all extended ACL entries* — **remover todas as entradas ACL estendidas**

    setfacl -b arquivo.txt

Depois:

    getfacl arquivo.txt

---

### 8. ACL em diretórios

Podemos aplicar ACL a um diretório:

    setfacl -m u:joao:rwx projetos/

Isso permite que `joao` tenha:

    rwx → leitura, escrita e acesso/execução

---

### 9. ACL padrão — Default ACL

**Default ACL** — **ACL Padrão**

Permite definir permissões que serão herdadas por novos arquivos e diretórios criados dentro de um diretório.

Exemplo:

    setfacl -m d:u:joao:rwx projetos/

**`d:`** → *default* — **padrão**

Verificar:

    getfacl projetos/

A ACL padrão é especialmente útil em diretórios compartilhados.

---

### 10. ACL e `mask`

A **ACL Mask** — **Máscara da ACL**

Define o limite máximo das permissões efetivas de:

- usuários ACL específicos;
- grupos ACL;
- grupo proprietário.

Exemplo:

    user:joao:rwx
    mask::r-x

Embora a entrada de `joao` mostre:

    rwx

As permissões efetivas serão:

    r-x

porque a `mask` limita a escrita.

O `getfacl` pode mostrar:

    user:joao:rwx        #effective:r-x

---

### 11. ACL × permissões tradicionais

Sem ACL:

    Dono → rwx
    Grupo → r-x
    Outros → ---

Com ACL podemos ter:

    Dono       → rwx
    joao       → r--
    maria      → rw-
    Grupo      → r-x
    Outros     → ---

Isso permite um controle muito mais detalhado.

---

### 12. Identificar ACL com `ls -l`

Quando um arquivo possui ACL estendida, o `ls -l` normalmente mostra um `+` após as permissões.

Exemplo:

    -rw-rw-r--+ 1 laerte desenvolvimento 1200 arquivo.txt

O `+` indica que existem **ACLs estendidas**.

Para descobrir exatamente quais:

    getfacl arquivo.txt

---

## Resumo LPIC-1

- **ACL** — *Access Control List* → Lista de Controle de Acesso.
- Permite permissões específicas para usuários e grupos.
- `getfacl` → visualizar ACL.
- `setfacl` → criar ou modificar ACL.
- `setfacl -m` → modificar/adicionar entrada.
- `setfacl -x` → remover uma entrada específica.
- `setfacl -b` → remover ACLs estendidas.
- `u:usuario:rwx` → ACL específica para usuário.
- `g:grupo:rwx` → ACL específica para grupo.
- `d:` → define **Default ACL — ACL Padrão**.
- `mask` → limita as permissões efetivas de determinadas entradas ACL.
- `ls -l` mostrando `+` → indica presença de ACL estendida.
- `getfacl` → mostra os detalhes da ACL.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
