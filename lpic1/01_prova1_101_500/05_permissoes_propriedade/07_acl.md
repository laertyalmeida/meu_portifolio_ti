# 07 — ACL

## ACL — Access Control List (Lista de Controle de Acesso)

**ACL** permite definir permissões mais específicas do que o modelo tradicional:

    User | Group | Others

Com ACL, podemos dar permissões diferentes para **usuários e grupos específicos**, sem alterar o dono ou o grupo principal do arquivo.

---

## 1. Ver ACL

`getfacl` — Get File Access Control List (Obter Lista de Controle de Acesso)

    getfacl arquivo.txt

Exemplo:

    # file: arquivo.txt
    # owner: laerte
    # group: linux
    user::rw-
    user:joao:r--
    group::r--
    mask::r--
    other::---

Nesse exemplo:

    Dono           → rw-
    Usuário joao   → r--
    Grupo          → r--
    Outros         → ---

---

## 2. Alterar ACL

`setfacl` — Set File Access Control List (Definir Lista de Controle de Acesso)

Adicionar permissões para um usuário:

    setfacl -m u:joao:r arquivo.txt

`-m` — modify (modificar)

Agora `joao` possui:

    r-- → read (leitura)

---

## 3. ACL para um grupo

    setfacl -m g:desenvolvedores:rw arquivo.txt

`g` — group (grupo)

O grupo `desenvolvedores` recebe:

    rw- → leitura e escrita

---

## 4. Remover uma ACL

    setfacl -x u:joao arquivo.txt

`-x` — remove (remover)

Remove a entrada específica do usuário `joao`.

Para remover uma ACL de grupo:

    setfacl -x g:desenvolvedores arquivo.txt

---

## 5. ACL padrão em diretórios

Uma **Default ACL (ACL padrão)** determina permissões que poderão ser herdadas por novos arquivos e diretórios criados dentro de um diretório.

Exemplo:

    setfacl -d -m g:desenvolvedores:rw projeto/

`-d` — default (padrão)

Isso cria uma ACL padrão para o grupo `desenvolvedores`.

Verifique com:

    getfacl projeto/

---

## 6. Mask — Máscara

A entrada:

    mask::rwx

define o limite máximo efetivo das permissões de:

- usuários específicos;
- grupos;
- grupo proprietário.

Exemplo:

    user:joao:rwx
    mask::r--

Embora `joao` tenha `rwx` configurado, a permissão **efetiva** será:

    r--

A `mask` pode limitar as permissões efetivas.

---

## 7. ACL × chmod

Permissões tradicionais:

    rwx | rwx | rwx
    user group others

ACL permite algo como:

    user:joao:r--
    user:maria:rw-
    group:dev:rwx

Assim, diferentes usuários podem ter permissões diferentes no mesmo arquivo.

---

## 8. ACL e permissões tradicionais

Nem todo arquivo possui ACLs adicionais.

Uma ACL estendida pode ser indicada pelo `+` no final das permissões:

    -rw-r--r--+ arquivo.txt

O `+` indica que existem **ACLs adicionais**.

---

## 9. Comandos principais

### Ver

    getfacl arquivo

### Adicionar/modificar usuário

    setfacl -m u:usuario:rwx arquivo

### Adicionar/modificar grupo

    setfacl -m g:grupo:rwx arquivo

### Remover usuário

    setfacl -x u:usuario arquivo

### Remover grupo

    setfacl -x g:grupo arquivo

### ACL padrão

    setfacl -d -m g:grupo:rwx diretorio/

---

## 10. LPIC-1 — O que lembrar

- **ACL** = Access Control List (Lista de Controle de Acesso).
- `getfacl` → consulta ACL.
- `setfacl` → modifica ACL.
- `-m` → modify (modificar).
- `-x` → remove (remover).
- `-d` → default (padrão).
- `u:` → user (usuário).
- `g:` → group (grupo).
- `mask` limita as permissões efetivas.
- `+` no `ls -l` indica ACL adicional.
- ACL permite permissões específicas para usuários e grupos.

### Resumo

    getfacl arquivo.txt

    setfacl -m u:joao:r arquivo.txt

    setfacl -m g:desenvolvedores:rw arquivo.txt

    setfacl -x u:joao arquivo.txt

    setfacl -d -m g:desenvolvedores:rw projeto/

> **"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
