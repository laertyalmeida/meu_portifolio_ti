# LPIC-1 - Módulo 01
## 2. BIOS e UEFI — Tópicos para Revisão

### 2.1 BIOS
- **BIOS** → Basic Input/Output System.
- Firmware tradicional da placa-mãe.
- Inicializa e verifica o hardware.
- Inicia o processo de boot.

### 2.2 POST
- **POST** → Power-On Self-Test.
- Teste inicial do hardware.
- Verifica componentes básicos do computador.

### 2.3 UEFI
- **UEFI** → Unified Extensible Firmware Interface.
- Firmware moderno.
- Substitui a BIOS tradicional.
- Suporta GPT, ESP e Secure Boot.

### 2.4 BIOS × UEFI
- **BIOS** → tecnologia tradicional.
- **UEFI** → tecnologia moderna.
- **BIOS/Legacy** → tradicionalmente associado ao MBR.
- **UEFI** → normalmente associado ao GPT.

### 2.5 MBR e GPT
- **MBR** → padrão antigo de particionamento.
- **GPT** → padrão moderno de particionamento.

### 2.6 ESP
- **ESP** → EFI System Partition.
- Partição usada pelo UEFI.
- Armazena arquivos de inicialização `.efi`.
- Normalmente montada em `/boot/efi`.

### 2.7 Secure Boot
- Recurso de segurança do UEFI.
- Verifica assinaturas durante o boot.
- Ajuda a impedir software não autorizado na inicialização.

### 2.8 Verificar UEFI no Linux

```bash
ls /sys/firmware/efi

2.9 Sequência do Boot

Hardware
   ↓
BIOS / UEFI
   ↓
POST
   ↓
Bootloader
   ↓
Kernel
   ↓
Sistema Operacional

📌 Para memorizar
BIOS/UEFI → inicializa o hardware
POST → testa o hardware
Bootloader → inicia o kernel
Kernel → núcleo do sistema operacional
UEFI → GPT + ESP + Secure Boot

