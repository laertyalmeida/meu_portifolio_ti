# Processos

## 04 — top e htop

### top — Process Monitor — Monitor de Processos

O `top` mostra os processos em execução **em tempo real**.

    top

Ele permite acompanhar:

- CPU — Processador
- Memory — Memória
- Load Average — Média de Carga
- PID — ID do Processo
- usuário
- estado do processo
- tempo de CPU
- comando

---

## Principais informações do top

Na parte superior:

    load average: 0.20, 0.15, 0.10

Representa a **Load Average — Média de Carga** do sistema:

    1 minuto | 5 minutos | 15 minutos

Abaixo aparecem os processos.

Exemplo simplificado:

    PID    USER     %CPU  %MEM   COMMAND
    1520   laerte   35.0   2.1   firefox
    1600   root      8.0   1.0   systemd

---

## Teclas importantes do top

Enquanto o `top` está aberto:

| Tecla | English | Português |
|---|---|---|
| `q` | Quit | Sair |
| `h` | Help | Ajuda |
| `k` | Kill | Enviar sinal ao processo |
| `r` | Renice | Alterar prioridade |
| `P` | CPU | Ordenar por uso de CPU |
| `M` | Memory | Ordenar por uso de memória |
| `1` | CPUs | Mostrar CPUs individualmente |
| `Space` | Refresh | Atualizar imediatamente |

Para sair:

    q

---

# htop — Interactive Process Viewer — Visualizador Interativo de Processos

O `htop` é uma alternativa mais interativa ao `top`.

    htop

Normalmente apresenta uma interface mais fácil de visualizar e navegar.

Pode mostrar:

- uso de CPU;
- uso de memória;
- uso de Swap;
- processos;
- PID;
- usuário;
- prioridade;
- consumo de CPU;
- consumo de memória.

---

## Navegação no htop

O `htop` permite usar o teclado para selecionar processos.

Algumas teclas comuns:

| Tecla | English | Português |
|---|---|---|
| `F1` | Help | Ajuda |
| `F2` | Setup | Configuração |
| `F3` | Search | Pesquisar |
| `F4` | Filter | Filtrar |
| `F5` | Tree | Árvore |
| `F6` | Sort | Ordenar |
| `F9` | Kill | Enviar sinal |
| `F10` | Quit | Sair |

Também é possível selecionar um processo e utilizar:

    F9

para escolher um sinal a ser enviado ao processo.

---

## top × htop

| `top` | `htop` |
|---|---|
| Geralmente disponível por padrão | Pode precisar ser instalado |
| Interface baseada em terminal | Interface mais interativa |
| Controle principalmente por teclas | Teclas e navegação mais amigáveis |
| Mostra processos em tempo real | Mostra processos em tempo real |
| Pode enviar sinais | Pode enviar sinais |
| Pode alterar prioridade | Pode alterar prioridade |

---

## CPU e Memória

Tanto `top` quanto `htop` ajudam a identificar processos que estão consumindo muitos recursos.

Exemplo:

    %CPU → percentual de CPU utilizado
    %MEM → percentual de memória utilizado

Um processo com alto `%CPU` pode estar utilizando bastante processamento.

Um processo com alto `%MEM` pode estar utilizando bastante memória RAM.

---

## Encerrar um processo

No `top`:

    k

Depois informe o PID do processo.

No `htop`:

    F9

Essas ações enviam um **Signal — Sinal** ao processo.

O estudo detalhado de sinais e `kill` será feito em uma página específica.

---

## Resumo LPIC-1

- `top` → **Process Monitor — Monitor de Processos**.
- `top` → monitora processos em tempo real.
- `htop` → **Interactive Process Viewer — Visualizador Interativo de Processos**.
- `htop` → alternativa mais interativa ao `top`.
- `%CPU` → uso de CPU pelo processo.
- `%MEM` → uso de memória pelo processo.
- `P` no `top` → ordenar por CPU.
- `M` no `top` → ordenar por memória.
- `k` no `top` → enviar sinal a um processo.
- `F9` no `htop` → enviar sinal.
- `q` no `top` → sair.
- `F10` no `htop` → sair.
- `Load Average` → média de carga do sistema em 1, 5 e 15 minutos.

**Conhecimento só tem valor quando é compartilhado** - Laerte Costa
