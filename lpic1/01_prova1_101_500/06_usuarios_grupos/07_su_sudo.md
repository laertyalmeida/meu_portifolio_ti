# Usuários e Grupos

## 07 — su e sudo

## su — Substitute User (Substituir Usuário)

O comando `su` permite executar um shell ou comando como **outro usuário**.

O uso mais comum é mudar para `root`.

    su

Será solicitada a senha do usuário de destino.

---

## 1. Mudar para outro usuário

    su usuario

Exemplo:

    su laerte

Inicia um shell como `laerte`.

---

## 2. Usar um Login Shell

`-` — login (ambiente de login)

    su - usuario

Exemplo:

    su - laerte

O ambiente é inicializado como se o usuário tivesse feito login normalmente.

Também pode ser escrito:

    su -l usuario

`-l` — login (login)

---

## 3. Executar apenas um comando

`-c` — command (comando)

    su -c "comando"

Exemplo:

    su -c "id"

Executa `id` como o usuário de destino e retorna ao usuário original.

Para outro usuário:

    su -c "whoami" laerte

---

# sudo — Superuser Do (Executar como Superusuário)

O `sudo` permite executar um comando com os privilégios de outro usuário, normalmente `root`, sem precisar iniciar um shell completo como esse usuário.

Exemplo:

    sudo apt update

A senha normalmente solicitada é a do **usuário que está executando o `sudo`**, e não necessariamente a senha do `root`.

---

## 4. Executar como outro usuário

`-u` — user (usuário)

    sudo -u laerte whoami

Resultado:

    laerte

Sem `-u`, o usuário padrão normalmente é:

    root

Portanto:

    sudo whoami

Normalmente retorna:

    root

---

## 5. Abrir um shell administrativo

    sudo -i

`-i` — login shell (shell de login)

Abre um ambiente de login como `root`.

Outra forma comum:

    sudo -s

`-s` — shell (shell)

Inicia um shell usando o ambiente atual, com os privilégios do usuário especificado.

---

# 6. su × sudo

| Comando | Função |
|---|---|
| `su` | muda para outro usuário |
| `su -` | muda para outro usuário com ambiente de login |
| `sudo comando` | executa um comando com privilégios elevados |
| `sudo -u usuario comando` | executa como outro usuário |
| `sudo -i` | abre shell de login como root |
| `sudo -s` | abre shell com privilégios elevados |

### Diferença importante

Com:

    su -

você normalmente precisa da **senha do usuário de destino**.

Com:

    sudo comando

a autenticação normalmente utiliza a **senha do usuário que executa o sudo**, desde que ele tenha autorização.

---

# 7. Configuração do sudo

O arquivo principal de configuração é:

    /etc/sudoers

⚠️ Não é recomendado editar esse arquivo diretamente com um editor comum.

Use:

    sudo visudo

`visudo` — Visual/Edit Sudoers (Editar configuração do sudo)

O `visudo` verifica a sintaxe antes de salvar, reduzindo o risco de deixar a configuração do `sudo` inválida.

---

## 8. Grupo administrativo

Em muitas distribuições, usuários administrativos pertencem a um grupo específico.

Exemplos comuns:

    sudo
    wheel

Exemplo:

    sudo usermod -aG sudo laerte

Depois, uma nova sessão normalmente é necessária para que a associação ao grupo seja reconhecida.

---

# 9. Verificar permissões do sudo

    sudo -l

`-l` — list (listar)

Mostra os comandos que o usuário atual está autorizado a executar através do `sudo`.

---

# 10. Exemplos práticos

### Executar comando como root

    sudo systemctl restart ssh

### Executar como outro usuário

    sudo -u laerte whoami

### Tornar-se root

    su -

### Shell administrativo com sudo

    sudo -i

### Ver permissões

    sudo -l

### Editar sudoers com segurança

    sudo visudo

---

# 11. LPIC-1 — O que lembrar

### `su`

- **su** = Substitute User (Substituir Usuário).
- `su usuario` → muda para outro usuário.
- `su - usuario` → login shell do usuário.
- `su -c "comando"` → executa um comando.
- `su -` → normalmente muda para `root` com ambiente de login.

### `sudo`

- **sudo** = Superuser Do (Executar como Superusuário).
- `sudo comando` → executa comando com privilégios elevados.
- `sudo -u usuario` → executa como outro usuário.
- `sudo -i` → shell de login como root.
- `sudo -s` → shell com privilégios elevados.
- `sudo -l` → lista permissões do sudo.
- `/etc/sudoers` → configuração principal.
- `visudo` → edita e verifica a configuração do sudo.
- Grupos comuns para administração: `sudo` e `wheel`.

### Resumo

    su -
    su - usuario
    su -c "comando"

    sudo comando
    sudo -u usuario comando
    sudo -i
    sudo -s
    sudo -l

    sudo visudo

> **"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
