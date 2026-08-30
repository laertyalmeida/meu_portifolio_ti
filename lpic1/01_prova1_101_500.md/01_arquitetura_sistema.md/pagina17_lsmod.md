# 📖 PÁGINA 17 — LSMOD

# 🧠 1. O QUE É `lsmod`?

`lsmod` é o comando utilizado para **listar os módulos do kernel que estão atualmente carregados**.

### Tradução

`ls`

→ **list → listar**

`mod`

→ **module → módulo**

Portanto:

**lsmod → list modules → listar módulos**

---

# 🔌 2. O QUE É UM MÓDULO CARREGADO?

Um módulo carregado é um módulo que está atualmente disponível dentro do kernel.

Exemplo:

```text
HARDWARE
   ↓
DRIVER
   ↓
MÓDULO
   ↓
KERNEL
```

Se um módulo está carregado, ele pode fornecer determinada funcionalidade ou suporte a um dispositivo.

---

# 🔍 3. USO BÁSICO

Comando:

```bash
lsmod
```

A saída normalmente possui três colunas principais:

```text
Module        Size        Used by
e1000e        ...         ...
snd_hda       ...         ...
usbcore       ...         ...
```

---

# 🧩 4. COLUNA `Module`

**Module**

→ módulo.

Mostra o nome do módulo carregado.

Exemplo:

```text
e1000e
```

É o nome do módulo.

---

# 📏 5. COLUNA `Size`

**Size**

→ tamanho.

Mostra o tamanho do módulo na memória.

Para a prova, o mais importante é reconhecer que:

**Size → tamanho do módulo**

---

# 🔗 6. COLUNA `Used by`

**Used by**

→ utilizado por.

Mostra informações sobre outros componentes/módulos que estão utilizando aquele módulo.

Para a prova:

**Used by → mostra quem utiliza o módulo.**

---

# 🔎 7. PROCURANDO UM MÓDULO

Podemos combinar `lsmod` com `grep`.

Exemplo:

```bash
lsmod | grep e1000e
```

### `|`

**pipe**

→ envia a saída do primeiro comando para o segundo.

### `grep`

→ procurar um padrão.

Portanto:

```bash
lsmod | grep e1000e
```

→ lista os módulos carregados e procura especificamente por `e1000e`.

---

# 🧠 8. `lsmod` NÃO CARREGA MÓDULOS

Uma diferença importante:

```text
lsmod
```

→ **lista** módulos.

Não carrega módulos.

Para carregar:

```bash
modprobe nome_do_modulo
```

Para remover:

```bash
modprobe -r nome_do_modulo
```

---

# ⚖️ 9. LSMOD x MODPROBE

### `lsmod`

**list modules**

→ lista módulos carregados.

### `modprobe`

**module + probe**

→ carrega ou remove módulos.

Resumo:

```text
lsmod
↓
VER módulos

modprobe
↓
GERENCIAR módulos
```

---

# 🔧 10. LSMOD E DRIVERS

Muitos drivers podem funcionar como módulos do kernel.

Podemos ter:

```text
DISPOSITIVO
    ↓
DRIVER
    ↓
MÓDULO DO KERNEL
    ↓
KERNEL
```

Exemplo:

```bash
lsmod | grep e1000e
```

Se aparecer `e1000e`, significa que esse módulo está carregado.

---

# 📂 11. LSMOD E `/proc`

As informações dos módulos também estão relacionadas ao kernel.

Um arquivo tradicional associado aos módulos carregados é:

```text
/proc/modules
```

Podemos consultar:

```bash
cat /proc/modules
```

### Tradução

**cat**

→ **concatenate → exibir/concatenar conteúdo**

**modules**

→ módulos.

O `lsmod` apresenta essas informações de uma forma mais legível.

---

# 📝 12. COMANDOS NECESSÁRIOS

### Listar módulos carregados

```bash
lsmod
```

**ls → list → listar**

**mod → module → módulo**

→ lista os módulos carregados.

---

### Procurar um módulo

```bash
lsmod | grep e1000e
```

**grep → procurar**

→ verifica se `e1000e` está entre os módulos carregados.

---

### Consultar diretamente `/proc/modules`

```bash
cat /proc/modules
```

**cat → concatenate → exibir conteúdo**

→ mostra informações sobre módulos carregados.

---

# 🎯 13. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que significa `lsmod`.
- Que `lsmod` significa **list modules**.
- Que `lsmod` lista módulos carregados.
- Que `lsmod` não carrega módulos.
- Reconhecer as colunas:
  - `Module`
  - `Size`
  - `Used by`
- Saber combinar `lsmod` com `grep`.
- Entender o uso do pipe `|`.
- Saber diferenciar `lsmod` de `modprobe`.
- Conhecer `/proc/modules`.
- Saber que `lsmod` mostra informações sobre módulos atualmente carregados.

---

# 🧠 RESUMO

```text
lsmod
↓
list modules
↓
lista módulos carregados
```

### Principais informações:

```text
Module
→ nome do módulo

Size
→ tamanho

Used by
→ quem utiliza o módulo
```

### Para procurar:

```bash
lsmod | grep nome_do_modulo
```

### Para consultar diretamente:

```bash
cat /proc/modules
```

---

# 🔄 PARA MEMORIZAR

```text
lsmod
   ↓
LISTA
   ↓
MÓDULOS CARREGADOS
```

Enquanto:

```text
modprobe
   ↓
GERENCIA
   ↓
MÓDULOS
```

E:

```text
modinfo
   ↓
MOSTRA INFORMAÇÕES
   ↓
SOBRE UM MÓDULO
```

# 🎯 COMANDO PRINCIPAL

```bash
lsmod
```

**Tradução: list modules → listar módulos**

**Função: mostrar os módulos do kernel atualmente carregados.**

# ✅ FIM DA PÁGINA 17
