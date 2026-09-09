# 01 — Arquitetura do Sistema

## 01 — BIOS e UEFI

### BIOS — Basic Input/Output System
**BIOS — Sistema Básico de Entrada/Saída**

Firmware tradicional responsável por inicializar o computador e preparar o hardware para o processo de boot — **inicialização**.

Durante o boot, a BIOS:

1. Inicializa o hardware.
2. Verifica os dispositivos.
3. Localiza um dispositivo de inicialização.
4. Inicia o **Bootloader — Carregador de Inicialização**.

---

### UEFI — Unified Extensible Firmware Interface
**UEFI — Interface de Firmware Extensível Unificada**

Firmware moderno que substituiu a BIOS tradicional.

Principais características:

- Suporte a **GPT — GUID Partition Table — Tabela de Partições GUID**.
- Utilização da **ESP — EFI System Partition — Partição de Sistema EFI**.
- Pode utilizar **Secure Boot — Inicialização Segura**.
- Utiliza arquivos de inicialização `.efi`.

---

### ESP — EFI System Partition

**ESP — EFI System Partition — Partição de Sistema EFI**

É a partição utilizada pelo UEFI para armazenar os arquivos necessários para a inicialização.

Normalmente utiliza:

    FAT32 — File Allocation Table 32 — Tabela de Alocação de Arquivos 32

No Linux, é comum a ESP estar montada em:

    /boot/efi

**`/boot` — boot — inicialização**  
Diretório relacionado aos arquivos necessários para inicializar o sistema.

**`/boot/efi` — boot/EFI — inicialização/EFI**  
Local comum onde a Partição de Sistema EFI é montada.

---

### MBR — Master Boot Record

**MBR — Registro Mestre de Inicialização**

Formato tradicional de particionamento que também pode participar do processo de inicialização em sistemas baseados em BIOS.

---

### GPT — GUID Partition Table

**GPT — Tabela de Partições GUID**

Formato moderno de particionamento, normalmente utilizado em sistemas UEFI.

---

### Secure Boot — Inicialização Segura

Recurso do UEFI que verifica assinaturas digitais dos componentes utilizados durante a inicialização.

Seu objetivo é permitir a execução de componentes de boot autorizados.

---

### Diretório `/sys/firmware/efi`

**`/sys` — system — sistema**

É um sistema de arquivos virtual utilizado pelo kernel para disponibilizar informações sobre hardware, dispositivos e outros componentes do sistema.

**`/sys/firmware/efi` — sistema/firmware/EFI**

Quando esse diretório existe, normalmente significa que o Linux foi inicializado em modo UEFI.

---

### Verificar o modo de inicialização

    test -d /sys/firmware/efi && echo "UEFI" || echo "BIOS"

**test — testar**  
Verifica uma condição.

`-d` — **directory — diretório**  
Verifica se o caminho é um diretório.

**echo — exibir**  
Mostra uma mensagem na tela.

---

### Comandos importantes

**lsblk — List Block Devices — Listar Dispositivos de Bloco**

    lsblk -f

`-f` — **filesystem — sistema de arquivos**  
Mostra informações sobre os sistemas de arquivos.

**fdisk — Fixed Disk — Disco Fixo**

    fdisk -l

`-l` — **list — listar**  
Lista informações sobre discos e partições.

---

### BIOS × UEFI

| BIOS | UEFI |
|---|---|
| Firmware tradicional | Firmware moderno |
| Boot tradicional | Inicialização por arquivos `.efi` |
| Frequentemente usado com MBR | Frequentemente usado com GPT |
| Mais limitado | Mais recursos |
| Não possui Secure Boot tradicional | Pode utilizar Secure Boot |

---

## Resumo LPIC-1

- **BIOS — Basic Input/Output System** → Sistema Básico de Entrada/Saída.
- **UEFI — Unified Extensible Firmware Interface** → Interface de Firmware Extensível Unificada.
- **Boot — Inicialização** → processo de iniciar o computador.
- **Bootloader — Carregador de Inicialização** → inicia o sistema operacional.
- **ESP — EFI System Partition** → Partição de Sistema EFI.
- **Secure Boot — Inicialização Segura** → verifica assinaturas dos componentes de inicialização.
- **MBR — Master Boot Record** → Registro Mestre de Inicialização.
- **GPT — GUID Partition Table** → Tabela de Partições GUID.
- **FAT32 — File Allocation Table 32** → Tabela de Alocação de Arquivos 32.
- `/boot` → **boot — inicialização**.
- `/boot/efi` → **EFI — inicialização do firmware UEFI**.
- `/sys` → **system — sistema**.
- `/sys/firmware/efi` → indica inicialização em modo UEFI.
- `lsblk` → **List Block Devices — Listar Dispositivos de Bloco**.
- `fdisk` → **Fixed Disk — Disco Fixo**.
- `-f` → **filesystem — sistema de arquivos**.
- `-l` → **list — listar**.

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
