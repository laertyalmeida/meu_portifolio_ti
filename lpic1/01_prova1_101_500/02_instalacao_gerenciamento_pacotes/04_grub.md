# Instalação e Gerenciamento de Pacotes

## 04 — GRUB

### GRUB — Grand Unified Bootloader — Grande Carregador de Inicialização Unificado

**GRUB** é o carregador de inicialização normalmente usado para iniciar sistemas Linux.

Ele aparece depois do **BIOS/UEFI** e antes do **Kernel Linux**.

### Processo de inicialização

    BIOS/UEFI
        ↓
    GRUB
        ↓
    Kernel Linux
        ↓
    initramfs
        ↓
    systemd
        ↓
    Serviços
        ↓
    Login

---

## Bootloader — Carregador de Inicialização

O **Bootloader — Carregador de Inicialização** é responsável por localizar e carregar o kernel na memória.

O GRUB também pode:

- iniciar diferentes kernels;
- iniciar diferentes sistemas operacionais;
- receber parâmetros para o kernel;
- oferecer um menu de inicialização;
- iniciar um modo de recuperação.

---

## GRUB 2

A versão moderna utilizada atualmente é o **GRUB 2**.

Arquivos e diretórios importantes:

    /boot/grub/

- `/boot` — boot — inicialização
- `/boot/grub` — arquivos de configuração e componentes do GRUB

Em sistemas UEFI, também pode existir:

    /boot/efi/

- `efi` — EFI — partição usada pelo firmware UEFI

---

## grub.cfg — Configuração do GRUB

O arquivo principal gerado de configuração é:

    /boot/grub/grub.cfg

Ele contém as entradas utilizadas pelo GRUB para inicializar os sistemas.

**Não é recomendado editar esse arquivo diretamente.**

Em muitas distribuições, a configuração é gerada a partir de:

    /etc/default/grub

- `/etc` — etcetera — configuração do sistema
- `default` — padrão
- `grub` — configuração principal do GRUB

Depois de alterar essa configuração, normalmente é necessário regenerar o arquivo do GRUB.

---

## update-grub — Atualizar GRUB

Em distribuições baseadas em Debian/Ubuntu:

    sudo update-grub

- `update` — atualizar
- `grub` — GRUB

O comando procura kernels e outros sistemas instalados e atualiza a configuração.

---

## grub-mkconfig — Gerar Configuração

O comando utilizado para gerar a configuração é:

    sudo grub-mkconfig -o /boot/grub/grub.cfg

- `grub-mkconfig` — GRUB Make Configuration — gerar configuração do GRUB
- `-o` — output — saída
- `/boot/grub/grub.cfg` — arquivo de configuração gerado

Em algumas distribuições, `update-grub` é apenas uma forma simplificada de executar esse processo.

---

## GRUB e Kernel

O GRUB precisa saber qual kernel deve ser carregado.

Os kernels geralmente ficam em:

    /boot/

Exemplos:

    /boot/vmlinuz-6.x.x
    /boot/initramfs-6.x.x.img

- `vmlinuz` — imagem comprimida do kernel Linux
- `initramfs` — Initial RAM Filesystem — sistema de arquivos inicial em RAM

---

## Kernel Parameters — Parâmetros do Kernel

O GRUB pode passar parâmetros para o kernel durante a inicialização.

Exemplo:

    quiet

- `quiet` — inicialização silenciosa, reduzindo mensagens exibidas

Outro exemplo:

    ro

- `ro` — read-only — somente leitura

Um parâmetro muito conhecido:

    single

- `single` — modo de usuário único

Os parâmetros aparecem na linha de inicialização do kernel no GRUB.

---

## GRUB e recuperação

O menu do GRUB pode permitir selecionar:

- diferentes versões do kernel;
- **Recovery Mode — Modo de Recuperação**;
- outros sistemas operacionais.

Isso é útil quando um kernel ou configuração apresenta problemas.

---

## BIOS × UEFI

O GRUB pode trabalhar em sistemas iniciados por:

    BIOS → GRUB → Kernel

ou:

    UEFI → GRUB → Kernel

Em sistemas UEFI, os arquivos de inicialização ficam na:

**ESP — EFI System Partition — Partição de Sistema EFI**

Normalmente montada em:

    /boot/efi/

---

## Comandos importantes

| Comando | Tradução | Função |
|---|---|---|
| `update-grub` | Atualizar GRUB | Regenera a configuração |
| `grub-mkconfig` | Gerar configuração | Cria `grub.cfg` |
| `grub-install` | Instalar GRUB | Instala o carregador de inicialização |
| `cat /etc/default/grub` | Exibir configuração | Mostra configurações do GRUB |

Exemplo:

    sudo grub-install /dev/sda

- `grub-install` — instalar GRUB
- `/dev/sda` — disco onde o GRUB será instalado

**Cuidado:** o destino depende do modo de inicialização (BIOS/UEFI) e da configuração do sistema.

---

## Resumo LPIC-1

- **GRUB — Grand Unified Bootloader — Grande Carregador de Inicialização Unificado**.
- GRUB é um **Bootloader — Carregador de Inicialização**.
- Ele fica entre o **BIOS/UEFI** e o **Kernel Linux**.
- `/boot` — diretório relacionado à inicialização.
- `/boot/grub/` — arquivos do GRUB.
- `/boot/grub/grub.cfg` — configuração gerada do GRUB.
- `/etc/default/grub` — configurações usadas para gerar o GRUB.
- `update-grub` — atualizar a configuração do GRUB.
- `grub-mkconfig` — gerar `grub.cfg`.
- `grub-install` — instalar o GRUB.
- `vmlinuz` — imagem do kernel.
- `initramfs` — sistema de arquivos inicial em RAM.
- GRUB pode passar **Kernel Parameters — Parâmetros do Kernel**.
- Em UEFI, a inicialização utiliza a **ESP — EFI System Partition — Partição de Sistema EFI**.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
