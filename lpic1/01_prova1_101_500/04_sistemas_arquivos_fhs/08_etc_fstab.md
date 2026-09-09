# Sistemas de Arquivos e FHS

## 08 — /etc/fstab

### 1. O que é `/etc/fstab`

`/etc/fstab` — *Filesystem Table* — **Tabela de Sistemas de Arquivos**

É o arquivo que define quais sistemas de arquivos podem ser montados e **como devem ser montados**.

Localização:

    /etc/fstab

Ele é usado principalmente para configurar montagens automáticas durante a inicialização do Linux.

---

### 2. Estrutura de uma linha

Uma entrada normalmente possui **6 campos**:

    dispositivo    ponto_de_montagem    tipo    opções    dump    fsck

Exemplo:

    UUID=7c8a1234-5678-90ab-cdef-1234567890ab  /dados  ext4  defaults  0  2

---

### 3. Campo 1 — Dispositivo

Identifica o sistema de arquivos que será montado.

Pode ser:

**Device** — **Dispositivo**

    /dev/sda1

**UUID** — *Universally Unique Identifier* — **Identificador Universalmente Único**

    UUID=7c8a1234-5678-90ab-cdef-1234567890ab

**LABEL** — *Label* — **Rótulo**

    LABEL=DADOS

O uso de `UUID` é muito comum no `/etc/fstab`.

Para descobrir:

    sudo blkid

---

### 4. Campo 2 — Mount Point

**Mount Point** — **Ponto de Montagem**

Indica onde o sistema de arquivos será acessado.

Exemplos:

    /
    /home
    /boot
    /boot/efi
    /dados

Exemplo:

    UUID=...    /dados    ext4    defaults    0    2

Nesse caso, a partição será montada em:

    /dados

---

### 5. Campo 3 — Filesystem Type

**Filesystem Type** — **Tipo de Sistema de Arquivos**

Exemplos:

| Tipo | Significado |
|---|---|
| `ext4` | Extended Filesystem 4 — Sistema de Arquivos Estendido 4 |
| `xfs` | X File System — Sistema de Arquivos X |
| `btrfs` | B-tree File System — Sistema de Arquivos B-tree |
| `vfat` | Virtual FAT — usado, por exemplo, em ESP |
| `swap` | espaço de troca |

Exemplo:

    UUID=...    /dados    ext4    defaults    0    2

---

### 6. Campo 4 — Mount Options

**Mount Options** — **Opções de Montagem**

Define como o sistema de arquivos será montado.

Opção comum:

    defaults

`defaults` — **opções padrão**

Normalmente representa um conjunto de opções padrão, como leitura/escrita e montagem automática.

Outras opções importantes:

| Opção | English | Português |
|---|---|---|
| `ro` | read-only | somente leitura |
| `rw` | read-write | leitura e escrita |
| `noauto` | no automatic mount | não montar automaticamente |
| `user` | user mount | permite montagem por usuário |
| `users` | users mount | permite montagem por usuários |
| `exec` | execute | permite execução |
| `noexec` | no execute | impede execução |
| `suid` | set-user-ID | permite SUID/SGID |
| `nosuid` | no set-user-ID | impede SUID/SGID |
| `dev` | devices | permite dispositivos |
| `nodev` | no devices | impede dispositivos |

---

### 7. Campo 5 — Dump

**dump** — **Backup pelo utilitário `dump`**

Historicamente indica se o sistema de arquivos deve ser considerado pelo comando `dump`.

Valores comuns:

    0 → não considerar
    1 → considerar

Na maioria dos sistemas modernos, utiliza-se:

    0

---

### 8. Campo 6 — fsck

**fsck** — *Filesystem Check* — **Verificação do Sistema de Arquivos**

Define a ordem em que os sistemas de arquivos devem ser verificados durante a inicialização.

Valores comuns:

    0 → não verificar
    1 → primeira prioridade
    2 → verificar depois do sistema de arquivos principal

Normalmente:

    /       → 1
    /home   → 2

---

### 9. Exemplo completo

    UUID=1111-2222  /       ext4  defaults  0  1
    UUID=3333-4444  /home   ext4  defaults  0  2

Interpretação:

    UUID=1111-2222 → dispositivo
    /              → ponto de montagem
    ext4           → sistema de arquivos
    defaults       → opções
    0              → dump
    1              → prioridade do fsck

---

### 10. Comentários

Linhas iniciadas com `#` são comentários:

    # Disco de dados
    UUID=aaaa-bbbb  /dados  ext4  defaults  0  2

Os comentários não são processados como entradas de montagem.

---

### 11. Testar o `/etc/fstab`

Depois de alterar o arquivo, é importante verificar se a configuração está correta.

    sudo mount -a

**`-a`** — *all* — **todos**

O comando tenta montar os sistemas de arquivos definidos no `/etc/fstab` que ainda não estejam montados.

Se houver erro de configuração, ele poderá ser apresentado antes de uma reinicialização.

---

### 12. Exemplo prático

Criar o ponto de montagem:

    sudo mkdir /dados

Descobrir o UUID:

    sudo blkid /dev/sdb1

Editar:

    sudo nano /etc/fstab

Adicionar:

    UUID=xxxx-xxxx  /dados  ext4  defaults  0  2

Testar:

    sudo mount -a

Verificar:

    findmnt /dados

---

### 13. Cuidados

O `/etc/fstab` é lido durante o processo de inicialização.

Uma entrada incorreta pode causar problemas na montagem dos sistemas de arquivos e até afetar a inicialização do sistema.

Antes de alterar:

    sudo cp /etc/fstab /etc/fstab.bak

Depois, teste:

    sudo mount -a

---

## Resumo LPIC-1

- `/etc/fstab` → **Filesystem Table — Tabela de Sistemas de Arquivos**.
- Define sistemas de arquivos e suas configurações de montagem.
- Possui normalmente **6 campos**.
- `UUID` → identifica a partição.
- Mount Point → local onde o sistema de arquivos será montado.
- `ext4`, `xfs`, `btrfs`, `vfat`, `swap` → exemplos de tipos.
- `defaults` → opções padrão.
- `0` no campo **dump** → não considerar pelo `dump`.
- `1` no campo **fsck** → primeira prioridade.
- `2` no campo **fsck** → verificar depois do sistema principal.
- `0` no campo **fsck** → não verificar.
- `sudo mount -a` → testa/tenta montar as entradas do `/etc/fstab`.
- Comentários começam com `#`.
- `UUID` é preferível a depender diretamente de `/dev/sdX`, pois a identificação do dispositivo pode mudar.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
