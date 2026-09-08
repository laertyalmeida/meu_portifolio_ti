# 07 — Processos
## 04 — top e htop

### top — Process Viewer (Visualizador de Processos)

O `top` mostra os processos **em tempo real**, permitindo acompanhar CPU, memória e outros recursos.

    top

A tela é atualizada continuamente.

Para sair:

    q

---

### Informações principais do top

Na parte superior, encontramos informações gerais do sistema:

- **load average** — carga média do sistema
- **Tasks** — quantidade de processos
- **%Cpu(s)** — uso da CPU
- **MiB Mem** — uso da memória RAM
- **MiB Swap** — uso da memória swap

Na lista de processos:

| Campo | Inglês | Português |
|---|---|---|
| PID | Process ID | ID do processo |
| USER | User | Usuário |
| PR | Priority | Prioridade |
| NI | Nice | Valor de ajuste de prioridade |
| VIRT | Virtual Memory | Memória virtual |
| RES | Resident Memory | Memória residente |
| SHR | Shared Memory | Memória compartilhada |
| S | State | Estado |
| %CPU | CPU Usage | Uso da CPU |
| %MEM | Memory Usage | Uso da memória |
| TIME+ | CPU Time | Tempo de CPU |
| COMMAND | Command | Comando |

---

### Teclas importantes do top

Enquanto o `top` está aberto:

| Tecla | Função |
|---|---|
| `q` | Quit — sair |
| `h` | Help — ajuda |
| `k` | Kill — enviar sinal para um processo |
| `r` | Renice — alterar prioridade |
| `P` | ordenar por CPU |
| `M` | ordenar por memória |
| `T` | ordenar por tempo de CPU |
| `1` | mostrar CPUs individualmente |

Exemplo:

    top

Pressione:

    P

Os processos serão ordenados pelo uso de CPU.

---

### top -p — Monitorar um PID

É possível acompanhar um processo específico:

    top -p 1250

- `-p` — PID (monitorar pelo ID do processo)

---

# htop — Interactive Process Viewer (Visualizador Interativo de Processos)

O `htop` é uma alternativa mais amigável ao `top`.

    htop

Ele apresenta uma interface interativa que facilita:

- visualizar processos;
- ordenar processos;
- identificar consumo de CPU;
- identificar consumo de memória;
- enviar sinais;
- navegar pela lista.

> O `htop` pode não estar instalado por padrão em algumas distribuições.

---

### Comandos e teclas importantes do htop

| Tecla | Função |
|---|---|
| `F1` | Help — ajuda |
| `F2` | Setup — configuração |
| `F3` | Search — pesquisar |
| `F4` | Filter — filtrar |
| `F5` | Tree — árvore de processos |
| `F6` | Sort — ordenar |
| `F9` | Kill — enviar sinal |
| `F10` | Quit — sair |

Também é possível usar o mouse para navegar na interface.

---

### top × htop

| Recurso | `top` | `htop` |
|---|---|---|
| Monitoramento em tempo real | ✅ | ✅ |
| CPU | ✅ | ✅ |
| Memória | ✅ | ✅ |
| Processos | ✅ | ✅ |
| Interface interativa | ✅ | ✅ |
| Árvore de processos | `--forest` | `F5` |
| Interface mais amigável | Básica | Mais amigável |
| Disponibilidade padrão | Muito comum | Nem sempre instalado |

---

### ⚠️ Atenção para a prova LPIC-1

**`ps`**
→ mostra uma fotografia dos processos naquele momento.

**`top`**
→ monitora processos continuamente e atualiza a tela.

**`htop`**
→ alternativa interativa ao `top`, geralmente mais fácil de visualizar.

Memorize:

    ps      → consultar processos
    top     → monitorar processos em tempo real
    htop    → monitorar processos com interface interativa

> **Conhecimento só tem valor quando é compartilhado** - Laerte Costa
