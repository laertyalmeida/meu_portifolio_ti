# 📖 HQ 2 — INSTALAÇÃO DO LINUX E GERENCIAMENTO DE PACOTES

# 📖 PÁGINA 9 — MOUNT

# 🧠 1. O QUE É `mount`?

`mount` é o comando utilizado para **montar um sistema de arquivos**.

Montar significa tornar um sistema de arquivos acessível através de um diretório do Linux.

```text
DISPOSITIVO
/dev/sda1
     ↓
SISTEMA DE ARQUIVOS
     ↓
mount
     ↓
PONTO DE MONTAGEM
/mnt
```

Depois da montagem, os arquivos da partição ficam acessíveis através de:

```text
/mnt
```

---

# 🔤 2. TRADUÇÃO

```text
mount
→ montar

mount point
→ ponto de montagem

unmount
→ desmontar
```

O comando para desmontar é:

```bash
umount
```

⚠️ É `umount`, e não `unmount`.

---

# 📂 3. MONTAGEM BÁSICA

Sintaxe:

```bash
mount DISPOSITIVO PONTO_DE_MONTAGEM
```

Exemplo:

```bash
sudo mount /dev/sda1 /mnt
```

Interpretação:

```text
/dev/sda1
→ partição

/mnt
→ ponto de montagem

mount
→ monta a partição no diretório
```

---

# 🧠 4. O PONTO DE MONTAGEM

O segundo argumento informa **onde** o sistema de arquivos será disponibilizado.

Exemplo:

```bash
sudo mount /dev/sda1 /dados
```

Nesse caso:

```text
/dev/sda1
→ sistema de arquivos

/dados
→ ponto de montagem
```

Após a montagem:

```text
/dados
```

passa a mostrar o conteúdo da partição.

---

# 🔍 5. `mount` SEM ARGUMENTOS

Executar:

```bash
mount
```

sem informar dispositivo ou diretório mostra os sistemas de arquivos atualmente montados.

Exemplo:

```text
/dev/sda1 on / type ext4
/dev/sda2 on /home type ext4
```

Podemos interpretar:

```text
/dev/sda1
→ dispositivo

/
→ ponto de montagem

ext4
→ sistema de arquivos
```

---

# 🆔 6. MONTAR POR UUID

Também podemos montar utilizando o UUID.

Exemplo:

```bash
sudo mount UUID=ABCD-1234 /mnt
```

Isso é útil porque o UUID identifica o sistema de arquivos.

Podemos descobrir o UUID com:

```bash
sudo blkid
```

---

# 📄 7. MONTAR PELO `/etc/fstab`

Quando o sistema de arquivos está configurado no:

```text
/etc/fstab
```

podemos utilizar:

```bash
sudo mount /dados
```

Nesse caso, o `mount` consulta o `/etc/fstab` para encontrar a configuração correspondente ao ponto de montagem.

Também podemos usar:

```bash
sudo mount -a
```

### `-a`

→ **all → todos**

Tenta montar todos os sistemas de arquivos configurados no `/etc/fstab`, exceto os marcados com `noauto`.

---

# 🧩 8. ESPECIFICANDO O TIPO DE SISTEMA DE ARQUIVOS

Podemos especificar o tipo utilizando:

```bash
sudo mount -t ext4 /dev/sda1 /mnt
```

### `-t`

→ **type → tipo**

Nesse exemplo:

```text
-t ext4
→ tipo do sistema de arquivos = ext4
```

Portanto:

```bash
mount -t ext4 /dev/sda1 /mnt
```

→ monta `/dev/sda1` como ext4 em `/mnt`.

---

# 🔒 9. MONTAGEM SOMENTE LEITURA

Podemos montar um sistema de arquivos como somente leitura:

```bash
sudo mount -o ro /dev/sda1 /mnt
```

### `-o`

→ **options → opções**

### `ro`

→ **read-only → somente leitura**

Portanto:

```text
-o ro
→ opção de montagem somente leitura
```

---

# ✏️ 10. MONTAGEM LEITURA E ESCRITA

A opção:

```text
rw
```

significa:

**read-write → leitura e escrita**

Exemplo:

```bash
sudo mount -o rw /dev/sda1 /mnt
```

---

# 🔄 11. REMONTAR UM SISTEMA DE ARQUIVOS

Podemos alterar opções de uma montagem existente utilizando:

```bash
sudo mount -o remount,rw /mnt
```

### `remount`

→ **remontar**

### `rw`

→ **read-write → leitura e escrita**

Isso pode ser utilizado, por exemplo, para remontar um sistema de arquivos como leitura e escrita.

---

# 📊 12. VERIFICAR A MONTAGEM

Depois de montar:

```bash
sudo mount /dev/sda1 /mnt
```

podemos verificar:

```bash
mount
```

ou:

```bash
findmnt /mnt
```

### `findmnt`

→ **find mount → encontrar/listar montagens**

---

# 💾 13. VER ESPAÇO DISPONÍVEL

Depois de montar, podemos verificar o espaço utilizado:

```bash
df -h
```

### `df`

→ **disk filesystem**

→ informações sobre uso dos sistemas de arquivos.

### `-h`

→ **human-readable → legível por humanos**

---

# ⛔ 14. DESMONTAR

Para desmontar:

```bash
sudo umount /mnt
```

### Tradução

```text
umount
→ unmount
→ desmontar
```

⚠️ O sistema de arquivos precisa deixar de estar em uso para ser desmontado normalmente.

---

# 🚨 15. ERRO "TARGET IS BUSY"

Se aparecer:

```text
target is busy
```

significa:

```text
o ponto de montagem está ocupado
```

Algum processo pode estar utilizando arquivos naquele sistema de arquivos.

Podemos investigar com:

```bash
lsof /mnt
```

### Tradução

**lsof = list open files**

→ listar arquivos abertos.

---

# 📝 16. COMANDOS NECESSÁRIOS

### Montagem básica

```bash
sudo mount /dev/sda1 /mnt
```

→ monta `/dev/sda1` em `/mnt`.

---

### Mostrar montagens

```bash
mount
```

→ mostra os sistemas de arquivos montados.

---

### Montar pelo UUID

```bash
sudo mount UUID=ABCD-1234 /mnt
```

→ monta o sistema de arquivos identificado pelo UUID.

---

### Montar entradas do `fstab`

```bash
sudo mount -a
```

**-a = all → todos**

→ tenta montar as entradas do `/etc/fstab`.

---

### Especificar o tipo

```bash
sudo mount -t ext4 /dev/sda1 /mnt
```

**-t = type → tipo**

→ informa o tipo do sistema de arquivos.

---

### Definir opções

```bash
sudo mount -o ro /dev/sda1 /mnt
```

**-o = options → opções**

**ro = read-only → somente leitura**

---

### Verificar uma montagem

```bash
findmnt /mnt
```

→ localiza informações sobre a montagem de `/mnt`.

---

### Ver espaço

```bash
df -h
```

**-h = human-readable → legível por humanos**

→ mostra espaço utilizado e disponível.

---

### Desmontar

```bash
sudo umount /mnt
```

→ desmonta `/mnt`.

---

# 🎯 17. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que significa montar um sistema de arquivos.
- O que faz o comando `mount`.
- A sintaxe básica do `mount`.
- O que é um ponto de montagem.
- Montar uma partição em um diretório.
- O que acontece ao executar `mount` sem argumentos.
- Montar utilizando UUID.
- A relação entre `mount` e `/etc/fstab`.
- O significado de `mount -a`.
- O significado de `-t`.
- O significado de `-o`.
- Conhecer `ro` e `rw`.
- O conceito de `remount`.
- Usar `findmnt`.
- Usar `df -h`.
- Usar `umount`.
- Entender o erro `target is busy`.

---

# 🧠 RESUMO

```text
mount
↓
MONTAR
↓
DISPOSITIVO
↓
SISTEMA DE ARQUIVOS
↓
PONTO DE MONTAGEM
```

### Exemplo:

```bash
sudo mount /dev/sda1 /mnt
```

```text
/dev/sda1
→ O QUE montar

/mnt
→ ONDE montar
```

### Principais opções:

```text
-t
→ type → tipo

-o
→ options → opções

-a
→ all → todos

ro
→ read-only → somente leitura

rw
→ read-write → leitura e escrita
```

---

# 🎯 PARA MEMORIZAR

```text
mount
→ MONTAR

umount
→ DESMONTAR

mount -a
→ MONTAR entradas do /etc/fstab

mount -t
→ INFORMAR tipo do filesystem

mount -o
→ INFORMAR opções

mount UUID=...
→ MONTAR usando UUID

findmnt
→ VER MONTAGENS

df -h
→ VER ESPAÇO
```

# 🔑 COMANDO PRINCIPAL

```bash
sudo mount /dev/sda1 /mnt
```

**mount → montar**

**Função → tornar o sistema de arquivos de `/dev/sda1` acessível através de `/mnt`.**

# ✅ FIM DA PÁGINA 9
