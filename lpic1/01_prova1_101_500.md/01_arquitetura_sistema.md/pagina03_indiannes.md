# 📖 PÁGINA 3 — ENDIANNESS

## 🧠 1. O QUE É ENDIANNESS?

**Endianness** é a forma como os **bytes** de um valor com múltiplos bytes são organizados na memória.

Existem principalmente dois tipos:

- **Big Endian**
- **Little Endian**

A diferença está na **ordem dos bytes**, e não na ordem dos bits dentro de cada byte.

---

## 🔵 2. BIG ENDIAN

No **Big Endian**, o byte mais significativo (**MSB — Most Significant Byte**) é armazenado primeiro, no menor endereço de memória.

Exemplo:

Valor: `0x12345678`

Memória:

`12 34 56 78`

Portanto:

**Big Endian → byte mais significativo primeiro.**

### 🧠 Para memorizar

**BIG → grande primeiro → MSB primeiro**

---

## 🟢 3. LITTLE ENDIAN

No **Little Endian**, o byte menos significativo (**LSB — Least Significant Byte**) é armazenado primeiro, no menor endereço de memória.

Exemplo:

Valor: `0x12345678`

Memória:

`78 56 34 12`

Portanto:

**Little Endian → byte menos significativo primeiro.**

### 🧠 Para memorizar

**LITTLE → pequeno primeiro → LSB primeiro**

---

## ⚖️ 4. BIG ENDIAN x LITTLE ENDIAN

Considere o valor:

`0x12345678`

### Big Endian

`12 34 56 78`

O `12` é armazenado primeiro porque é o byte mais significativo.

### Little Endian

`78 56 34 12`

O `78` é armazenado primeiro porque é o byte menos significativo.

Resumo:

| Endianness | Primeiro byte |
|---|---|
| Big Endian | MSB |
| Little Endian | LSB |

---

## 🔢 5. BYTE x BIT

Não confunda **bit** com **byte**.

### Bit

É a menor unidade de informação e pode assumir:

`0` ou `1`

### Byte

Um byte possui:

`8 bits`

Por exemplo:

`0x12345678`

possui 4 bytes:

`12 | 34 | 56 | 78`

Como cada byte possui 8 bits:

`4 bytes × 8 = 32 bits`

---

## 🧠 6. MSB E LSB

### MSB

**MSB = Most Significant Byte**

Tradução:

**Byte mais significativo**

No valor:

`0x12345678`

o MSB é:

`12`

### LSB

**LSB = Least Significant Byte**

Tradução:

**Byte menos significativo**

No valor:

`0x12345678`

o LSB é:

`78`

---

## 🔍 7. COMO VER O ENDIANNESS NO LINUX

O comando principal para consultar isso é:

`lscpu`

Procure na saída:

`Byte Order:`

Exemplo:

`Byte Order: Little Endian`

Isso significa que o sistema utiliza:

**Little Endian**

Ou seja, o byte menos significativo é armazenado primeiro.

---

## 🖥️ 8. `lscpu`

### Tradução

`lscpu` pode ser entendido como:

**ls = list → listar**

**cpu = Central Processing Unit → Unidade Central de Processamento**

Portanto:

**lscpu → list CPU → listar informações da CPU**

Comando:

`lscpu`

Informação importante para esta página:

`Byte Order:`

---

## 📝 9. FLAGS DO `lscpu`

Para verificar o Endianness, **não é necessário utilizar uma flag**.

O comando simples já é suficiente:

`lscpu`

### `-e`

**extended = estendido**

Comando:

`lscpu -e`

Exibe informações estendidas da CPU.

### `-p`

**parse = analisar/processar**

Comando:

`lscpu -p`

Exibe informações da CPU em um formato adequado para análise/processamento.

### ⚠️ Para esta página

Não é necessário decorar `-e` ou `-p` para descobrir o Endianness.

O essencial é:

`lscpu`

e localizar:

`Byte Order:`

---

## 🎯 10. O QUE VOCÊ PRECISA SABER PARA A PROVA

Ao terminar esta página, você deve saber:

- O que é Endianness.
- Que Endianness determina a ordem dos bytes na memória.
- O que é Big Endian.
- O que é Little Endian.
- Que Big Endian coloca o MSB primeiro.
- Que Little Endian coloca o LSB primeiro.
- O significado de MSB.
- O significado de LSB.
- Que 1 byte possui 8 bits.
- Diferenciar byte de bit.
- Reconhecer um valor hexadecimal formado por vários bytes.
- Usar `lscpu`.
- Identificar `Byte Order:` na saída do `lscpu`.
- Reconhecer `Little Endian`.
- Reconhecer `Big Endian`.

---

## 🧠 RESUMO

**ENDIANNESS**

→ Ordem dos bytes na memória.

**BIG ENDIAN**

→ MSB primeiro.

→ Byte mais significativo primeiro.

**LITTLE ENDIAN**

→ LSB primeiro.

→ Byte menos significativo primeiro.

**MSB**

→ Most Significant Byte.

→ Byte mais significativo.

**LSB**

→ Least Significant Byte.

→ Byte menos significativo.

**BIT**

→ 0 ou 1.

**BYTE**

→ 8 bits.

**lscpu**

→ list CPU.

→ Lista informações da CPU.

**Byte Order**

→ Ordem dos bytes utilizada pelo sistema.

Exemplo:

`Byte Order: Little Endian`

→ O sistema utiliza Little Endian.

---

# ✅ FIM DA PÁGINA 3
