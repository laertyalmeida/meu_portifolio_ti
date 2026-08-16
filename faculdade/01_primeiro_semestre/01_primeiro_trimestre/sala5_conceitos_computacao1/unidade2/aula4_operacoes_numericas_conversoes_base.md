# Capítulo 4 — Operações numéricas e conversões de base

## 1. Introdução

Os computadores digitais utilizam principalmente o **sistema de numeração binário (base 2)** para representar e processar informações. Neste capítulo são estudadas operações aritméticas em diferentes bases e as principais técnicas de conversão entre os sistemas **decimal, binário e hexadecimal**.

Os principais assuntos são:

* Operações de soma em binário e hexadecimal;
* Subtração em binário;
* Conversão de decimal para binário;
* Conversão de binário para decimal;
* Conversão de decimal para hexadecimal;
* Conversão de hexadecimal para decimal;
* Conversão de hexadecimal para binário.

O objetivo não é apenas obter o resultado de uma conversão, mas compreender como os dispositivos digitais representam e manipulam os números.

---

# 2. Operações numéricas

Os computadores são chamados de **computadores digitais** porque trabalham internamente com o sistema binário.

Uma das principais razões para o uso do sistema binário é a facilidade de construção dos dispositivos eletrônicos. É mais simples trabalhar com dois estados de tensão do que com dez níveis diferentes necessários para representar diretamente os algarismos de 0 a 9.

Assim, os dispositivos digitais utilizam dois estados lógicos:

* **0 → nível baixo**
* **1 → nível alto**

Em um exemplo de sistema digital, determinadas faixas de tensão representam o valor 1 e outras representam o valor 0. Existem também faixas consideradas inválidas, que não são utilizadas para representar esses estados.

## 2.1 Quantidade de possibilidades com N bits

Quando utilizamos **N bits**, podemos representar:

**2ᴺ possibilidades**

Essas possibilidades correspondem aos números decimais de:

**0 até 2ᴺ − 1**

### Exemplo com 4 bits

Com quatro bits temos:

**2⁴ = 16 possibilidades**

Os valores binários vão de:

**0000₂ até 1111₂**

Correspondendo aos valores decimais:

**0 até 15**

Portanto, quatro bits permitem representar 16 valores diferentes.

---

# 3. Sistema hexadecimal

O sistema hexadecimal utiliza **16 símbolos**:

**0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F**

As letras representam valores decimais:

| Hexadecimal | Decimal |
| ----------- | ------: |
| A           |      10 |
| B           |      11 |
| C           |      12 |
| D           |      13 |
| E           |      14 |
| F           |      15 |

O hexadecimal é muito utilizado porque permite representar grandes sequências binárias utilizando uma quantidade menor de caracteres.

Uma sequência extensa de zeros e uns pode ser difícil de visualizar e mais sujeita a erros. A representação hexadecimal torna essa informação mais compacta e fácil de interpretar.

Esse sistema é bastante utilizado em áreas relacionadas a **microprocessadores, circuitos digitais, software e hardware**.

---

# 4. Soma em diferentes bases

A lógica da soma é semelhante nos diferentes sistemas numéricos. A principal diferença está na quantidade de símbolos disponíveis em cada base.

Quando o resultado ultrapassa o maior algarismo disponível naquela posição, ocorre um **estouro**, também conhecido como **"vai 1"**.

No sistema decimal, por exemplo:

**7 + 7 = 14**

O 4 permanece na posição atual e o 1 é levado para a próxima posição.

Esse mesmo princípio aparece nas operações binárias e hexadecimais.

---

# 5. Soma binária

O sistema binário possui somente dois algarismos:

**0 e 1**

Por isso, existem apenas quatro possibilidades básicas para a soma de dois bits:

| Operação | Resultado |
| -------- | --------- |
| 0 + 0    | 0         |
| 1 + 0    | 1         |
| 0 + 1    | 1         |
| 1 + 1    | 0, vai 1  |

A operação mais importante é:

**1 + 1 = 10₂**

Isso significa que colocamos **0 na posição atual** e levamos **1 para a próxima posição**.

## 5.1 Exemplo

Podemos somar:

**137₁₀ + 72₁₀**

Convertendo os números para binário:

```text
137₁₀ = 10001001₂
 72₁₀ = 01001000₂
```

Realizando a soma:

```text
  10001001
+ 01001000
-----------
  11010001
```

O resultado corresponde a:

**209₁₀**

Portanto:

**137₁₀ + 72₁₀ = 209₁₀**

e

**10001001₂ + 01001000₂ = 11010001₂**.

---

# 6. Soma hexadecimal

O sistema hexadecimal possui 16 símbolos e pode ser representado utilizando o número 16 ou a letra H para indicar a base.

Exemplos:

* **6AD₁₆**
* **26H**

A técnica da soma hexadecimal segue a mesma ideia das demais bases: os valores são organizados em sequência e, quando ultrapassamos o maior símbolo disponível, ocorre um estouro e o valor é levado para a próxima posição.

## 6.1 Exemplo simples

Considere:

**8₁₆ + A₁₆**

Como:

**A = 10₁₀**

Temos:

**8 + 10 = 18₁₀**

Em hexadecimal, 18 decimal corresponde a:

**12₁₆**

Assim:

```text
  8
+ A
---
 12
```

O resultado é:

**12₁₆**

## 6.2 Exemplo com números maiores

Considere:

**531₁₆ + 19C₁₆**

Realizamos a soma começando pela direita:

```text
  531
+ 19C
-----
  6CD
```

Resultado:

**531₁₆ + 19C₁₆ = 6CD₁₆**

---

# 7. Subtração binária

A subtração binária segue uma lógica semelhante à subtração decimal, mas existem somente quatro combinações básicas:

| Operação | Resultado                |
| -------- | ------------------------ |
| 0 − 0    | 0                        |
| 1 − 1    | 0                        |
| 1 − 0    | 1                        |
| 0 − 1    | precisa pedir emprestado |

Quando temos:

**0 − 1**

é necessário pegar emprestado da posição seguinte à esquerda.

O valor emprestado permite realizar:

**10₂ − 1₂ = 1₂**

Esse processo é semelhante ao "empresta 1" da subtração decimal.

## 7.1 Exemplo

Considere:

**10011₂ − 1000₂**

Organizando:

```text
  10011
- 01000
-------
  01011
```

Resultado:

**10011₂ − 1000₂ = 1011₂**

---

# 8. MSB e LSB

Na representação binária, cada bit possui uma posição e um peso.

Dois termos importantes são:

### MSB — Most Significant Bit

É o **bit mais significativo**, ou seja, aquele que possui o maior valor de acordo com sua posição.

### LSB — Least Significant Bit

É o **bit menos significativo**, ou seja, aquele que possui o menor peso.

O LSB corresponde à posição mais à direita e possui peso:

**2⁰ = 1**

Os pesos aumentam conforme avançamos para a esquerda.

---

# 9. Conversão de decimal para binário

Existem diferentes formas de realizar a conversão entre decimal e binário.

Uma das formas consiste em identificar quais potências de 2 podem ser utilizadas para formar o número decimal.

Outra técnica bastante prática é o método das **divisões sucessivas por 2**.

## 9.1 Divisões sucessivas por 2

O número decimal é dividido repetidamente por 2.

Em cada divisão registramos o resto:

* resto 0;
* ou resto 1.

O processo continua até que o quociente seja 0.

Depois, os restos são lidos **de baixo para cima**, começando pelo último resto, que representa o MSB.

### Exemplo: 30₁₀ para binário

```text
30 / 2 = 15  resto 0
15 / 2 =  7  resto 1
 7 / 2 =  3  resto 1
 3 / 2 =  1  resto 1
```

O último quociente é 1.

Lendo os valores na ordem inversa:

```text
11110
```

Portanto:

**30₁₀ = 11110₂**

---

# 10. Conversão de binário para decimal

Para transformar um número binário em decimal, devemos observar o peso de cada posição.

Cada posição representa uma potência de 2:

```text
... 2⁴  2³  2²  2¹  2⁰
```

Multiplicamos cada bit pelo peso correspondente e somamos os resultados.

## 10.1 Exemplo

Converter:

**10011₂**

Temos:

```text
1 0 0 1 1
↓ ↓ ↓ ↓ ↓
2⁴ 2³ 2² 2¹ 2⁰
```

Somando apenas as posições que possuem 1:

```text
2⁴ + 2¹ + 2⁰
= 16 + 2 + 1
= 19
```

Portanto:

**10011₂ = 19₁₀**

### Outro exemplo

Para:

**110011₂**

Temos:

```text
2⁵ + 2⁴ + 2¹ + 2⁰
= 32 + 16 + 2 + 1
= 51
```

Logo:

**110011₂ = 51₁₀**

---

# 11. Conversão de decimal para hexadecimal

A conversão de decimal para hexadecimal utiliza o mesmo princípio das divisões sucessivas usadas para converter decimal em binário.

A diferença é que, neste caso, dividimos sucessivamente por:

**16**

Os restos são utilizados para formar o número hexadecimal e devem ser lidos do último resultado para o primeiro.

## 11.1 Exemplo: 373₁₀ para hexadecimal

```text
373 / 16 = 23  resto 5
 23 / 16 =  1  resto 7
  1 / 16 =  0  resto 1
```

Lendo os restos de baixo para cima:

```text
175
```

Portanto:

**373₁₀ = 175₁₆**

## 11.2 Exemplo: 231₁₀ para hexadecimal

```text
231 / 16 = 14  resto 7
 14 / 16 =  0  resto 14
```

O valor decimal 14 corresponde à letra:

**E**

Assim:

**231₁₀ = E7₁₆**

---

# 12. Conversão de hexadecimal para decimal

Cada posição de um número hexadecimal possui um peso baseado em uma potência de 16.

Da direita para a esquerda:

```text
16⁰ = 1
16¹ = 16
16² = 256
16³ = 4096
...
```

Para realizar a conversão:

1. Identificamos o valor decimal de cada símbolo hexadecimal;
2. Multiplicamos cada valor pela potência de 16 correspondente;
3. Somamos os resultados.

## 12.1 Exemplo: 356₁₆ para decimal

```text
3 × 16² = 768
5 × 16¹ = 80
6 × 16⁰ = 6
```

Somando:

```text
768 + 80 + 6 = 854
```

Portanto:

**356₁₆ = 854₁₀**

## 12.2 Exemplo: 2AF₁₆ para decimal

Como:

* A = 10;
* F = 15.

Temos:

```text
2 × 16² = 512
10 × 16¹ = 160
15 × 16⁰ = 15
```

Somando:

```text
512 + 160 + 15 = 687
```

Portanto:

**2AF₁₆ = 687₁₀**

---

# 13. Conversão de hexadecimal para binário

A conversão entre hexadecimal e binário é especialmente simples porque:

**16 = 2⁴**

Isso significa que cada algarismo hexadecimal pode ser representado por um grupo de **4 bits**.

Por exemplo:

| Hexadecimal | Binário |
| ----------- | ------- |
| 0           | 0000    |
| 1           | 0001    |
| 2           | 0010    |
| 3           | 0011    |
| 4           | 0100    |
| 5           | 0101    |
| 6           | 0110    |
| 7           | 0111    |
| 8           | 1000    |
| 9           | 1001    |
| A           | 1010    |
| B           | 1011    |
| C           | 1100    |
| D           | 1101    |
| E           | 1110    |
| F           | 1111    |

Essa correspondência permite transformar cada símbolo hexadecimal diretamente em quatro bits.

## 13.1 Exemplo: 5B₁₆ para binário

O algarismo:

**5₁₆ = 0101₂**

e:

**B₁₆ = 1011₂**

Concatenando:

```text
0101 1011
```

Podemos representar o resultado sem o zero inicial:

**1011011₂**

Assim:

**5B₁₆ = 1011011₂**

## 13.2 Exemplo: 3AB₁₆

Convertendo cada símbolo:

```text
3 = 0011
A = 1010
B = 1011
```

Concatenando:

```text
0011 1010 1011
```

O resultado é:

**1110101011₂**, considerando a retirada dos zeros iniciais.

---

# 14. Resumo das principais conversões

## Decimal → Binário

Dividir sucessivamente por **2** e ler os restos de baixo para cima.

```text
Decimal
   ↓
Divisões por 2
   ↓
Restos
   ↓
Leitura inversa
   ↓
Binário
```

## Binário → Decimal

Multiplicar cada bit pela potência de 2 correspondente e somar.

```text
Bits
 ↓
Pesos de 2
 ↓
Multiplicação
 ↓
Soma
 ↓
Decimal
```

## Decimal → Hexadecimal

Dividir sucessivamente por **16** e ler os restos de baixo para cima.

```text
Decimal
   ↓
Divisões por 16
   ↓
Restos
   ↓
Leitura inversa
   ↓
Hexadecimal
```

## Hexadecimal → Decimal

Multiplicar cada símbolo pela potência de 16 correspondente e somar.

```text
Hexadecimal
    ↓
Pesos de 16
    ↓
Multiplicação
    ↓
Soma
    ↓
Decimal
```

## Hexadecimal → Binário

Converter cada símbolo hexadecimal diretamente para seu grupo equivalente de 4 bits e concatenar os resultados.

```text
Hexadecimal
     ↓
Cada símbolo
     ↓
4 bits
     ↓
Concatenação
     ↓
Binário
```

---

# 15. Considerações finais

O estudo das operações numéricas e das conversões de base é fundamental para compreender como os computadores representam e processam informações.

O **binário** é a base principal dos sistemas digitais porque utiliza apenas dois estados. O **hexadecimal**, por sua vez, facilita a representação de sequências binárias extensas, tornando-as menores e mais fáceis de interpretar.

As principais técnicas estudadas foram:

* Soma binária;
* Soma hexadecimal;
* Subtração binária;
* Decimal → binário;
* Binário → decimal;
* Decimal → hexadecimal;
* Hexadecimal → decimal;
* Hexadecimal → binário.

Mesmo existindo calculadoras e ferramentas que realizam essas conversões automaticamente, compreender o processo é importante para entender as operações realizadas internamente pelos dispositivos digitais.

---

📌 **Observação:** Este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo foi reorganizado e escrito em linguagem simples para facilitar a compreensão e a revisão. Não substitui o material oficial da disciplina.

