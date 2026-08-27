# ⚙️ LPIC-1 — BIOS / UEFI
# PARTE 2 — BOOT, GPT, ESP E SECURE BOOT

## 1. PROCESSO DE BOOT
- O que é Boot
- O que acontece depois do Power On
- Transferência de controle
- Firmware → Bootloader
- Bootloader → Kernel

## 2. BIOS LEGACY
- Modo Legacy
- BIOS + MBR
- Como o boot acontece
- MBR como código de inicialização
- Limitações do processo Legacy

## 3. MBR
- Master Boot Record
- Localização no disco
- Estrutura básica
- Código de boot
- Tabela de partições
- Identificador/assinatura do disco
- Limitações do MBR

## 4. UEFI
- UEFI e o processo de boot
- UEFI + GPT
- Firmware UEFI
- Arquivos EFI
- Boot Manager
- Entradas de boot

## 5. GPT
- GUID Partition Table
- Estrutura do GPT
- GPT Header
- Partition Entries
- Backup GPT Header
- Vantagens sobre MBR
- Limites de tamanho e quantidade de partições

## 6. ESP — EFI SYSTEM PARTITION
- O que é ESP
- Função da ESP
- Sistema de arquivos FAT32
- Arquivos `.efi`
- Bootloaders na ESP
- Estrutura de diretórios
- ESP × `/boot`

## 7. UEFI BOOT MANAGER
- O que é Boot Manager
- Entradas de boot
- Ordem das entradas
- Identificação dos sistemas
- Como o UEFI encontra o bootloader

## 8. SECURE BOOT
- O que é Secure Boot
- Objetivo
- Assinaturas digitais
- Chaves
- Verificação do bootloader
- Cadeia de confiança
- Secure Boot × segurança

## 9. UEFI × GRUB
- O papel do UEFI
- O papel do GRUB
- Como UEFI inicia o GRUB
- GRUB como arquivo `.efi`
- UEFI → GRUB → Kernel

## 10. MODO LEGACY × MODO UEFI

### Legacy

BIOS
 ↓
MBR
 ↓
Bootloader
 ↓
Kernel

### UEFI

UEFI
 ↓
ESP
 ↓
Arquivo `.efi`
 ↓
Bootloader
 ↓
Kernel

## 11. COMO IDENTIFICAR O MODO DE BOOT NO LINUX
- `/sys/firmware/efi`
- Verificar se o sistema iniciou em UEFI
- Identificar ESP
- Identificar GPT
- Identificar entradas de boot

## 12. COMANDOS IMPORTANTES

### Verificar UEFI

```bash
ls /sys/firmware/efi
