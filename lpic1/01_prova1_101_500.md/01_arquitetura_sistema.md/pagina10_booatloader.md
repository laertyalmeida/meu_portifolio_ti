# 📖 PÁGINA 10 — BOOTLOADER

# 🧠 1. O QUE É BOOTLOADER?

**Bootloader** significa:

**carregador de inicialização**

É o programa responsável por iniciar o carregamento do sistema operacional.

No Linux, o bootloader mais importante que você precisa conhecer é:

**GRUB**

**GRUB = GRand Unified Bootloader**

Tradução aproximada:

**Grande Bootloader Unificado**

Fluxo:

**BIOS/UEFI → Bootloader/GRUB → Kernel → Linux**

---

# 🚀 2. O QUE O BOOTLOADER FAZ?

O bootloader é executado antes do kernel.

Suas principais funções são:

- Localizar o kernel.
- Carregar o kernel na memória.
- Passar informações/parâmetros para o kernel.
- Permitir escolher entre diferentes opções de inicialização.

Em um computador com vários sistemas operacionais, o bootloader pode apresentar um menu para escolher qual sistema iniciar.

---

# 🐧 3. GRUB

**GRUB = GRand Unified Bootloader**

É um bootloader muito utilizado em sistemas Linux.

O GRUB pode:

- Carregar o kernel Linux.
- Carregar o `initramfs`.
- Apresentar um menu de boot.
- Permitir selecionar diferentes kernels.
- Receber parâmetros que serão passados ao kernel.

---

# 💽 4. GRUB E BIOS

Quando o computador utiliza BIOS tradicional, o processo pode ser representado assim:

**BIOS → GRUB → Kernel**

Em sistemas BIOS tradicionais, o GRUB pode utilizar o:

**MBR**

**MBR = Master Boot Record**

Tradução:

**Registro Mestre de Inicialização**

O MBR fica no início do disco.

---

# 🖥️ 5. GRUB E UEFI

Em sistemas UEFI, o GRUB normalmente é armazenado na:

**ESP**

**ESP = EFI System Partition**

Tradução:

**Partição de Sistema EFI**

A ESP normalmente utiliza:

**FAT32**

Fluxo:

**UEFI → ESP → GRUB → Kernel**

---

# 📂 6. ARQUIVOS IMPORTANTES DO GRUB

Um arquivo importante é:

`/etc/default/grub`

Ele contém configurações utilizadas para gerar a configuração do GRUB.

Outro local importante é:

`/boot/grub/`

ou, dependendo do modo de boot:

`/boot/efi/`

### ⚠️ IMPORTANTE

Não confunda:

`/etc/default/grub`

→ arquivo de configuração usado para definir opções.

`/boot/grub/`

→ arquivos relacionados ao GRUB.

---

# ⚙️ 7. `/etc/default/grub`

Podemos visualizar:

`cat /etc/default/grub`

### Tradução

**cat = concatenate**

→ concatenar/exibir conteúdo.

O arquivo pode conter configurações como:

`GRUB_TIMEOUT=5`

Isso define o tempo de espera do menu do GRUB.

Também pode existir:

`GRUB_CMDLINE_LINUX_DEFAULT`

Essa variável define parâmetros que podem ser adicionados à linha de comando do kernel.

---

# 🔄 8. GERANDO A CONFIGURAÇÃO DO GRUB

Depois de alterar:

`/etc/default/grub`

é necessário gerar novamente a configuração utilizada pelo GRUB.

Em sistemas Debian, um comando comum é:

`update-grub`

### Tradução

**update = atualizar**

**grub = GRUB**

Portanto:

**update-grub → atualizar a configuração do GRUB**

Ele normalmente gera/atualiza:

`/boot/grub/grub.cfg`

---

# 📄 9. `grub.cfg`

O arquivo:

`/boot/grub/grub.cfg`

contém a configuração que o GRUB utiliza durante o boot.

### ⚠️ IMPORTANTE

Normalmente não devemos editar `grub.cfg` diretamente.

O procedimento comum é:

**Alterar `/etc/default/grub`**

↓

**Executar `update-grub`**

↓

**Atualizar `/boot/grub/grub.cfg`**

---

# 🧠 10. PARÂMETROS DO KERNEL

O GRUB pode passar parâmetros para o kernel.

Esses parâmetros aparecem na linha de comando do kernel.

Podemos visualizar os parâmetros utilizados pelo kernel atual com:

`cat /proc/cmdline`

### Tradução

**cat = concatenate**

→ exibir conteúdo.

`/proc/cmdline`

→ linha de comando utilizada para iniciar o kernel.

Exemplo:

`BOOT_IMAGE=/boot/vmlinuz... ro quiet`

---

# 🔍 11. `vmlinuz`

Você pode encontrar arquivos como:

`/boot/vmlinuz`

ou:

`/boot/vmlinuz-...`

O `vmlinuz` representa uma imagem do kernel Linux utilizada no processo de boot.

De forma simplificada:

**GRUB → carrega vmlinuz → Kernel**

---

# 📦 12. INITRAMFS E BOOTLOADER

Durante o boot, o GRUB também pode carregar o:

**initramfs**

**initramfs = initial RAM filesystem**

Tradução:

**sistema de arquivos RAM inicial**

Fluxo:

**GRUB → Kernel + initramfs → Sistema Linux**

O initramfs fornece ferramentas, módulos e arquivos necessários durante as primeiras etapas da inicialização.

---

# 🛠️ 13. `grub-install`

O comando:

`grub-install`

é utilizado para instalar o GRUB no sistema.

### Tradução

**grub = GRUB**

**install = instalar**

Portanto:

**grub-install → instalar o GRUB**

### ⚠️ ATENÇÃO

É um comando de administração do boot.

Não execute `grub-install` sem saber exatamente qual dispositivo e modo de boot estão sendo utilizados.

Para a prova, o importante é reconhecer sua função.

---

# 🔎 14. `efibootmgr`

Em sistemas UEFI, o:

`efibootmgr`

pode consultar e gerenciar entradas de boot armazenadas nas variáveis EFI.

### Tradução

**EFI Boot Manager**

→ Gerenciador de Boot EFI.

Comando:

`efibootmgr`

Pode mostrar:

`Boot0000`

`Boot0001`

e:

`BootOrder`

Isso permite visualizar a ordem de inicialização configurada no firmware UEFI.

---

# 📝 15. COMANDOS NECESSÁRIOS

### Ver configuração do GRUB

`cat /etc/default/grub`

**cat → concatenate → exibir conteúdo**

### Atualizar configuração do GRUB

`update-grub`

**update → atualizar**

### Consultar parâmetros do kernel

`cat /proc/cmdline`

**cmdline → command line → linha de comando**

### Instalar GRUB

`grub-install`

**install → instalar**

### Consultar entradas de boot UEFI

`efibootmgr`

**EFI Boot Manager → Gerenciador de Boot EFI**

---

# 🎯 16. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que é um bootloader.
- Que bootloader significa carregador de inicialização.
- O que é GRUB.
- Que GRUB significa **GRand Unified Bootloader**.
- O papel do GRUB no processo de boot.
- A relação entre BIOS e GRUB.
- A relação entre UEFI e GRUB.
- A relação entre GRUB e MBR.
- A relação entre GRUB e ESP.
- Que a ESP normalmente utiliza FAT32.
- Conhecer `/etc/default/grub`.
- Conhecer `/boot/grub/`.
- Conhecer `grub.cfg`.
- Saber por que `update-grub` é utilizado.
- Saber que `grub.cfg` normalmente não deve ser editado diretamente.
- Conhecer parâmetros do kernel.
- Consultar `/proc/cmdline`.
- Conhecer `vmlinuz`.
- Entender a relação entre GRUB, kernel e initramfs.
- Saber para que serve `grub-install`.
- Conhecer `efibootmgr` no contexto de UEFI.

---

# 🧠 RESUMO

**BOOTLOADER**

→ carregador de inicialização.

→ inicia o carregamento do sistema operacional.

**GRUB**

→ GRand Unified Bootloader.

→ bootloader muito utilizado no Linux.

**BIOS → GRUB → Kernel**

**UEFI → ESP → GRUB → Kernel**

**MBR**

→ Master Boot Record.

→ Registro Mestre de Inicialização.

**ESP**

→ EFI System Partition.

→ Partição de Sistema EFI.

→ normalmente FAT32.

**/etc/default/grub**

→ configurações utilizadas para gerar a configuração do GRUB.

**update-grub**

→ atualiza/gera a configuração do GRUB.

**/boot/grub/grub.cfg**

→ configuração utilizada pelo GRUB.

**/proc/cmdline**

→ parâmetros passados ao kernel durante o boot.

**vmlinuz**

→ imagem do kernel Linux.

**initramfs**

→ sistema de arquivos inicial em RAM.

**grub-install**

→ instala o GRUB.

**efibootmgr**

→ consulta/gerencia entradas de boot UEFI.

---

# 🔄 FLUXO PARA MEMORIZAR

### BIOS

**BIOS**

↓

**GRUB**

↓

**Kernel**

↓

**initramfs**

↓

**Linux**

### UEFI

**UEFI**

↓

**ESP**

↓

**GRUB**

↓

**Kernel**

↓

**initramfs**

↓

**Linux**

# ✅ FIM DA PÁGINA 10
