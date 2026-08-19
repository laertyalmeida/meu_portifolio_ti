# LPIC-1 — BIOS e UEFI
## Principais comandos

- `dmesg | grep -i bios`
- `dmesg | grep -i uefi`
- `ls /sys/firmware/efi`
- `test -d /sys/firmware/efi && echo "UEFI" || echo "BIOS"`
- `efibootmgr`
- `efivar`
- `dmidecode`
- `dmidecode -t bios`
- `dmidecode -t system`
- `hostnamectl`
- `bootctl`

LPIC-1 — Módulo 01

BIOS e UEFI — Comandos

1. "dmesg | grep -i bios"

Termos em inglês → tradução:

- "dmesg" → diagnostic message → mensagens de diagnóstico
- "grep" → search/filter → pesquisar/filtrar
- "BIOS" → Basic Input/Output System → Sistema Básico de Entrada/Saída
- "case-insensitive" → indiferente a maiúsculas/minúsculas

Comando → significado:

- "dmesg" → exibe mensagens do kernel
- "grep" → filtra linhas que correspondem a um texto
- "|" → pipe → envia a saída de um comando para outro

Flag/opção → significado:

- "-i" → ignore case → ignora diferença entre maiúsculas e minúsculas

Saída → interpretação:

BIOS-provided physical RAM map:
BIOS-e820:

→ Mostra mensagens relacionadas à BIOS registradas pelo kernel.

---

2. "dmesg | grep -i uefi"

Termos em inglês → tradução:

- "UEFI" → Unified Extensible Firmware Interface → Interface de Firmware Extensível Unificada

Comando → significado:

- "dmesg" → exibe mensagens do kernel
- "grep" → filtra mensagens relacionadas a UEFI

Flag/opção:

- "-i" → ignora maiúsculas/minúsculas

Saída → interpretação:

UEFI: ...

→ Indica mensagens relacionadas ao UEFI durante a inicialização.

---

3. "ls /sys/firmware/efi"

Termos em inglês → tradução:

- "ls" → list → listar
- "firmware" → firmware → software básico do hardware
- "efi" → Extensible Firmware Interface → Interface de Firmware Extensível

Comando → significado:

- "ls" → lista o conteúdo de um diretório
- "/sys/firmware/efi" → interface do kernel para informações do firmware UEFI

Flag/opção:

- Não utiliza flag obrigatória.

Saída → interpretação:

efivars
fw_platform_size
runtime
sysfs

→ Se esse diretório existir e estiver disponível, o sistema foi inicializado em modo UEFI.

Se não existir:

ls: cannot access '/sys/firmware/efi'

→ Normalmente indica inicialização em modo BIOS/Legacy.

---

4. "test -d /sys/firmware/efi && echo "UEFI" || echo "BIOS""

Termos em inglês → tradução:

- "test" → testar/verificar
- "directory" → diretório
- "echo" → exibir/imprimir

Comando → significado:

- "test -d" → verifica se o diretório existe
- "&&" → executa o próximo comando se o anterior funcionar
- "||" → executa o próximo comando se o anterior falhar

Flag/opção:

- "-d" → directory → verifica se é um diretório

Saída → interpretação:

UEFI

→ Sistema inicializado em modo UEFI.

Ou:

BIOS

→ Sistema inicializado em modo BIOS/Legacy.

---

5. "efibootmgr"

Termos em inglês → tradução:

- "EFI" → Extensible Firmware Interface → Interface de Firmware Extensível
- "boot" → inicialização
- "manager" → gerenciador

Comando → significado:

- Gerencia e exibe entradas de inicialização UEFI.

Flag/opção:

- Sem opção → mostra as entradas de boot configuradas.

Saída → interpretação:

BootCurrent: 0001
BootOrder: 0001,0000
Boot0000* Debian
Boot0001* UEFI OS

→ Mostra a ordem e as entradas de inicialização registradas no firmware UEFI.

---

6. "efivar"

Termos em inglês → tradução:

- "EFI" → Extensible Firmware Interface
- "var" → variable → variável

Comando → significado:

- Trabalha com variáveis armazenadas pelo firmware UEFI.

Flag/opção:

- "-l" → lista as variáveis EFI.

Saída → interpretação:

Boot0000-...
Boot0001-...

→ Mostra variáveis armazenadas no firmware UEFI.

«⚠️ É um comando mais avançado. Alterar variáveis EFI incorretamente pode afetar a inicialização.»

---

7. "dmidecode"

Termos em inglês → tradução:

- "DMI" → Desktop Management Interface → Interface de Gerenciamento do Computador
- "decode" → decodificar

Comando → significado:

- Consulta informações fornecidas pelo firmware através do DMI/SMBIOS.

Flag/opção:

- "-t" → type → tipo
- "-t bios" → informações da BIOS
- "-t system" → informações do sistema

Saída → interpretação:

Manufacturer: ...
Product Name: ...
Version: ...

→ Permite consultar informações do hardware e do firmware.

---

8. "dmidecode -t bios"

Termos em inglês → tradução:

- "BIOS" → Basic Input/Output System → Sistema Básico de Entrada/Saída

Comando → significado:

- Mostra informações específicas da BIOS/firmware.

Flag/opção:

- "-t" → type → tipo
- "bios" → seleciona informações da BIOS

Saída → interpretação:

BIOS Information
    Vendor: ...
    Version: ...
    Release Date: ...

→ Mostra fabricante, versão e data da BIOS.

---

9. "dmidecode -t system"

Termos em inglês → tradução:

- "system" → sistema

Comando → significado:

- Mostra informações do sistema fornecidas pelo firmware.

Flag/opção:

- "-t" → type → tipo
- "system" → seleciona informações do sistema

Saída → interpretação:

System Information
    Manufacturer: ...
    Product Name: ...
    Version: ...

→ Mostra informações como fabricante e modelo do computador.

---

10. "hostnamectl"

Termos em inglês → tradução:

- "hostname" → nome do computador
- "ctl" → control → controle

Comando → significado:

- Exibe informações do sistema e do hostname.

Flag/opção:

- Sem opção → mostra informações gerais.

Saída → interpretação:

Operating System: Debian GNU/Linux
Kernel: Linux 6.12...
Architecture: x86-64

→ Pode mostrar a arquitetura, kernel e outras informações do sistema.

---

11. "bootctl"

Termos em inglês → tradução:

- "boot" → inicialização
- "ctl" → control → controle

Comando → significado:

- Consulta e gerencia informações relacionadas ao systemd-boot e à inicialização UEFI.

Flag/opção:

- "status" → mostra o estado das informações de boot.

Saída → interpretação:

System:
      Firmware: UEFI
 Firmware Arch: x64

→ Pode indicar se o sistema está utilizando UEFI e fornecer informações sobre o processo de boot.

---

📌 Resumo dos comandos

Comando| Função principal
"dmesg | grep -i bios"| Procura mensagens da BIOS
"dmesg | grep -i uefi"| Procura mensagens do UEFI
"ls /sys/firmware/efi"| Verifica interface UEFI
"test -d /sys/firmware/efi ..."| Identifica UEFI ou BIOS
"efibootmgr"| Gerencia entradas de boot UEFI
"efivar"| Trabalha com variáveis UEFI
"dmidecode"| Consulta informações DMI/SMBIOS
"dmidecode -t bios"| Informações da BIOS
"dmidecode -t system"| Informações do sistema
"hostnamectl"| Informações do sistema
"bootctl"| Informações do boot/systemd-boot

🧠 Prioridade para LPIC-1

Essenciais:

ls /sys/firmware/efi
efibootmgr
dmidecode -t bios
dmidecode -t system
dmesg | grep -i bios
dmesg | grep -i uefi

Complementares:

efivar
hostnamectl
bootctl
dmidecode

📌 Observação

Para entender BIOS/UEFI, o mais importante é saber identificar o modo de inicialização, consultar informações do firmware e entender como o sistema Linux interage com o firmware durante o boot.
