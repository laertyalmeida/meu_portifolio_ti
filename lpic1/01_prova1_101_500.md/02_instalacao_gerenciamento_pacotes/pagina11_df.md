# 📖 HQ 2 — INSTALAÇÃO DO LINUX E GERENCIAMENTO DE PACOTES

# 📖 PÁGINA 11 — DF

# 🧠 1. O QUE É `df`?

`df` é utilizado para mostrar o **espaço em disco disponível e utilizado pelos sistemas de arquivos**.

### Tradução

**df = disk free**

→ **espaço livre em disco**

Exemplo:

```bash
df
```

O comando mostra informações como:

```text
Filesystem
1K-blocks
Used
Available
Use%
Mounted on
```

---

# 💾 2. O QUE `df` MOSTRA?

Imagine uma partição:

```text
/dev/sda1
↓
100 GB
```

O `df` pode mostrar:

```text
Total
↓
100 GB

Usado
↓
40 GB

Disponível
↓
60 GB
```

Portanto:

```text
df
↓
ESPAÇO DO SISTEMA DE ARQUIVOS
```

---

# 🔤 3. PRINCIPAIS COLUNAS

Exemplo:

```text
Filesystem      1K-blocks    Used  Available  Use%  Mounted on
/dev/sda1        102400000   40G       60G     40%       /
```

### `Filesystem`

→ sistema de arquivos/dispositivo.

### `1K-blocks`

→ quantidade de blocos de 1 KiB.

### `Used`

→ espaço utilizado.

### `Available`

→ espaço disponível.

### `Use%`

→ percentual utilizado.

### `Mounted on`

→ ponto onde está montado.

---

# 👀 4. `df -h`

O comando mais utilizado:

```bash
df -h
```

### `-h`

→ **human-readable**

→ **legível para humanos**

Em vez de mostrar números difíceis de interpretar:

```text
102400000
```

pode mostrar:

```text
100G
40G
60G
```

---

# 📊 5. INTERPRETANDO `df -h`

Exemplo:

```text
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       100G   40G   60G  40% /
```

Interpretação:

```text
/dev/sda1
→ sistema de arquivos

100G
→ tamanho total

40G
→ espaço utilizado

60G
→ espaço disponível

40%
→ percentual utilizado

/
→ ponto de montagem
```

---

# 📁 6. `df -h /`

Podemos verificar especificamente o sistema de arquivos onde está o diretório raiz:

```bash
df -h /
```

Isso mostra o espaço disponível para:

```text
/
```

---

# 📂 7. `df -h /home`

Também podemos verificar:

```bash
df -h /home
```

Isso mostra o sistema de arquivos que contém:

```text
/home
```

É útil quando `/home` está em uma partição separada.

---

# 🧠 8. `df -T`

Podemos solicitar que o `df` mostre também o **tipo do sistema de arquivos**:

```bash
df -T
```

### `-T`

→ **type → tipo**

Exemplo:

```text
Filesystem     Type   Size  Used Avail Use% Mounted on
/dev/sda1      ext4   100G   40G   60G  40% /
```

Agora podemos identificar:

```text
ext4
→ tipo do sistema de arquivos
```

---

# 🔢 9. `df -Th`

Podemos combinar as opções:

```bash
df -Th
```

### `-T`

→ type → tipo.

### `-h`

→ human-readable → legível para humanos.

Resultado:

```text
Filesystem     Type   Size  Used Avail Use% Mounted on
/dev/sda1      ext4   100G   40G   60G  40% /
```

É uma forma muito prática de visualizar:

```text
TIPO + ESPAÇO
```

---

# 📦 10. `df -i`

Existe também:

```bash
df -i
```

Essa opção mostra informações sobre **inodes**.

### `-i`

→ **inodes**

Exemplo:

```text
Filesystem      Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1      6553600  200000 6353600    4% /
```

Isso é importante porque um sistema de arquivos pode ter espaço em disco disponível, mas ficar sem inodes.

---

# 🧠 11. O QUE É INODE?

Um **inode** é uma estrutura utilizada pelo sistema de arquivos para armazenar informações sobre um arquivo.

De forma simplificada:

```text
ARQUIVO
   ↓
INODE
   ↓
informações do arquivo
```

O inode não é o conteúdo do arquivo.

Ele contém informações como:

- Permissões
- Proprietário
- Tamanho
- Datas
- Localização dos dados

Para esta página, basta entender que:

```text
df -i
→ mostra uso de inodes
```

---

# ⚖️ 12. `df` x `du`

É muito importante não confundir:

```text
df
→ espaço disponível/utilizado no sistema de arquivos
```

```text
du
→ espaço utilizado por arquivos e diretórios
```

Exemplo:

```bash
df -h
```

→ quanto espaço o sistema de arquivos possui e quanto está sendo utilizado.

Enquanto:

```bash
du -sh /home
```

→ quanto espaço `/home` está ocupando.

---

# 📝 13. COMANDOS NECESSÁRIOS

### Mostrar espaço dos sistemas de arquivos

```bash
df
```

→ mostra espaço utilizado e disponível.

---

### Mostrar de forma legível

```bash
df -h
```

**-h = human-readable → legível para humanos**

---

### Mostrar tipo do sistema de arquivos

```bash
df -T
```

**-T = type → tipo**

---

### Mostrar tipo + tamanho legível

```bash
df -Th
```

**-T = type → tipo**

**-h = human-readable → legível para humanos**

---

### Mostrar uso de inodes

```bash
df -i
```

**-i = inodes**

→ mostra uso de inodes.

---

### Ver espaço da raiz

```bash
df -h /
```

→ mostra o uso do sistema de arquivos que contém `/`.

---

### Ver espaço do `/home`

```bash
df -h /home
```

→ mostra o uso do sistema de arquivos que contém `/home`.

---

# 🎯 14. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que faz `df`.
- Que `df` significa **disk free**.
- Que `df` mostra espaço utilizado e disponível nos sistemas de arquivos.
- Entender `Used`.
- Entender `Available`.
- Entender `Use%`.
- Entender `Mounted on`.
- Usar `df -h`.
- Saber que `-h` significa **human-readable**.
- Usar `df -T`.
- Saber que `-T` significa **type**.
- Usar `df -Th`.
- Conhecer `df -i`.
- Saber que `-i` mostra informações de inodes.
- Saber diferenciar `df` de `du`.

---

# 🧠 RESUMO

```text
df
↓
DISK FREE
↓
ESPAÇO DO SISTEMA DE ARQUIVOS
```

### Principais informações:

```text
Size
→ tamanho

Used
→ usado

Available
→ disponível

Use%
→ percentual utilizado

Mounted on
→ ponto de montagem
```

---

# 🔑 PRINCIPAIS OPÇÕES

```text
-h
→ human-readable
→ legível para humanos

-T
→ type
→ mostrar tipo do sistema de arquivos

-i
→ inodes
→ mostrar uso de inodes
```

---

# ⚖️ NÃO CONFUNDA

```text
df
↓
QUANTO ESPAÇO O SISTEMA DE ARQUIVOS TEM/USA
```

```text
du
↓
QUANTO ESPAÇO ARQUIVOS E DIRETÓRIOS ESTÃO USANDO
```

---

# 🎯 PARA MEMORIZAR

```bash
df -h
```

→ **ver espaço em disco de forma legível**

```bash
df -Th
```

→ **ver espaço + tipo do sistema de arquivos**

```bash
df -i
```

→ **ver uso de inodes**

# ✅ FIM DA PÁGINA 11
```
