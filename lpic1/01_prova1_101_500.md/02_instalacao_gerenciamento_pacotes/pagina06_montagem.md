# 📖 HQ 2 — INSTALAÇÃO DO LINUX E GERENCIAMENTO DE PACOTES

# 📖 PÁGINA 6 — MONTAGEM

# 🧠 1. O QUE É MONTAGEM?

**Montar (mount)** é tornar um sistema de arquivos acessível dentro da árvore de diretórios do Linux.

No Linux, não trabalhamos normalmente com letras de unidade como:

```text
C:
D:
E:
```

Em vez disso, os sistemas de arquivos são conectados à árvore de diretórios.

Exemplo:

```text
/
├── etc
├── home
├── usr
├── var
└── dados
```

Se uma partição for montada em:

```text
/dados
```

ela ficará acessível através desse diretório.

---

# 🔗 2. PARTIÇÃO → MONTAGEM

O processo pode ser entendido assim:

```text
/dev/sda2
    ↓
sistema de arquivos
    ↓
mount
    ↓
/dados
```

Depois da montagem:

```text
/dados
```

passa a dar acesso ao conteúdo da partição.

---

# 📁 3. PONTO DE MONTAGEM

O diretório onde um sistema de arquivos é conectado é chamado de:

**mount point**

Tradução:

**ponto de montagem**

Exemplo:

```text
/dev/sda2
     ↓
   /dados
```

Nesse caso:

```text
/dados
```

é o ponto de montagem.

---

# 🛠️ 4. `mount`

O comando:

```bash
mount
```

é utilizado para montar sistemas de arquivos.

### Tradução

**mount**

→ montar.

---

# 📥 5. MONTANDO UMA PARTIÇÃO

Exemplo:

```bash
sudo mount /dev/sda2 /mnt
```

Interpretação:

```text
/dev/sda2
→ dispositivo/partição

/mnt
→ ponto de montagem

mount
→ conecta a partição ao diretório
```

Depois disso, o conteúdo de `/dev/sda2` estará acessível através de:

```text
/mnt
```

---

# 📂 6. O DIRETÓRIO `/mnt`

`/mnt` é tradicionalmente utilizado como ponto de montagem temporário.

Exemplo:

```bash
sudo mount /dev/sda2 /mnt
```

Isso não significa que toda montagem deve obrigatoriamente utilizar `/mnt`.

Podemos criar outros pontos de montagem, como:

```text
/dados
/backup
/midia
```

---

# 🔍 7. VERIFICANDO MONTAGENS

Executar:

```bash
mount
```

sem argumentos mostra os sistemas de arquivos atualmente montados.

Também podemos utilizar:

```bash
findmnt
```

### Tradução

**find**

→ encontrar.

**mnt**

→ mount → montagem.

Portanto:

**findmnt → encontrar/listar pontos de montagem.**

---

# 🧠 8. `mount -l`

Comando:

```bash
mount -l
```

### `-l`

→ **list → listar**

Mostra os sistemas de arquivos montados, incluindo informações de identificação quando disponíveis.

---

# 📊 9. `df`

O comando:

```bash
df
```

mostra o espaço disponível e utilizado nos sistemas de arquivos montados.

### Tradução

**df = disk filesystem**

→ sistema de arquivos do disco.

Na prática:

**df → mostra o uso de espaço dos sistemas de arquivos.**

---

# 📏 10. `df -h`

Comando:

```bash
df -h
```

### `-h`

→ **human-readable → legível por humanos**

Exemplo:

```text
Filesystem      Size  Used Avail Use%
/dev/sda1       100G   40G   60G  40%
```

Mostra:

- Tamanho total
- Espaço utilizado
- Espaço disponível
- Percentual utilizado

---

# ⛔ 11. `umount`

Para desmontar um sistema de arquivos:

```bash
sudo umount /mnt
```

### Tradução

**umount**

→ **unmount → desmontar**

⚠️ O comando é `umount`, e não `unmount`.

---

# 🔌 12. DESMONTAR PELO DISPOSITIVO

Também podemos desmontar informando o dispositivo:

```bash
sudo umount /dev/sda2
```

Ou pelo ponto de montagem:

```bash
sudo umount /mnt
```

Os dois podem representar a mesma montagem.

---

# 🚫 13. POR QUE UMA DESMONTAGEM PODE FALHAR?

Se algum processo estiver utilizando o sistema de arquivos, a desmontagem pode falhar.

Exemplo:

```text
target is busy
```

Tradução:

**o destino está ocupado.**

Isso significa que algum processo ainda está utilizando aquele sistema de arquivos.

Podemos investigar com:

```bash
lsof /mnt
```

### Tradução

**lsof = list open files**

→ listar arquivos abertos.

---

# 📝 14. COMANDOS NECESSÁRIOS

### Montar

```bash
sudo mount /dev/sda2 /mnt
```

→ monta `/dev/sda2` em `/mnt`.

---

### Listar montagens

```bash
mount
```

→ mostra sistemas de arquivos montados.

---

### Listar montagens

```bash
mount -l
```

**-l = list → listar**

---

### Encontrar pontos de montagem

```bash
findmnt
```

→ **find mount → encontrar/listar montagens.**

---

### Ver espaço utilizado

```bash
df -h
```

**-h = human-readable → legível por humanos**

---

### Desmontar

```bash
sudo umount /mnt
```

→ desmonta o sistema de arquivos de `/mnt`.

---

### Ver processos usando o ponto de montagem

```bash
lsof /mnt
```

**lsof = list open files → listar arquivos abertos**

---

# 🎯 15. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que significa montar um sistema de arquivos.
- O que é um ponto de montagem.
- A relação entre partição, sistema de arquivos e montagem.
- Que o Linux utiliza uma árvore de diretórios.
- Que `/mnt` é tradicionalmente usado para montagens temporárias.
- Usar `mount`.
- Montar uma partição em um diretório.
- Usar `umount`.
- Saber que `umount` significa **unmount**.
- Desmontar pelo dispositivo ou pelo ponto de montagem.
- Usar `findmnt`.
- Usar `df`.
- Usar `df -h`.
- Saber que `-h` significa **human-readable**.
- Entender por que um sistema de arquivos pode não ser desmontado.
- Conhecer `lsof` para identificar processos que estão utilizando arquivos.

---

# 🧠 RESUMO

```text
PARTIÇÃO
   ↓
SISTEMA DE ARQUIVOS
   ↓
MOUNT
   ↓
PONTO DE MONTAGEM
   ↓
ACESSO AOS ARQUIVOS
```

### Montar:

```bash
mount /dev/sda2 /mnt
```

### Desmontar:

```bash
umount /mnt
```

### Ver montagens:

```bash
findmnt
```

### Ver espaço:

```bash
df -h
```

---

# 🔑 PALAVRAS-CHAVE

```text
mount
→ montar

mount point
→ ponto de montagem

umount
→ unmount → desmontar

df
→ disk filesystem → uso de espaço dos sistemas de arquivos

findmnt
→ encontrar/listar montagens

lsof
→ list open files → listar arquivos abertos
```

# 🎯 PARA MEMORIZAR

```text
mount
→ CONECTA

umount
→ DESCONECTA

findmnt
→ MOSTRA MONTAGENS

df -h
→ MOSTRA ESPAÇO

lsof
→ MOSTRA QUEM ESTÁ USANDO
```

# ✅ FIM DA PÁGINA 6
