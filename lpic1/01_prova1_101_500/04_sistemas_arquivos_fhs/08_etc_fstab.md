# 08 — /etc/fstab

## /etc/fstab — Filesystem Table (Tabela de Sistemas de Arquivos)

O arquivo `/etc/fstab` define **quais sistemas de arquivos devem ser montados** e **como devem ser montados**.

Ele é usado principalmente para configurar montagens **automáticas durante a inicialização do Linux**.

    /etc/fstab
         ↓
    configurações de montagem
         ↓
    mount
         ↓
    sistema de arquivos montado

---

## Estrutura do /etc/fstab

Cada linha normalmente possui **6 campos**:

    <dispositivo> <ponto> <tipo> <opções> <dump> <pass>

Exemplo:

    UUID=a1b2-c3d4  /home  ext4  defaults  0  2

### Os 6 campos

| Campo | Inglês | Português | Função |
|---|---|---|---|
| 1 | Device | Dispositivo | Partição, UUID ou LABEL |
| 2 | Mount Point | Ponto de Montagem | Diretório onde será montado |
| 3 | Filesystem Type | Tipo de Sistema de Arquivos | `ext4`, `xfs`, `swap` etc. |
| 4 | Options | Opções | Define como será montado |
| 5 | Dump | Backup | Controle usado pelo `dump` |
| 6 | Pass | Verificação | Ordem de verificação pelo `fsck` |

---

## 1 — Device (Dispositivo)

Pode utilizar o nome do dispositivo:

    /dev/sda1

Ou, preferencialmente, o UUID:

    UUID=a1b2-c3d4

Também pode usar um LABEL:

    LABEL=Dados

### Memorize

    /dev/sda1 → dispositivo
    UUID=...  → identificador único
    LABEL=... → rótulo

---

## 2 — Mount Point (Ponto de Montagem)

Define onde o sistema de arquivos ficará acessível.

    /home
    /mnt/dados
    /backup

Exemplo:

    UUID=a1b2-c3d4  /dados  ext4  defaults  0  2

---

## 3 — Filesystem Type (Tipo de Sistema de Arquivos)

Indica o tipo do filesystem.

Exemplos:

    ext4
    xfs
    vfat
    swap

---

## 4 — Options (Opções)

Define como o sistema de arquivos será montado.

### `defaults`

    defaults

Usa as opções padrão de montagem.

Outras opções comuns:

| Opção | Inglês | Português |
|---|---|---|
| `ro` | read-only | somente leitura |
| `rw` | read-write | leitura e escrita |
| `noauto` | no automatic | não montar automaticamente |
| `user` | user | permite montagem pelo usuário |
| `users` | users | permite montagem por usuários |
| `defaults` | defaults | opções padrão |

---

## 5 — Dump

Exemplo:

    0

O campo `dump` controla se o sistema de arquivos será considerado pelo utilitário de backup `dump`.

Para a maioria dos sistemas modernos, utiliza-se:

    0

---

## 6 — Pass

Define a ordem de verificação pelo `fsck`.

Valores comuns:

    0 → não verificar
    1 → verificar primeiro
    2 → verificar depois

Normalmente:

    /      → 1
    outros → 2

---

## Testar o /etc/fstab

Depois de alterar o arquivo, é importante testar a configuração.

    mount -a

`-a` — all (todos)

Monta todas as entradas apropriadas do `/etc/fstab`.

Se houver erro, o sistema normalmente informa qual entrada está incorreta.

---

## Exemplo completo

    UUID=a1b2-c3d4  /      ext4  defaults  0  1
    UUID=e5f6-g7h8  /home  ext4  defaults  0  2

Interpretação:

    UUID=a1b2-c3d4
          ↓
        /
          ↓
       ext4
          ↓
      defaults
          ↓
        0  1

---

## LPIC-1 — O que saber

- `/etc/fstab` — arquivo de configuração de montagens.
- Conhecer os **6 campos**.
- Saber o significado de `UUID`, `LABEL` e `/dev/sda1`.
- Entender **Mount Point (Ponto de Montagem)**.
- Conhecer `defaults`, `ro`, `rw` e `noauto`.
- Entender `dump` e `pass`.
- Saber que
