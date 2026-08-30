# 📖 PÁGINA 6 — PCI E PCI EXPRESS (PCIe)

## 🧠 1. O QUE É PCI?

**PCI = Peripheral Component Interconnect**

Tradução:

**Interconexão de Componentes Periféricos**

PCI é um padrão de barramento utilizado para conectar dispositivos de hardware ao computador.

Exemplos:

- Placa de rede
- Placa de som
- Placa de vídeo
- Controladora de armazenamento

---

# 🚀 2. O QUE É PCI EXPRESS?

**PCI Express = Peripheral Component Interconnect Express**

É uma evolução do PCI.

É normalmente abreviado como:

**PCIe**

O PCIe é utilizado atualmente para conectar dispositivos de alta velocidade.

Exemplos:

- Placas de vídeo
- Placas de rede de alta velocidade
- SSDs NVMe
- Placas de expansão

---

# ⚖️ 3. PCI x PCIe

### PCI

É um barramento mais antigo.

Possui uma arquitetura de barramento compartilhado.

### PCIe

É uma tecnologia mais moderna.

Utiliza **links seriais ponto a ponto** entre o dispositivo e o controlador.

Resumo:

**PCI**

→ tecnologia mais antiga.

→ barramento compartilhado.

**PCIe**

→ evolução do PCI.

→ comunicação ponto a ponto.

---

# 🛣️ 4. LANES DO PCIe

PCIe utiliza **lanes (faixas/canais)** para comunicação.

Uma lane possui canais de comunicação para transmissão e recepção de dados.

Os dispositivos PCIe podem utilizar diferentes quantidades de lanes.

Exemplos:

**x1**

→ 1 lane.

**x4**

→ 4 lanes.

**x8**

→ 8 lanes.

**x16**

→ 16 lanes.

Exemplo comum:

**Placa de vídeo PCIe x16**

→ utiliza uma conexão PCIe com 16 lanes.

### ⚠️ IMPORTANTE

`x16` não significa:

```text
❌ 16 bits
❌ 16 cores
❌ 16 threads
```

Significa:

**16 lanes PCIe.**

---

# 🔢 5. GERAÇÕES DO PCIe

O PCIe possui diferentes gerações.

Exemplos:

- PCIe 1.0
- PCIe 2.0
- PCIe 3.0
- PCIe 4.0
- PCIe 5.0
- PCIe 6.0

Cada geração aumenta a capacidade de transferência.

### 🧠 PARA A PROVA

O mais importante é reconhecer:

**PCIe**

→ evolução do PCI.

→ utiliza comunicação serial ponto a ponto.

→ pode utilizar diferentes quantidades de lanes.

---

# 🔍 6. `lspci`

O principal comando Linux para identificar dispositivos PCI é:

`lspci`

### Tradução

`ls`

→ **list → listar**

`pci`

→ **Peripheral Component Interconnect**

Portanto:

**lspci → list PCI → listar dispositivos PCI**

Execute:

`lspci`

Exemplo:

`00:14.0 USB controller: Intel Corporation ...`

Isso mostra um dispositivo/controlador conectado à infraestrutura PCI.

---

# 🧠 7. INTERPRETANDO O `lspci`

Considere:

`00:14.0 USB controller: Intel Corporation ...`

### `00:14.0`

É o endereço do dispositivo no barramento PCI.

### `USB controller`

É o tipo de dispositivo/controlador.

### `Intel Corporation`

É o fabricante.

Portanto, o `lspci` permite identificar:

**Endereço → Dispositivo → Fabricante**

---

# 🔎 8. `lspci -v`

A opção:

`-v`

significa:

**verbose = detalhado**

Comando:

`lspci -v`

Mostra informações mais detalhadas sobre os dispositivos PCI.

Interpretação:

`lspci`

→ list PCI → listar dispositivos PCI.

`-v`

→ verbose → detalhado.

---

# 🔬 9. `lspci -vv`

Podemos aumentar ainda mais o nível de detalhes:

`lspci -vv`

A ideia é:

`-v`

→ verbose → detalhado.

`-vv`

→ very verbose → muito detalhado.

---

# 🧰 10. `lspci -k`

A opção:

`-k`

mostra informações sobre os drivers do kernel associados aos dispositivos.

Comando:

`lspci -k`

Exemplo:

`Kernel driver in use: e1000e`

Interpretação:

`Kernel driver in use`

→ driver do kernel atualmente utilizado.

`e1000e`

→ nome do driver/módulo utilizado pelo dispositivo.

Isso permite relacionar:

**Dispositivo PCI → Driver do kernel**

---

# 🆔 11. `lspci -nn`

A opção:

`-n`

mostra identificadores numéricos.

A opção:

`-nn`

mostra os identificadores numéricos junto com os nomes.

Comando:

`lspci -nn`

Exemplo conceitual:

`[8086:1234]`

Esse identificador pode ajudar a identificar:

**Fabricante → Dispositivo**

### 🧠 Para memorizar

`-n`

→ **numeric → numérico**

`-nn`

→ mostra IDs numéricos juntamente com os nomes.

---

# 🔍 12. `lspci -t`

A opção:

`-t`

significa:

**tree = árvore**

Comando:

`lspci -t`

Mostra a estrutura dos dispositivos PCI em formato de árvore.

Isso ajuda a visualizar como os dispositivos estão conectados à hierarquia PCI.

---

# 📂 13. PCI E `/sys`

Informações dos dispositivos PCI também podem ser encontradas em:

`/sys/bus/pci/`

O diretório:

`/sys`

é uma interface fornecida pelo kernel para expor informações sobre dispositivos e outros componentes do sistema.

Para visualizar dispositivos PCI:

`ls /sys/bus/pci/devices/`

Interpretação:

`ls`

→ list → listar.

`/sys/bus/pci/devices/`

→ dispositivos registrados no barramento PCI.

---

# 📝 14. COMANDOS NECESSÁRIOS

### Listar dispositivos PCI

`lspci`

### Informações detalhadas

`lspci -v`

### Mais detalhes

`lspci -vv`

### Mostrar driver do kernel

`lspci -k`

### Mostrar IDs numéricos

`lspci -nn`

### Mostrar hierarquia PCI

`lspci -t`

### Consultar dispositivos PCI no `/sys`

`ls /sys/bus/pci/devices/`

---

# 🎯 15. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que significa PCI.
- Que PCI significa **Peripheral Component Interconnect**.
- O que é um barramento PCI.
- O que significa PCI Express.
- Que PCIe é a evolução do PCI.
- Diferença básica entre PCI e PCIe.
- Que PCIe utiliza comunicação ponto a ponto.
- O que é uma lane PCIe.
- O significado de `x1`, `x4`, `x8` e `x16`.
- Que `x16` significa 16 lanes.
- Que `x16` não significa 16 bits.
- Reconhecer algumas gerações do PCIe.
- Usar `lspci`.
- Saber que `ls` significa **list**.
- Usar `lspci -v`.
- Saber que `-v` significa **verbose**.
- Usar `lspci -k`.
- Saber que `-k` mostra o driver do kernel.
- Usar `lspci -nn`.
- Saber que `-n` significa **numeric**.
- Usar `lspci -t`.
- Saber que `-t` significa **tree**.
- Conhecer `/sys/bus/pci/devices/`.

---

# 🧠 RESUMO

**PCI**

→ Peripheral Component Interconnect.

→ Barramento para conexão de dispositivos.

**PCIe**

→ Peripheral Component Interconnect Express.

→ Evolução do PCI.

**PCIe lane**

→ Canal de comunicação do PCIe.

**x1**

→ 1 lane.

**x4**

→ 4 lanes.

**x8**

→ 8 lanes.

**x16**

→ 16 lanes.

**lspci**

→ list PCI.

→ Lista dispositivos PCI.

**lspci -v**

→ verbose.

→ Informações detalhadas.

**lspci -vv**

→ very verbose.

→ Mais detalhes.

**lspci -k**

→ Mostra o driver do kernel utilizado.

**lspci -nn**

→ numeric.

→ Mostra identificadores numéricos junto aos nomes.

**lspci -t**

→ tree.

→ Mostra a hierarquia PCI em árvore.

**/sys/bus/pci/devices/**

→ Informações dos dispositivos PCI expostas pelo kernel.

---

# ✅ FIM DA PÁGINA 6
