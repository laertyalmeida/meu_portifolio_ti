# Boot e Inicialização

## 04 — systemd

### 1. O que é systemd?

**systemd — System and Service Manager — Gerenciador do Sistema e Serviços**

É o sistema de inicialização usado por muitas distribuições Linux modernas.

Normalmente, ele é executado como:

    PID 1

O `systemd` assume o controle depois que o kernel termina sua preparação inicial.

---

### 2. Onde o systemd entra no Boot?

    BIOS / UEFI
          ↓
      Bootloader
          ↓
       Kernel
          ↓
      initramfs
          ↓
    systemd (PID 1)
          ↓
      Serviços
          ↓
        Login

---

### 3. Principais funções

O `systemd` pode:

- iniciar serviços;
- parar e reiniciar serviços;
- controlar a ordem de inicialização;
- gerenciar dependências;
- montar sistemas de arquivos;
- controlar targets;
- registrar mensagens no journal;
- gerenciar alguns recursos do sistema.

---

### 4. systemctl

**systemctl — systemd Control — Controle do systemd**

É o principal comando para controlar e consultar o `systemd`.

Verificar o estado geral:

    systemctl status

Verificar se o systemd está funcionando:

    systemctl is-system-running

---

### 5. Gerenciar serviços

**Service — Serviço**

Ver o estado de um serviço:

    systemctl status ssh

Iniciar:

    sudo systemctl start ssh

**start — Iniciar**

Parar:

    sudo systemctl stop ssh

**stop — Parar**

Reiniciar:

    sudo systemctl restart ssh

**restart — Reiniciar**

Recarregar a configuração do serviço:

    sudo systemctl reload ssh

**reload — Recarregar**

---

### 6. Habilitar no boot

**enable — Habilitar**

Faz o serviço ser configurado para iniciar automaticamente conforme as dependências/configuração da unidade.

    sudo systemctl enable ssh

Desabilitar:

    sudo systemctl disable ssh

**disable — Desabilitar**

É possível fazer as duas coisas ao mesmo tempo:

    sudo systemctl enable --now ssh

`--now` — Agora — habilita e inicia imediatamente.

---

### 7. Ver serviços

Listar unidades de serviço carregadas:

    systemctl list-units --type=service

Listar serviços instalados e seu estado de habilitação:

    systemctl list-unit-files --type=service

---

### 8. Unit

**Unit — Unidade**

O `systemd` trabalha com diferentes tipos de unidades.

| Tipo | Função |
|---|---|
| `.service` | Serviço |
| `.socket` | Socket |
| `.target` | Grupo/estado de unidades |
| `.mount` | Ponto de montagem |
| `.timer` | Temporizador |
| `.path` | Monitoramento de caminho |
| `.device` | Dispositivo |

Exemplos:

    ssh.service
    graphical.target
    cron.timer

---

### 9. Target

**Target — Alvo/Estado do Sistema**

Um `target` reúne unidades que devem estar ativas para alcançar determinado estado do sistema.

Ver o target padrão:

    systemctl get-default

Alterar o target padrão:

    sudo systemctl set-default graphical.target

Targets comuns:

    multi-user.target
    graphical.target
    rescue.target
    emergency.target

---

### 10. Journal

O `systemd` utiliza o **journald** para registrar mensagens.

Consultar o journal:

    journalctl

Mensagens do kernel:

    journalctl -k

Mensagens do boot atual:

    journalctl -b

Mensagens de um serviço:

    journalctl -u ssh

`-u` — Unit — Unidade

Acompanhar mensagens em tempo real:

    journalctl -f

`-f` — Follow — Acompanhar

---

### 11. systemd × SysVinit

| SysVinit | systemd |
|---|---|
| Runlevels | Targets |
| Scripts de inicialização | Units |
| `/etc/inittab` | Units/configurações do systemd |
| `service` | `systemctl` |
| Logs separados/variáveis | `journalctl` / journald |

O `systemd` também possui mecanismos de compatibilidade com componentes do modelo SysVinit em muitos sistemas.

---

### 12. Diretórios importantes

Arquivos e unidades podem aparecer em:

    /etc/systemd/system/

    /usr/lib/systemd/system/

Em algumas distribuições, unidades fornecidas por pacotes podem estar em:

    /lib/systemd/system/

A localização exata pode variar conforme a distribuição e o layout do sistema.

---

## Resumo LPIC-1

- **systemd** → sistema moderno de inicialização e gerenciamento de serviços.
- Normalmente executa como **PID 1**.
- `systemctl` → controla o systemd.
- `start` → inicia.
- `stop` → para.
- `restart` → reinicia.
- `reload` → recarrega configuração.
- `enable` → habilita para inicialização automática.
- `disable` → desabilita.
- `--now` → aplica a ação imediatamente.
- **Unit** → unidade gerenciada pelo systemd.
- `.service` → serviço.
- `.target` → estado/grupo de unidades.
- `journalctl` → consulta logs do journal.
- `journalctl -b` → mensagens do boot.
- `journalctl -u serviço` → mensagens de uma unidade.
- `systemctl get-default` → mostra o target padrão.

**Fluxo:**

    Kernel
      ↓
    systemd (PID 1)
      ↓
    Units
      ↓
    Services / Targets
      ↓
    Sistema pronto

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
