# Usuários e Grupos

## 07 — su e sudo

### su — Substitute User — Substituir Usuário

O `su` permite assumir a identidade de outro usuário, normalmente `root`.

    su

Tenta iniciar um shell como `root`.

    su - laerte

Inicia um shell como `laerte`, carregando o ambiente de login desse usuário.

### `-` — Login — Ambiente de Login

O `-` faz o `su` carregar um ambiente semelhante ao de um login normal.

Exemplo:

    su - root

ou:

    su - laerte

---

### Executar apenas um comando com `su`

    su -c "comando"

**`-c` — Command — Comando**

Exemplo:

    su -c "id"

Executa `id` como o usuário alvo e retorna ao usuário anterior.

Para outro usuário:

    su -c "id" laerte

---

## sudo — Superuser Do — Executar como Superusuário

O `sudo` permite executar um comando com privilégios de outro usuário, normalmente `root`.

Exemplo:

    sudo apt update

Ou:

    sudo systemctl restart ssh

Por padrão, o usuário normalmente autentica usando **sua própria senha**, conforme a configuração do `sudo`.

---

## Executar como outro usuário

    sudo -u laerte id

**`-u` — User — Usuário**

Executa o comando como `laerte`.

Exemplo:

    sudo -u laerte whoami

Resultado:

    laerte

---

## Abrir um shell administrativo

Uma forma comum:

    sudo -i

**`-i` — Login Shell — Shell de Login**

Abre um shell de login como `root`.

Outra possibilidade:

    sudo -s

**`-s` — Shell — Shell**

Inicia um shell usando o ambiente atual.

---

## sudo e /etc/sudoers

As permissões do `sudo` são controladas principalmente por:

    /etc/sudoers

Também podem existir arquivos adicionais em:

    /etc/sudoers.d/

Para editar a configuração principal, use:

    sudo visudo

**visudo — Edit Sudoers Safely — Editar Sudoers com Segurança**

O `visudo` verifica a sintaxe antes de aplicar a configuração, ajudando a evitar erros que poderiam quebrar o acesso administrativo.

---

## Diferença entre su e sudo

| Comando | Função |
|---|---|
| `su` | Trocar para outro usuário |
| `su -` | Trocar para outro usuário com ambiente de login |
| `su -c` | Executar um comando como outro usuário |
| `sudo` | Executar um comando com privilégios elevados |
| `sudo -u` | Executar como um usuário específico |
| `sudo -i` | Abrir shell de login como outro usuário, normalmente `root` |
| `sudo -s` | Abrir um shell |

### Exemplo prático

Com `su`:

    su -
    whoami
    apt update
    exit

Com `sudo`:

    sudo apt update

No primeiro caso, você **entra em outro usuário**.

No segundo, você **eleva os privilégios somente para o comando**.

---

## Resumo LPIC-1

- `su` → **Substitute User — Substituir Usuário**.
- `su -` → troca de usuário com ambiente de login.
- `su -c` → executa um comando como outro usuário.
- `sudo` → **Superuser Do — Executar com privilégios elevados**.
- `sudo -u` → executar como outro usuário.
- `sudo -i` → shell de login com privilégios do usuário alvo.
- `sudo -s` → iniciar um shell.
- `/etc/sudoers` → configuração principal do `sudo`.
- `/etc/sudoers.d/` → configurações adicionais.
- `visudo` → editar e validar a configuração do `sudo`.
- `su` normalmente exige a senha do **usuário alvo**.
- `sudo` normalmente exige a senha do **usuário que está executando o comando**.

**Conhecimento só tem valor quando é compartilhado** - Laerte Costa
