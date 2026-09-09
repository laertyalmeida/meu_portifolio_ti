# Boot e Inicialização

## 05 — systemctl

### 1. O que é systemctl?

**systemctl — systemd Control — Controle do systemd**

É o principal comando usado para **consultar e controlar o systemd**.

Com ele podemos:

- iniciar serviços;
- parar serviços;
- reiniciar serviços;
- verificar status;
- habilitar serviços no boot;
- desabilitar serviços;
- consultar unidades;
- controlar targets.

---

### 2. Verificar o status de um serviço

    systemctl status ssh

**status — Status — Estado**

Mostra informações como:

- se o serviço está ativo;
- PID;
- quando foi iniciado;
- últimas mensagens;
- processo principal.

Exemplo:

    Active: active (running)

---

### 3. Iniciar um serviço

    sudo systemctl start ssh

**start — Iniciar**

Inicia o serviço **agora**, mas isso não significa necessariamente que ele será iniciado automaticamente no próximo boot.

---

### 4. Parar um serviço

    sudo systemctl stop ssh

**stop — Parar**

Interrompe o serviço.

---

### 5. Reiniciar um serviço

    sudo systemctl restart ssh

**restart — Reiniciar**

Para e inicia novamente o serviço.

Útil depois de alterações que precisam de uma reinicialização do serviço.

---

### 6. Recarregar a configuração

    sudo systemctl reload ssh

**reload — Recarregar**

Solicita ao serviço que recarregue sua configuração sem necessariamente encerrá-lo.

> Nem todo serviço suporta `reload`.

---

### 7. Habilitar no boot

    sudo systemctl enable ssh

**enable — Habilitar**

Configura o serviço para ser iniciado automaticamente durante o boot, conforme sua unidade e dependências.

---

### 8. Desabilitar no boot

    sudo systemctl disable ssh

**disable — Desabilitar**

Remove a configuração que permite o início automático do serviço no boot.

Isso não significa necessariamente que o serviço será parado imediatamente.

---

### 9. Habilitar e iniciar imediatamente

    sudo systemctl enable --now ssh

`--now` — **Now — Agora**

Faz as duas ações:

    enable + start

Para desabilitar e parar:

    sudo systemctl disable --now ssh

---

### 10. Verificar se está ativo

    systemctl is-active ssh

**is-active — Está Ativo**

Retorna, por exemplo:

    active

---

### 11. Verificar se está habilitado

    systemctl is-enabled ssh

**is-enabled — Está Habilitado**

Pode retornar:

    enabled

Isso responde a uma pergunta diferente:

    is-active  → está rodando agora?
    is-enabled → está configurado para iniciar automaticamente?

---

### 12. Reiniciar o systemd

Para recarregar os arquivos de unidades depois de uma alteração:

    sudo systemctl daemon-reload

**daemon-reload — Recarregar o Gerenciador**

Faz o systemd reler os arquivos de unidades.

> `daemon-reload` **não reinicia os serviços**.

---

### 13. Listar unidades

    systemctl list-units

Lista as unidades atualmente carregadas.

Somente serviços:

    systemctl list-units --type=service

**`--type` — Tipo**

---

### 14. Listar arquivos de unidades

    systemctl list-unit-files

Mostra arquivos de unidades instalados e seu estado, como:

    enabled
    disabled
    static
    masked

Somente serviços:

    systemctl list-unit-files --type=service

---

### 15. Mascarar um serviço

**mask — Mascarar**

Impede que uma unidade seja iniciada normalmente.

    sudo systemctl mask ssh

Para remover a máscara:

    sudo systemctl unmask ssh

**unmask — Desmascarar**

> `mask` é mais forte que `disable`: um serviço desabilitado ainda pode ser iniciado manualmente; uma unidade mascarada fica impedida de iniciar normalmente.

---

### 16. Consultar o target padrão

    systemctl get-default

Exemplo:

    graphical.target

Alterar:

    sudo systemctl set-default multi-user.target

**set-default — Definir Padrão**

---

### 17. systemctl no diagnóstico

Comandos importantes:

    systemctl status

    systemctl --failed

    systemctl list-units --failed

`--failed` — **Failed — Falhou**

Para descobrir serviços que falharam durante a inicialização.

---

### 18. Comandos essenciais

| Comando | Função |
|---|---|
| `systemctl status serviço` | Ver estado |
| `systemctl start serviço` | Iniciar |
| `systemctl stop serviço` | Parar |
| `systemctl restart serviço` | Reiniciar |
| `systemctl reload serviço` | Recarregar configuração |
| `systemctl enable serviço` | Habilitar no boot |
| `systemctl disable serviço` | Desabilitar no boot |
| `systemctl is-active serviço` | Verificar se está ativo |
| `systemctl is-enabled serviço` | Verificar se está habilitado |
| `systemctl daemon-reload` | Recarregar arquivos de unidades |
| `systemctl --failed` | Ver unidades com falha |
| `systemctl get-default` | Ver target padrão |
| `systemctl set-default TARGET` | Definir target padrão |

---

## Resumo LPIC-1

- `systemctl` → principal comando de controle do **systemd**.
- `status` → consultar estado.
- `start` → iniciar.
- `stop` → parar.
- `restart` → reiniciar.
- `reload` → recarregar configuração do serviço.
- `enable` → iniciar automaticamente no boot.
- `disable` → não iniciar automaticamente no boot.
- `enable --now` → habilitar e iniciar imediatamente.
- `is-active` → verificar se está ativo.
- `is-enabled` → verificar se está habilitado.
- `daemon-reload` → fazer o systemd reler arquivos de unidades.
- `mask` → impedir o início normal de uma unidade.
- `unmask` → remover o bloqueio.
- `--failed` → mostrar unidades que falharam.
- `get-default` → mostrar o target padrão.

### Diferença fundamental

    start
    → inicia agora

    enable
    → configura para iniciar no boot

    enable --now
    → inicia agora + configura para o boot

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
