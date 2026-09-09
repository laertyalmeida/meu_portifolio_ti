# Boot e Inicialização

## 03 — init

### 1. O que é init?

**init — Initialization — Inicialização**

`init` é o **primeiro processo do espaço de usuário** iniciado pelo kernel durante o boot.

Ele recebe:

    PID 1

Sua principal função é iniciar e organizar os demais processos e serviços necessários para o sistema funcionar.

---

### 2. Onde o init entra no Boot?

Fluxo simplificado:

    BIOS / UEFI
          ↓
      Bootloader
          ↓
       Kernel
          ↓
      initramfs
          ↓
        init
       PID 1
          ↓
       Serviços
          ↓
        Login

O kernel inicia o processo `init` depois de preparar o ambiente básico.

---

### 3. PID 1

O primeiro processo recebe o **PID — Process ID — ID do Processo** `1`.

Podemos verificar:

    ps -p 1 -f

Ou:

    cat /proc/1/comm

Em sistemas modernos, normalmente veremos:

    systemd

---

### 4. init tradicional

Historicamente, muitas distribuições Linux utilizavam o:

**SysVinit — System V Initialization — Inicialização System V**

Nesse modelo, o `/etc/inittab` era um dos arquivos importantes de configuração.

Exemplo tradicional:

    /etc/inittab

O SysVinit utilizava **runlevels — níveis de execução** para definir o estado do sistema.

---

### 5. Runlevels

**Runlevel — Nível de Execução**

Os runlevels tradicionais eram representados por números:

| Runlevel | Uso tradicional |
|---|---|
| `0` | Halt — Desligar |
| `1` | Single User — Usuário Único / manutenção |
| `2` | Multi-user — Multiusuário |
| `3` | Multi-user + rede, sem interface gráfica |
| `4` | Não definido por padrão |
| `5` | Multi-user + interface gráfica |
| `6` | Reboot — Reiniciar |

A interpretação de alguns runlevels, especialmente `2`, podia variar entre distribuições.

---

### 6. init e systemd

Nas distribuições Linux modernas, o `systemd` normalmente ocupa o lugar do antigo SysVinit como **PID 1**.

    PID 1
      ↓
    systemd

Isso não significa que o conceito de `init` desapareceu.

O `init` continua sendo o nome tradicional para o **processo inicial do sistema**.

Ver o processo:

    ps -p 1 -o pid,comm,args

Exemplo:

    PID COMMAND  COMMAND
      1 systemd  /sbin/init

Em muitos sistemas:

    /sbin/init → systemd

---

### 7. init × systemd

| Conceito | Função |
|---|---|
| `init` | Processo inicial, PID 1 |
| SysVinit | Implementação tradicional do init |
| systemd | Implementação moderna do processo inicial e gerenciador de serviços |
| PID 1 | Identificação do primeiro processo do espaço de usuário |

---

### 8. Por que o PID 1 é importante?

O processo `init`/`systemd` possui responsabilidades especiais.

Entre elas:

- iniciar serviços;
- controlar processos do sistema;
- participar do gerenciamento de processos órfãos;
- manter o sistema em um estado operacional.

Se o processo PID 1 terminar de forma inesperada, o comportamento pode ser crítico para o sistema.

---

### 9. Comandos relacionados ao init

Ver o PID 1:

    ps -p 1 -f

Ver o executável:

    readlink -f /proc/1/exe

Ver a versão do systemd:

    systemctl --version

Ver serviços:

    systemctl list-units --type=service

---

## Resumo LPIC-1

- **init — Initialization — Inicialização** → processo inicial do espaço de usuário.
- Normalmente possui **PID 1**.
- É iniciado pelo **kernel**.
- Tradicionalmente, o Linux utilizava **SysVinit**.
- O SysVinit utilizava **runlevels**.
- Sistemas modernos geralmente utilizam **systemd** como PID 1.
- `/sbin/init` pode ser um link para o `systemd`.
- `ps -p 1 -f` → verifica qual processo está ocupando o PID 1.
- `systemd` → além de ser o init moderno, gerencia serviços e outras partes da inicialização.

**Fluxo:**

    Kernel
      ↓
    init (PID 1)
      ↓
    systemd
      ↓
    Serviços
      ↓
    Sistema pronto

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
