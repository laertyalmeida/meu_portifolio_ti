PARTE 3 — BOOT DO LINUX

1. O que é Boot
2. O que acontece depois da BIOS/UEFI
3. Bootloader
4. GRUB
5. MBR × GPT no processo de boot
6. BIOS + GRUB
7. UEFI + GRUB
8. EFI System Partition (ESP)
9. Kernel
10. initramfs / initrd
11. Como o GRUB encontra o Kernel
12. Como o Kernel é carregado
13. Parâmetros passados ao Kernel
14. O que acontece depois que o Kernel inicia
15. Visão completa do processo:
    
    Energia
       ↓
    CPU
       ↓
    BIOS/UEFI
       ↓
    Bootloader (GRUB)
       ↓
    Kernel
       ↓
    initramfs
       ↓
    systemd
       ↓
    Serviços
       ↓
    Sistema Linux pronto
