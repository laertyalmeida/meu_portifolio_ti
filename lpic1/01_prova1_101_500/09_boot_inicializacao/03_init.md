# 09 — Boot e Inicialização
## 03 — init

### init — Initialization Process (Processo de Inicialização)

O **init** é o processo responsável por iniciar e organizar o ambiente de **User Space — Espaço do Usuário** depois que o kernel Linux é carregado.

Fluxo simplificado:

    Firmware
       ↓
    Bootloader
       ↓
    Kernel
       ↓
    init
       ↓
    Serviços
       ↓
    Login

---

### PID 1

O processo `init` tradicionalmente ocupa:

    PID = 1

Podemos verificar:

    ps -p 1 -f

Exemplo:

    UID   PID  PPID  CMD
    root    1     0  /sbin/init

O processo com **PID 1** possui uma função fundamental: iniciar e supervisionar o restante do espaço de usuário.

---

### init tradicional

Em sistemas Linux antigos, era comum utilizar o:

    SysVinit

O SysVinit utiliza **runlevels — níveis de execução** para definir o estado de operação do sistema.

Exemplos tradicionais:

| Runlevel | Função tradicional |
|---:|---|
| `0` | Halt — desligar |
| `1` | Single User — modo de usuário único |
| `2` | Multi-user — multiusuário |
| `3` | Multi-user — multiusuário, normalmente sem interface gráfica |
| `4` | Não padronizado |
| `5` | Multi-user + GUI — multiusuário com interface gráfica |
| `6` | Reboot — reiniciar |

⚠️ A utilização exata dos runlevels `2`, `3`, `4` e `5` pode variar entre distribuições.

---

### systemd — Init moderno

Em muitas distribuições Linux atuais, o `init` tradicional foi substituído pelo:

    systemd

Mesmo utilizando `systemd`, o conceito de **PID 1** continua existindo.

Verifique:

    ps -p 1 -o pid,comm,args

Exemplo:

    PID COMMAND CMD
      1 systemd /sbin/init

Aqui:

    /sbin/init → pode ser um link para systemd

Portanto, `init` pode aparecer no caminho do processo mesmo quando o sistema está utilizando `systemd`.

---

### systemd × SysVinit

| SysVinit | systemd |
|---|---|
| Sistema tradicional | Sistema moderno |
| Usa runlevels | Usa targets |
| Scripts de inicialização | Units |
| Inicialização mais sequencial | Pode iniciar unidades em paralelo |
| Comando tradicional: `service` | Comando principal: `systemctl` |

---

### Target — Alvo de Inicialização

No `systemd`, os **targets** substituem o conceito de runlevels.

Exemplos:

    multi-user.target

→ modo multiusuário sem exigir interface gráfica.

    graphical.target

→ modo multiusuário com interface gráfica.

Ver o target padrão:

    systemctl get-default

Alterar o target padrão:

    sudo systemctl set-default graphical.target

---

### systemctl — Control Systemd (Controlar o systemd)

O `systemctl` permite controlar serviços e outras unidades do `systemd`.

Ver o estado de um serviço:

    systemctl status nome.service

Iniciar:

    sudo systemctl start nome.service

Parar:

    sudo systemctl stop nome.service

Reiniciar:

    sudo systemctl restart nome.service

Ativar no boot:

    sudo systemctl enable nome.service

Desativar no boot:

    sudo systemctl disable nome.service

---

### init × systemd

Não pense que são necessariamente dois processos diferentes.

A ideia principal é:

    init
     ↓
    função de inicialização

Em sistemas antigos:

    init → SysVinit

Em sistemas modernos:

    init → systemd como PID 1

---

### Ver qual sistema de init está sendo usado

Uma forma prática:

    ps -p 1 -o comm=

Exemplo:

    systemd

Outra possibilidade:

    readlink -f /sbin/init

Isso pode mostrar:

    /usr/lib/systemd/systemd

ou outro programa de inicialização, dependendo da distribuição.

---

### ⚠️ Atenção para a prova LPIC-1

Memorize:

**init**
→ processo responsável pela inicialização do espaço de usuário.

**PID 1**
→ identificação tradicional do processo de inicialização.

**SysVinit**
→ sistema tradicional de inicialização baseado em runlevels.

**systemd**
→ sistema moderno de inicialização e gerenciamento de serviços.

**`systemctl`**
→ ferramenta principal para administrar o `systemd`.

**Runlevel**
→ conceito tradicional do SysVinit.

**Target**
→ conceito utilizado pelo systemd.

### Resumo

    Linux antigo:

    Kernel
      ↓
    init (SysVinit)
      ↓
    Runlevels
      ↓
    Serviços


    Linux moderno:

    Kernel
      ↓
    systemd (PID 1)
      ↓
    Targets
      ↓
    Services

> **Conhecimento só tem valor quando é compartilhado** - Laerte Costa
