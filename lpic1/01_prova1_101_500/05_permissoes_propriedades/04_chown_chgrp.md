# Permissões e Propriedade

## 04 — chown e chgrp

### 1. `chown`

**chown** — *Change Owner* — **Alterar Dono**

Usado para alterar o proprietário de um arquivo ou diretório.

Sintaxe:

    chown usuário arquivo

Exemplo:

    sudo chown joao arquivo.txt

Agora:

    Dono → joao

---

### 2. Alterar dono e grupo

Podemos alterar os dois ao mesmo tempo:

    sudo chown joao:alunos arquivo.txt

Resultado:

    Dono  → joao
    Grupo → alunos

A estrutura é:

    usuário:grupo

---

### 3. Alterar somente o grupo com `chown`

Também podemos usar:

    sudo chown :alunos arquivo.txt

O dono permanece o mesmo e apenas o grupo é alterado.

---

### 4. `chown` recursivo

**`-R`** — *Recursive* — **Recursivo**

Aplica a alteração ao diretório e ao seu conteúdo.

    sudo chown -R joao:alunos projetos/

Exemplo:

    projetos/
    ├── arquivo1.txt
    ├── arquivo2.txt
    └── documentos/

Todos passarão a ter:

    Dono  → joao
    Grupo → alunos

---

### 5. `chgrp`

**chgrp** — *Change Group* — **Alterar Grupo**

Altera somente o grupo de um arquivo ou diretório.

Sintaxe:

    chgrp grupo arquivo

Exemplo:

    sudo chgrp alunos arquivo.txt

Resultado:

    Dono  → permanece
    Grupo → alunos

---

### 6. `chgrp` recursivo

Também aceita `-R`:

    sudo chgrp -R alunos projetos/

Altera o grupo do diretório e de seu conteúdo.

---

### 7. Verificar dono e grupo

Use:

    ls -l

Exemplo:

    -rw-r--r-- 1 joao alunos 1200 arquivo.txt

Interpretação:

    joao   → dono
    alunos → grupo

Também podemos usar:

    stat arquivo.txt

**stat** — *Status* — **Informações detalhadas do arquivo**

---

### 8. `chown` × `chgrp`

| Comando | Função |
|---|---|
| `chown` | altera o dono |
| `chown usuário:grupo` | altera dono e grupo |
| `chown :grupo` | altera somente o grupo |
| `chgrp` | altera somente o grupo |
| `-R` | aplica recursivamente |

---

### 9. Exemplo completo

Verificar:

    ls -l arquivo.txt

Alterar dono:

    sudo chown maria arquivo.txt

Alterar grupo:

    sudo chgrp desenvolvimento arquivo.txt

Verificar novamente:

    ls -l arquivo.txt

Resultado:

    -rw-r--r-- 1 maria desenvolvimento 1200 arquivo.txt

---

## Resumo LPIC-1

- `chown` → **Change Owner — Alterar Dono**.
- `chgrp` → **Change Group — Alterar Grupo**.
- `chown usuário arquivo` → altera o dono.
- `chown usuário:grupo arquivo` → altera dono e grupo.
- `chown :grupo arquivo` → altera somente o grupo.
- `chgrp grupo arquivo` → altera somente o grupo.
- `-R` → **Recursive — Recursivo**.
- `ls -l` → mostra dono e grupo.
- `stat` → mostra informações detalhadas.
- `sudo` é normalmente necessário para alterar a propriedade de arquivos que não pertencem ao usuário.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
