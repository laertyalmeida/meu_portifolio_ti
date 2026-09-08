# Usuários e Grupos

## 05 — groupadd, groupmod e groupdel

## Group Management — Gerenciamento de Grupos

Os principais comandos para administrar grupos no Linux são:

| Comando | Inglês | Português |
|---|---|---|
| `groupadd` | Group Add | Adicionar Grupo |
| `groupmod` | Group Modify | Modificar Grupo |
| `groupdel` | Group Delete | Excluir Grupo |

---

# 1. groupadd — Group Add (Adicionar Grupo)

Cria um novo grupo.

    sudo groupadd desenvolvedores

Depois, podemos verificar:

    getent group desenvolvedores

Exemplo:

    desenvolvedores:x:1001:

---

## Definir um GID

`-g` — GID (ID do Grupo)

    sudo groupadd -g 1500 desenvolvedores

O grupo será criado com GID `1500`.

⚠️ O GID precisa estar disponível.

---

# 2. groupmod — Group Modify (Modificar Grupo)

Altera informações de um grupo existente.

## Alterar o nome

`-n` — new name (novo nome)

    sudo groupmod -n programadores desenvolvedores

O grupo:

    desenvolvedores

passará a se chamar:

    programadores

O **GID permanece o mesmo**.

---

## Alterar o GID

`-g` — GID (ID do Grupo)

    sudo groupmod -g 1600 programadores

O GID do grupo passa a ser `1600`.

⚠️ Alterar GIDs exige cuidado, pois arquivos podem continuar pertencendo ao GID antigo.

---

# 3. groupdel — Group Delete (Excluir Grupo)

Remove um grupo.

    sudo groupdel programadores

Depois disso, o grupo deixa de existir.

### Atenção

O `groupdel` não deve ser usado para remover o **grupo primário de um usuário** enquanto esse usuário ainda estiver utilizando esse grupo como grupo primário.

Primeiro altere o grupo primário ou remova a conta do usuário, conforme a situação.

---

# 4. Adicionar usuários ao grupo

O `groupadd` apenas **cria o grupo**.

Para adicionar um usuário:

    sudo usermod -aG desenvolvedores laerte

`-a` — append (adicionar)

`-G` — supplementary groups (grupos suplementares)

Verifique:

    groups laerte

Ou:

    id laerte

---

# 5. Consultar grupos

### Todos os grupos

    getent group

### Grupo específico

    getent group desenvolvedores

### Arquivo local de grupos

    cat /etc/group

---

# 6. `/etc/group`

As informações dos grupos locais ficam normalmente em:

    /etc/group

Exemplo:

    desenvolvedores:x:1001:laerte,maria

Estrutura:

    grupo : senha : GID : usuários

Nesse exemplo:

    Grupo    → desenvolvedores
    GID      → 1001
    Membros  → laerte, maria

---

# 7. Exemplos práticos

### Criar grupo

    sudo groupadd desenvolvedores

### Criar com GID específico

    sudo groupadd -g 1500 desenvolvedores

### Alterar nome

    sudo groupmod -n programadores desenvolvedores

### Alterar GID

    sudo groupmod -g 1600 programadores

### Adicionar usuário

    sudo usermod -aG programadores laerte

### Verificar

    getent group programadores

### Excluir grupo

    sudo groupdel programadores

---

# 8. groupadd × groupmod × groupdel

| Comando | Função |
|---|---|
| `groupadd` | Cria um grupo |
| `groupmod` | Modifica um grupo |
| `groupdel` | Exclui um grupo |

### Principais opções

    groupadd -g GID grupo

    groupmod -n novo_nome grupo

    groupmod -g novo_GID grupo

    groupdel grupo

---

# 9. LPIC-1 — O que lembrar

- `groupadd` → cria grupos.
- `groupmod` → modifica grupos.
- `groupdel` → remove grupos.
- `-g` → define/altera o GID.
- `-n` → define um novo nome.
- `/etc/group` → informações dos grupos locais.
- `getent group` → consulta grupos da base configurada.
- `usermod -aG` → adiciona usuário a grupos suplementares.
- Não remova o grupo primário de um usuário que ainda depende dele.

### Resumo

    sudo groupadd grupo

    sudo groupadd -g 1500 grupo

    sudo groupmod -n novo_nome grupo

    sudo groupmod -g 1600 grupo

    sudo groupdel grupo

    sudo usermod -aG grupo usuario

    getent group grupo

> **"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
