# Usuários e Grupos

## 03 — /etc/passwd e /etc/shadow

### /etc/passwd — Password File — Arquivo de Usuários

O `/etc/passwd` contém informações básicas sobre as contas de usuários do sistema.

Pode ser consultado com:

    cat /etc/passwd

Cada usuário ocupa uma linha com **7 campos**, separados por `:`.

Exemplo:

    laerte:x:1000:1000:Laerte Costa:/home/laerte:/bin/bash

| Campo | Significado |
|---|---|
| `laerte` | Username — Nome do usuário |
| `x` | Password — Senha armazenada em `/etc/shadow` |
| `1000` | UID — ID do usuário |
| `1000` | GID — ID do grupo primário |
| `Laerte Costa` | GECOS — Informações do usuário |
| `/home/laerte` | Home Directory — Diretório pessoal |
| `/bin/bash` | Login Shell — Shell de login |

> **Importante:** o `x` não é a senha. Ele indica que as informações protegidas da senha estão no `/etc/shadow`.

---

### /etc/shadow — Shadow Password File — Arquivo de Senhas Protegidas

O `/etc/shadow` armazena informações protegidas relacionadas às senhas dos usuários.

    sudo cat /etc/shadow

Exemplo simplificado:

    laerte:$y$j9T$...:20000:0:99999:7:::

Os campos são separados por `:`.

Os principais campos são:

| Campo | Significado |
|---|---|
| `laerte` | Username — Nome do usuário |
| `$y$...` | Password Hash — Hash da senha |
| `20000` | Última alteração da senha |
| `0` | Mínimo de dias antes de alterar |
| `99999` | Máximo de dias da senha |
| `7` | Aviso antes da expiração |

Os campos restantes tratam de expiração e desativação da conta.

---

## Por que existem dois arquivos?

O Linux separa as informações básicas da conta das informações protegidas da senha.

    /etc/passwd
        ↓
    informações da conta
        ↓
    UID, GID, Home, Shell

    /etc/shadow
        ↓
    informações protegidas
        ↓
    hash da senha e expiração

O `/etc/passwd` normalmente pode ser lido por usuários comuns.

O `/etc/shadow` possui acesso mais restrito.

---

## Consultando um usuário

Para consultar informações de uma conta:

    getent passwd laerte

Para consultar informações de senha:

    sudo getent shadow laerte

Também podemos usar:

    id laerte

---

## Conta sem senha

No `/etc/shadow`, o campo da senha pode possuir caracteres especiais.

Alguns exemplos:

    !
    *
    
Eles podem indicar que o login por senha está bloqueado ou que aquela conta não possui uma senha utilizável, dependendo da configuração.

---

## Segurança

Nunca altere manualmente `/etc/passwd` ou `/etc/shadow` sem saber exatamente o que está fazendo.

Para administrar senhas, prefira comandos apropriados, como:

    passwd usuario

Para informações de expiração:

    chage usuario

---

## Resumo LPIC-1

| Arquivo | Função |
|---|---|
| `/etc/passwd` | Informações básicas das contas |
| `/etc/shadow` | Informações protegidas das senhas |
| `UID` | ID do usuário |
| `GID` | ID do grupo primário |
| `/home/usuario` | Diretório pessoal |
| `/bin/bash` | Shell de login |
| `x` em `/etc/passwd` | Senha armazenada em `/etc/shadow` |
| `passwd` | Gerenciar senha |
| `chage` | Gerenciar validade da senha |
| `getent passwd` | Consultar contas |
| `getent shadow` | Consultar informações do shadow |

**Conhecimento só tem valor quando é compartilhado** - Laerte Costa
