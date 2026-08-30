Sistema de Arquivos Linux

File System — Sistema de Arquivos

O File System (Sistema de Arquivos) é a forma como o Linux organiza arquivos, diretórios e dispositivos de armazenamento.

No Linux, tudo começa em:

/

Esse é o Root Directory (Diretório Raiz).

---

Root Directory — Diretório Raiz

A estrutura básica pode ser vista assim:

/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── tmp
├── usr
└── var

Não é necessário decorar tudo de uma vez. Vamos estudar cada parte nas próximas páginas.

---

"/home" — Home (Diretório Pessoal)

Guarda os diretórios pessoais dos usuários.

Exemplo:

/home/joao
/home/maria

Normalmente, os arquivos pessoais ficam dentro de "/home".

---

"/root" — Root User Home (Diretório Pessoal do Administrador)

É o diretório pessoal do usuário root, o administrador do sistema.

Não confunda:

/      → diretório raiz
/root  → diretório pessoal do usuário root

---

"/etc" — Configuration (Configurações)

Guarda arquivos de configuração do sistema e de vários programas.

Exemplo:

/etc/passwd
/etc/hosts
/etc/fstab

---

"/var" — Variable Data (Dados Variáveis)

Guarda dados que mudam durante o funcionamento do sistema.

Exemplos:

/var/log
/var/cache
/var/tmp

---

"/tmp" — Temporary (Temporário)

Usado para arquivos temporários.

/tmp

Arquivos nesse diretório podem ser removidos automaticamente pelo sistema.

---

"/dev" — Devices (Dispositivos)

Contém arquivos que representam dispositivos.

Exemplos:

/dev/sda
/dev/null
/dev/tty

O Linux trata muitos dispositivos como arquivos.

---

"/proc" — Processes (Processos)

É um sistema de arquivos virtual que fornece informações sobre o kernel e processos.

Exemplo:

/proc/cpuinfo
/proc/meminfo

Podemos consultar:

cat /proc/cpuinfo

---

"/sys" — System (Sistema)

Outro sistema de arquivos virtual.

Fornece informações sobre dispositivos, hardware e recursos do kernel.

/sys

---

"/boot" — Boot (Inicialização)

Contém arquivos necessários para a inicialização do sistema.

Pode conter:

kernel
initramfs
arquivos do bootloader

---

LPIC-1 — O que saber

/       → Root Directory (Diretório Raiz)
/home   → usuários
/root   → home do root
/etc    → configurações
/var    → dados variáveis
/tmp    → temporários
/dev    → dispositivos
/proc   → informações de processos/kernel
/sys    → informações do sistema/kernel
/boot   → inicialização

Para memorizar

/        → começa tudo
/home    → usuários
/etc     → configurações
/var     → dados que mudam
/dev     → dispositivos
/proc    → processos/kernel
/boot    → inicialização
