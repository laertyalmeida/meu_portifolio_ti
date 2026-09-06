Directory Structure — Estrutura de Diretórios

Como o Linux organiza os arquivos

No Linux, tudo começa pelo diretório:

/

Ele é chamado de Root Directory — Diretório Raiz.

Todos os outros diretórios ficam abaixo dele.

/
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

---

"/home" — Home Directory (Diretório Pessoal)

Guarda os arquivos pessoais dos usuários.

/home/joao
/home/maria

Exemplo:

cd /home

→ entra no diretório onde ficam os diretórios pessoais.

---

"/root" — Root Home (Diretório Pessoal do Root)

É o diretório pessoal do usuário "root".

Não confunda:

/       → Root Directory → Diretório Raiz
/root   → Root Home     → Diretório pessoal do root

---

"/etc" — Configuration (Configurações)

Guarda arquivos de configuração do sistema e dos programas.

Exemplos:

/etc/passwd
/etc/hosts
/etc/fstab

Pense:

/etc
 ↓
configurações

---

"/bin" — Essential Commands (Comandos Essenciais)

Contém comandos essenciais para o sistema.

Exemplos:

ls
cp
mv
rm
cat

Em sistemas Linux modernos, "/bin" normalmente é um link para "/usr/bin".

---

"/sbin" — System Commands (Comandos do Sistema)

Contém comandos usados principalmente para administração do sistema.

Exemplos:

ip
fsck
mount

Em sistemas modernos, "/sbin" normalmente é um link para "/usr/sbin".

---

"/usr" — User Programs (Programas do Usuário)

Contém grande parte dos programas, bibliotecas e arquivos usados pelo sistema.

Exemplos:

/usr/bin
/usr/sbin
/usr/lib
/usr/share

É um dos diretórios mais importantes do Linux.

---

"/var" — Variable Data (Dados Variáveis)

Guarda dados que mudam enquanto o sistema funciona.

Exemplos:

/var/log
/var/cache
/var/lib

"/var/log"

Guarda arquivos de logs — registros.

/var/log/

---

"/tmp" — Temporary (Temporário)

Usado para arquivos temporários.

/tmp

Programas podem criar arquivos temporários nesse diretório.

---

"/dev" — Devices (Dispositivos)

Contém arquivos que representam dispositivos.

Exemplos:

/dev/sda
/dev/null
/dev/tty

No Linux, muitos dispositivos são acessados como arquivos.

---

"/proc" — Processes (Processos)

É um sistema de arquivos virtual que fornece informações sobre processos e o kernel.

Exemplos:

/proc/cpuinfo
/proc/meminfo
/proc/1234

Podemos consultar:

cat /proc/cpuinfo

→ mostra informações sobre o processador.

---

"/sys" — System (Sistema)

É outro sistema de arquivos virtual.

Fornece informações sobre:

hardware
dispositivos
kernel

Fica em:

/sys

---

"/boot" — Boot (Inicialização)

Contém arquivos necessários para iniciar o Linux.

Pode conter:

kernel
initramfs
bootloader

---

"/media" — Removable Media (Mídia Removível)

Usado normalmente para montar mídias removíveis automaticamente.

Exemplo:

/media/usuario/USB

---

"/mnt" — Mount (Montagem)

Usado tradicionalmente como ponto de montagem temporário.

Exemplo:

mount /dev/sdb1 /mnt

---

"/opt" — Optional Software (Software Opcional)

Usado para instalar softwares adicionais que não fazem parte da instalação padrão.

Exemplo:

/opt/programa

---

"/run" — Runtime Data (Dados de Execução)

Guarda informações temporárias relacionadas aos programas em execução.

Exemplos:

PID
sockets
arquivos temporários de serviços

O conteúdo normalmente desaparece após a reinicialização.

---

🧠 Para a LPIC-1

Os diretórios mais importantes:

/       → Diretório Raiz
/boot   → Inicialização
/dev    → Dispositivos
/etc    → Configurações
/home   → Arquivos dos usuários
/root   → Diretório pessoal do root
/tmp    → Temporários
/usr    → Programas e arquivos do sistema
/var    → Dados variáveis
/proc   → Processos e informações do kernel
/sys    → Hardware e kernel
/mnt    → Montagem temporária
/media  → Mídias removíveis
/opt    → Software adicional
/run    → Dados de execução

Regra para memorizar

/etc
→ configurações

/home
→ usuários

/var
→ dados que mudam

/tmp
→ temporários

/dev
→ dispositivos

/boot
→ inicialização

/usr
→ programas

/proc
→ processos/kernel

/sys
→ hardware/kernel
