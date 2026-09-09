# Usuários e Grupos

## 06 — passwd e chage

### 1. passwd

**passwd** — *Password* — **Senha**

Usado para criar, alterar ou administrar a senha de um usuário.

Alterar a senha do usuário atual:

    passwd

Alterar a senha de outro usuário:

    sudo passwd laerte

---

### 2. Principais opções do `passwd`

| Opção | English | Português |
|---|---|---|
| `-d` | Delete | Remover a senha |
| `-l` | Lock | Bloquear a senha |
| `-u` | Unlock | Desbloquear a senha |
| `-S` | Status | Mostrar status da senha |
| `-e` | Expire | Forçar expiração da senha |
| `-n` | Minimum Days | Definir mínimo de dias |
| `-x` | Maximum Days | Definir máximo de dias |
| `-w` | Warning Days | Definir dias de aviso |
| `-i` | Inactive Days | Definir dias de inatividade |

Exemplo:

    sudo passwd -S laerte

**`-S` — Status — Status**

Mostra informações sobre o estado da senha.

---

# 3. chage

**chage** — *Change Age* — **Alterar validade da senha**

É usado para administrar a **expiração e validade da senha** de um usuário.

Exemplo:

    sudo chage -l laerte

**`-l` — List — Listar**

Mostra as informações de validade da senha.

---

### 4. Principais opções do `chage`

| Opção | English | Português |
|---|---|---|
| `-l` | List | Listar informações |
| `-m` | Minimum Days | Mínimo de dias |
| `-M` | Maximum Days | Máximo de dias |
| `-W` | Warning Days | Dias de aviso |
| `-I` | Inactive Days | Dias de inatividade |
| `-E` | Expire Date | Data de expiração |
| `-d` | Last Day | Data da última alteração |

---

### 5. Definir validade da senha

Exemplo:

    sudo chage -M 90 laerte

A senha deverá ser alterada após **90 dias**.

Definir aviso de 7 dias:

    sudo chage -W 7 laerte

O usuário será avisado durante os últimos 7 dias antes da expiração.

---

### 6. Definir período mínimo

    sudo chage -m 1 laerte

O usuário deverá esperar **1 dia** antes de poder alterar novamente a senha.

---

### 7. Expirar a senha imediatamente

Uma técnica comum:

    sudo chage -d 0 laerte

Isso força o usuário a alterar a senha no próximo login.

---

### 8. Expiração da conta

Podemos definir uma data para expiração da conta:

    sudo chage -E 2026-12-31 laerte

**`-E` — Expire Date — Data de Expiração**

---

### 9. Ver todas as configurações

    sudo chage -l laerte

Exemplo de informações:

    Last password change
    Password expires
    Password inactive
    Account expires
    Minimum number of days
    Maximum number of days
    Number of days of warning

Tradução:

| English | Português |
|---|---|
| Last password change | Última alteração da senha |
| Password expires | Senha expira |
| Password inactive | Senha inativa |
| Account expires | Conta expira |
| Minimum number of days | Número mínimo de dias |
| Maximum number of days | Número máximo de dias |
| Number of days of warning | Número de dias de aviso |

---

### 10. passwd × chage

**passwd** trabalha principalmente com a **senha**.

    sudo passwd laerte

**chage** trabalha principalmente com a **validade da senha e da conta**.

    sudo chage -l laerte

Pense assim:

    passwd → senha
    chage  → validade/expiração

---

## Resumo LPIC-1

- `passwd` → **Password — Senha**.
- `passwd` → alterar senha.
- `passwd -S` → mostrar status da senha.
- `passwd -l` → bloquear senha.
- `passwd -u` → desbloquear senha.
- `passwd -e` → forçar expiração da senha.
- `chage` → **Change Age — Alterar validade da senha**.
- `chage -l` → listar informações de validade.
- `chage -m` → mínimo de dias.
- `chage -M` → máximo de dias.
- `chage -W` → dias de aviso.
- `chage -I` → dias de inatividade.
- `chage -E` → data de expiração da conta.
- `chage -d 0` → força alteração da senha no próximo login.
- `/etc/shadow` → armazena informações protegidas relacionadas às senhas e sua validade.

**Conhecimento só tem valor quando é compartilhado - Laerte Costa**
