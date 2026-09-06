"/proc" e "/sys"

O Linux possui dois diretórios especiais que permitem consultar informações sobre o sistema e o hardware:

/proc
/sys

Eles não funcionam como diretórios comuns. O conteúdo é fornecido pelo kernel Linux enquanto o sistema está funcionando.

---

"/proc" — Process Information (Informações de Processos)

O "/proc" contém informações sobre:

- Processos
- CPU
- Memória
- Kernel
- Sistema

Exemplo:

cat /proc/cpuinfo

→ Mostra informações sobre a CPU.

cat /proc/meminfo

→ Mostra informações sobre a memória.

---

"/proc/<PID>"

Cada processo possui um diretório dentro de "/proc".

Por exemplo:

/proc/1234

O número "1234" é o PID — Process ID (ID do Processo).

Podemos consultar informações desse processo:

ls /proc/1234

---

"/sys" — Sysfs (Sistema de Arquivos do Sistema)

O "/sys" apresenta informações sobre hardware, dispositivos e kernel.

Exemplo:

ls /sys

Você encontrará diretórios como:

block
bus
class
devices
firmware
kernel
module

---

"/proc" x "/sys"

"/proc"| "/sys"
Processos e informações do sistema| Hardware e dispositivos
CPU e memória| Dispositivos e barramentos
Informações do kernel| Informações do kernel

Uma forma simples de lembrar:

/proc → processos + sistema

/sys → hardware + dispositivos

---

Comando

"cat" — Concatenate (Concatenar)

Mostra o conteúdo de um arquivo.

cat /proc/meminfo

---

"ls" — List (Listar)

Lista arquivos e diretórios.

ls /sys

---

LPIC-1 — O que saber

- "/proc" fornece informações sobre processos e o sistema.
- "/sys" fornece informações sobre hardware e dispositivos.
- Ambos são usados pelo Linux para expor informações do kernel.
- "/proc/<PID>" contém informações relacionadas a um processo.
- O conteúdo desses diretórios é principalmente virtual e gerado pelo kernel.

---

Resumo

/proc
 ↓
Processos
CPU
Memória
Kernel

/sys
 ↓
Hardware
Dispositivos
Barramentos
Kernel

Para memorizar:

«"/proc" → informações do sistema e processos
"/sys" → informações de hardware e dispositivos»
