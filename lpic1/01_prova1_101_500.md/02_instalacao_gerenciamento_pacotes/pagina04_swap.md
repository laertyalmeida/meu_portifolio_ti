# 📖 HQ 2 — INSTALAÇÃO DO LINUX E GERENCIAMENTO DE PACOTES

# 📖 PÁGINA 4 — SWAP

# 🧠 1. O QUE É SWAP?

**Swap** é uma área de armazenamento utilizada pelo Linux como **memória virtual**.

Quando a RAM está sob pressão, o kernel pode mover algumas páginas de memória para a área de swap.

```text
RAM
↓
memória principal

SWAP
↓
área de armazenamento usada como memória virtual
```

⚠️ Swap é muito mais lenta que a RAM, porque normalmente está em um dispositivo de armazenamento.

---

# 💾 2. SWAP PODE SER PARTIÇÃO OU ARQUIVO

A swap pode ser criada como:

### Partição swap

```text
/dev/sda3
```

### Arquivo swap

```text
/swapfile
```

Portanto:

```text
SWAP
├── partição
└── arquivo
```

---

# 🧠 3. PARA QUE SERVE?

A swap pode ajudar quando a memória RAM disponível é insuficiente.

Exemplo:

```text
RAM
┌──────────────────┐
│ processos        │
│ processos        │
│ processos        │
│       CHEIA      │
└──────────────────┘
          ↓
        SWAP
┌──────────────────┐
│ páginas de       │
│ memória          │
└──────────────────┘
```

O kernel pode mover páginas menos utilizadas para a swap, liberando espaço na RAM para outras necessidades.

---

# 🔄 4. SWAP NÃO É SUBSTITUTO DA RAM

É importante entender:

```text
RAM
→ memória principal
→ muito rápida

SWAP
→ memória virtual em armazenamento
→ muito mais lenta
```

Portanto:

**Ter swap não significa ter mais RAM física.**

---

# 🔍 5. VERIFICAR A SWAP

Comando:

```bash
swapon --show
```

Mostra as áreas de swap ativas.

### Tradução

**swapon**

→ ativar/gerenciar swap.

**--show**

→ mostrar.

---

# 📊 6. `free`

Podemos verificar RAM e swap usando:

```bash
free -h
```

### Tradução

**free**

→ livre.

Mostra informações sobre memória.

### `-h`

→ **human-readable → legível por humanos**

Exemplo:

```text
              total   used   free
Mem:           3.8G    ...    ...
Swap:          2.0G    ...    ...
```

A linha `Swap` mostra informações sobre a área de swap.

---

# 🔌 7. ATIVAR UMA SWAP

O comando:

```bash
swapon
```

é utilizado para ativar uma área de swap.

Exemplo:

```bash
sudo swapon /dev/sda3
```

ou:

```bash
sudo swapon /swapfile
```

### Tradução

**swapon**

→ **swap on → ativar swap**

---

# ⛔ 8. DESATIVAR UMA SWAP

O comando:

```bash
swapoff
```

desativa uma área de swap.

Exemplo:

```bash
sudo swapoff /dev/sda3
```

ou:

```bash
sudo swapoff /swapfile
```

### Tradução

**swapoff**

→ **swap off → desativar swap**

---

# 🧩 9. SWAP NO `/etc/fstab`

Para ativar uma swap automaticamente durante a inicialização, sua configuração pode estar no:

```text
/etc/fstab
```

Exemplo:

```text
UUID=xxxx-xxxx none swap sw 0 0
```

Observe:

```text
none
```

→ não é um ponto de montagem comum.

```text
swap
```

→ tipo da área.

```text
sw
```

→ opções de swap.

---

# 🔢 10. `swapon -s`

Em sistemas onde essa forma é disponível:

```bash
swapon -s
```

mostra um resumo das áreas de swap.

### `-s`

→ **summary → resumo**

Para sistemas modernos, prefira:

```bash
swapon --show
```

---

# 🧠 11. OOM E SWAP

Quando a memória disponível fica extremamente baixa, o Linux pode chegar a uma situação de:

**OOM = Out Of Memory**

Tradução:

**sem memória**

O kernel possui mecanismos para lidar com falta de memória e, em determinadas situações, pode encerrar processos para recuperar memória.

A existência de swap pode ajudar a adiar situações de falta de memória, mas não elimina o problema.

---

# 📝 12. COMANDOS NECESSÁRIOS

### Mostrar swap ativa

```bash
swapon --show
```

→ mostra as áreas de swap ativas.

---

### Ativar swap

```bash
sudo swapon /dev/sda3
```

→ ativa a swap.

---

### Desativar swap

```bash
sudo swapoff /dev/sda3
```

→ desativa a swap.

---

### Ver RAM e swap

```bash
free -h
```

**free → livre**

**-h = human-readable → legível por humanos**

---

### Mostrar resumo da swap

```bash
swapon -s
```

**-s = summary → resumo**

---

# 🎯 13. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que é swap.
- Que swap é utilizada como memória virtual.
- Que swap pode ser uma partição.
- Que swap pode ser um arquivo.
- Que swap é muito mais lenta que RAM.
- Que swap não substitui RAM física.
- Que o kernel pode mover páginas de memória para swap.
- Usar `swapon`.
- Usar `swapoff`.
- Usar `swapon --show`.
- Conhecer `swapon -s`.
- Usar `free -h`.
- Reconhecer a linha `Swap` na saída do `free`.
- Conhecer a relação entre swap e `/etc/fstab`.
- Entender o conceito básico de OOM.

---

# 🧠 RESUMO

```text
SWAP
↓
MEMÓRIA VIRTUAL
↓
UTILIZA ARMAZENAMENTO
↓
MAIS LENTA QUE RAM
```

Pode existir como:

```text
PARTIÇÃO
/dev/sda3
```

ou:

```text
ARQUIVO
/swapfile
```

### Principais comandos:

```text
swapon
→ ativar swap

swapoff
→ desativar swap

swapon --show
→ mostrar swap ativa

free -h
→ mostrar RAM e swap
```

---

# 🔄 PARA MEMORIZAR

```text
RAM
↓
memória física
↓
rápida

SWAP
↓
memória virtual
↓
armazenamento
↓
mais lenta
```

# 🎯 COMANDOS PRINCIPAIS

```bash
swapon --show
```

→ **mostrar áreas de swap ativas**

```bash
free -h
```

→ **mostrar memória RAM e swap de forma legível**

```bash
sudo swapon /dev/sda3
```

→ **ativar swap**

```bash
sudo swapoff /dev/sda3
```

→ **desativar swap**

# ✅ FIM DA PÁGINA 4
