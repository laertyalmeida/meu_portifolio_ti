# 📖 PÁGINA 8 — UEFI

# 🧠 1. O QUE É UEFI?

**UEFI = Unified Extensible Firmware Interface**

Tradução:

**Interface de Firmware Extensível Unificada**

UEFI é uma especificação moderna de firmware utilizada para inicializar o computador e preparar o hardware antes do carregamento do sistema operacional.

De forma simplificada:

**Ligar → UEFI → Bootloader → Kernel → Linux**

---

# ⚙️ 2. UEFI É FIRMWARE

Assim como a BIOS tradicional, o UEFI é firmware.

Portanto:

**UEFI ≠ Sistema operacional**

O firmware é executado antes do sistema operacional.

Sua função inclui inicializar o hardware e localizar um programa de inicialização.

---

# 💽 3. UEFI E GPT

Uma diferença importante entre BIOS tradicional e UEFI é a forma como o processo de boot pode ser organizado.

UEFI normalmente trabalha com discos utilizando:

**GPT**

**GPT = GUID Partition Table**

Tradução:

**Tabela de Partições GUID**

Comparação:

**BIOS tradicional → MBR**

**UEFI → GPT**

### ⚠️ IMPORTANTE

UEFI pode trabalhar com MBR em determinados cenários, portanto não memorize que UEFI "só funciona com GPT".

Para a prova, memorize a associação principal:

**UEFI → GPT**

---

# 🥾 4. UEFI E ESP

Sistemas UEFI utilizam normalmente uma partição especial chamada:

**ESP = EFI System Partition**

Tradução:

**Partição de Sistema EFI**

A ESP é uma partição utilizada para armazenar arquivos necessários ao processo de inicialização UEFI.

Normalmente utiliza o sistema de arquivos:

**FAT32**

---

# 📂 5. ONDE FICA A ESP?

A ESP normalmente é montada em:

`/boot/efi`

Exemplo:

`/boot/efi`

→ ponto de montagem comum da EFI System Partition.

Dentro dela podem existir arquivos de boot, incluindo arquivos utilizados pelo bootloader.

---

# 🚀 6. UEFI E BOOTLOADER

No modo UEFI, o firmware procura arquivos de boot na **ESP**.

O bootloader pode estar armazenado nessa partição.

No Linux, um exemplo comum é:

**GRUB**

Fluxo:

**UEFI → ESP → GRUB → Kernel → Linux**

---

# 🔐 7. SECURE BOOT

**Secure Boot** é um recurso do UEFI.

Seu objetivo é ajudar a impedir que componentes não autorizados sejam executados durante o processo de inicialização.

O UEFI verifica assinaturas digitais dos componentes de boot conforme as chaves e políticas configuradas.

### 🧠 PARA MEMORIZAR

**Secure Boot → UEFI**

---

# 🆔 8. GPT

**GPT = GUID Partition Table**

Tradução:

**Tabela de Partições GUID**

GPT é um esquema moderno de particionamento.

Ele utiliza identificadores únicos (**GUIDs**) para identificar partições.

Uma característica importante é que GPT suporta discos muito maiores que o limite tradicional associado ao MBR.

---

# ⚖️ 9. MBR x GPT

### MBR

**MBR = Master Boot Record**

→ esquema de particionamento tradicional.

→ associado principalmente ao boot BIOS tradicional.

### GPT

**GPT = GUID Partition Table**

→ esquema de particionamento moderno.

→ normalmente utilizado com UEFI.

Resumo:

**BIOS tradicional → MBR**

**UEFI → GPT + ESP**

---

# 🧠 10. COMO IDENTIFICAR SE O SISTEMA ESTÁ EM UEFI

Uma maneira simples é verificar se existe:

`/sys/firmware/efi`

Podemos executar:

`ls /sys/firmware/efi`

Se o diretório existir e possuir conteúdo, o sistema provavelmente foi inicializado em modo UEFI.

Se o diretório não existir, o sistema provavelmente foi inicializado utilizando BIOS/Legacy.

---

# 🔍 11. `ls`

### Tradução

**ls = list**

Significa:

**listar**

Comando:

`ls /sys/firmware/efi`

Interpretação:

`ls`

→ list → listar.

`/sys/firmware/efi`

→ interface do kernel relacionada ao firmware UEFI.

---

# 📂 12. `findmnt`

O comando:

`findmnt`

pode ser utilizado para identificar onde uma partição está montada.

### Tradução

**findmnt = find mount**

→ encontrar montagem.

Para procurar a ESP:

`findmnt /boot/efi`

Se estiver montada, o comando mostrará informações sobre a partição.

---

# 💾 13. `lsblk`

O comando:

`lsblk`

lista dispositivos de bloco.

### Tradução

`ls`

→ list → listar.

`blk`

→ block → bloco.

Portanto:

**lsblk → list block devices → listar dispositivos de bloco**

Pode ser utilizado para visualizar discos e partições.

Uma forma útil:

`lsblk -f`

### `-f`

**filesystem = sistema de arquivos**

Mostra informações sobre sistemas de arquivos.

Isso pode ajudar a identificar a ESP, que normalmente utiliza FAT32.

---

# 🧰 14. `efibootmgr`

Em sistemas UEFI, o comando:

`efibootmgr`

pode ser utilizado para visualizar e gerenciar entradas de boot UEFI.

### Tradução

**EFI Boot Manager**

→ Gerenciador de Boot EFI.

Executar:

`efibootmgr`

pode mostrar entradas como:

`Boot0000`

`Boot0001`

e a ordem de inicialização.

### ⚠️ IMPORTANTE

O `efibootmgr` depende de o sistema ter sido inicializado em modo UEFI e de o acesso às variáveis EFI estar disponível.

---

# 📝 15. COMANDOS NECESSÁRIOS

### Verificar UEFI

`ls /sys/firmware/efi`

### Verificar montagem da ESP

`findmnt /boot/efi`

### Listar discos e partições

`lsblk`

### Mostrar sistemas de arquivos

`lsblk -f`

### Consultar entradas de boot UEFI

`efibootmgr`

---

# 🎯 16. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O significado de UEFI.
- Que UEFI significa **Unified Extensible Firmware Interface**.
- Que UEFI é firmware.
- Diferença entre firmware e sistema operacional.
- A relação entre UEFI e GPT.
- O significado de GPT.
- O significado de GUID.
- O que é uma ESP.
- O significado de EFI System Partition.
- Que a ESP normalmente utiliza FAT32.
- Que `/boot/efi` é um ponto de montagem comum da ESP.
- A relação entre UEFI, ESP e bootloader.
- O que é Secure Boot.
- Que Secure Boot é um recurso do UEFI.
- Diferença básica entre BIOS/MBR e UEFI/GPT.
- Como verificar a presença de `/sys/firmware/efi`.
- Usar `findmnt`.
- Usar `lsblk`.
- Entender `lsblk -f`.
- Conhecer `efibootmgr`.

---

# 🧠 RESUMO

**UEFI**

→ Unified Extensible Firmware Interface.

→ Interface de Firmware Extensível Unificada.

→ Firmware moderno.

**GPT**

→ GUID Partition Table.

→ Tabela de Partições GUID.

**GUID**

→ Globally Unique Identifier.

→ Identificador Globalmente Único.

**ESP**

→ EFI System Partition.

→ Partição de Sistema EFI.

→ Normalmente FAT32.

**/boot/efi**

→ Ponto de montagem comum da ESP.

**Secure Boot**

→ Recurso de segurança do UEFI.

**UEFI → ESP → Bootloader → Kernel → Linux**

**BIOS tradicional → MBR → Bootloader → Kernel → Linux**

---

# 🔧 COMANDOS

**ls**

→ list → listar.

`ls /sys/firmware/efi`

→ verifica a presença da interface UEFI.

**findmnt**

→ find mount → encontrar montagem.

`findmnt /boot/efi`

→ verifica a montagem da ESP.

**lsblk**

→ list block devices → listar dispositivos de bloco.

`lsblk -f`

→ mostra sistemas de arquivos.

**efibootmgr**

→ EFI Boot Manager.

→ Consulta entradas de boot UEFI.

---

# 🧠 PARA DECORAR

```text
BIOS tradicional
└── MBR

UEFI
├── GPT
├── ESP
│   └── FAT32
├── Secure Boot
└── Bootloader

ESP
└── /boot/efi

UEFI
└── /sys/firmware/efi
```

# ✅ FIM DA PÁGINA
