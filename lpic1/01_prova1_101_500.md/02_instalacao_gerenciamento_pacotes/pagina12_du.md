# 📖 HQ 2 — INSTALAÇÃO DO LINUX E GERENCIAMENTO DE PACOTES

# 📖 PÁGINA 12 — DU

# 🧠 1. O QUE É `du`?

`du` é utilizado para mostrar **quanto espaço arquivos e diretórios estão ocupando no disco**.

### Tradução

**du = disk usage**

→ **uso do disco**

A ideia principal é:

```text
df
→ quanto espaço existe/está disponível no filesystem

du
→ quanto espaço arquivos e diretórios estão ocupando
```

---

# 📁 2. `du` BÁSICO

Comando:

```bash
du
```

Mostra o uso de disco dos diretórios a partir do diretório atual.

Exemplo:

```text
4       ./Documentos
120     ./Downloads
500     ./Projetos
```

Os valores normalmente são apresentados em **KiB** por padrão.

---

# 👀 3. `du -h`

Comando:

```bash
du -h
```

### `-h`

→ **human-readable**

→ **legível para humanos**

Em vez de:

```text
10240
```

podemos obter algo como:

```text
10M
```

ou:

```text
2.5G
```

---

# 📊 4. `du -s`

Comando:

```bash
du -s /home
```

### `-s`

→ **summarize**

→ **resumir**

Mostra apenas o total do diretório informado.

Sem `-s`, o `du` pode mostrar vários subdiretórios.

Com `-s`:

```text
/home
↓
TOTAL
```

---

# ⭐ 5. `du -sh`

Uma combinação muito importante:

```bash
du -sh /home
```

### `-s`

→ **summarize → resumir**

### `-h`

→ **human-readable → legível para humanos**

Resultado:

```text
15G     /home
```

Interpretação:

```text
/home
→ está utilizando aproximadamente 15 GB
```

---

# 📂 6. DESCOBRINDO O QUE ESTÁ OCUPANDO ESPAÇO

Podemos executar:

```bash
du -h /home
```

Isso mostra o uso dos diretórios dentro de `/home`.

Exemplo:

```text
500M    /home/laerte/Documentos
2.0G    /home/laerte/Downloads
8.0G    /home/laerte/Projetos
11G     /home/laerte
```

Assim podemos identificar quais diretórios estão ocupando mais espaço.

---

# 🔝 7. `du` COMBINADO COM `sort`

Podemos ordenar os resultados:

```bash
du -h /home | sort -h
```

### `sort`

→ **ordenar**

### `-h`

→ **human-readable → valores legíveis**

Isso permite visualizar os diretórios em ordem de tamanho.

---

# 📏 8. `du -sh *`

Comando:

```bash
du -sh *
```

Mostra o tamanho de cada arquivo/diretório existente no diretório atual.

Exemplo:

```text
500M    Documentos
2.0G    Downloads
8.0G    Projetos
```

É um comando muito útil para descobrir rapidamente onde o espaço está sendo utilizado.

---

# 🧠 9. `du` x `df`

Essa diferença é muito importante para a prova.

### `df`

```text
df
↓
DISK FREE
↓
ESPAÇO DO SISTEMA DE ARQUIVOS
```

Mostra:

- Espaço total
- Espaço utilizado
- Espaço disponível
- Percentual utilizado

---

### `du`

```text
du
↓
DISK USAGE
↓
USO DOS ARQUIVOS E DIRETÓRIOS
```

Mostra quanto espaço arquivos e diretórios estão ocupando.

---

# ⚖️ 10. EXEMPLO PRÁTICO

Imagine:

```text
/dev/sda1
→ 100 GB

Usado
→ 80 GB

Disponível
→ 20 GB
```

O:

```bash
df -h
```

mostra a situação do sistema de arquivos.

Já:

```bash
du -sh /home
```

pode mostrar:

```text
50G    /home
```

Ou seja:

```text
df
→ visão do filesystem

du
→ visão dos arquivos/diretórios
```

---

# 📝 11. COMANDOS NECESSÁRIOS

### Mostrar uso de disco

```bash
du
```

→ mostra o uso de disco dos diretórios.

---

### Formato legível

```bash
du -h
```

**-h = human-readable → legível para humanos**

---

### Mostrar somente o total

```bash
du -s /home
```

**-s = summarize → resumir**

---

### Total em formato legível

```bash
du -sh /home
```

**-s = summarize → resumir**

**-h = human-readable → legível para humanos**

---

### Ver tamanho dos itens do diretório atual

```bash
du -sh *
```

→ mostra o tamanho de cada item.

---

### Ordenar resultados

```bash
du -h /home | sort -h
```

**sort = ordenar**

**-h = human-readable → valores legíveis**

---

# 🎯 12. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que faz `du`.
- Que `du` significa **disk usage**.
- Que `du` mostra o espaço utilizado por arquivos e diretórios.
- Usar `du`.
- Usar `du -h`.
- Saber que `-h` significa **human-readable**.
- Usar `du -s`.
- Saber que `-s` significa **summarize**.
- Usar `du -sh`.
- Saber diferenciar `du` de `df`.
- Entender que `df` trabalha com a visão do sistema de arquivos.
- Entender que `du` trabalha com a utilização de arquivos e diretórios.
- Saber usar `du` para descobrir o que está ocupando espaço.

---

# 🧠 RESUMO

```text
du
↓
DISK USAGE
↓
USO DO DISCO
↓
ARQUIVOS + DIRETÓRIOS
```

### Principais opções:

```text
-h
→ human-readable
→ legível para humanos

-s
→ summarize
→ mostrar somente o total
```

---

# 🔑 COMANDO PRINCIPAL

```bash
du -sh /home
```

Interpretação:

```text
du
→ uso do disco

-s
→ mostrar somente o total

-h
→ formato legível

/home
→ diretório analisado
```

Resultado:

```text
15G    /home
```

→ `/home` está utilizando aproximadamente **15 GB**.

---

# ⚖️ PARA NÃO CONFUNDIR

```text
df
→ DISK FREE
→ espaço disponível/utilizado no filesystem
```

```text
du
→ DISK USAGE
→ espaço utilizado por arquivos e diretórios
```

# 🎯 PARA MEMORIZAR

```bash
df -h
```

→ **Quanto espaço o filesystem tem/usa?**

```bash
du -sh /home
```

→ **Quanto espaço o /home está ocupando?**

```bash
du -sh *
```

→ **Quanto cada item do diretório atual está ocupando?**

# ✅ FIM DA PÁGINA 12
