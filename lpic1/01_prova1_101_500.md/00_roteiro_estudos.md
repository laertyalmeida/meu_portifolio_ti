# 📚 ROTEIRO DE ESTUDOS — LPIC-1 PROVA 1 (101-500)

> 🎯 Objetivo: estudar exclusivamente o conteúdo necessário para a **LPIC-1 Prova 1 (101-500)**.

---

# 1. 🧠 ARQUITETURA DO SISTEMA

- CPU e arquitetura
- 32 bits e 64 bits
- Endianness
- Dispositivos e barramentos
- USB
- PCI/PCIe
- BIOS
- UEFI
- Inicialização do sistema
- Bootloader
- Kernel
- Módulos do kernel
- `/proc`
- `/sys`
- `lspci`
- `lsusb`
- `lsmod`
- `modprobe`
- `dmesg`

---

# 2. 💿 INSTALAÇÃO DO LINUX E GERENCIAMENTO DE PACOTES

## 2.1 Particionamento e sistemas de arquivos

- Partições
- MBR
- GPT
- Swap
- Sistemas de arquivos
- Montagem
- `/etc/fstab`
- UUID
- `mount`
- `umount`
- `df`
- `du`

## 2.2 Gerenciamento de pacotes Debian

- `dpkg`
- `apt`
- Repositórios
- Instalação de pacotes
- Remoção de pacotes
- Atualização de pacotes
- Consulta de pacotes

## 2.3 Gerenciamento de pacotes RPM

- RPM
- YUM/DNF
- Conceitos de pacotes RPM

---

# 3. ⌨️ COMANDOS GNU E UNIX

## 3.1 Linha de comando

- Shell
- Terminal
- Comandos internos e externos
- Variáveis
- PATH
- Histórico
- Alias

## 3.2 Manipulação de arquivos e diretórios

- `ls`
- `cp`
- `mv`
- `rm`
- `mkdir`
- `rmdir`
- `touch`
- `file`
- `find`
- `locate`

## 3.3 Visualização e processamento de texto

- `cat`
- `less`
- `more`
- `head`
- `tail`
- `cut`
- `sort`
- `uniq`
- `wc`
- `tr`
- `grep`
- `sed`

## 3.4 Redirecionamento e pipes

- `>`
- `>>`
- `<`
- `|`
- `2>`
- `2>&1`

## 3.5 Processos

- `ps`
- `top`
- `pgrep`
- `pkill`
- `kill`
- `killall`
- `jobs`
- `bg`
- `fg`
- `nice`
- `renice`

## 3.6 Expressões regulares

- Caracteres literais
- Metacaracteres
- Classes
- `^`
- `$`
- `.`
- `*`
- `+`
- `?`
- `[]`

## 3.7 Arquivamento e compressão

- `tar`
- `gzip`
- `gunzip`
- `bzip2`
- `bunzip2`
- `xz`
- `unxz`

---

# 4. 💾 DISPOSITIVOS, SISTEMAS DE ARQUIVOS E FHS

## 4.1 Hierarquia de diretórios

- `/`
- `/boot`
- `/dev`
- `/etc`
- `/home`
- `/lib`
- `/media`
- `/mnt`
- `/opt`
- `/proc`
- `/root`
- `/run`
- `/sbin`
- `/srv`
- `/sys`
- `/tmp`
- `/usr`
- `/var`

## 4.2 Dispositivos

- `/dev`
- Dispositivos de bloco
- Dispositivos de caractere
- `udev`

## 4.3 Sistemas de arquivos

- ext4
- XFS
- Btrfs
- VFS
- Journaling
- Inodes
- Links físicos
- Links simbólicos

## 4.4 Permissões

- `r`
- `w`
- `x`
- Permissões de usuário
- Permissões de grupo
- Permissões de outros
- `chmod`
- `chown`
- `chgrp`
- `umask`
- SUID
- SGID
- Sticky Bit

---

# 5. 📦 GERENCIAMENTO DE SOFTWARE E BIBLIOTECAS COMPARTILHADAS

- Bibliotecas compartilhadas
- Bibliotecas estáticas
- `ldd`
- `ldconfig`
- `/etc/ld.so.conf`
- `LD_LIBRARY_PATH`
- Gerenciamento de pacotes
- Dependências

---

# 6. ⚙️ GERENCIAMENTO DE SISTEMA

## 6.1 Inicialização e desligamento

- Boot
- Shutdown
- Reboot
- `systemctl`
- Targets
- Serviços

## 6.2 Systemd

- `systemd`
- Units
- Services
- Targets
- `systemctl`
- Habilitar serviços
- Desabilitar serviços
- Iniciar serviços
- Parar serviços
- Verificar status de serviços

## 6.3 Logs

- `journalctl`
- `/var/log`
- Logs do sistema
- Logs de serviços

## 6.4 Agendamento

- `cron`
- `crontab`
- `at`
- Systemd Timers

## 6.5 Processos e recursos

- Processos
- CPU
- Memória
- Load Average
- `free`
- `uptime`
- `vmstat`
- `ps`
- `top`

---

# 7. 🌐 FUNDAMENTOS DE REDES

- Conceitos básicos de rede
- IPv4
- IPv6
- Endereços IP
- Máscara de rede
- CIDR
- Gateway
- DNS
- DHCP
- Hostname
- `/etc/hosts`
- `/etc/resolv.conf`
- Rotas
- Interfaces de rede

## Comandos de rede

- `ip`
- `ping`
- `ss`
- `traceroute`
- `tracepath`
- `hostname`
- `dig`
- `host`
- `nslookup`

---

# 8. 🔐 SEGURANÇA

## 8.1 Usuários e grupos

- Usuários
- Grupos
- UID
- GID
- `/etc/passwd`
- `/etc/shadow`
- `/etc/group`
- `useradd`
- `usermod`
- `userdel`
- `groupadd`
- `passwd`

## 8.2 Privilégios

- `root`
- `su`
- `sudo`
- `/etc/sudoers`

## 8.3 Segurança de arquivos

- Permissões
- Ownership
- SUID
- SGID
- Sticky Bit
- Umask

---

# 🎯 ORDEM DO NOSSO ESTUDO

Seguiremos exatamente esta sequência:

**1. Arquitetura do Sistema**  
↓  
**2. Instalação e Gerenciamento de Pacotes**  
↓  
**3. Comandos GNU e Unix**  
↓  
**4. Dispositivos, Sistemas de Arquivos e FHS**  
↓  
**5. Bibliotecas e Gerenciamento de Software**  
↓  
**6. Gerenciamento de Sistema**  
↓  
**7. Fundamentos de Redes**  
↓  
**8. Segurança**

---

# 📌 REGRA DO ROTEIRO

Este roteiro é exclusivamente para:

**LPIC-1 — Prova 1 — 101-500**

Não vamos misturar conteúdos da **Prova 2 — 102-500** neste material.

A partir deste roteiro, cada assunto será transformado em páginas de estudo detalhadas.
