# Sistemas de Arquivos e FHS

## 07 — mount e umount

### 1. `mount`

**mount** — *Mount* — **Montar**

Liga um sistema de arquivos a um diretório do Linux, chamado **Mount Point** — **Ponto de Montagem**.

Exemplo:

    sudo mount /dev/sdb1 /mnt

Interpretação:

    /dev/sdb1 → partição
    /mnt      → ponto de montagem

Depois da montagem, os arquivos de `/dev/sdb1` ficam acessíveis através de:

    /mnt

---

### 2. Ponto de montagem

**Mount Point** — **Ponto de Montagem**

É o diretório onde o sistema de arquivos será acessado.

Exemplos comuns:

    /mnt
    /media
    /home
    /boot
    /boot/efi

Criando um ponto de montagem:

    sudo mkdir /mnt/dados

Montando:

    sudo mount /dev/sdb1 /mnt/dados

Acessando:

    cd /mnt/dados

---

### 3. `umount`

**umount** — *Unmount* — **Desmontar**

Remove a montagem de um sistema de arquivos.

Exemplo:

    sudo umount /mnt/dados

Também é possível desmontar informando o dispositivo:

    sudo umount /dev/sdb1

> O comando é `umount`, e não `unmount`.

---

### 4. Visualizar montagens

`mount` sem argumentos mostra os sistemas de arquivos atualmente montados:

    mount

Uma forma mais organizada:

    findmnt

**findmnt** — *Find Mounts* — **Localizar Montagens**

Exemplo:

    findmnt /dev/sda1

---

### 5. `mount` com sistema de arquivos

Podemos informar o tipo:

    sudo mount -t ext4 /dev/sdb1 /mnt/dados

**`-t`** — *type* — **tipo**

Exemplo:

    sudo mount -t xfs /dev/sdb1 /mnt/dados

---

### 6. Montar usando UUID

Em vez de usar:

    sudo mount /dev/sdb1 /mnt/dados

Podemos usar o UUID:

    sudo mount UUID=7c8a-1234 /mnt/dados

Isso é muito importante porque o nome `/dev/sdb1` pode mudar conforme os dispositivos são detectados.

Para descobrir o UUID:

    sudo blkid

---

### 7. Montar usando LABEL

Também podemos usar o **LABEL** — **Rótulo**:

    sudo mount LABEL=DADOS /mnt/dados

Consultar:

    sudo blkid

---

### 8. Opções importantes do `mount`

| Opção | English | Português |
|---|---|---|
| `-t` | type | tipo do sistema de arquivos |
| `-a` | all | montar todos os sistemas definidos no `/etc/fstab` |
| `-o` | options | definir opções de montagem |
| `-r` | read-only | somente leitura |
| `-v` | verbose | mostrar detalhes da operação |

Exemplos:

    sudo mount -a

    sudo mount -o ro /dev/sdb1 /mnt/dados

`ro` — *read-only* — **somente leitura**

---

### 9. Desmontar corretamente

Antes de desmontar, saia do diretório:

    cd ~

Depois:

    sudo umount /mnt/dados

Se aparecer:

    target is busy

significa que algum processo ainda está usando o ponto de montagem.

Para descobrir quem está usando:

    sudo lsof /mnt/dados

ou:

    sudo fuser -m /mnt/dados

**lsof** — *List Open Files* — **Listar Arquivos Abertos**

**fuser** — *File User* — **Identificar processos que usam um arquivo ou sistema de arquivos**

---

### 10. `mount` × `umount`

| Comando | Função |
|---|---|
| `mount` | montar |
| `umount` | desmontar |
| `findmnt` | localizar/visualizar montagens |
| `blkid` | identificar UUID, LABEL e TYPE |
| `lsblk -f` | visualizar discos, partições e sistemas de arquivos |

Fluxo básico:

    lsblk -f
    sudo mkdir /mnt/dados
    sudo mount /dev/sdb1 /mnt/dados
    cd /mnt/dados
    sudo umount /mnt/dados

---

## Resumo LPIC-1

- `mount` → monta um sistema de arquivos.
- `umount` → desmonta um sistema de arquivos.
- **Mount Point** → ponto de montagem.
- `/mnt` → local tradicional para montagens temporárias.
- `/media` → usado normalmente para mídias removíveis.
- `mount -t` → especifica o tipo do sistema de arquivos.
- `mount -a` → monta os sistemas definidos no `/etc/fstab`.
- `mount -o ro` → monta somente para leitura.
- Podemos montar usando **dispositivo**, **UUID** ou **LABEL**.
- Antes de desmontar, nenhum processo deve estar usando o sistema de arquivos.
- `target is busy` → algo ainda está usando o ponto de montagem.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
