# 09 — Boot e Inicialização
## 08 — SysVinit e Runlevels

### O que é SysVinit?

**SysVinit — System V Initialization (Inicialização System V)**

É um sistema tradicional usado pelo Linux para iniciar o sistema e controlar serviços.

Antes da popularização do `systemd`, muitas distribuições utilizavam o **SysVinit**.

O SysVinit utiliza **runlevels** para definir o estado de funcionamento do sistema.

---

# 1. Runlevel — Nível de execução

**Runlevel — Nível de execução**

Um runlevel representa um determinado estado do sistema.

Os runlevels tradicionais são:

| Runlevel | Significado | Uso |
|---:|---|---|
| `0` | Halt | Desligar |
| `1` | Single User | Modo usuário único/manutenção |
| `2` | Multi-user | Multiusuário |
| `3` | Multi-user | Multiusuário, sem interface gráfica |
| `4` | Unused | Não utilizado por padrão |
| `5` | Graphical | Multiusuário com interface gráfica |
| `6` | Reboot | Reiniciar |

⚠️ A utilização dos runlevels `2`, `3`, `4` e `5` pode variar conforme a distribuição.

---

# 2. Runlevel 0

**Halt — Parada**

    Runlevel 0

Desliga o sistema.

Equivalente moderno:

    systemctl poweroff

---

# 3. Runlevel 1

**Single User — Usuário único**

    Runlevel 1

Usado principalmente para:

- manutenção;
- recuperação;
- correção de problemas;
- tarefas administrativas.

Normalmente inicia apenas o mínimo necessário.

Equivalente aproximado no `systemd`:

    rescue.target

---

# 4. Runlevel 2

**Multi-user — Multiusuário**

    Runlevel 2

Tradicionalmente representa um modo multiusuário.

⚠️ O significado exato depende da distribuição.

---

# 5. Runlevel 3

**Multi-user — Multiusuário sem interface gráfica**

    Runlevel 3

Sistema multiusuário com serviços de rede, normalmente sem ambiente gráfico.

Equivalente aproximado no `systemd`:

    multi-user.target

---

# 6. Runlevel 4

**Unused — Não utilizado**

    Runlevel 4

Tradicionalmente reservado ou não utilizado.

Seu comportamento pode ser personalizado pela distribuição ou pelo administrador.

---

# 7. Runlevel 5

**Graphical — Gráfico**

    Runlevel 5

Sistema multiusuário com interface gráfica.

Equivalente aproximado no `systemd`:

    graphical.target

---

# 8. Runlevel 6

**Reboot — Reinicialização**

    Runlevel 6

Reinicia o computador.

Equivalente moderno:

    systemctl reboot

---

# 9. Comando runlevel

O comando:

    runlevel

Mostra o runlevel anterior e o atual.

Exemplo:

    N 5

Interpretação:

    N → não havia runlevel anterior registrado
    5 → runlevel atual

---

# 10. Comando telinit

**telinit — Change Initialization Level (Alterar nível de inicialização)**

Em sistemas SysVinit, podia ser utilizado para mudar o runlevel.

Exemplo:

    telinit 3

→ mudar para o runlevel 3.

Outro exemplo:

    telinit 5

→ mudar para o runlevel 5.

Em sistemas modernos com `systemd`, esse comando pode existir apenas por compatibilidade.

---

# 11. Comando init

O `init` é o processo tradicional de inicialização.

Exemplo:

    init 3

→ solicitar mudança para o runlevel 3.

No SysVinit, o `init` normalmente possui:

    PID 1

No `systemd`, o PID 1 normalmente é o próprio `systemd`.

Verificar:

    ps -p 1 -o pid,comm,args

---

# 12. SysVinit e scripts de serviços

O SysVinit tradicional utiliza scripts de inicialização.

Um local comum é:

    /etc/init.d/

Exemplo:

    /etc/init.d/ssh

Esses scripts podem ser utilizados para iniciar, parar ou reiniciar serviços.

Exemplo tradicional:

    sudo /etc/init.d/ssh start

    sudo /etc/init.d/ssh stop

    sudo /etc/init.d/ssh restart

---

# 13. update-rc.d

Em sistemas Debian e derivados, o comando:

    update-rc.d

pode ser utilizado para configurar a inicialização de scripts SysV.

Exemplo:

    sudo update-rc.d ssh enable

**enable — habilitar**

---

# 14. chkconfig

Em sistemas tradicionais derivados de Red Hat, o:

    chkconfig

era utilizado para administrar serviços e seus runlevels.

Exemplo:

    chkconfig --list

**--list — listar**

Em sistemas modernos, seu uso pode ser substituído por ferramentas baseadas em `systemd`.

---

# 15. SysVinit x systemd

| SysVinit | systemd |
|---|---|
| Runlevels | Targets |
| Scripts `/etc/init.d/` | Unit files |
| `init` | `systemd` |
| `telinit` | `systemctl` |
| `service` | `systemctl` |
| `chkconfig` | `systemctl enable/disable` |
| Inicialização mais sequencial | Inicialização com maior paralelismo |

---

# 16. Relação entre Runlevels e Targets

O `systemd` não utiliza runlevels como seu mecanismo principal.

Ele utiliza **targets**.

Correspondências aproximadas:

    Runlevel 0 → poweroff.target
    Runlevel 1 → rescue.target
    Runlevel 3 → multi-user.target
    Runlevel 5 → graphical.target
    Runlevel 6 → reboot.target

⚠️ São correspondências aproximadas. Targets são mais flexíveis que os runlevels tradicionais.

---

# 🎯 LPIC-1 — O que memorizar

### SysVinit

Sistema tradicional de inicialização.

### Runlevel

Representa um estado do sistema.

### Mais importantes

    0 → desligar
    1 → manutenção
    3 → multiusuário sem gráfico
    5 → multiusuário gráfico
    6 → reiniciar

### Comandos

    runlevel
    init
    telinit
    service
    chkconfig
    update-rc.d

### Arquivos

    /etc/init.d/

→ scripts tradicionais de inicialização.

---

## 🧠 Para decorar

**SysVinit → Runlevels**

**systemd → Targets**

    Runlevel 0 → poweroff.target
    Runlevel 1 → rescue.target
    Runlevel 3 → multi-user.target
    Runlevel 5 → graphical.target
    Runlevel 6 → reboot.target

> ⭐ **Pegadinha LPIC-1:** não trate os runlevels `2`, `3`, `4` e `5` como absolutamente iguais em todas as distribuições. A definição pode variar.

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
