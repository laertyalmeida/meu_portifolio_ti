# 📖 HQ 2 — INSTALAÇÃO DO LINUX E GERENCIAMENTO DE PACOTES

# 📖 PÁGINA 8 — UUID

# 🧠 1. O QUE É UUID?

**UUID = Universally Unique Identifier**

Tradução:

**Identificador Universalmente Único**

No Linux, um UUID pode identificar de forma única um sistema de arquivos ou uma partição.

Exemplo:

```text
UUID=550e8400-e29b-41d4-a716-446655440000
```

Em vez de depender apenas do nome do dispositivo:

```text
/dev/sda1
```

podemos utilizar seu UUID.

---

# 💽 2. POR QUE USAR UUID?

Os nomes dos dispositivos podem mudar dependendo da ordem em que os dispositivos são detectados.

Por exemplo:

```text
/dev/sda1
```

pode ser identificado de outra forma em determinadas situações.

O UUID permanece associado ao sistema de arquivos.

Por isso, é muito comum encontrar UUID no:

```text
/etc/fstab
```

---

# 🔗 3. UUID E `/etc/fstab`

Exemplo:

```text
UUID=ABCD-1234  /dados  ext4  defaults  0  2
```

Interpretação:

```text
UUID=ABCD-1234
→ identifica o sistema de arquivos

/dados
→ ponto de montagem

ext4
→ sistema de arquivos

defaults
→ opções padrão

0
→ dump

2
→ ordem de verificação pelo fsck
```

Assim, o Linux consegue localizar o sistema de arquivos pelo UUID e montá-lo em:

```text
/dados
```

---

# 🔍 4. `blkid`

O principal comando para consultar UUIDs é:

```bash
sudo blkid
```

### Tradução

**blkid**

→ **block device identification**

→ identificação de dispositivos de bloco.

Exemplo:

```text
/dev/sda1: UUID="ABCD-1234" TYPE="ext4"
/dev/sda2: UUID="EFGH-5678" TYPE="swap"
```

---

# 🧠 5. INTERPRETANDO `blkid`

Considere:

```text
/dev/sda1: UUID="ABCD-1234" TYPE="ext4"
```

Temos:

```text
/dev/sda1
→ dispositivo/partição

UUID="ABCD-1234"
→ identificador único

TYPE="ext4"
→ sistema de arquivos
```

---

# 🔎 6. `lsblk -f`

Também podemos consultar UUIDs utilizando:

```bash
lsblk -f
```

### Tradução

`ls`

→ **list → listar**

`blk`

→ **block → bloco**

`-f`

→ **filesystem → sistema de arquivos**

A saída pode mostrar:

```text
NAME   FSTYPE FSVER LABEL UUID
sda1   ext4         ...   ABCD-1234
sda2   swap         ...   EFGH-5678
```

---

# 🆔 7. UUID x PARTUUID

É importante não confundir:

```text
UUID
```

com:

```text
PARTUUID
```

### UUID

Identifica o **sistema de arquivos**.

### PARTUUID

Identifica a **partição** na tabela de partições.

Exemplo:

```text
/dev/sda1
UUID=ABCD-1234
PARTUUID=1111-2222
```

Para a prova, memorize:

```text
UUID
→ sistema de arquivos

PARTUUID
→ partição
```

---

# 🧩 8. UUID NÃO É O NOME DO DISPOSITIVO

Observe:

```text
/dev/sda1
```

é o nome do dispositivo.

Já:

```text
UUID=ABCD-1234
```

é um identificador associado ao sistema de arquivos.

Portanto:

```text
/dev/sda1
→ nome/caminho do dispositivo

UUID
→ identificador
```

---

# 🔄 9. UUID E MONTAGEM

Podemos montar utilizando o UUID:

```bash
sudo mount UUID=ABCD-1234 /mnt
```

Interpretação:

```text
mount
→ montar

UUID=ABCD-1234
→ sistema de arquivos que será localizado

/mnt
→ ponto de montagem
```

Isso permite montar o sistema de arquivos sem informar diretamente:

```text
/dev/sda1
```

---

# 📝 10. COMANDOS NECESSÁRIOS

### Mostrar UUIDs

```bash
sudo blkid
```

→ identifica dispositivos e mostra UUIDs.

### Mostrar UUIDs e sistemas de arquivos

```bash
lsblk -f
```

→ lista dispositivos, sistemas de arquivos e UUIDs.

### Montar utilizando UUID

```bash
sudo mount UUID=ABCD-1234 /mnt
```

→ monta o sistema de arquivos identificado pelo UUID.

### Consultar o `fstab`

```bash
cat /etc/fstab
```

→ mostra configurações que podem utilizar UUIDs.

---

# 🎯 11. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O significado de UUID.
- Que UUID significa **Universally Unique Identifier**.
- A tradução de UUID.
- Para que UUID é utilizado.
- Por que UUID é utilizado no `/etc/fstab`.
- A diferença entre UUID e `/dev/sda1`.
- A diferença entre UUID e PARTUUID.
- Que UUID normalmente identifica o sistema de arquivos.
- Que PARTUUID identifica a partição.
- Usar `blkid`.
- Usar `lsblk -f`.
- Reconhecer `UUID=` no `/etc/fstab`.
- Saber que é possível montar utilizando UUID.

---

# 🧠 RESUMO

```text
UUID
↓
Universally Unique Identifier
↓
Identificador Universalmente Único
↓
IDENTIFICA O SISTEMA DE ARQUIVOS
```

### Exemplo:

```text
/dev/sda1
↓
UUID=ABCD-1234
↓
ext4
```

### No `/etc/fstab`:

```text
UUID=ABCD-1234  /dados  ext4  defaults  0  2
```

---

# 🔑 PARA MEMORIZAR

```text
/dev/sda1
→ nome/caminho do dispositivo

UUID
→ identifica o sistema de arquivos

PARTUUID
→ identifica a partição
```

```text
blkid
→ mostra UUIDs

lsblk -f
→ mostra sistemas de arquivos + UUIDs

/etc/fstab
→ pode utilizar UUID para montar automaticamente
```

# 🎯 COMANDO PRINCIPAL

```bash
sudo blkid
```

**blkid → block device identification**

**Função → identificar dispositivos de bloco e mostrar informações como UUID e tipo do sistema de arquivos.**

# ✅ FIM DA PÁGINA 8
