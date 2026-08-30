# 📖 HQ 2 — INSTALAÇÃO DO LINUX E GERENCIAMENTO DE PACOTES

# 📖 PÁGINA 2 — MBR

# 🧠 1. O QUE É MBR?

**MBR = Master Boot Record**

Tradução:

**Registro Mestre de Inicialização**

MBR é um formato tradicional de **tabela de partições** e também está relacionado ao código de inicialização localizado no início do disco.

É um padrão antigo, muito associado ao modo de inicialização **BIOS**.

---

# 💽 2. ONDE FICA O MBR?

O MBR fica no início do disco.

Representação simplificada:

```text
DISCO
┌──────────────────────────────────────────────┐
│ MBR                                          │
│ ↓                                            │
│ Informações de inicialização + partições    │
├──────────────────────────────────────────────┤
│ Partição 1                                   │
├──────────────────────────────────────────────┤
│ Partição 2                                   │
├──────────────────────────────────────────────┤
│ Partição 3                                   │
└──────────────────────────────────────────────┘
```

---

# 🔢 3. LIMITE DE 4 PARTIÇÕES PRIMÁRIAS

Uma limitação importante do MBR é permitir até:

**4 partições primárias**

Exemplo:

```text
MBR
│
├── Primária 1
├── Primária 2
├── Primária 3
└── Primária 4
```

Para criar mais partições, utiliza-se o conceito de:

**partição estendida**

Dentro dela podem existir:

**partições lógicas**

Exemplo:

```text
MBR
│
├── Primária
├── Primária
├── Primária
└── Estendida
     ├── Lógica
     ├── Lógica
     └── Lógica
```

---

# 💾 4. LIMITE DE TAMANHO

Com o esquema tradicional de MBR, utilizando setores de 512 bytes, existe um limite aproximado de:

**2 TiB**

para um disco/partição endereçável nesse esquema.

Esse é um dos motivos pelos quais o GPT foi criado para substituir as limitações do MBR em sistemas modernos.

---

# 🧩 5. MBR x GPT

Você precisa saber a diferença básica:

```text
MBR
→ antigo
→ muito associado ao BIOS
→ até 4 partições primárias
→ limite tradicional de aproximadamente 2 TiB
```

```text
GPT
→ moderno
→ utilizado normalmente com UEFI
→ suporta muito mais partições
→ suporta discos muito maiores
```

A comparação detalhada com GPT será estudada na próxima página.

---

# 🔍 6. IDENTIFICANDO MBR COM `fdisk`

Podemos verificar a tabela de partições usando:

```bash
sudo fdisk -l
```

Na saída, o sistema pode indicar algo como:

```text
Disklabel type: dos
```

Nesse contexto:

**dos → MBR**

O `fdisk` utiliza `dos` para identificar a tabela de partições MBR.

---

# 🛠️ 7. `fdisk`

O comando:

```bash
fdisk
```

é uma ferramenta para manipulação de tabelas de partição.

### Tradução

**fdisk**

→ ferramenta de gerenciamento/particionamento de discos.

Podemos abrir um disco:

```bash
sudo fdisk /dev/sda
```

Dentro do `fdisk`, podemos consultar a tabela de partições.

A opção:

```text
p
```

→ **print → imprimir/mostrar**

mostra a tabela de partições.

---

# 📝 8. COMANDOS NECESSÁRIOS

### Ver tabela de partições

```bash
sudo fdisk -l
```

**fdisk**

→ ferramenta de gerenciamento de partições.

**-l**

→ **list → listar**

---

### Abrir o disco

```bash
sudo fdisk /dev/sda
```

→ abre o disco `/dev/sda` para gerenciamento.

---

### Dentro do `fdisk`

```text
p
```

**print → mostrar/imprimir**

→ mostra a tabela de partições.

---

# 🎯 9. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O significado de MBR.
- Que MBR significa **Master Boot Record**.
- A tradução de MBR.
- Que MBR é uma tabela de partições tradicional.
- Que o MBR fica no início do disco.
- A relação tradicional entre MBR e BIOS.
- Que MBR suporta até 4 partições primárias.
- O conceito de partição estendida.
- O conceito de partição lógica.
- O limite tradicional de aproximadamente 2 TiB.
- A diferença básica entre MBR e GPT.
- Usar `fdisk -l`.
- Reconhecer `Disklabel type: dos` como MBR.
- Saber que `p` no `fdisk` significa **print**.

---

# 🧠 RESUMO

```text
MBR
│
├── Master Boot Record
│
├── tabela de partições tradicional
│
├── início do disco
│
├── associado ao BIOS
│
├── até 4 partições primárias
│
├── pode usar partição estendida
│      └── partições lógicas
│
└── limite tradicional ≈ 2 TiB
```

# ⚖️ PARA MEMORIZAR

```text
MBR
→ antigo
→ BIOS
→ 4 partições primárias
→ ≈ 2 TiB
```

```text
GPT
→ moderno
→ UEFI
→ muitas partições
→ discos muito maiores
```

# 🔑 PALAVRAS-CHAVE

```text
MBR
→ Master Boot Record
→ Registro Mestre de Inicialização

Primary
→ primária

Extended
→ estendida

Logical
→ lógica

fdisk
→ gerenciamento de partições

-l
→ list → listar

p
→ print → mostrar
```

# ✅ FIM DA PÁGINA 2
