# 08 — Memória
## 02 — Swap

### Swap — Área de Troca

**Swap** é uma área do armazenamento usada pelo Linux para auxiliar o gerenciamento da memória.

Pode ser criada como:

- **Swap Partition** — Partição Swap
- **Swap File** — Arquivo Swap

A Swap não é RAM. Ela fica no dispositivo de armazenamento e, por isso, é normalmente muito mais lenta.

---

### Para que serve a Swap?

Quando existe pressão de memória, o Linux pode mover **páginas de memória** pouco utilizadas da RAM para a Swap.

    RAM
     │
     │ páginas pouco usadas
     ↓
    Swap

Isso libera espaço na RAM para outros dados e processos.

⚠️ Usar Swap não significa necessariamente que a RAM acabou. O kernel pode utilizar Swap por diferentes motivos de gerenciamento de memória.

---

### Ver o uso da Swap

Use:

    free -h

Exemplo:

    Swap:    2Gi    512Mi    1.5Gi

Significa:

- `2Gi` → total de Swap
- `512Mi` → Swap utilizada
- `1.5Gi` → Swap disponível

---

### swapon — Enable Swap (Ativar Swap)

Para visualizar as áreas de Swap ativas:

    swapon --show

Exemplo:

    NAME      TYPE      SIZE   USED  PRIO
    /swapfile file      2G     0B    -2

---

### swapoff — Disable Swap (Desativar Swap)

Para desativar uma área de Swap:

    sudo swapoff /swapfile

⚠️ O sistema precisa conseguir acomodar na RAM os dados que estavam na Swap.

---

### Criando um Swap File

Um exemplo comum:

    sudo fallocate -l 2G /swapfile

Criar permissões adequadas:

    sudo chmod 600 /swapfile

Preparar o arquivo:

    sudo mkswap /swapfile

- `mkswap` — Make Swap (preparar área Swap)

Ativar:

    sudo swapon /swapfile

Verificar:

    swapon --show

---

### Tornando a Swap permanente

Para ativar automaticamente durante o boot, uma entrada pode ser adicionada ao:

    /etc/fstab

Exemplo:

    /swapfile none swap sw 0 0

Depois:

    sudo swapon -a

- `-a` — all (ativar todas as áreas de Swap configuradas)

---

### Swap Partition — Partição Swap

Uma partição também pode ser preparada para Swap:

    sudo mkswap /dev/sdb2

Depois:

    sudo swapon /dev/sdb2

Verificar:

    swapon --show

---

### swappiness — Tendência de uso da Swap

O parâmetro **swappiness** controla a tendência do kernel de utilizar Swap.

Consultar:

    cat /proc/sys/vm/swappiness

Exemplo:

    60

Um valor maior geralmente indica maior disposição para utilizar Swap.

⚠️ **Swappiness não significa "percentual de RAM que será usado antes da Swap".**

---

### Alterar temporariamente

    sudo sysctl vm.swappiness=10

Consultar:

    sysctl vm.swappiness

Essa alteração normalmente não sobrevive a um reboot.

---

### Swap × RAM

| RAM | Swap |
|---|---|
| Memória física | Área de troca |
| Muito mais rápida | Mais lenta |
| Está na memória principal | Fica no armazenamento |
| Usada diretamente pelos processos | Usada pelo gerenciamento de memória |

---

### Comandos importantes

    free -h
    swapon --show
    sudo swapon /swapfile
    sudo swapoff /swapfile
    sudo mkswap /swapfile
    cat /proc/sys/vm/swappiness

---

### ⚠️ Atenção para a prova LPIC-1

Memorize:

**`mkswap`**
→ prepara uma partição ou arquivo para ser usado como Swap.

**`swapon`**
→ ativa Swap.

**`swapoff`**
→ desativa Swap.

**`swapon --show`**
→ mostra as áreas de Swap ativas.

**`free -h`**
→ mostra RAM e Swap.

**`/etc/fstab`**
→ pode configurar a Swap para ser ativada automaticamente no boot.

**Swap ≠ RAM**
→ Swap ajuda no gerenciamento da memória, mas é muito mais lenta que a RAM.

> **Conhecimento só tem valor quando é compartilhado** - Laerte Costa
