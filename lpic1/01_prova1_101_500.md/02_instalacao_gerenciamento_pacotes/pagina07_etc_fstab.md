# 📖 HQ 2 — INSTALAÇÃO DO LINUX E GERENCIAMENTO DE PACOTES

# 📖 PÁGINA 7 — /ETC/FSTAB

# 🧠 1. O QUE É `/etc/fstab`?

`/etc/fstab` é o arquivo que contém informações sobre **sistemas de arquivos que devem ser montados**.

### Tradução

`fstab`

→ **File Systems Table**

→ Tabela de Sistemas de Arquivos.

Portanto:

```text
/etc/fstab
↓
File Systems Table
↓
Tabela de Sistemas de Arquivos
```

Ele é utilizado principalmente para definir montagens que devem ocorrer automaticamente durante a inicialização do sistema.

---

# 🔄 2. MONTAGEM MANUAL x AUTOMÁTICA

Podemos montar manualmente:

```bash
sudo mount /dev/sda2 /mnt
```

Nesse caso, a montagem é feita naquele momento.

Para definir uma montagem persistente:

```text
/etc/fstab
```

pode conter a configuração.

Resumo:

```text
mount
↓
montagem manual

/etc/fstab
↓
configuração de montagens
↓
montagem automática
```

---

# 📄 3. ESTRUTURA DO `/etc/fstab`

Uma entrada do `fstab` possui normalmente **seis campos**:

```text
<device> <mount_point> <filesystem> <options> <dump> <pass>
```

Exemplo:

```text
UUID=xxxx-xxxx  /home  ext4  defaults  0  2
```

---

# 1️⃣ 4. PRIMEIRO CAMPO — DISPOSITIVO

Exemplo:

```text
UUID=xxxx-xxxx
```

Identifica o sistema de arquivos que será montado.

Também pode ser utilizado um dispositivo:

```text
/dev/sda2
```

ou outros identificadores.

O uso de UUID é comum porque o nome do dispositivo pode mudar dependendo da detecção dos discos.

---

# 2️⃣ 5. SEGUNDO CAMPO — PONTO DE MONTAGEM

Exemplo:

```text
/home
```

É o diretório onde o sistema de arquivos será montado.

Outro exemplo:

```text
/mnt
```

---

# 3️⃣ 6. TERCEIRO CAMPO — SISTEMA DE ARQUIVOS

Exemplo:

```text
ext4
```

Indica o tipo de sistema de arquivos.

Outros exemplos:

```text
xfs
btrfs
vfat
swap
```

---

# 4️⃣ 7. QUARTO CAMPO — OPÇÕES

Exemplo:

```text
defaults
```

Define opções de montagem padrão.

Outras opções importantes:

```text
ro
rw
noauto
user
users
exec
noexec
```

### `ro`

→ **read-only → somente leitura**

### `rw`

→ **read-write → leitura e escrita**

### `noauto`

→ não montar automaticamente.

### `user`

→ permite que um usuário monte o sistema de arquivos.

### `users`

→ permite que usuários montem e desmontem.

### `exec`

→ permite execução de programas.

### `noexec`

→ impede execução de programas.

Para a prova, é importante reconhecer essas opções.

---

# 5️⃣ 8. QUINTO CAMPO — `dump`

Exemplo:

```text
0
```

O campo `dump` é utilizado pelo utilitário `dump` para determinar se o sistema de arquivos deve ser considerado para backup.

Na prática, o valor mais comum é:

```text
0
```

---

# 6️⃣ 9. SEXTO CAMPO — `pass`

O campo:

```text
pass
```

define a ordem utilizada pelo `fsck` para verificar sistemas de arquivos durante a inicialização.

Valores comuns:

```text
0
1
2
```

### `0`

→ não verificar pelo `fsck`.

### `1`

→ primeira prioridade.

Normalmente utilizado para:

```text
/
```

### `2`

→ verificar depois dos sistemas com prioridade `1`.

Normalmente utilizado para outros sistemas de arquivos.

---

# 🧠 10. EXEMPLO COMPLETO

```text
UUID=1234-5678  /home  ext4  defaults  0  2
```

Interpretando:

```text
UUID=1234-5678
→ sistema de arquivos

/home
→ ponto de montagem

ext4
→ sistema de arquivos

defaults
→ opções padrão

0
→ dump desativado

2
→ verificação posterior pelo fsck
```

---

# 🔍 11. VERIFICAR O `/etc/fstab`

Podemos visualizar:

```bash
cat /etc/fstab
```

### Tradução

**cat**

→ **concatenate → exibir/concatenar conteúdo**

Isso mostra o conteúdo do arquivo.

Também podemos usar:

```bash
less /etc/fstab
```

### Tradução

**less**

→ visualizar conteúdo página por página.

---

# 🧪 12. TESTAR O `fstab`

Depois de alterar o `/etc/fstab`, podemos testar as configurações com:

```bash
sudo mount -a
```

### Tradução

**mount**

→ montar.

**-a**

→ **all → todos**

Portanto:

```bash
mount -a
```

→ tenta montar todos os sistemas de arquivos configurados no `/etc/fstab`, exceto os marcados com `noauto`.

⚠️ Esse comando é muito importante para verificar se uma alteração no `fstab` está correta antes de reiniciar.

---

# 🆔 13. UUID NO `fstab`

É comum encontrar:

```text
UUID=xxxx-xxxx
```

em vez de:

```text
/dev/sda1
```

O UUID identifica o sistema de arquivos.

Podemos descobrir UUIDs com:

```bash
blkid
```

Exemplo:

```text
/dev/sda1: UUID="ABCD-1234" TYPE="ext4"
```

Então podemos utilizar:

```text
UUID=ABCD-1234  /dados  ext4  defaults  0  2
```

---

# 📝 14. COMANDOS NECESSÁRIOS

### Mostrar o `fstab`

```bash
cat /etc/fstab
```

→ exibe o conteúdo do arquivo.

### Visualizar página por página

```bash
less /etc/fstab
```

→ visualiza o conteúdo.

### Montar entradas do `fstab`

```bash
sudo mount -a
```

**-a = all → todos**

→ tenta montar as entradas configuradas.

### Descobrir UUID

```bash
sudo blkid
```

→ identifica dispositivos, sistemas de arquivos e UUIDs.

---

# 🎯 15. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que é `/etc/fstab`.
- O significado de `fstab`.
- Que significa **File Systems Table**.
- Que o arquivo configura sistemas de arquivos para montagem.
- A diferença entre montagem manual e configuração persistente.
- Conhecer os seis campos do `fstab`.
- Saber o que representa cada campo.
- Reconhecer `UUID`.
- Saber o que é um ponto de montagem.
- Reconhecer o campo de tipo de sistema de arquivos.
- Conhecer `defaults`.
- Conhecer `ro` e `rw`.
- Conhecer `noauto`.
- Conhecer `user` e `users`.
- Conhecer `exec` e `noexec`.
- Entender o campo `dump`.
- Entender o campo `pass`.
- Saber que `pass=1` normalmente corresponde à raiz.
- Saber que `pass=2` é utilizado para outros sistemas de arquivos.
- Usar `cat /etc/fstab`.
- Usar `mount -a`.
- Usar `blkid` para descobrir UUIDs.

---

# 🧠 RESUMO

```text
/etc/fstab
↓
File Systems Table
↓
Tabela de Sistemas de Arquivos
↓
CONFIGURA MONTAGENS
```

### Estrutura:

```text
1. device
2. mount point
3. filesystem
4. options
5. dump
6. pass
```

### Exemplo:

```text
UUID=xxxx  /home  ext4  defaults  0  2
```

---

# 🔑 CAMPOS PARA DECORAR

```text
DEVICE
↓
O QUE montar

MOUNT POINT
↓
ONDE montar

FILESYSTEM
↓
QUAL sistema de arquivos

OPTIONS
↓
COMO montar

DUMP
↓
BACKUP

PASS
↓
ORDEM DO fsck
```

---

# 🎯 COMANDO MAIS IMPORTANTE

```bash
sudo mount -a
```

**Tradução: mount all → montar todos**

**Função: tenta montar os sistemas de arquivos configurados no `/etc/fstab`.**

# ⚠️ REGRA IMPORTANTE

Depois de modificar:

```text
/etc/fstab
```

teste antes de reiniciar:

```bash
sudo mount -a
```

Isso ajuda a detectar erros de configuração no `fstab`.

# ✅ FIM DA PÁGINA 7
