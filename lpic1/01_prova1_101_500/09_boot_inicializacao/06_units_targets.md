# 09 — Boot e Inicialização
## 06 — Units e Targets

### 1. Unit — Unidade

**Unit** — Unidade é um recurso que o `systemd` consegue gerenciar.

Cada tipo de recurso possui uma extensão diferente.

Exemplos:

| Unit | Significado | Português |
|---|---|---|
| `.service` | Service | Serviço |
| `.socket` | Socket | Soquete |
| `.target` | Target | Alvo/estado |
| `.mount` | Mount | Ponto de montagem |
| `.timer` | Timer | Temporizador |
| `.path` | Path | Caminho |
| `.device` | Device | Dispositivo |

Exemplo:

    ssh.service

É uma **unit do tipo service**.

---

## 2. Service Unit

**Service** — Serviço

Representa um programa ou serviço gerenciado pelo `systemd`.

Exemplos:

    ssh.service
    cron.service
    NetworkManager.service

Consultar:

    systemctl status ssh.service

Também é possível omitir `.service`:

    systemctl status ssh

---

## 3. Target Unit

**Target** — Alvo/estado

Um target agrupa outras units para representar determinado estado do sistema.

Exemplos:

    multi-user.target
    graphical.target
    rescue.target
    emergency.target

Pense no target como um **ponto de organização do sistema**.

---

## 4. Principais Targets

### multi-user.target

**Multi-user** — Multiusuário

Representa um sistema em modo multiusuário, normalmente sem interface gráfica.

Aproxima-se do antigo:

    Runlevel 3

---

### graphical.target

**Graphical** — Gráfico

Representa o modo gráfico.

Normalmente inclui:

    multi-user.target
           ↓
    graphical.target

Aproxima-se do antigo:

    Runlevel 5

---

### rescue.target

**Rescue** — Recuperação

Modo de recuperação para manutenção do sistema.

Pode ser usado para solucionar problemas sem iniciar todos os serviços normais.

---

### emergency.target

**Emergency** — Emergência

Modo mínimo de emergência.

É ainda mais básico que `rescue.target`.

---

## 5. Ver o target padrão

    systemctl get-default

Exemplo:

    graphical.target

Isso indica o target usado como padrão durante a inicialização.

---

## 6. Alterar o target padrão

Para iniciar normalmente em modo texto:

    sudo systemctl set-default multi-user.target

Para iniciar normalmente em modo gráfico:

    sudo systemctl set-default graphical.target

### Atenção

`set-default` altera o **padrão para os próximos boots**.

Ele não significa simplesmente "mudar imediatamente para esse modo".

---

## 7. Ativar um target imediatamente

**isolate** — isolar/ativar um target

    sudo systemctl isolate multi-user.target

Isso muda o estado atual do sistema para o target especificado.

⚠️ Pode parar serviços que não fazem parte das dependências desse target.

---

## 8. Ver as Units

Listar units carregadas:

    systemctl list-units

Listar somente serviços:

    systemctl list-units --type=service

Listar somente targets:

    systemctl list-units --type=target

---

## 9. Ver arquivos de Units

    systemctl list-unit-files

Somente serviços:

    systemctl list-unit-files --type=service

Somente targets:

    systemctl list-unit-files --type=target

### Diferença importante

**list-units**

→ mostra units atualmente carregadas/ativas no contexto do `systemd`.

**list-unit-files**

→ mostra os arquivos de configuração de units instalados e seus estados.

---

## 10. Ver dependências

Para visualizar as dependências de um target:

    systemctl list-dependencies graphical.target

Exemplo simplificado:

    graphical.target
    ├── multi-user.target
    ├── network.target
    └── display-manager.service

Isso ajuda a entender como o `systemd` organiza a inicialização.

---

## 11. Unit Files

Os arquivos de configuração das units normalmente possuem extensões como:

    .service
    .socket
    .target
    .mount
    .timer

Exemplo:

    /usr/lib/systemd/system/ssh.service

ou, dependendo da distribuição:

    /lib/systemd/system/ssh.service

Configurações administrativas locais geralmente ficam em:

    /etc/systemd/system/

---

# 🔑 Resumo LPIC-1

### Unit

É um recurso gerenciado pelo `systemd`.

### Service

Representa um serviço:

    ssh.service

### Target

Agrupa units e representa um estado do sistema:

    multi-user.target
    graphical.target

### Comandos essenciais

    systemctl get-default

→ Ver target padrão.

    sudo systemctl set-default graphical.target

→ Definir target gráfico como padrão.

    sudo systemctl isolate multi-user.target

→ Mudar imediatamente para o target.

    systemctl list-units --type=service

→ Listar serviços carregados.

    systemctl list-units --type=target

→ Listar targets carregados.

    systemctl list-dependencies graphical.target

→ Ver dependências.

---

## 🧠 Para decorar

**Unit** → recurso gerenciado

**Service** → serviço

**Target** → grupo/estado

**multi-user.target** → modo texto/multiusuário

**graphical.target** → modo gráfico

**rescue.target** → recuperação

**emergency.target** → emergência

**get-default** → descobrir padrão

**set-default** → definir padrão

**isolate** → mudar imediatamente

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
