# 08 — Memória
## 05 — OOM Killer

### OOM Killer — Out Of Memory Killer (Finalizador por Falta de Memória)

O **OOM Killer** é um mecanismo do kernel Linux usado quando o sistema enfrenta uma situação grave de **falta de memória**.

**OOM** significa:

    Out Of Memory
    → Sem Memória Disponível

Quando a memória disponível fica extremamente baixa e o sistema não consegue atender novas solicitações, o kernel pode escolher um ou mais processos para encerrar e liberar memória.

---

### Por que o OOM Killer existe?

Imagine:

    RAM + Swap
         ↓
    Memória muito pressionada
         ↓
    Sistema não consegue atender
    novas solicitações de memória
         ↓
    OOM Killer
         ↓
    Processo(s) encerrado(s)
         ↓
    Memória liberada

O objetivo é tentar manter o sistema funcionando.

---

### OOM não significa simplesmente "RAM cheia"

O kernel considera diversos fatores ao avaliar a pressão de memória.

Por isso:

    RAM cheia ≠ necessariamente OOM

Linux utiliza RAM livre para cache e buffers. Uma grande quantidade de memória marcada como `used` não significa automaticamente que existe um problema.

O problema ocorre quando o sistema **não consegue satisfazer as necessidades de memória** adequadamente.

---

### Qual processo é escolhido?

O kernel calcula uma pontuação chamada:

    oom_score

Quanto maior a pontuação, maior a tendência de o processo ser escolhido pelo OOM Killer.

Consultar:

    cat /proc/PID/oom_score

Exemplo:

    cat /proc/1250/oom_score

Resultado:

    350

---

### oom_score_adj — Ajuste da Pontuação

Existe também:

    /proc/PID/oom_score_adj

Consultar:

    cat /proc/1250/oom_score_adj

O valor permite ajustar a preferência do kernel para selecionar determinado processo em uma situação de OOM.

Faixa típica:

    -1000 → proteção máxima contra OOM
     0    → padrão
    +1000 → maior preferência para ser finalizado

⚠️ Alterar esse valor normalmente exige privilégios adequados.

---

### Identificando um OOM Killer

Mensagens do OOM Killer podem aparecer nos logs do kernel.

Use:

    dmesg | grep -i "out of memory"

ou:

    dmesg | grep -i "killed process"

- `grep` — search (pesquisar)
- `-i` — ignore case (ignorar maiúsculas/minúsculas)
- `|` — pipe (encaminhar a saída)

Em sistemas que utilizam o `journalctl`:

    journalctl -k | grep -i "out of memory"

- `-k` — kernel (mostrar mensagens do kernel)

---

### Exemplo de mensagem

Uma mensagem de log pode indicar algo semelhante a:

    Out of memory: Killed process 1250 (programa)

Isso significa que o kernel detectou uma condição de falta de memória e encerrou o processo indicado para tentar liberar recursos.

---

### OOM Killer × kill

Não confunda:

    kill PID

com:

    OOM Killer

**`kill`**
→ usuário ou processo envia um sinal para outro processo.

**OOM Killer**
→ mecanismo do kernel usado em condições de falta grave de memória.

---

### Como reduzir o risco de OOM?

Algumas medidas:

- adicionar mais RAM;
- configurar Swap adequadamente;
- identificar processos que consomem muita memória;
- corrigir vazamentos de memória;
- limitar recursos de serviços quando apropriado;
- monitorar o uso de memória.

Para observar rapidamente:

    free -h

Para acompanhar processos:

    top

Ou:

    htop

---

### ⚠️ Atenção para a prova LPIC-1

Memorize:

**OOM**
→ Out Of Memory — falta de memória.

**OOM Killer**
→ mecanismo do kernel que pode encerrar processos para liberar memória em uma situação crítica.

**`oom_score`**
→ pontuação usada para ajudar a determinar quais processos são candidatos ao OOM.

**`oom_score_adj`**
→ permite ajustar a preferência de seleção.

**`/proc/PID/oom_score`**
→ mostra a pontuação de um processo.

**`dmesg` / `journalctl -k`**
→ podem revelar mensagens relacionadas ao OOM Killer.

### Resumo

    Memória insuficiente
           ↓
    Pressão extrema de memória
           ↓
       OOM Killer
           ↓
    seleciona processo(s)
           ↓
       processo encerrado
           ↓
     memória liberada

> **Conhecimento só tem valor quando é compartilhado** - Laerte Costa
