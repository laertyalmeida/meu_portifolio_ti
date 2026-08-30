# 📖 PÁGINA 13 — /PROC

# 🧠 1. O QUE É `/proc`?

`/proc` é um **sistema de arquivos virtual** fornecido pelo kernel Linux.

Ele não funciona como um diretório comum armazenado no disco.

As informações são fornecidas pelo kernel e representam o estado atual do sistema.

O `/proc` permite consultar informações sobre:

- Processos
- CPU
- Memória
- Kernel
- Hardware
- Parâmetros do sistema

---

# 📂 2. SISTEMA DE ARQUIVOS VIRTUAL

Um sistema de arquivos virtual não precisa representar arquivos físicos armazenados no disco.

No caso do `/proc`, o kernel fornece as informações quando elas são consultadas.

Por isso:

**/proc**

→ informações dinâmicas do sistema.

---

# 🔢 3. DIRETÓRIOS DE PROCESSOS

Dentro de `/proc`, existem diretórios com números.

Exemplo:

`/proc/1`

`/proc/100`

`/proc/2500`

Esses números representam:

**PID = Process ID**

Tradução:

**Identificador do Processo**

Portanto:

`/proc/1`

→ informações do processo com PID 1.

`/proc/2500`

→ informações do processo com PID 2500.

---

# 🔍 4. `/proc/[PID]/`

Cada processo possui informações dentro de seu próprio diretório.

Exemplo:

`/proc/1/`

Pode conter arquivos como:

`cmdline`

→ linha de comando utilizada pelo processo.

`status`

→ informações sobre o estado do processo.

`fd/`

→ descritores de arquivos utilizados pelo processo.

---

# 🧠 5. `/proc/cpuinfo`

O arquivo:

`/proc/cpuinfo`

contém informações sobre o processador.

Podemos consultar:

`cat /proc/cpuinfo`

### Tradução

**cat = concatenate**

→ concatenar/exibir conteúdo.

`cpuinfo`

→ CPU information → informações da CPU.

Pode apresentar informações como:

- Modelo da CPU
- Número de processadores lógicos
- Núcleos
- Threads
- Flags da CPU

---

# 💾 6. `/proc/meminfo`

O arquivo:

`/proc/meminfo`

apresenta informações sobre a memória.

Comando:

`cat /proc/meminfo`

### Tradução

`meminfo`

→ memory information → informações da memória.

Pode apresentar:

- Memória total
- Memória livre
- Memória disponível
- Memória utilizada pelo kernel
- Swap

---

# 🚀 7. `/proc/cmdline`

O arquivo:

`/proc/cmdline`

mostra os parâmetros utilizados para iniciar o kernel.

Comando:

`cat /proc/cmdline`

Exemplo:

`BOOT_IMAGE=... ro quiet`

Esses parâmetros normalmente são fornecidos pelo bootloader.

Fluxo:

**GRUB → parâmetros → Kernel**

---

# 🧠 8. `/proc/version`

O arquivo:

`/proc/version`

apresenta informações sobre a versão do kernel e outros dados relacionados à compilação.

Comando:

`cat /proc/version`

---

# ⚙️ 9. `/proc/loadavg`

O arquivo:

`/proc/loadavg`

apresenta informações relacionadas à carga do sistema.

Comando:

`cat /proc/loadavg`

Ele apresenta valores relacionados à carga média do sistema em diferentes períodos.

---

# 🔧 10. `/proc/uptime`

O arquivo:

`/proc/uptime`

mostra informações sobre o tempo de funcionamento do sistema.

Comando:

`cat /proc/uptime`

O primeiro valor representa aproximadamente quanto tempo o sistema está ligado, em segundos.

---

# 🌐 11. `/proc/net/`

O diretório:

`/proc/net/`

contém informações relacionadas à rede fornecidas pelo kernel.

Exemplo:

`/proc/net/dev`

Pode ser utilizado para consultar estatísticas das interfaces de rede.

---

# 🔎 12. `grep` COM `/proc`

Podemos combinar `/proc` com `grep`.

Exemplo:

`grep "model name" /proc/cpuinfo`

### Tradução

**grep**

→ procurar um padrão.

**model name**

→ nome do modelo.

**/proc/cpuinfo**

→ informações da CPU.

Resultado:

→ mostra as linhas contendo o modelo da CPU.

---

# 🧰 13. `ps` E `/proc`

O comando:

`ps`

mostra informações sobre processos.

Grande parte das informações apresentadas pelo sistema de processos está relacionada às informações disponibilizadas pelo kernel através de `/proc`.

Exemplo:

`ps`

ou:

`ps aux`

### `a`

**all users**

→ processos de todos os usuários.

### `u`

**user-oriented**

→ formato orientado ao usuário.

### `x`

→ inclui processos que não possuem terminal associado.

---

# 🔢 14. PID 1

Como vimos na inicialização:

`/proc/1`

representa o processo:

**PID 1**

Podemos consultar:

`cat /proc/1/status`

Isso permite visualizar informações sobre o processo de PID 1.

Em sistemas Linux modernos, normalmente:

**PID 1 → systemd**

---

# 📝 15. COMANDOS NECESSÁRIOS

### Listar conteúdo do `/proc`

`ls /proc`

**ls = list → listar**

### Informações da CPU

`cat /proc/cpuinfo`

**cat = concatenate → exibir conteúdo**

### Informações da memória

`cat /proc/meminfo`

### Parâmetros do kernel

`cat /proc/cmdline`

### Versão do kernel

`cat /proc/version`

### Carga do sistema

`cat /proc/loadavg`

### Tempo ligado

`cat /proc/uptime`

### Informações de rede

`cat /proc/net/dev`

### Informações de um processo

`cat /proc/1/status`

### Procurar informações

`grep "model name" /proc/cpuinfo`

**grep → procurar**

---

# 🎯 16. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que é `/proc`.
- Que `/proc` é um sistema de arquivos virtual.
- Que suas informações são fornecidas pelo kernel.
- Que `/proc` contém informações dinâmicas do sistema.
- Que diretórios numéricos representam PIDs.
- O significado de PID.
- O que é `/proc/[PID]/`.
- Conhecer `/proc/cpuinfo`.
- Conhecer `/proc/meminfo`.
- Conhecer `/proc/cmdline`.
- Conhecer `/proc/version`.
- Conhecer `/proc/loadavg`.
- Conhecer `/proc/uptime`.
- Conhecer `/proc/net/`.
- Saber consultar arquivos de `/proc` usando `cat`.
- Saber utilizar `grep` para pesquisar informações.
- Entender a relação entre `/proc` e processos.
- Saber que `/proc/1` representa o processo de PID 1.

---

# 🧠 RESUMO

**/proc**

→ sistema de arquivos virtual.

→ fornece informações do kernel e do sistema.

**/proc/[PID]**

→ informações de determinado processo.

**/proc/1**

→ processo de PID 1.

**/proc/cpuinfo**

→ informações da CPU.

**/proc/meminfo**

→ informações da memória.

**/proc/cmdline**

→ parâmetros utilizados para iniciar o kernel.

**/proc/version**

→ informações da versão do kernel.

**/proc/loadavg**

→ carga média do sistema.

**/proc/uptime**

→ tempo de funcionamento do sistema.

**/proc/net/**

→ informações relacionadas à rede.

**cat**

→ concatenate → exibir/concatenar conteúdo.

**grep**

→ procurar um padrão.

---

# 🧠 PARA DECORAR

```text
/proc
├── cpuinfo     → CPU
├── meminfo     → memória
├── cmdline     → parâmetros do kernel
├── version     → versão do kernel
├── loadavg     → carga do sistema
├── uptime      → tempo ligado
├── net/        → rede
└── [PID]/      → informações de processos
```

# ✅ FIM DA PÁGINA 13
