# Memória

## 02 — Swap (Área de Troca)

**Swap — Área de Troca** é um espaço no disco usado pelo Linux para armazenar temporariamente páginas de memória que não precisam estar na RAM naquele momento.

> **RAM = memória física**
>
> **Swap = espaço no disco usado como memória de apoio**

---

### 1. Como funciona

Quando a RAM começa a ficar ocupada, o Linux pode mover páginas de memória menos usadas para a Swap.

    Programa
       ↓
    Memória Virtual
       ↓
    ┌──────────────┐
    │     RAM      │
    └──────────────┘
       ↕
    ┌──────────────┐
    │     Swap     │
    │    (disco)   │
    └──────────────┘

A Swap é **muito mais lenta que a RAM**, porque normalmente está em um dispositivo de armazenamento.

---

### 2. Swap pode ser

| Tipo | Nome em inglês | Descrição |
|---|---|---|
| Partição Swap | Swap Partition | Partição dedicada à Swap |
| Arquivo Swap | Swap File | Arquivo usado como Swap |

Exemplos:

    /dev/sda2
    /dev/nvme0n1p3

ou:

    /swapfile

---

### 3. Ver a Swap

    swapon --show

**swapon — Enable Swap — Ativar Swap**

Mostra as áreas de Swap atualmente ativas.

Outra opção:

    free -h

**free — Display Memory Usage — Exibir Uso da Memória**

`-h` — Human Readable — Formato Legível

Exemplo:

    Swap:   2.0Gi   0B   2.0Gi

---

### 4. Criar uma Swap

Para uma **partição**:

    sudo mkswap /dev/sdb2

**mkswap — Make Swap — Criar Swap**

Depois:

    sudo swapon /dev/sdb2

**swapon — Enable Swap — Ativar Swap**

Para desativar:

    sudo swapoff /dev/sdb2

**swapoff — Disable Swap — Desativar Swap**

---

### 5. Criar Swap em arquivo

Exemplo:

    sudo fallocate -l 2G /swapfile

    sudo chmod 600 /swapfile

    sudo mkswap /swapfile

    sudo swapon /swapfile

Verificar:

    swapon --show

---

### 6. Ativar automaticamente no boot

A Swap pode ser configurada no:

    /etc/fstab

Exemplo usando uma partição:

    UUID=xxxx-xxxx none swap sw 0 0

Exemplo usando arquivo:

    /swapfile none swap sw 0 0

Depois de alterar o `/etc/fstab`, pode testar com:

    sudo swapon -a

**`-a` — All — Todos**

Ativa as áreas de Swap configuradas no `/etc/fstab`.

---

### 7. Swap não substitui RAM

A Swap ajuda quando a RAM está sob pressão, mas **não transforma o disco em RAM**.

    RAM → muito rápida
    Swap → muito mais lenta

Ter muita Swap não significa ter mais RAM física.

---

### 8. Ver informações da memória

    free -h

    swapon --show

    cat /proc/meminfo

Algumas informações importantes:

| Campo | Significado |
|---|---|
| `MemTotal` | RAM total |
| `MemFree` | RAM livre |
| `MemAvailable` | RAM disponível |
| `SwapTotal` | Swap total |
| `SwapFree` | Swap livre |

---

## Resumo LPIC-1

- **Swap** = Área de Troca usada como apoio à RAM.
- Pode ser **partição** ou **arquivo**.
- Swap fica no armazenamento e é muito mais lenta que RAM.
- `mkswap` → prepara uma área para Swap.
- `swapon` → ativa Swap.
- `swapoff` → desativa Swap.
- `swapon --show` → mostra Swap ativa.
- `free -h` → mostra RAM e Swap.
- `/etc/fstab` → pode configurar Swap para ativação automática.
- Swap **não é RAM adicional física**.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
