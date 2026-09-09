# Usuários e Grupos

## 08 — /etc/skel e /home

### /etc/skel — Skeleton Directory — Diretório Modelo

O `/etc/skel` contém arquivos e diretórios que podem ser usados como **modelo para novos usuários**.

    ls -la /etc/skel

Exemplo:

    /etc/skel/.bashrc
    /etc/skel/.profile

Ao criar um usuário com um diretório pessoal, esses arquivos podem ser copiados para o novo **Home Directory — Diretório Pessoal**.

Exemplo:

    sudo useradd -m laerte

O resultado normalmente será:

    /home/laerte/

com os arquivos padrão provenientes de:

    /etc/skel/

> A cópia depende das opções utilizadas no `useradd` e da configuração do sistema.

---

## /home — Home Directory — Diretórios Pessoais

O `/home` normalmente contém os diretórios pessoais dos usuários comuns.

Exemplo:

    /home/laerte
    /home/joao
    /home/maria

Cada usuário normalmente possui seu próprio diretório.

Exemplo:

    /home/laerte

Dentro dele podem existir:

    /home/laerte/Documents
    /home/laerte/Downloads
    /home/laerte/.bashrc

---

## $HOME — Home Directory — Diretório Pessoal

A variável `$HOME` indica o diretório pessoal do usuário atual.

    echo $HOME

Exemplo:

    /home/laerte

O símbolo `~` também representa o diretório pessoal do usuário atual:

    cd ~

É equivalente a:

    cd "$HOME"

---

## Criando o Home com useradd

Criar usuário sem especificar `-m` pode depender da configuração do sistema para criar o diretório pessoal.

Para solicitar explicitamente a criação:

    sudo useradd -m laerte

**`-m` — Create Home — Criar Diretório Pessoal**

Podemos definir outro local:

    sudo useradd -m -d /home/empresa/laerte laerte

**`-d` — Home Directory — Diretório Pessoal**

---

## /etc/skel × /home

| Diretório | Função |
|---|---|
| `/etc/skel` | Modelo para novos usuários |
| `/home` | Diretórios pessoais dos usuários |
| `/home/laerte` | Home do usuário `laerte` |
| `$HOME` | Variável que aponta para o Home atual |
| `~` | Atalho para o Home atual |

Fluxo simplificado:

    /etc/skel
         ↓
    useradd -m
         ↓
    /home/laerte
         ↓
    arquivos pessoais do usuário

---

## Arquivos ocultos

Arquivos iniciados por `.` são normalmente arquivos ocultos.

Exemplo:

    /home/laerte/.bashrc

Para visualizá-los:

    ls -la /home/laerte

**`-a` — All — Todos**

---

## Resumo LPIC-1

- `/etc/skel` → **Skeleton Directory — Diretório Modelo**.
- `/etc/skel` → contém arquivos usados como modelo para novos usuários.
- `/home` → **Home Directory — Diretórios Pessoais**.
- `/home/usuario` → diretório pessoal de um usuário.
- `$HOME` → variável que indica o Home do usuário atual.
- `~` → representa o Home do usuário atual.
- `useradd -m` → solicita a criação do diretório pessoal.
- `useradd -d` → define o diretório pessoal.
- `.bashrc` → exemplo de arquivo de configuração que pode estar no Home.
- Arquivos iniciados por `.` → normalmente são arquivos ocultos.

**Conhecimento só tem valor quando é compartilhado** - Laerte Costa
