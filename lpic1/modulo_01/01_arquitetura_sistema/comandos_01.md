LPIC-1 — Módulo 01

CPU e Arquitetura — Comandos

# LPIC-1 — CPU e Arquitetura
## Principais comandos

- `uname -m`
- `uname -r`
- `uname -a`
- `lscpu`
- `cat /proc/cpuinfo`
- `arch`
- `nproc`
- `getconf LONG_BIT`
- `lspci`
- `dmidecode`
- `hwinfo`



1. "uname -m"

Termo em inglês → tradução:

- "uname" → Unix Name → Nome do Unix/sistema
- "machine" → máquina

Comando → significado:

- "uname" → exibe informações sobre o sistema
- "-m" → mostra a arquitetura da máquina

Flag/opção → significado:

- "-m" → machine → arquitetura da máquina

Saída → interpretação:

x86_64

→ Sistema com arquitetura 64 bits, compatível com AMD64/x86-64.

---

2. "uname -r"

Termo em inglês → tradução:

- "uname" → Unix Name → Nome do Unix/sistema
- "release" → versão/lançamento

Comando → significado:

- "uname" → exibe informações sobre o sistema
- "-r" → mostra a versão do kernel

Flag/opção → significado:

- "-r" → release → versão do kernel

Saída → interpretação:

6.12.74-amd64

→ Indica a versão do kernel Linux em execução.

---

3. "uname -a"

Termo em inglês → tradução:

- "all" → todos

Comando → significado:

- "uname" → exibe informações sobre o sistema
- "-a" → mostra todas as informações disponíveis

Flag/opção → significado:

- "-a" → all → todos

Saída → interpretação:

Linux computador 6.12.74-amd64 #1 SMP ... x86_64 GNU/Linux

→ Mostra várias informações, incluindo:

- Sistema operacional
- Nome do computador
- Versão do kernel
- Arquitetura
- Outras informações do sistema

---

4. "lscpu"

Termo em inglês → tradução:

- "ls" → list → listar
- "CPU" → Central Processing Unit → Unidade Central de Processamento

Comando → significado:

- "lscpu" → lista informações detalhadas da CPU

Flag/opção:

- Não é necessária para a consulta básica.

Saída → interpretação:

Architecture:        x86_64
CPU(s):              4
Model name:          Intel(R) ...

→ Permite identificar:

- Arquitetura da CPU
- CPUs lógicas
- Modelo do processador
- Threads
- Núcleos
- Família da CPU
- Modos de operação

---

5. "cat /proc/cpuinfo"

Termos em inglês → tradução:

- "cat" → concatenate → concatenar/exibir conteúdo
- "CPU" → Central Processing Unit → Unidade Central de Processamento
- "info" → information → informação

Comando → significado:

- "cat" → exibe o conteúdo de um arquivo
- "/proc/cpuinfo" → arquivo virtual do Linux com informações sobre a CPU

Flag/opção:

- Não utiliza flag obrigatória.

Saída → interpretação:

processor       : 0
vendor_id       : GenuineIntel
model name      : Intel(R) ...
cpu MHz         : ...
cache size      : ...

→ Apresenta informações detalhadas sobre cada CPU/thread lógica.

---

6. "arch"

Termo em inglês → tradução:

- "arch" → architecture → arquitetura

Comando → significado:

- Mostra a arquitetura do sistema.

Flag/opção:

- Não utiliza flag obrigatória.

Saída → interpretação:

x86_64

→ Sistema de arquitetura 64 bits (x86-64).

---

7. "getconf LONG_BIT"

Termos em inglês → tradução:

- "getconf" → get configuration → obter configuração
- "LONG_BIT" → quantidade de bits do tipo "long"

Comando → significado:

- "getconf" → consulta valores de configuração do sistema
- "LONG_BIT" → informa a quantidade de bits utilizada pelo tipo "long"

Flag/opção:

- "LONG_BIT" → quantidade de bits

Saída → interpretação:

64

→ Ambiente de 64 bits.

---

8. "nproc"

Termos em inglês → tradução:

- "nproc" → number of processors → número de processadores

Comando → significado:

- Mostra a quantidade de unidades de processamento disponíveis para o sistema.

Flag/opção:

- Sem opção → mostra a quantidade disponível.

Saída → interpretação:

4

→ Existem 4 CPUs lógicas disponíveis.

---

9. "lspci"

Termos em inglês → tradução:

- "ls" → list → listar
- "PCI" → Peripheral Component Interconnect → Interconexão de Componentes Periféricos

Comando → significado:

- Lista dispositivos conectados ao barramento PCI.

Flag/opção:

- "-nn" → mostra identificadores numéricos dos dispositivos.

Saída → interpretação:

00:00.0 Host bridge: Intel Corporation ...

→ Mostra componentes de hardware conectados ao barramento PCI.

---

10. "dmidecode"

Termos em inglês → tradução:

- "DMI" → Desktop Management Interface → Interface de Gerenciamento do Computador
- "decode" → decodificar

Comando → significado:

- Consulta informações de hardware fornecidas pelo firmware/BIOS/UEFI através do DMI/SMBIOS.

Flag/opção:

- "-t processor" → informações do processador
- "-t memory" → informações da memória
- "-t system" → informações do sistema

Saída → interpretação:

Manufacturer: Intel
Version: ...
Core Count: 4
Thread Count: 4

→ Mostra informações do hardware identificadas pelo firmware.

---

11. "hwinfo"

Termos em inglês → tradução:

- "hw" → hardware → equipamento físico
- "info" → information → informação

Comando → significado:

- Exibe informações detalhadas sobre o hardware.

Flag/opção:

- "--cpu" → mostra informações da CPU
- "--memory" → mostra informações da memória

Saída → interpretação:

Model: ...
Clock: ...

→ Apresenta informações detalhadas sobre o hardware.

---

📌 Resumo dos comandos

Comando| Função principal
"uname -m"| Mostra a arquitetura
"uname -r"| Mostra a versão do kernel
"uname -a"| Mostra informações gerais do sistema
"lscpu"| Mostra informações da CPU
"cat /proc/cpuinfo"| Mostra informações detalhadas da CPU
"arch"| Mostra a arquitetura
"getconf LONG_BIT"| Verifica ambiente 32/64 bits
"nproc"| Mostra CPUs lógicas disponíveis
"lspci"| Lista dispositivos PCI
"dmidecode"| Consulta informações do hardware/firmware
"hwinfo"| Mostra informações detalhadas do hardware

🧠 Prioridade para LPIC-1

Essenciais:

uname -m
uname -r
uname -a
lscpu
cat /proc/cpuinfo

Complementares:

arch
nproc
getconf LONG_BIT
lspci
dmidecode
hwinfo

📌 Observação

Os comandos mais importantes para CPU e arquitetura são "uname", "lscpu" e "/proc/cpuinfo". Os demais complementam a identificação e investigação do hardware.
