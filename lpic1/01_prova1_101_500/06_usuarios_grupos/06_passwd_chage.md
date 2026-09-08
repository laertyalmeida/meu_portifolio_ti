# Usuários e Grupos

## 06 — passwd e chage

## passwd — Password (Senha)

O comando `passwd` é usado para **criar ou alterar a senha** de usuários e também para controlar alguns aspectos relacionados ao estado da senha.

---

## 1. Alterar a própria senha

    passwd

O sistema solicitará:

    Current password:
    New password:
    Retype new password:

---

## 2. Alterar a senha de outro usuário

Normalmente requer privilégios administrativos:

    sudo passwd usuario

Exemplo:

    sudo passwd laerte

---

## 3. Bloquear e desbloquear senha

`-l` — lock (bloquear)

    sudo passwd -l usuario

Bloqueia a autenticação por senha da conta.

`-u` — unlock (desbloquear)

    sudo passwd -u usuario

Desbloqueia a autenticação por senha.

⚠️ O bloqueio da senha não é necessariamente o mesmo que bloquear toda e qualquer forma de acesso à conta.

---

## 4. Forçar troca de senha

`-e` — expire (expirar)

    sudo passwd -e usuario

Faz a senha expirar, normalmente obrigando o usuário a definir uma nova senha no próximo login.

---

## 5. Remover a senha

`-d` — delete (excluir)

    sudo passwd -d usuario

Remove a senha da conta.

⚠️ Isso pode permitir autenticação sem senha dependendo da configuração do sistema. Use com muito cuidado.

---

# chage — Change Age (Alterar Validade)

O `chage` controla a **idade e a validade da senha** de um usuário.

É usado principalmente para definir regras como:

- quantidade máxima de dias da senha;
- quantidade mínima de dias;
- aviso antes da expiração;
- data de expiração da conta.

---

## 6. Ver informações de validade

`-l` — list (listar)

    sudo chage -l usuario

Exemplo de informações:

    Last password change
    Password expires
    Password inactive
    Account expires
    Minimum number of days
    Maximum number of days
    Number of days of warning

---

## 7. Definir validade máxima da senha

`-M` — maximum days (dias máximos)

    sudo chage -M 90 usuario

A senha deverá ser alterada após 90 dias, conforme a política configurada.

---

## 8. Definir período mínimo

`-m` — minimum days (dias mínimos)

    sudo chage -m 1 usuario

O usuário deverá esperar pelo menos 1 dia antes de alterar novamente a senha.

---

## 9. Definir aviso de expiração

`-W` — warning (aviso)

    sudo chage -W 7 usuario

O usuário receberá aviso durante os últimos 7 dias antes da expiração da senha.

---

## 10. Definir inatividade

`-I` — inactive (inatividade)

    sudo chage -I 30 usuario

Define quantos dias após a expiração da senha a conta poderá permanecer inativa antes de ser desabilitada.

---

## 11. Definir data de expiração da conta

`-E` — expire (expirar)

    sudo chage -E 2026-12-31 usuario

Define uma data de expiração para a **conta**.

⚠️ Não confunda:

    Expiração da senha → quando a senha precisa ser alterada.

    Expiração da conta → quando a conta deixa de ser utilizável conforme a política.

---

## 12. Forçar troca no próximo login

Também podemos usar:

    sudo chage -d 0 usuario

`-d` — last day (último dia da alteração da senha)

Definir `0` como último dia de alteração faz a senha ser considerada expirada, normalmente forçando a troca no próximo login.

---

# 13. passwd × chage

| Comando | Função principal |
|---|---|
| `passwd` | Gerenciar senha |
| `chage` | Gerenciar validade/idade da senha |

### `passwd`

    passwd
    sudo passwd usuario
    sudo passwd -l usuario
    sudo passwd -u usuario
    sudo passwd -e usuario

### `chage`

    sudo chage -l usuario
    sudo chage -M 90 usuario
    sudo chage -m 1 usuario
    sudo chage -W 7 usuario
    sudo chage -I 30 usuario
    sudo chage -E 2026-12-31 usuario

---

# 14. Relação com `/etc/shadow`

As informações controladas pelo `chage` estão relacionadas aos campos de validade presentes em:

    /etc/shadow

Por isso, `chage` é preferível a editar `/etc/shadow` manualmente.

---

# 15. LPIC-1 — O que lembrar

### passwd

- `passwd` → altera senha.
- `-l` → lock (bloquear).
- `-u` → unlock (desbloquear).
- `-e` → expire (expirar).
- `-d` → delete (excluir senha).

### chage

- `-l` → list (listar).
- `-m` → minimum (mínimo).
- `-M` → maximum (máximo).
- `-W` → warning (aviso).
- `-I` → inactive (inatividade).
- `-E` → expire (expiração da conta).
- `-d` → last day (último dia da senha).

### Resumo

    passwd

    sudo passwd usuario

    sudo passwd -l usuario
    sudo passwd -u usuario
    sudo passwd -e usuario

    sudo chage -l usuario
    sudo chage -M 90 usuario
    sudo chage -m 1 usuario
    sudo chage -W 7 usuario
    sudo chage -I 30 usuario
    sudo chage -E 2026-12-31 usuario

> **"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
