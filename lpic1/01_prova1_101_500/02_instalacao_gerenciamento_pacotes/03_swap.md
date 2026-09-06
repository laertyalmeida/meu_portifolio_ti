Swap

Swap — Área de Troca

Swap (Área de Troca) é um espaço no disco que o Linux pode usar quando precisa de memória além da RAM disponível.

RAM
 ↓
Fica cheia
 ↓
Linux pode usar
 ↓
Swap

A swap é mais lenta que a RAM, porque está no armazenamento.

---

Para que serve?

A swap pode ajudar quando:

- A RAM está muito ocupada.
- O sistema precisa liberar espaço na RAM.
- O computador entra em hibernação — dependendo da configuração.

Swap não substitui a RAM. Ela funciona como um espaço auxiliar.

---

Swap pode ser:

Swap Partition — Partição Swap

Uma partição inteira é usada como swap.

/dev/sda3 → swap

Swap File — Arquivo Swap

Um arquivo dentro de um sistema de arquivos é usado como swap.

/swapfile

---

Verificar a Swap

"free" — Free (Livre)

Mostra informações sobre o uso da memória.

free -h

"-h" — Human-readable (Legível por humanos)

Mostra os valores usando unidades mais fáceis de ler, como:

MiB
GiB

---

"swapon" — Swap On (Ativar Swap)

Mostra as áreas de swap ativas:

swapon --show

"--show" — Show (Mostrar)

Exibe as áreas de swap ativas.

---

"swapoff" — Swap Off (Desativar Swap)

Desativa uma área de swap.

sudo swapoff /dev/sda3

---

Criar Swap File

Um arquivo também pode ser usado como swap.

Exemplo:

sudo fallocate -l 2G /swapfile

"-l" — Length (Tamanho)

Define o tamanho do arquivo.

Nesse exemplo:

2G → 2 GB

Depois:

sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile

"600" — Permissões

Somente o proprietário pode ler e escrever no arquivo.

---

LPIC-1 — O que saber

- Swap é uma área de armazenamento usada como memória auxiliar.
- Swap é mais lenta que RAM.
- Pode ser uma partição ou um arquivo.
- "free -h" mostra memória de forma legível.
- "swapon" mostra/ativa swap.
- "swapoff" desativa swap.
- "mkswap" prepara uma área para ser usada como swap.
- Um swap file deve ter permissões restritas.

---

Resumo

RAM → rápida
 ↓
Quando necessário
 ↓
Swap → mais lenta

Swap
├── Partição
└── Arquivo

free -h       → memória
swapon        → swap
swapoff       → desativar
mkswap        → preparar swap

-h → Human-readable
-l → Length
