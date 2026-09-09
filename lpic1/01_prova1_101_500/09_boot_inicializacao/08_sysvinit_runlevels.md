# Boot e Inicialização

## 08 — SysVinit e Runlevels

### 1. O que é SysVinit?

**SysVinit — System V Initialization — Inicialização System V**

É um sistema tradicional de inicialização usado por distribuições Linux antes da adoção do `systemd`.

O processo principal do SysVinit é:

    init

Normalmente:

    PID 1 → init

Sua função é iniciar os serviços e colocar o sistema em determinado estado de operação.

---

### 2. Runlevel

**Runlevel — Nível de Execução**

No SysVinit, um **runlevel** representa um estado de funcionamento do sistema.

Os runlevels tradicionais são:

| Runlevel | Significado tradicional |
|---|---|
| `0` | Halt — Desligar |
| `1` | Single User — Usuário Único / manutenção |
| `2` | Multi-user — Multiusuário |
| `3` | Multi-user — Multiusuário com rede, sem interface gráfica |
| `4` | Não definido por padrão |
| `5` | Multi-user + GUI — Multiusuário com interface gráfica |
| `6` | Reboot — Reiniciar |

> A utilização dos runlevels `2`, `3`, `4` e `5` pode variar entre distribuições.

---

### 3. Runlevel 0

**Runlevel 0 — Halt — Desligamento**

É utilizado para desligar o sistema.

    init 0

ou, em sistemas SysVinit:

    telinit 0

---

### 4. Runlevel 1

**Runlevel 1 — Single User — Usuário Único**

Usado principalmente para:

- manutenção;
- recuperação;
- diagnóstico;
- operações administrativas.

Normalmente inicia apenas os serviços essenciais.

---

### 5. Runlevel 3

**Runlevel 3 — Multi-user — Multiusuário**

Estado tradicional de um sistema Linux com:

- vários usuários;
- serviços de rede;
- sem ambiente gráfico.

Muito usado em servidores tradicionais.

---

### 6. Runlevel 5

**Runlevel 5 — Multi-user + GUI — Multiusuário com Interface Gráfica**

Estado tradicional usado para iniciar:

- serviços;
- rede;
- sistema multiusuário;
- interface gráfica.

---

### 7. Runlevel 6

**Runlevel 6 — Reboot — Reinicialização**

Usado para reiniciar o sistema.

    init 6

ou:

    telinit 6

---

### 8. Ver o Runlevel

Em sistemas SysVinit, pode ser utilizado:

    runlevel

Exemplo:

    N 3

Significa que não havia um runlevel anterior (`N`) e o atual é `3`.

Outro comando tradicional:

    who -r

Mostra informações sobre o runlevel atual.

---

### 9. Alterar o Runlevel

Com SysVinit:

    init 3

ou:

    telinit 3

Isso solicita a mudança para o runlevel `3`.

Exemplo:

    init 1

→ entra no modo de usuário único.

---

### 10. Scripts de inicialização

O SysVinit utiliza scripts para iniciar e parar serviços.

Um local tradicional é:

    /etc/init.d/

Exemplo:

    /etc/init.d/ssh

Esses scripts podem receber ações como:

    start
    stop
    restart
    status

Exemplo:

    sudo /etc/init.d/ssh status

---

### 11. Diretórios rc

O SysVinit também utiliza diretórios relacionados aos runlevels.

Exemplos:

    /etc/rc0.d/
    /etc/rc1.d/
    /etc/rc2.d/
    /etc/rc3.d/
    /etc/rc4.d/
    /etc/rc5.d/
    /etc/rc6.d/

Eles indicam quais serviços devem ser iniciados ou encerrados em cada runlevel.

---

### 12. Scripts S e K

Dentro dos diretórios `rc*.d`, era comum encontrar nomes como:

    S01ssh
    K20apache2

**S — Start — Iniciar**

Indica um serviço que deve ser iniciado.

**K — Kill — Encerrar**

Indica um serviço que deve ser encerrado.

O número indica a ordem de execução.

Exemplo:

    S01ssh

→ iniciar o serviço na ordem `01`.

---

### 13. SysVinit × systemd

| SysVinit | systemd |
|---|---|
| `init` | `systemd` |
| Runlevels | Targets |
| `/etc/init.d/` | Units |
| Scripts | Units/serviços |
| `init 3` | `systemctl isolate multi-user.target` |
| `init 5` | `systemctl isolate graphical.target` |

O `systemd` possui mecanismos de compatibilidade para muitos scripts e conceitos do SysVinit.

---

### 14. Equivalência com Targets

No `systemd`, os antigos runlevels possuem equivalentes em forma de targets.

| SysVinit | systemd |
|---|---|
| `0` | `poweroff.target` |
| `1` | `rescue.target` |
| `3` | `multi-user.target` |
| `5` | `graphical.target` |
| `6` | `reboot.target` |

Os runlevels `2` e `4` não possuem uma equivalência universal única, pois seu significado pode variar.

---

## Resumo LPIC-1

- **SysVinit** → sistema tradicional de inicialização.
- `init` → processo principal, normalmente **PID 1**.
- **Runlevel** → estado de funcionamento do sistema.
- `0` → desligar.
- `1` → usuário único / manutenção.
- `3` → multiusuário, normalmente sem interface gráfica.
- `5` → multiusuário com interface gráfica.
- `6` → reiniciar.
- `runlevel` → mostra o runlevel atual.
- `init N` → solicita mudança para o runlevel `N`.
- `/etc/init.d/` → scripts tradicionais de serviços.
- `/etc/rc*.d/` → diretórios associados aos runlevels.
- `S` → iniciar.
- `K` → encerrar.
- `systemd` substituiu o SysVinit em muitas distribuições modernas.
- No `systemd`, **targets** substituem o conceito tradicional de runlevels.

### Relação principal

    SysVinit
       ↓
    Runlevels
       ↓
    systemd
       ↓
    Targets

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
