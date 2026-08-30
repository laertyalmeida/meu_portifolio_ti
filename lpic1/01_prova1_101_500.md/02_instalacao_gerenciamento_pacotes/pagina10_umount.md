# 📖 HQ 2 — INSTALAÇÃO DO LINUX E GERENCIAMENTO DE PACOTES

# 📖 PÁGINA 10 — UMOUNT

# 🧠 1. O QUE É `umount`?

`umount` é o comando utilizado para **desmontar um sistema de arquivos**.

Desmontar significa remover a associação entre um sistema de arquivos e seu ponto de montagem.

```text
MONTADO

/dev/sda1
    ↓
   /mnt
```

Depois:

```bash
sudo umount /mnt
```

```text
/dev/sda1
    X
   /mnt
```

O sistema de arquivos deixa de estar acessível através daquele ponto de montagem.

---

# 🔤 2. TRADUÇÃO

```text
mount
→ montar

unmount
→ desmontar

umount
→ comando Linux para "unmount"
```

⚠️ O comando é:

```bash
umount
```

e não:

```bash
unmount
```

---

# 📂 3. DESMONTAR PELO PONTO DE MONTAGEM

Exemplo:

```bash
sudo umount /mnt
```

Interpretação:

```text
umount
→ desmontar

/mnt
→ ponto de montagem
```

O sistema de arquivos montado em `/mnt` será desmontado.

---

# 💽 4. DESMONTAR PELO DISPOSITIVO

Também podemos informar o dispositivo:

```bash
sudo umount /dev/sda1
```

Assim, o Linux desmontará o sistema de arquivos associado a esse dispositivo.

Podemos usar:

```text
/mnt
```

ou:

```text
/dev/sda1
```

dependendo da situação.

---

# 🚫 5. QUANDO O `umount` NÃO FUNCIONA?

Um erro comum é:

```text
target is busy
```

Tradução:

**o destino está ocupado.**

Isso geralmente significa que algum processo ainda está utilizando o sistema de arquivos.

Exemplo:

```text
/dev/sda1
   ↓
/mnt
   ↓
algum processo está usando arquivos
```

Enquanto o sistema de arquivos estiver em uso, a desmontagem normal pode falhar.

---

# 📍 6. DIRETÓRIO ATUAL

Um motivo comum para `umount` falhar é o terminal estar dentro do ponto de montagem.

Exemplo:

```bash
cd /mnt
```

Agora estamos dentro de:

```text
/mnt
```

Se tentarmos:

```bash
sudo umount /mnt
```

podemos receber:

```text
target is busy
```

Devemos sair do diretório:

```bash
cd /
```

e então tentar novamente:

```bash
sudo umount /mnt
```

---

# 🔍 7. DESCOBRIR QUEM ESTÁ USANDO

Podemos utilizar:

```bash
lsof /mnt
```

### Tradução

**lsof = list open files**

→ listar arquivos abertos.

Isso ajuda a descobrir quais processos estão utilizando arquivos dentro de `/mnt`.

---

# 🔎 8. `fuser`

Outro comando importante:

```bash
fuser -m /mnt
```

### Tradução

**fuser**

→ identifica processos que estão utilizando um arquivo ou sistema de arquivos.

### `-m`

→ **mount point → ponto de montagem**

Nesse contexto:

```bash
fuser -m /mnt
```

→ mostra processos utilizando o sistema de arquivos montado em `/mnt`.

---

# ⚠️ 9. `umount -l`

Existe a opção:

```bash
sudo umount -l /mnt
```

### `-l`

→ **lazy → preguiçoso**

É uma **lazy unmount**.

O sistema de arquivos é separado da árvore de arquivos imediatamente, mas a limpeza efetiva ocorre quando ele deixa de estar ocupado.

Para a prova, basta reconhecer:

```text
-l
→ lazy → desmontagem "preguiçosa"
```

---

# ⚠️ 10. CUIDADO COM `umount -f`

Existe também:

```bash
sudo umount -f /mnt
```

### `-f`

→ **force → forçar**

Solicita uma desmontagem forçada.

Essa opção é especialmente associada a sistemas de arquivos remotos, como NFS, e não deve ser usada sem entender as consequências.

Para a prova:

```text
-f
→ force → forçar
```

---

# 🧠 11. `umount` NÃO APAGA OS DADOS

Desmontar:

```bash
sudo umount /mnt
```

não significa apagar a partição.

Ele apenas remove a montagem.

```text
umount
→ desmonta

rm
→ remove arquivos

mkfs
→ cria/formata sistema de arquivos
```

São operações completamente diferentes.

---

# 📝 12. COMANDOS NECESSÁRIOS

### Desmontar pelo ponto de montagem

```bash
sudo umount /mnt
```

→ desmonta o sistema de arquivos de `/mnt`.

---

### Desmontar pelo dispositivo

```bash
sudo umount /dev/sda1
```

→ desmonta o sistema de arquivos associado a `/dev/sda1`.

---

### Ver processos usando a montagem

```bash
lsof /mnt
```

**lsof = list open files**

→ lista arquivos abertos e ajuda a identificar processos utilizando `/mnt`.

---

### Identificar processos usando a montagem

```bash
fuser -m /mnt
```

**fuser → identifica processos que utilizam um arquivo/sistema de arquivos**

**-m → mount → ponto de montagem**

---

### Lazy unmount

```bash
sudo umount -l /mnt
```

**-l = lazy → preguiçoso**

→ desmontagem lazy.

---

### Force unmount

```bash
sudo umount -f /mnt
```

**-f = force → forçar**

→ desmontagem forçada.

---

# 🎯 13. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que faz `umount`.
- Que `umount` significa **unmount → desmontar**.
- Que o comando correto é `umount`.
- Desmontar pelo ponto de montagem.
- Desmontar pelo dispositivo.
- Que desmontar não apaga os dados.
- O significado de `target is busy`.
- Por que um sistema de arquivos pode estar ocupado.
- Que o diretório atual pode impedir a desmontagem.
- Usar `lsof`.
- Usar `fuser`.
- Reconhecer `umount -l`.
- Saber que `-l` significa **lazy**.
- Reconhecer `umount -f`.
- Saber que `-f` significa **force**.

---

# 🧠 RESUMO

```text
mount
↓
MONTAR
↓
/dev/sda1 → /mnt
```

```text
umount
↓
DESMONTAR
↓
/dev/sda1 X /mnt
```

### Se aparecer:

```text
target is busy
```

significa:

```text
O SISTEMA DE ARQUIVOS ESTÁ SENDO UTILIZADO
```

Podemos investigar:

```bash
lsof /mnt
```

ou:

```bash
fuser -m /mnt
```

---

# 🔑 PARA MEMORIZAR

```text
mount
→ montar

umount
→ desmontar

lsof
→ list open files
→ listar arquivos abertos

fuser
→ identificar processos usando arquivos/sistemas de arquivos

-l
→ lazy → desmontagem lazy

-f
→ force → forçar
```

# 🎯 COMANDO PRINCIPAL

```bash
sudo umount /mnt
```

**umount → unmount → desmontar**

**Função → desmontar o sistema de arquivos associado ao ponto de montagem `/mnt`.**

# ⚠️ REGRA PRÁTICA

Se aparecer:

```text
target is busy
```

primeiro saia do diretório:

```bash
cd /
```

Depois investigue:

```bash
lsof /mnt
```

ou:

```bash
fuser -m /mnt
```

# ✅ FIM DA PÁGINA 10
