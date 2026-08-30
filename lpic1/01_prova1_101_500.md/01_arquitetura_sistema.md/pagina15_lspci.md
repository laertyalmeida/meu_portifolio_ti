# 📖 PÁGINA 15 — LSPCI

# 🧠 1. O QUE É `lspci`?

`lspci` é um comando utilizado para listar dispositivos conectados ao barramento **PCI**.

### Tradução

`ls`

→ **list → listar**

`pci`

→ **Peripheral Component Interconnect**

→ Interconexão de Componentes Periféricos.

Portanto:

**lspci → list PCI → listar dispositivos PCI**

---

# 🔍 2. USO BÁSICO

Comando:

`lspci`

Mostra os dispositivos PCI detectados pelo sistema.

Exemplo:

`00:14.0 USB controller: Intel Corporation ...`

Podemos encontrar dispositivos como:

- Controladores USB
- Placas de rede
- Controladores SATA
- Placas de vídeo
- Controladores de áudio

---

# 🧩 3. ENTENDENDO A SAÍDA

Exemplo:

`00:1f.6 Ethernet controller: Intel Corporation ...`

### `00:1f.6`

Endereço do dispositivo no barramento PCI.

### `Ethernet controller`

Tipo de dispositivo.

### `Intel Corporation`

Fabricante.

Portanto:

**Endereço → Tipo → Fabricante**

---

# 🔎 4. `lspci -v`

Comando:

`lspci -v`

### Tradução

**verbose**

→ detalhado.

A opção `-v` apresenta informações mais detalhadas sobre os dispositivos.

### `-v`

→ **verbose → detalhado**

---

# 🔬 5. `lspci -vv`

Comando:

`lspci -vv`

A opção `-vv` aumenta ainda mais o nível de detalhes.

### `-vv`

→ **very verbose → muito detalhado**

---

# 🆔 6. `lspci -n`

Comando:

`lspci -n`

A opção `-n` mostra identificadores numéricos em vez de tentar apresentar nomes.

### `-n`

→ **numeric → numérico**

Isso é útil para identificar dispositivos através dos seus IDs.

---

# 🆔 7. `lspci -nn`

Comando:

`lspci -nn`

Mostra os identificadores numéricos junto com os nomes.

Exemplo:

`Ethernet controller [0200]: Intel Corporation [8086:...]`

### `-nn`

→ mostra **nomes + IDs numéricos**.

---

# 🧠 8. ID PCI

Um dispositivo PCI possui identificadores que ajudam a identificar:

**Vendor ID**

→ ID do fabricante.

**Device ID**

→ ID do dispositivo.

Um formato comum é:

`8086:xxxx`

Onde:

`8086`

→ identificador do fabricante.

O segundo valor identifica o dispositivo.

### 🧠 Para a prova

Não é necessário decorar IDs específicos.

É importante entender que:

**IDs PCI → identificam fabricante e dispositivo.**

---

# 🔧 9. `lspci -k`

Comando:

`lspci -k`

Mostra informações sobre os drivers utilizados pelos dispositivos PCI.

Pode aparecer:

`Kernel driver in use: ...`

e:

`Kernel modules: ...`

### Tradução

**Kernel**

→ núcleo.

**driver**

→ controlador.

**module**

→ módulo.

Portanto:

`lspci -k`

→ mostra o driver do kernel e os módulos associados ao dispositivo.

---

# 🌳 10. `lspci -t`

Comando:

`lspci -t`

### Tradução

**tree = árvore**

Mostra os dispositivos PCI em uma estrutura hierárquica.

### `-t`

→ **tree → árvore**

Isso ajuda a visualizar a topologia do barramento PCI.

---

# 🔍 11. COMBINANDO OPÇÕES

As opções podem ser combinadas.

Exemplo:

`lspci -nnk`

Isso permite:

`-nn`

→ nomes + IDs numéricos.

`-k`

→ informações sobre drivers e módulos.

Assim, podemos obter informações bastante úteis sobre um dispositivo PCI.

---

# 📂 12. RELAÇÃO COM `/sys`

O `lspci` obtém informações disponibilizadas pelo sistema sobre os dispositivos PCI.

O kernel também expõe informações relacionadas ao PCI através de:

`/sys/bus/pci/`

Especialmente:

`/sys/bus/pci/devices/`

Portanto:

**lspci**

→ ferramenta de consulta.

**/sys/bus/pci/**

→ interface do kernel com informações dos dispositivos PCI.

---

# 🧠 13. RELAÇÃO COM DRIVERS

Uma sequência importante é:

**Hardware PCI**

↓

**Kernel**

↓

**Driver**

↓

**Dispositivo funcionando**

O comando:

`lspci -k`

ajuda a descobrir qual driver está sendo utilizado.

Exemplo:

`Kernel driver in use: e1000e`

Isso significa que o dispositivo está utilizando o módulo/driver `e1000e`.

---

# 📝 14. COMANDOS NECESSÁRIOS

### Listar dispositivos PCI

`lspci`

→ list PCI → listar dispositivos PCI.

### Informações detalhadas

`lspci -v`

→ `-v = verbose → detalhado`

### Informações muito detalhadas

`lspci -vv`

→ `-vv = very verbose → muito detalhado`

### IDs numéricos

`lspci -n`

→ `-n = numeric → numérico`

### Nomes + IDs

`lspci -nn`

→ nomes + identificadores numéricos.

### Drivers e módulos

`lspci -k`

→ mostra driver do kernel e módulos associados.

### Árvore PCI

`lspci -t`

→ `-t = tree → árvore`

### Informações completas

`lspci -nnk`

→ IDs + nomes + drivers/módulos.

---

# 🎯 15. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- Para que serve `lspci`.
- Que `lspci` lista dispositivos PCI.
- O significado de `ls`.
- O significado de PCI.
- Interpretar uma linha básica do `lspci`.
- O que é o endereço PCI.
- O que são Vendor ID e Device ID.
- Usar `lspci -v`.
- Saber que `-v` significa verbose.
- Usar `lspci -vv`.
- Saber que `-vv` aumenta o nível de detalhes.
- Usar `lspci -n`.
- Saber que `-n` significa numeric.
- Usar `lspci -nn`.
- Saber que `-nn` mostra nomes e IDs numéricos.
- Usar `lspci -k`.
- Saber que `-k` mostra drivers e módulos.
- Usar `lspci -t`.
- Saber que `-t` significa tree.
- Entender a relação entre `lspci`, kernel, drivers e `/sys`.

---

# 🧠 RESUMO

**lspci**

→ list PCI.

→ lista dispositivos PCI.

**-v**

→ verbose → detalhado.

**-vv**

→ very verbose → muito detalhado.

**-n**

→ numeric → numérico.

**-nn**

→ nomes + IDs numéricos.

**-k**

→ mostra drivers e módulos do kernel.

**-t**

→ tree → árvore.

**lspci -nnk**

→ nomes + IDs + drivers/módulos.

---

# 🔄 PARA MEMORIZAR

```text
lspci
│
├── -v    → verbose → detalhado
├── -vv   → very verbose → muito detalhado
├── -n    → numeric → numérico
├── -nn   → nomes + IDs
├── -k    → drivers/módulos
└── -t    → tree → árvore
```

# 🎯 COMANDO MAIS IMPORTANTE

```bash
lspci -nnk
```

**Lista dispositivos PCI, mostra seus identificadores e informa quais drivers/módulos estão associados.**

# ✅ FIM DA PÁGINA 15
