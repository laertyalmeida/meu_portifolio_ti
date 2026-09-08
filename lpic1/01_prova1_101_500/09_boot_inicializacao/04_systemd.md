# 09 — Boot e Inicialização
## 04 — systemd

### systemd — System and Service Manager (Gerenciador do Sistema e Serviços)

O **systemd** é o sistema de inicialização e gerenciamento de serviços usado por muitas distribuições Linux modernas.

Ele normalmente executa como:

    PID 1

Sua função não é apenas iniciar o sistema. O `systemd` também gerencia serviços, unidades, dependências, logs e outros recursos.

---

### O que o systemd faz?

Principais funções:

- iniciar serviços durante o boot;
- parar e reiniciar serviços;
- controlar dependências entre serviços;
- iniciar unidades em paralelo quando possível;
- gerenciar targets;
- acompanhar processos;
- trabalhar com logs através do `journald`;
- responder a eventos do sistema.

Fluxo:

    Kernel
       ↓
    systemd (PID 1)
       ↓
    Units
       ↓
    Services
       ↓
    Sistema pronto

---

# Unit — Unidade

O `systemd` organiza recursos do sistema em **Units — Unidades**.

Existem vários tipos:

| Extensão | Tipo | Função |
|---|---|---|
| `.service` | Service | Serviço |
| `.socket` | Socket | Socket de comunicação |
| `.target` | Target | Grupo lógico de unidades |
| `.mount` | Mount | Ponto de montagem |
| `.timer` | Timer | Agendamento |
| `.path` | Path | Monitoramento de caminhos |
| `.device` | Device | Dispositivo |

Para listar unidades:

    systemctl list-units

---

### Service — Serviço

Uma unidade `.service` representa normalmente um serviço do sistema.

Exemplo:

    ssh.service

Consultar:

    systemctl status ssh.service

Em algumas distribuições o nome pode ser diferente, como:

    sshd.service

---

### systemctl — Control systemd (Controlar o systemd)

O comando principal para administrar o `systemd` é:

    systemctl

---

### Iniciar um serviço

    sudo systemctl start nome.service

- `start` — iniciar

O serviço é iniciado imediatamente, mas isso não significa necessariamente que será iniciado automaticamente no próximo boot.

---

### Parar um serviço

    sudo systemctl stop nome.service

- `stop` — parar

---

### Reiniciar um serviço

    sudo systemctl restart nome.service

- `restart` — reiniciar

---

### Recarregar a configuração

Alguns serviços permitem:

    sudo systemctl reload nome.service

- `reload` — recarregar

O processo continua executando, mas sua configuração é recarregada quando o serviço suporta essa operação.

---

### Status — Status do Serviço

    systemctl status nome.service

Mostra informações como:

- se está ativo;
- PID;
- estado;
- últimas mensagens;
- processo principal.

Estados comuns:

    active
    inactive
    failed
    activating
    deactivating

---

# Enable — Habilitar no Boot

Para fazer um serviço iniciar automaticamente durante o boot:

    sudo systemctl enable nome.service

- `enable` — habilitar

⚠️ **Enable não significa iniciar agora.**

Ele configura o serviço para ser iniciado automaticamente conforme as dependências do sistema.

---

### Disable — Desabilitar no Boot

    sudo systemctl disable nome.service

- `disable` — desabilitar

Impede que a unidade seja habilitada para inicialização automática.

---

### Enable + Start

Para habilitar e iniciar imediatamente:

    sudo systemctl enable --now nome.service

- `--now` — agora (iniciar/parar imediatamente junto com a alteração)

---

# Target — Alvo

Um **target** agrupa unidades relacionadas e representa um determinado estado do sistema.

Exemplos:

    multi-user.target
    graphical.target

---

### Ver o Target padrão

    systemctl get-default

Exemplo:

    graphical.target

---

### Alterar o Target padrão

    sudo systemctl set-default multi-user.target

- `set-default` — definir padrão

Isso altera o estado de inicialização padrão.

---

### Ver unidades com falha

    systemctl --failed

Mostra unidades que estão em estado de falha.

---

### Listar serviços

    systemctl list-units --type=service

- `--type` — tipo

Para listar também serviços que não estão ativos:

    systemctl list-unit-files --type=service

---

# systemd-analyze — Analyze systemd (Analisar o systemd)

O `systemd-analyze` permite analisar o processo de inicialização.

    systemd-analyze

Mostra informações sobre o tempo de boot.

Para identificar serviços que demoraram mais:

    systemd-analyze blame

---

# journalctl — Query Journal (Consultar o Journal)

O `systemd` normalmente utiliza o **systemd-journald** para registrar logs.

Consultar logs:

    journalctl

Logs do kernel:

    journalctl -k

- `-k` — kernel (kernel)

Logs do boot atual:

    journalctl -b

- `-b` — boot (inicialização)

---

### systemd × SysVinit

| SysVinit | systemd |
|---|---|
| Runlevels | Targets |
| Scripts | Units |
| `service` | `systemctl` |
| Inicialização tradicional | Inicialização moderna |
| Menos integração | Maior integração com serviços e recursos |

---

### ⚠️ Atenção para a prova LPIC-1

Memorize:

**`systemd`**
→ sistema de inicialização e gerenciamento de serviços.

**PID 1**
→ normalmente `systemd` em sistemas modernos.

**`systemctl`**
→ administra unidades e serviços.

**`start`**
→ iniciar agora.

**`stop`**
→ parar agora.

**`restart`**
→ reiniciar.

**`enable`**
→ habilitar para inicialização automática.

**`disable`**
→ desabilitar inicialização automática.

**`status`**
→ consultar estado.

**`target`**
→ agrupa unidades e representa um estado do sistema.

**`journalctl`**
→ consultar logs do journal.

**`systemd-analyze`**
→ analisar o processo de boot.

### Resumo

    systemd
       │
       ├── systemctl
       │     ├── start
       │     ├── stop
       │     ├── restart
       │     ├── enable
       │     └── status
       │
       ├── Units
       │     ├── services
       │     ├── targets
       │     ├── timers
       │     └── mounts
       │
       └── journald
             ↓
           Logs

> **Conhecimento só tem valor quando é compartilhado** - Laerte Costa
