# 02 — Permissões rwx

## Permissions — Permissões

No Linux, as permissões controlam o que um usuário pode fazer com um **arquivo ou diretório**.

As três permissões básicas são:

    r → read    → leitura
    w → write   → escrita
    x → execute → execução

---

## r — Read (Leitura)

Permite **ler o conteúdo**.

Em arquivos:

    r → pode visualizar o conteúdo

Em diretórios:

    r → pode listar o conteúdo do diretório

---

## w — Write (Escrita)

Permite **alterar o conteúdo**.

Em arquivos:

    w → pode modificar o conteúdo

Em diretórios:

    w → pode criar, excluir e renomear itens
         dentro do diretório, dependendo das demais permissões

---

## x — Execute (Execução)

Permite executar um arquivo como programa ou script.

Em diretórios:

    x → permite acessar/atravessar o diretório

Exemplo:

    cd /home/laerte

Para acessar um diretório, a permissão `x` é especialmente importante.

---

## User, Group e Others

As permissões são divididas em três categorias:

    User   → usuário/dono
    Group  → grupo
    Others → outros

Exemplo:

    -rwxr-xr--

Separando:

    rwx | r-x | r--
     ↓     ↓     ↓
    User  Group Others

---

## Entendendo rwx

### User — Usuário/Dono

    rwx

    r → read    → leitura
    w → write   → escrita
    x → execute → execução

O dono pode **ler, escrever e executar**.

### Group — Grupo

    r-x

    r → leitura
    - → sem escrita
    x → execução

O grupo pode **ler e executar**, mas não escrever.

### Others — Outros

    r--

    r → leitura
    - → sem escrita
    - → sem execução

Outros usuários podem apenas **ler**.

---

## Primeiro caractere

Exemplo:

    -rwxr-xr--

O primeiro caractere indica o tipo:

    - → arquivo regular
    d → diretório
    l → link simbólico

Portanto:

    -rwxr-xr--

    -     → arquivo
    rwx   → dono
    r-x   → grupo
    r--   → outros

---

## Permissões em diretórios

As permissões têm um significado especial em diretórios:

| Permissão | Inglês | Português |
|---|---|---|
| `r` | read | listar conteúdo |
| `w` | write | criar/remover/renomear |
| `x` | execute | acessar/atravessar |

### Memorize

    Arquivo:

    r → ler
    w → alterar
    x → executar

    Diretório:

    r → listar
    w → criar/remover/renomear
    x → acessar/atravessar

---

## Exemplo com ls -l

    ls -l arquivo.txt

Resultado:

    -rwxr-xr-- 1 laerte usuarios 1200 arquivo.txt

Interpretação:

    -    → arquivo regular
    rwx  → dono: leitura + escrita + execução
    r-x  → grupo: leitura + execução
    r--  → outros: somente leitura

---

## Ordem para memorizar

Sempre pense:

    User | Group | Others
     ↓       ↓       ↓
    rwx |    rwx |   rwx

Ou:

    Dono → Grupo → Outros

---

## LPIC-1 — O que saber

- `r` = read — leitura.
- `w` = write — escrita.
- `x` = execute — execução.
- As permissões são divididas em **User, Group e Others**.
- Saber interpretar `rwxr-xr--`.
- Saber diferenciar permissões em **arquivos** e **diretórios**.
- O `x` em diretórios significa **acessar/atravessar**.
- O primeiro caractere de `ls -l` indica o tipo do objeto.

---

## Resumo

    rwx | r-x | r--
     ↓     ↓     ↓
    Dono  Grupo Outros

    r → read    → leitura
    w → write   → escrita
    x → execute → execução

    Arquivo:
    r → ler
    w → alterar
    x → executar

    Diretório:
    r → listar
    w → criar/remover/renomear
    x → acessar/atravessar

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
