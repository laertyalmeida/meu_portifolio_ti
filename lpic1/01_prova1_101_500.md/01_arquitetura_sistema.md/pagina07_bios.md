# 📖 PÁGINA 7 — BIOS

# 🧠 1. O QUE É BIOS?

**BIOS = Basic Input/Output System**

Tradução:

**Sistema Básico de Entrada/Saída**

É um firmware responsável por iniciar o computador e realizar as primeiras etapas de inicialização do hardware.

De forma simplificada:

**Ligar computador → BIOS → Inicialização do hardware → Bootloader → Kernel → Sistema Linux**

---

# ⚙️ 2. BIOS É FIRMWARE

**Firmware** é um software gravado em uma memória não volátil do dispositivo.

A BIOS é um tipo de firmware.

Ela fica disponível antes do sistema operacional ser carregado.

Portanto:

**BIOS ≠ Sistema operacional**

A BIOS prepara o computador para que o processo de inicialização possa continuar.

---

# 🔌 3. O QUE A BIOS FAZ?

Durante a inicialização, a BIOS realiza tarefas como:

- Inicializar componentes básicos do hardware.
- Verificar o hardware necessário para iniciar o computador.
- Identificar dispositivos de armazenamento.
- Procurar um dispositivo de inicialização.
- Iniciar o processo de boot.

O processo de verificação inicial do hardware é tradicionalmente associado ao:

**POST**

**POST = Power-On Self-Test**

Tradução:

**Autoteste ao ligar**

---

# 🧪 4. POST

O **POST** é realizado durante a inicialização do computador.

Seu objetivo é verificar se componentes básicos necessários ao funcionamento estão disponíveis.

Exemplos de componentes verificados:

- CPU
- Memória RAM
- Teclado
- Dispositivos básicos de hardware

De forma simplificada:

**Ligar → POST → Hardware inicializado → Continuar boot**

---

# 💾 5. BIOS E DISPOSITIVO DE BOOT

Depois da inicialização do hardware, a BIOS procura um dispositivo configurado para inicialização.

Pode ser, por exemplo:

- Disco rígido
- SSD
- USB
- CD/DVD

A BIOS segue a ordem de boot configurada.

Exemplo:

**1º USB → 2º SSD → 3º DVD**

Se não houver um dispositivo inicializável na primeira opção, pode tentar a próxima.

---

# 🚀 6. BIOS E BOOTLOADER

A BIOS não é o Linux.

Ela inicia o processo que posteriormente permitirá carregar o sistema operacional.

De forma simplificada:

**BIOS → Bootloader → Kernel → Sistema operacional**

No Linux, um bootloader muito comum é:

**GRUB**

**GRUB = GRand Unified Bootloader**

O GRUB é responsável por iniciar o kernel Linux.

---

# 💽 7. BIOS E MBR

Em sistemas que utilizam BIOS tradicional, é comum encontrar discos utilizando:

**MBR**

**MBR = Master Boot Record**

Tradução:

**Registro Mestre de Inicialização**

O MBR fica no início do disco e pode conter informações necessárias para iniciar o sistema.

Em um sistema BIOS tradicional:

**BIOS → MBR → Bootloader → Kernel**

### ⚠️ IMPORTANTE

Não confunda:

**BIOS**

→ firmware.

**MBR**

→ estrutura de inicialização localizada no início do disco.

**Bootloader**

→ programa responsável por iniciar o sistema operacional.

**Kernel**

→ núcleo do sistema operacional.

---

# 🧠 8. BIOS x UEFI

A BIOS tradicional é uma tecnologia mais antiga.

**UEFI = Unified Extensible Firmware Interface**

Tradução:

**Interface de Firmware Extensível Unificada**

O UEFI é uma alternativa moderna ao BIOS tradicional.

Comparação:

**BIOS tradicional**

→ tecnologia mais antiga.

→ frequentemente associada a MBR.

**UEFI**

→ tecnologia moderna.

→ normalmente utiliza GPT.

→ pode utilizar uma partição EFI/ESP.

---

# 🔐 9. BIOS E SECURE BOOT

O **Secure Boot** é um recurso associado ao UEFI, e não à BIOS tradicional.

Seu objetivo é verificar componentes de inicialização utilizando mecanismos de assinatura e confiança.

Portanto:

**Secure Boot → UEFI**

Não memorize como uma função da BIOS tradicional.

---

# 🛠️ 10. ACESSANDO A CONFIGURAÇÃO DA BIOS

A configuração da BIOS normalmente pode ser acessada durante a inicialização do computador.

Dependendo do fabricante, uma tecla como:

**Delete**

ou:

**F2**

pode abrir a configuração.

Outras teclas também podem ser utilizadas dependendo do equipamento.

### ⚠️ Para a prova

O importante é compreender que:

**BIOS Setup**

→ permite configurar opções relacionadas ao firmware e ao processo de inicialização.

---

# 🐧 11. COMO VER INFORMAÇÕES DA BIOS NO LINUX

O Linux pode disponibilizar informações do firmware através do:

`/sys`

Um caminho importante é:

`/sys/class/dmi/id/`

Arquivos nesse diretório podem fornecer informações sobre o firmware e o hardware.

Por exemplo:

`bios_vendor`

→ fabricante da BIOS.

`bios_version`

→ versão da BIOS.

`bios_date`

→ data da BIOS.

Podemos consultar:

`cat /sys/class/dmi/id/bios_vendor`

ou:

`cat /sys/class/dmi/id/bios_version`

---

# 📖 12. INTERPRETANDO `cat`

### Tradução

**cat = concatenate**

Tradução literal:

**concatenar**

Também é utilizado para exibir o conteúdo de arquivos.

Exemplo:

`cat /sys/class/dmi/id/bios_version`

Interpretação:

**cat**

→ concatenate → exibir/concatenar conteúdo.

**/sys/class/dmi/id/bios_version**

→ arquivo que contém a versão da BIOS.

---

# 📝 13. COMANDOS NECESSÁRIOS

### Consultar fabricante da BIOS

`cat /sys/class/dmi/id/bios_vendor`

### Consultar versão da BIOS

`cat /sys/class/dmi/id/bios_version`

### Consultar data da BIOS

`cat /sys/class/dmi/id/bios_date`

### Tradução principal

**cat**

→ concatenate → concatenar/exibir conteúdo.

---

# 🎯 14. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O significado de BIOS.
- Que BIOS significa **Basic Input/Output System**.
- Que BIOS é firmware.
- Diferença entre firmware e sistema operacional.
- O que é POST.
- Que POST significa **Power-On Self-Test**.
- Que a BIOS inicializa componentes básicos do hardware.
- Que a BIOS participa do processo de boot.
- O que é um dispositivo de boot.
- O que é bootloader.
- O que é GRUB.
- O que é MBR.
- Diferenciar BIOS, MBR, bootloader e kernel.
- A relação básica entre BIOS e MBR.
- A diferença básica entre BIOS e UEFI.
- Que UEFI é uma tecnologia moderna de firmware.
- Que UEFI normalmente trabalha com GPT.
- Que Secure Boot está associado ao UEFI.
- Conhecer `/sys/class/dmi/id/`.
- Consultar informações da BIOS com `cat`.

---

# 🧠 RESUMO

**BIOS**

→ Basic Input/Output System.

→ Sistema Básico de Entrada/Saída.

→ Firmware responsável pelas primeiras etapas de inicialização.

**FIRMWARE**

→ Software integrado ao hardware.

**POST**

→ Power-On Self-Test.

→ Autoteste ao ligar.

**BOOT**

→ Processo de inicialização do computador.

**BOOTLOADER**

→ Programa que inicia o sistema operacional.

**GRUB**

→ GRand Unified Bootloader.

→ Bootloader muito utilizado no Linux.

**MBR**

→ Master Boot Record.

→ Registro Mestre de Inicialização.

**BIOS tradicional**

→ Tecnologia de firmware mais antiga.

→ Frequentemente associada ao MBR.

**UEFI**

→ Unified Extensible Firmware Interface.

→ Firmware moderno.

→ Normalmente associado ao GPT.

**Secure Boot**

→ Recurso associado ao UEFI.

**cat**

→ concatenate.

→ Exibe/concatena conteúdo.

**/sys/class/dmi/id/**

→ Informações de hardware e firmware disponibilizadas pelo kernel.

---

# 🔄 FLUXO PARA MEMORIZAR

**Computador ligado**

↓

**BIOS**

↓

**POST**

↓

**Inicialização do hardware**

↓

**Dispositivo de boot**

↓

**Bootloader / GRUB**

↓

**Kernel**

↓

**Sistema Linux**

# ✅ FIM DA PÁGINA 7
