# 09 — Boot e Inicialização
## 05 — systemctl

### O que é o systemctl?

`systemctl` é o principal comando para controlar o **systemd**, o sistema responsável por inicializar o Linux e gerenciar serviços.

Com ele podemos:

- iniciar serviços;
- parar serviços;
- reiniciar serviços;
- consultar status;
- habilitar serviços no boot;
- desabilitar serviços;
- trabalhar com targets;
- consultar unidades com falha.

---

## Comandos principais

### start — iniciar

Inicia um serviço imediatamente.

    sudo systemctl start ssh

**start** — iniciar

---

### stop — parar

Para um serviço imediatamente.

    sudo systemctl stop ssh

**stop** — parar

---

### restart — reiniciar

Para e inicia novamente o serviço.

    sudo systemctl restart ssh

**restart** — reiniciar

---

### reload — recarregar

Recarrega a configuração do serviço sem necessariamente interrompê-lo.

    sudo systemctl reload ssh

**reload** — recarregar

> Nem todo serviço suporta `reload`.

---

### status — estado

Mostra o estado atual do serviço.

    systemctl status ssh

Pode mostrar:

- se está ativo;
- se está parado;
- se falhou;
- PID;
- mensagens recentes do serviço.

---

## enable e disable

### enable — habilitar

Configura o serviço para iniciar automaticamente durante o boot.

    sudo systemctl enable ssh

**enable** — habilitar

⚠️ `enable` normalmente **não inicia o serviço imediatamente**.

---

### disable — desabilitar

Remove a configuração que faz o serviço iniciar automaticamente no boot.

    sudo systemctl disable ssh

**disable** — desabilitar

---

### enable --now

Habilita **e inicia imediatamente**.

    sudo systemctl enable --now ssh

É uma combinação muito útil.

---

## is-enabled

Verifica se o serviço está habilitado para iniciar no boot.

    systemctl is-enabled ssh

Possíveis resultados:

    enabled
    disabled
    static
    masked

---

## is-active

Verifica se o serviço está ativo.

    systemctl is-active ssh

Resultado comum:

    active

---

## Serviços com falha

Para listar unidades que falharam:

    systemctl --failed

Útil para descobrir rapidamente problemas durante a inicialização.

---

## Listar serviços

### list-units

Mostra unidades carregadas atualmente.

    systemctl list-units --type=service

**--type=service** — limitar ao tipo serviço

---

### list-unit-files

Mostra os arquivos de unidades instalados e seu estado de habilitação.

    systemctl list-unit-files --type=service

---

## Targets

O `systemd` utiliza **targets** para representar estados ou grupos de unidades.

Exemplos:

- `multi-user.target` — modo multiusuário, geralmente sem interface gráfica
- `graphical.target` — modo gráfico
- `rescue.target` — modo de recuperação
- `emergency.target` — modo de emergência

Ver o target padrão:

    systemctl get-default

Alterar o target padrão:

    sudo systemctl set-default multi-user.target

Ou:

    sudo systemctl set-default graphical.target

---

## Alterar o estado imediatamente

É possível mudar para um target sem reiniciar:

    sudo systemctl isolate multi-user.target

**isolate** — isolar/ativar somente o target e suas dependências

⚠️ Pode encerrar serviços e sessões que não pertençam ao target.

---

## Reiniciar e desligar

Reiniciar o computador:

    sudo systemctl reboot

Desligar:

    sudo systemctl poweroff

Suspender:

    systemctl suspend

---

## Relação com o processo de boot

A sequência simplificada é:

    Firmware
       ↓
    Bootloader
       ↓
    Kernel
       ↓
    systemd (PID 1)
       ↓
    Targets
       ↓
    Services
       ↓
    Login

O `systemctl` conversa com o `systemd` para controlar essa estrutura.

---

## Comandos essenciais para a LPIC-1

| Comando | Função |
|---|---|
| `systemctl start serviço` | Iniciar |
| `systemctl stop serviço` | Parar |
| `systemctl restart serviço` | Reiniciar |
| `systemctl reload serviço` | Recarregar configuração |
| `systemctl status serviço` | Ver estado |
| `systemctl enable serviço` | Habilitar no boot |
| `systemctl disable serviço` | Desabilitar no boot |
| `systemctl enable --now serviço` | Habilitar e iniciar |
| `systemctl is-active serviço` | Verificar se está ativo |
| `systemctl is-enabled serviço` | Verificar se inicia no boot |
| `systemctl --failed` | Ver unidades com falha |
| `systemctl get-default` | Ver target padrão |
| `systemctl set-default TARGET` | Definir target padrão |
| `systemctl list-units` | Listar unidades |
| `systemctl reboot` | Reiniciar |
| `systemctl poweroff` | Desligar |

---

## 🎯 LPIC-1 — O que memorizar

**start** → inicia agora

**stop** → para agora

**restart** → reinicia agora

**reload** → recarrega configuração

**enable** → inicia automaticamente no boot

**disable** → não inicia automaticamente no boot

**enable --now** → habilita + inicia agora

**status** → mostra o estado

**get-default** → mostra o target padrão

**set-default** → define o target padrão

> ⭐ Pegadinha comum:
>
> `systemctl start ssh` **não significa** que o SSH iniciará automaticamente no próximo boot.
>
> Para isso, use:
>
> `systemctl enable ssh`

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
