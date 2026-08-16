# Capítulo 4 — Operações numéricas e conversões de base

## 1. Operações numéricas

* Computadores digitais → sistema binário.
* Binário:

  * `0` → nível baixo;
  * `1` → nível alto.
* `N` bits → `2ᴺ` possibilidades.
* Valores → `0` até `2ᴺ − 1`.

## 2. Sistema hexadecimal

* Base 16.
* Símbolos:

  * `0–9`
  * `A–F`
* Correspondências:

  * A = 10
  * B = 11
  * C = 12
  * D = 13
  * E = 14
  * F = 15
* Vantagem → representação compacta de sequências binárias.

## 3. Soma binária

* `0 + 0 = 0`
* `1 + 0 = 1`
* `0 + 1 = 1`
* `1 + 1 = 0`, vai 1.
* Estouro → "vai 1".

## 4. Soma hexadecimal

* Mesma lógica das demais bases.
* Símbolos:

  * `0–9`, `A–F`.
* Quando ultrapassa `F` → ocorre estouro.

## 5. Subtração binária

* `0 − 0 = 0`
* `1 − 1 = 0`
* `1 − 0 = 1`
* `0 − 1` → precisa emprestar.
* Empréstimo → `10₂ − 1₂ = 1₂`.

## 6. MSB e LSB

* **MSB** → bit mais significativo.
* **LSB** → bit menos significativo.
* LSB → peso `2⁰ = 1`.
* Pesos aumentam para a esquerda.

## 7. Decimal → binário

* Método das divisões sucessivas por `2`.
* Guardar os restos.
* Ler restos de baixo para cima.
* Último valor → MSB.

### Exemplo

```text
30 / 2 → resto 0
15 / 2 → resto 1
 7 / 2 → resto 1
 3 / 2 → resto 1

30₁₀ = 11110₂
```

## 8. Binário → decimal

* Usar potências de `2`.
* Multiplicar cada bit pelo peso.
* Somar somente as posições com `1`.

### Exemplo

```text
10011₂
= 2⁴ + 2¹ + 2⁰
= 16 + 2 + 1
= 19₁₀
```

## 9. Decimal → hexadecimal

* Divisões sucessivas por `16`.
* Guardar os restos.
* Ler de baixo para cima.
* Valores 10–15 → A–F.

### Exemplos

```text
373₁₀ = 175₁₆
231₁₀ = E7₁₆
```

## 10. Hexadecimal → decimal

* Usar potências de `16`.
* Da direita para a esquerda:

  * `16⁰ = 1`
  * `16¹ = 16`
  * `16² = 256`
* Multiplicar e somar.

### Exemplos

```text
356₁₆ = 854₁₀
2AF₁₆ = 687₁₀
```

## 11. Hexadecimal → binário

* Cada hexadecimal corresponde a **4 bits**.
* Converter cada símbolo e concatenar.

### Exemplos

```text
5 = 0101
B = 1011

5B₁₆ = 01011011₂
```

```text
3 = 0011
A = 1010
B = 1011

3AB₁₆ = 001110101011₂
```

## 12. Fórmulas e regras para memorizar

* `N bits → 2ᴺ possibilidades`
* Maior valor com N bits → `2ᴺ − 1`
* Decimal → binário → dividir por `2`.
* Binário → decimal → potências de `2`.
* Decimal → hexadecimal → dividir por `16`.
* Hexadecimal → decimal → potências de `16`.
* Hexadecimal → binário → cada dígito = `4 bits`.
* Soma binária:

  * `1 + 1 = 10₂`.
* Subtração binária:

  * `0 − 1` → empréstimo.

---

📌 **Observação:** Este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo foi reorganizado e escrito em linguagem simples para facilitar a compreensão e a revisão. Não substitui o material oficial da disciplina.

