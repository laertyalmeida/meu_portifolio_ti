# Sistemas de Arquivos e FHS

## 02 — FHS

**FHS — Filesystem Hierarchy Standard — Padrão de Hierarquia do Sistema de Arquivos**

O **FHS** define uma organização padrão para os principais diretórios de sistemas Linux e Unix.

A ideia é simples: cada diretório tem uma finalidade específica.

---

## 1. Estrutura básica

A árvore começa em:

    /

A partir dela existem diretórios com funções diferentes:

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
    ├── srv
    ├── sys
    ├── tmp
    ├── usr
    └── var

---

## 2. `/` — Root — Raiz

É o ponto inicial da hierarquia.

Todos os arquivos e diretórios ficam abaixo de `/`.

Exemplo:

    /etc/hostname

O caminho começa em `/` e depois entra em `etc`.

---

## 3. `/bin` — Binaries — Binários

Contém comandos essenciais para os usuários e para o funcionamento básico do sistema.

Exemplos:

    /bin/ls
    /bin/cp
    /bin/mv
    /bin/cat

Em sistemas modernos com **usr merge — unificação com `/usr`**, `/bin` pode ser um link simbólico para `/usr/bin`.

---

## 4. `/sbin` — System Binaries — Binários do Sistema

Contém comandos utilizados principalmente para administração e manutenção do sistema.

Exemplos:

    /sbin/fsck
    /sbin/mount
    /sbin/reboot

Em sistemas modernos, `/sbin` também pode ser um link simbólico para `/usr/sbin`.

---

## 5. `/lib` — Libraries — Bibliotecas

Contém bibliotecas essenciais usadas pelos programas e pelo sistema.

Exemplos:

    /lib
    /lib64

Em sistemas com **usr merge**, podem apontar para diretórios dentro de `/usr`.

---

## 6. `/etc` — Configuration — Configuração

Contém arquivos de configuração do sistema.

Exemplos:

    /etc/passwd
    /etc/shadow
    /etc/fstab
    /etc/hostname
    /etc/hosts

Regra prática:

**`/etc` = configuração.**

---

## 7. `/dev` — Devices — Dispositivos

Contém arquivos especiais que representam dispositivos.

Exemplos:

    /dev/sda
    /dev/sda1
    /dev/nvme0n1
    /dev/null

Regra prática:

**`/dev` = dispositivos.**

---

## 8. `/proc` — Processes — Processos

É um **Virtual Filesystem — Sistema de Arquivos Virtual**.

Fornece informações sobre:

- processos;
- memória;
- CPU;
- kernel;
- dispositivos e configurações do sistema.

Exemplos:

    /proc/cpuinfo
    /proc/meminfo
    /proc/uptime

Consultar:

    cat /proc/meminfo

---

## 9. `/sys` — System — Sistema

Também é um sistema de arquivos virtual.

Fornece informações sobre:

- hardware;
- dispositivos;
- drivers;
- kernel.

Exemplos:

    /sys/class/
    /sys/devices/
    /sys/block/

---

## 10. `/boot` — Boot — Inicialização

Contém arquivos utilizados durante a inicialização do sistema.

Exemplos:

    /boot/vmlinuz
    /boot/initramfs
    /boot/grub/

---

## 11. `/home` — Home — Diretórios Pessoais

Contém os diretórios dos usuários comuns.

Exemplo:

    /home/laerte
    /home/joao

Arquivos pessoais normalmente ficam dentro do respectivo diretório `/home`.

---

## 12. `/root` — Root Home — Diretório Pessoal do Root

É o diretório pessoal do usuário administrativo `root`.

    /root

Não confunda:

    /
    /root

`/` = raiz do sistema.

`/root` = diretório pessoal do usuário `root`.

---

## 13. `/run` — Runtime — Execução

Contém dados temporários relacionados aos processos em execução desde a inicialização.

Exemplos:

    /run/lock
    /run/user/

Seu conteúdo normalmente é recriado durante o boot.

---

## 14. `/tmp` — Temporary — Temporário

Usado para arquivos temporários.

Exemplo:

    /tmp/arquivo.tmp

Não é apropriado para armazenar dados permanentes importantes.

---

## 15. `/usr` — User System Resources — Recursos do Sistema

Contém grande parte dos programas, bibliotecas e dados utilizados pelo sistema.

Principais subdiretórios:

    /usr/bin
    /usr/sbin
    /usr/lib
    /usr/share
    /usr/local

### `/usr/bin`

Programas e comandos.

### `/usr/sbin`

Programas administrativos.

### `/usr/lib`

Bibliotecas.

### `/usr/share`

Dados compartilhados, documentação e outros arquivos independentes da arquitetura.

### `/usr/local`

Software instalado localmente pelo administrador.

---

## 16. `/var` — Variable — Variável

Contém dados que mudam durante o funcionamento do sistema.

Exemplos:

    /var/log
    /var/cache
    /var/lib
    /var/tmp

### `/var/log`

Contém registros (**Log — Registro**) do sistema e de serviços.

---

## 17. `/media` — Media — Mídia

Ponto normalmente utilizado para montar mídias removíveis.

Exemplo:

    /media/laerte/USB

---

## 18. `/mnt` — Mount — Montagem

Ponto tradicional para montar temporariamente sistemas de arquivos.

Exemplo:

    mount /dev/sdb1 /mnt

---

## 19. `/opt` — Optional — Opcional

Pode ser usado para instalar software adicional que não faz parte da organização principal da distribuição.

Exemplo:

    /opt/programa/

---

## 20. `/srv` — Service — Serviço

Pode armazenar dados disponibilizados por serviços do sistema.

Exemplo:

    /srv/www/

---

## 21. `/usr/local` — Local — Local

Usado para software e arquivos instalados localmente pelo administrador, separados dos arquivos normalmente fornecidos pela distribuição.

Exemplos:

    /usr/local/bin
    /usr/local/sbin
    /usr/local/lib

---

## 22. `/var/tmp` — Variable Temporary — Temporário Variável

Também armazena arquivos temporários, mas possui uma diferença importante em relação a `/tmp`.

**`/tmp`** → temporários de curta duração.

**`/var/tmp`** → temporários que podem precisar permanecer por mais tempo, inclusive após uma reinicialização, dependendo da política do sistema.

---

## 23. Diretórios essenciais para memorizar

| Diretório | Função principal |
|---|---|
| `/` | Raiz |
| `/bin` | Comandos essenciais |
| `/sbin` | Comandos administrativos |
| `/lib` | Bibliotecas essenciais |
| `/boot` | Inicialização |
| `/dev` | Dispositivos |
| `/etc` | Configurações |
| `/home` | Usuários |
| `/root` | Home do root |
| `/proc` | Processos e informações do kernel |
| `/sys` | Hardware e kernel |
| `/run` | Dados de execução |
| `/tmp` | Temporários |
| `/usr` | Programas e recursos do sistema |
| `/var` | Dados variáveis |
| `/media` | Mídias removíveis |
| `/mnt` | Montagens temporárias |
| `/opt` | Software adicional |
| `/srv` | Dados de serviços |

---

## 24. FHS × Linux moderno

O FHS ajuda a entender **onde os arquivos devem estar**, mas distribuições modernas podem implementar a estrutura de maneira diferente.

Um exemplo é o **usr merge — unificação do `/usr`**.

Nesse modelo, diretórios tradicionais como:

    /bin
    /sbin
    /lib

podem ser **Symbolic Links — Links Simbólicos** para:

    /usr/bin
    /usr/sbin
    /usr/lib

Por isso, encontrar:

    /bin -> /usr/bin

não significa necessariamente que o sistema esteja errado.

---

## Resumo LPIC-1

- **FHS** → Filesystem Hierarchy Standard — Padrão de Hierarquia do Sistema de Arquivos.
- `/` → raiz de toda a hierarquia.
- `/bin` → comandos essenciais.
- `/sbin` → comandos administrativos.
- `/lib` → bibliotecas essenciais.
- `/boot` → arquivos de inicialização.
- `/dev` → dispositivos.
- `/etc` → configurações.
- `/home` → arquivos pessoais dos usuários.
- `/root` → diretório pessoal do `root`.
- `/proc` → informações virtuais sobre processos e kernel.
- `/sys` → informações virtuais sobre hardware e kernel.
- `/run` → dados temporários de execução.
- `/tmp` → arquivos temporários.
- `/usr` → programas, bibliotecas e recursos do sistema.
- `/usr/local` → software instalado localmente.
- `/var` → dados que mudam durante a operação.
- `/var/log` → registros do sistema e serviços.
- `/media` → mídias removíveis.
- `/mnt` → montagens temporárias.
- `/opt` → software adicional.
- `/srv` → dados fornecidos por serviços.
- `/var/tmp` → arquivos temporários que podem permanecer por mais tempo.
- Sistemas Linux modernos podem usar **usr merge**, fazendo `/bin`, `/sbin` e `/lib` apontarem para `/usr`.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
