# Boot e Inicialização

## 06 — Units e Targets

### 1. Units — Unidades

**Unit — Unidade**

No `systemd`, uma **unit** é um recurso que o sistema pode gerenciar.

Cada unidade possui um tipo, identificado normalmente pela extensão do arquivo.

Exemplo:

    ssh.service

    graphical.target

    backup.timer

---

### 2. Principais tipos de Units

| Unit | Inglês | Português | Função |
|---|---|---|---|
| `.service` | Service | Serviço | Gerencia serviços e processos |
| `.target` | Target | Alvo/Estado | Agrupa unidades |
| `.socket` | Socket | Socket | Comunicação entre processos |
| `.mount` | Mount | Montagem | Gerencia pontos de montagem |
| `.automount` | Automount | Montagem Automática | Monta sob demanda |
| `.timer` | Timer | Temporizador | Executa unidades em horários definidos |
| `.path` | Path | Caminho | Monitora alterações em caminhos |
| `.device` | Device | Dispositivo | Representa dispositivos do sistema |

Para o LPIC-1, dê atenção principalmente a:

    .service
    .target
    .mount
    .timer
    .socket

---

### 3. Service

**Service — Serviço**

Representa um serviço ou processo gerenciado pelo `systemd`.

Exemplo:

    ssh.service

Consultar:

    systemctl status ssh.service

O `.service` pode ser omitido:

    systemctl status ssh

---

### 4. Target

**Target — Alvo/Estado do Sistema**

Um `target` agrupa outras unidades e representa um determinado estado do sistema.

Exemplo:

    graphical.target

Pode reunir:

    serviços
    sockets
    mounts
    outros targets

---

### 5. Targets comuns

| Target | Função |
|---|---|
| `multi-user.target` | Sistema multiusuário, normalmente sem login gráfico |
| `graphical.target` | Sistema multiusuário com interface gráfica |
| `rescue.target` | Modo de recuperação |
| `emergency.target` | Ambiente mínimo de emergência |
| `reboot.target` | Reinicialização |
| `poweroff.target` | Desligamento |

---

### 6. Target padrão

Ver o target padrão:

    systemctl get-default

Exemplo:

    graphical.target

Alterar para modo multiusuário:

    sudo systemctl set-default multi-user.target

Alterar para interface gráfica:

    sudo systemctl set-default graphical.target

---

### 7. Targets possuem dependências

Um target pode depender de várias unidades.

Exemplo simplificado:

    graphical.target
          ↓
    multi-user.target
          ↓
       serviços
          ↓
       sockets
          ↓
       mounts

O `systemd` utiliza essas relações para determinar o que precisa ser iniciado.

---

### 8. Ver unidades ativas

    systemctl list-units

Somente serviços:

    systemctl list-units --type=service

Somente targets:

    systemctl list-units --type=target

---

### 9. Ver arquivos de Units

    systemctl list-unit-files

Somente serviços:

    systemctl list-unit-files --type=service

Somente targets:

    systemctl list-unit-files --type=target

Diferença:

    list-units
    → unidades carregadas/ativas no momento

    list-unit-files
    → arquivos de unidades instalados e seus estados

---

### 10. Ver dependências

Para descobrir o que um target inicia ou depende:

    systemctl list-dependencies graphical.target

**list-dependencies — Listar Dependências**

Também podemos consultar um serviço:

    systemctl list-dependencies ssh.service

---

### 11. Iniciar um Target

Um target pode ser ativado:

    sudo systemctl start multi-user.target

Ou:

    sudo systemctl isolate multi-user.target

**isolate — Isolar**

O `isolate` ativa o target e encerra unidades que não são necessárias para o novo estado, conforme as dependências e configurações.

> Use `isolate` com cuidado, principalmente em sistemas em produção.

---

### 12. Mount Unit

**Mount Unit — Unidade de Montagem**

O `systemd` também pode gerenciar pontos de montagem.

Exemplo:

    home.mount

O nome da unit é relacionado ao caminho de montagem.

Exemplo:

    /home

pode ser representado por:

    home.mount

---

### 13. Timer Unit

**Timer — Temporizador**

Uma `.timer` pode iniciar outra unidade, geralmente uma `.service`, em determinado momento ou intervalo.

Exemplo:

    backup.timer
          ↓
    backup.service

Ver timers:

    systemctl list-timers

---

### 14. Socket Unit

**Socket — Socket**

Uma `.socket` representa um mecanismo de comunicação entre processos e pode trabalhar junto com um `.service`.

Exemplo:

    exemplo.socket
          ↓
    exemplo.service

Isso permite que determinados serviços sejam iniciados sob demanda quando uma comunicação chega ao socket.

---

### 15. Relação entre Units e Targets

    systemd
       │
       ├── service
       ├── socket
       ├── mount
       ├── timer
       └── target
              │
              ├── service
              ├── mount
              └── socket

**Unit** é o conceito geral.

**Target** é um tipo de unit usado principalmente para agrupar unidades e representar um estado desejado do sistema.

---

## Resumo LPIC-1

- **Unit — Unidade** → recurso gerenciado pelo `systemd`.
- `.service` → serviços.
- `.target` → estados/grupos de unidades.
- `.mount` → pontos de montagem.
- `.timer` → temporizadores.
- `.socket` → sockets.
- `systemctl list-units` → unidades carregadas.
- `systemctl list-unit-files` → arquivos de unidades instalados.
- `systemctl list-dependencies` → mostra dependências.
- `systemctl get-default` → mostra o target padrão.
- `systemctl set-default` → define o target padrão.
- `multi-user.target` → modo multiusuário.
- `graphical.target` → modo gráfico.
- `rescue.target` → modo de recuperação.
- `emergency.target` → modo mínimo de emergência.

### Conceito principal

    Unit
      ↓
    recurso gerenciado pelo systemd

    Target
      ↓
    Unit que representa um estado
    e agrupa outras Units

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
