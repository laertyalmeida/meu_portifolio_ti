# GRUB — Gerenciador de Inicialização

GRUB (**GRand Unified Bootloader**) é o programa responsável por iniciar o Linux.

Quando o computador liga:

Computador
 ↓
BIOS/UEFI
 ↓
GRUB
 ↓
Kernel Linux
 ↓
Sistema Linux

O GRUB aparece antes do Linux iniciar.

---

## Para que serve?

O GRUB pode:

- Iniciar o Linux.
- Escolher entre diferentes sistemas operacionais.
- Escolher diferentes kernels Linux.
- Passar parâmetros para o kernel durante a inicialização.
- Iniciar um modo de recuperação, dependendo da configuração.

---

## Onde fica a configuração?

A configuração principal do GRUB geralmente fica em:

/boot/grub/grub.cfg

Esse arquivo contém as entradas que aparecem no menu do GRUB.

**Importante:** normalmente não é recomendado editar esse arquivo diretamente.

As configurações usadas para gerar o `grub.cfg` ficam principalmente em:

/etc/default/grub

E scripts relacionados ficam em:

/etc/grub.d/

---

## Atualizar a configuração

Depois de alterar configurações do GRUB, é necessário gerar novamente o arquivo de configuração.

Em sistemas Debian/Ubuntu, por exemplo:

sudo update-grub

"update-grub" — Update GRUB (Atualizar GRUB)

Atualiza o arquivo de configuração do GRUB.

---

## Instalar o GRUB

O GRUB pode ser instalado no dispositivo de inicialização.

Exemplo:

sudo grub-install /dev/sda

"grub-install" — GRUB Install (Instalar GRUB)

Instala o GRUB no dispositivo indicado.

Nesse exemplo:

/dev/sda → disco

---

## Kernel e GRUB

O GRUB pode apresentar diferentes kernels instalados.

Por exemplo:

GRUB
├── Linux Kernel 6.x
├── Linux Kernel 5.x
└── Recovery Mode

Isso permite escolher qual kernel será iniciado.

---

## Parâmetros do Kernel

O GRUB também pode passar parâmetros para o kernel.

Exemplo:

quiet

ou:

nomodeset

Esses parâmetros podem alterar o comportamento do Linux durante a inicialização.

---

## GRUB e arquivos importantes

/etc/default/grub
        ↓
Configurações
        ↓
/etc/grub.d/
        ↓
Scripts
        ↓
update-grub
        ↓
/boot/grub/grub.cfg

---

## LPIC-1 — O que saber

- GRUB é um **bootloader** — Gerenciador de Inicialização.
- Ele é executado antes do kernel Linux.
- Pode iniciar diferentes kernels.
- Pode iniciar diferentes sistemas operacionais.
- Pode passar parâmetros para o kernel.
- `/boot/grub/grub.cfg` contém a configuração gerada do GRUB.
- `/etc/default/grub` contém configurações do GRUB em muitas distribuições.
- `update-grub` gera/atualiza a configuração em sistemas Debian/Ubuntu.
- `grub-install` instala o GRUB.

---

## Resumo

Computador
 ↓
BIOS/UEFI
 ↓
GRUB
 ↓
Kernel
 ↓
Linux

GRUB
├── Inicia Linux
├── Escolhe kernel
├── Escolhe sistema operacional
└── Passa parâmetros ao kernel

Arquivos:

/etc/default/grub → configurações
/etc/grub.d/      → scripts
/boot/grub/grub.cfg → configuração gerada

Comandos:

update-grub  → atualizar configuração
grub-install → instalar GRUB

GRUB → Bootloader → Gerenciador de Inicialização
