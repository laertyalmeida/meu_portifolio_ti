# 📖 PÁGINA 19 — DMESG

# 🧠 1. O QUE É `dmesg`?

`dmesg` é utilizado para **exibir mensagens do kernel Linux**.

Essas mensagens são especialmente úteis para verificar acontecimentos relacionados a:

- Inicialização do sistema
- Hardware
- Drivers
- Dispositivos
- USB
- PCI
- Rede
- Erros do kernel

### Tradução

`dmesg`

→ **display message**

→ exibir mensagens.

Portanto:

**dmesg → exibir mensagens do kernel**

---

# 🧠 2. DE ONDE VÊM AS MENSAGENS?

Durante o funcionamento do sistema, o kernel registra mensagens relacionadas aos eventos que acontecem.

Exemplos:

```text
Kernel iniciou
↓
Detectou CPU
↓
Detectou memória
↓
Detectou PCI
↓
Detectou USB
↓
Carregou drivers
↓
Detectou dispositivos
```

Esses eventos podem aparecer nas mensagens consultadas pelo `dmesg`.

---

# 🔌 3. EXEMPLO COM USB

Conectamos um pendrive.

O kernel detecta o dispositivo.

Podemos consultar:

```bash
dmesg
```

E procurar informações sobre USB:

```bash
dmesg | grep -i usb
```

### `|`

**pipe**

→ envia a saída de um comando para outro.

### `grep`

→ procurar um padrão.

### `-i`

**ignore case**

→ ignorar maiúsculas e minúsculas.

Portanto:

```bash
dmesg | grep -i usb
```

→ procura mensagens relacionadas a USB.

---

# 🔎 4. PROCURANDO ERROS

Podemos procurar palavras relacionadas a erros:

```bash
dmesg | grep -i error
```

### `error`

→ erro.

Também podemos procurar:

```bash
dmesg | grep -i fail
```

### `fail`

→ falha.

Esses comandos podem ajudar na investigação de problemas de hardware e drivers.

---

# 🕐 5. `dmesg -T`

A opção:

```bash
dmesg -T
```

mostra os timestamps de forma mais legível, utilizando datas/horários humanos.

### `-T`

→ **human-readable timestamps**

→ timestamps legíveis por humanos.

Sem `-T`, os timestamps podem aparecer como valores relativos ao tempo desde o início do kernel.

---

# 📊 6. `dmesg -H`

A opção:

```bash
dmesg -H
```

ativa uma saída mais amigável para leitura humana.

### `-H`

→ **human-readable**

→ legível por humanos.

Pode melhorar a apresentação das mensagens no terminal.

---

# 🚨 7. `dmesg -l`

A opção:

```bash
dmesg -l error
```

permite selecionar mensagens de determinados níveis de prioridade.

### `-l`

→ **level → nível**

Exemplo:

```bash
dmesg -l err
```

→ mostra mensagens de nível de erro.

Também podemos consultar níveis como:

```text
emerg
alert
crit
err
warn
notice
info
debug
```

Para a prova, o mais importante é entender:

**`-l` → filtrar por nível de mensagem.**

---

# 🔢 8. NÍVEIS DE MENSAGEM

As mensagens do kernel possuem níveis de prioridade.

Do mais grave para o menos grave:

```text
emerg
alert
crit
err
warn
notice
info
debug
```

### Significados

**emerg**

→ emergency → emergência.

**alert**

→ alerta.

**crit**

→ critical → crítico.

**err**

→ error → erro.

**warn**

→ warning → aviso.

**notice**

→ aviso/notificação.

**info**

→ information → informação.

**debug**

→ depuração.

---

# 🔄 9. `dmesg -w`

A opção:

```bash
dmesg -w
```

permite acompanhar novas mensagens do kernel conforme elas aparecem.

### `-w`

→ **wait → esperar**

O comando permanece aguardando novas mensagens.

Isso é útil, por exemplo, para observar o que acontece quando conectamos um dispositivo USB.

---

# 🧠 10. EXEMPLO PRÁTICO

Abra:

```bash
dmesg -w
```

Depois conecte um dispositivo USB.

O kernel pode detectar:

```text
USB device detected
↓
Driver identificado
↓
Dispositivo registrado
```

As novas mensagens podem aparecer no terminal.

Para sair:

```text
Ctrl + C
```

---

# 🔐 11. PERMISSÕES

Em alguns sistemas, o acesso às mensagens do kernel pode ser restrito.

Se:

```bash
dmesg
```

retornar uma mensagem relacionada a permissão, pode ser necessário:

```bash
sudo dmesg
```

### `sudo`

**superuser do**

→ executar como superusuário.

---

# 🧩 12. DMESG E DRIVERS

O `dmesg` é muito útil para verificar problemas relacionados a drivers.

Exemplo:

```bash
dmesg | grep -i driver
```

Podemos procurar mensagens relacionadas ao carregamento ou funcionamento de drivers.

Fluxo:

```text
HARDWARE
   ↓
KERNEL
   ↓
DRIVER
   ↓
MENSAGEM NO KERNEL
   ↓
dmesg
```

---

# 🔌 13. DMESG E PCI

Para procurar eventos relacionados ao PCI:

```bash
dmesg | grep -i pci
```

### Interpretação

```text
dmesg
→ mensagens do kernel

|
→ pipe

grep
→ procurar

-i
→ ignorar maiúsculas/minúsculas

pci
→ texto procurado
```

Resultado:

→ mensagens do kernel relacionadas a PCI.

---

# 🌐 14. DMESG E REDE

Também podemos procurar mensagens relacionadas à rede:

```bash
dmesg | grep -i network
```

ou pelo nome de uma interface/driver.

Exemplo:

```bash
dmesg | grep -i e1000e
```

Isso pode ajudar a verificar eventos relacionados ao driver.

---

# 📝 15. COMANDOS NECESSÁRIOS

### Mostrar mensagens do kernel

```bash
dmesg
```

→ exibe mensagens do kernel.

### Timestamps legíveis

```bash
dmesg -T
```

→ `-T = timestamps legíveis`.

### Saída amigável

```bash
dmesg -H
```

→ `-H = human-readable → legível por humanos`.

### Filtrar por nível

```bash
dmesg -l err
```

→ `-l = level → nível`.

### Acompanhar novas mensagens

```bash
dmesg -w
```

→ `-w = wait → aguardar novas mensagens`.

### Procurar USB

```bash
dmesg | grep -i usb
```

→ procura mensagens USB.

### Procurar PCI

```bash
dmesg | grep -i pci
```

→ procura mensagens PCI.

### Procurar erros

```bash
dmesg | grep -i error
```

→ procura mensagens contendo "error".

### Executar com privilégios

```bash
sudo dmesg
```

→ executa `dmesg` como superusuário.

---

# 🎯 16. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que é `dmesg`.
- Que `dmesg` exibe mensagens do kernel.
- Para que as mensagens do kernel são utilizadas.
- Usar `dmesg`.
- Combinar `dmesg` com `grep`.
- Entender o pipe `|`.
- Entender `grep -i`.
- Conhecer `dmesg -T`.
- Conhecer `dmesg -H`.
- Conhecer `dmesg -l`.
- Entender níveis de prioridade das mensagens.
- Conhecer `dmesg -w`.
- Saber que `-w` acompanha novas mensagens.
- Entender a relação entre `dmesg`, hardware e drivers.
- Usar `dmesg` para investigar USB.
- Usar `dmesg` para investigar PCI.
- Entender que o acesso ao buffer do kernel pode exigir privilégios administrativos.

---

# 🧠 RESUMO

```text
dmesg
↓
DISPLAY MESSAGES
↓
EXIBE MENSAGENS DO KERNEL
```

### Principais opções:

```text
-T
→ timestamps legíveis

-H
→ human-readable → saída amigável

-l
→ level → filtrar por nível

-w
→ wait → acompanhar novas mensagens
```

### Com `grep`:

```bash
dmesg | grep -i usb
```

→ mensagens relacionadas a USB.

```bash
dmesg | grep -i pci
```

→ mensagens relacionadas a PCI.

```bash
dmesg | grep -i error
```

→ mensagens relacionadas a erros.

---

# 🔄 PARA MEMORIZAR

```text
HARDWARE
   ↓
KERNEL
   ↓
EVENTO
   ↓
MENSAGEM
   ↓
dmesg
   ↓
ADMINISTRADOR
```

# 🎯 COMANDO PRINCIPAL

```bash
dmesg
```

**Tradução: display messages → exibir mensagens**

**Função: consultar mensagens produzidas pelo kernel, especialmente úteis para diagnosticar hardware, drivers e inicialização.**

# ✅ FIM DA PÁGINA 19
