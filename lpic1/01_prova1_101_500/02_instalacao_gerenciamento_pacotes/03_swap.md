# Instalação e Gerenciamento de Pacotes

## 03 — Swap

### Swap — Área de Troca

**Swap — Área de Troca** é um espaço em disco usado pelo Linux como extensão da memória RAM.

Quando a RAM está sob pressão, o kernel pode mover algumas páginas de memória para a **Swap**, liberando RAM para outras tarefas.

    RAM
     ↓
    memória principal

    Swap
     ↓
    espaço em disco usado como apoio à memória

**Importante:** Swap é muito mais lenta que a RAM.

---

## Swap Partition — Partição Swap

É uma partição dedicada exclusivamente à Swap.

Exemplo:

    /dev/sda3

Para preparar a partição:

    sudo mkswap /dev/sda3

- `mkswap` — Make Swap — preparar área Swap

Ativar:

    sudo swapon /dev/sda3

- `swapon` — ativar Swap

Desativar:

    sudo swapoff /dev/sda3

- `swapoff` — desativar Swap

---

## Swap File — Arquivo Swap

Também é possível usar um arquivo em vez de uma partição.

Exemplo:

    sudo fallocate -l 2G /swapfile

- `fallocate` — File Allocation — alocar espaço
- `-l` — length — tamanho
- `2G` — 2 gigabytes

Definir permissões:

    sudo chmod 600 /swapfile

- `chmod` — Change Mode — alterar permissões
- `600` — somente o proprietário pode ler e escrever

Preparar:

    sudo mkswap /swapfile

Ativar:

    sudo swapon /swapfile

---

## Verificar a Swap

### free — Livre

    free -h

- `-h` — human-readable — formato legível para humanos

Exemplo:

    Swap:
    2Gi    0B    2Gi

Mostra:

- **total** — quantidade total de Swap;
- **used** — quantidade utilizada;
- **free** — quantidade livre.

---

### swapon — Ativar/Consultar Swap

    swapon --show

- `--show` — mostrar informações da Swap

Também podemos usar:

    cat /proc/swaps

- `/proc` — Process Information — informações de processos/sistema
- `/proc/swaps` — informações sobre as áreas Swap ativas

---

## Swappiness — Tendência de Uso da Swap

**Swappiness — Tendência de Uso da Swap** é um parâmetro do kernel que influencia a preferência do Linux em utilizar Swap.

Ver o valor atual:

    cat /proc/sys/vm/swappiness

Exemplo:

    60

Alterar temporariamente:

    sudo sysctl vm.swappiness=10

- `sysctl` — System Control — controle de parâmetros do kernel
- `vm` — Virtual Memory — memória virtual

A alteração feita dessa forma normalmente não permanece após a reinicialização.

---

## Swap no /etc/fstab

Para ativar a Swap automaticamente durante o boot, ela pode ser configurada no:

    /etc/fstab

- `/etc` — etcetera — arquivos de configuração do sistema
- `fstab` — File Systems Table — tabela de sistemas de arquivos

Exemplo de uma entrada:

    /swapfile none swap defaults 0 0

Para uma partição:

    /dev/sda3 none swap defaults 0 0

Depois, é possível ativar as entradas configuradas com:

    sudo swapon -a

- `-a` — all — todos

---

## Swap × RAM

| RAM | Swap |
|---|---|
| Memória física | Espaço em disco |
| Muito mais rápida | Muito mais lenta |
| Uso principal | Apoio à memória |
| Volátil | Persistente enquanto configurada no disco |

Swap **não substitui** uma quantidade adequada de RAM.

---

## Resumo LPIC-1

- **Swap — Área de Troca** = espaço em disco usado como apoio à memória.
- **Swap Partition — Partição Swap** = partição dedicada à Swap.
- **Swap File — Arquivo Swap** = arquivo usado como Swap.
- `mkswap` = preparar Swap.
- `swapon` = ativar Swap.
- `swapoff` = desativar Swap.
- `free -h` = verificar memória e Swap.
- `swapon --show` = mostrar Swap ativa.
- `/proc/swaps` = informações sobre Swap ativa.
- `swappiness` = influencia a tendência de uso da Swap.
- `/etc/fstab` = pode configurar a ativação automática da Swap.
- **RAM é muito mais rápida que Swap.**

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
