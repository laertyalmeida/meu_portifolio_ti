# Capítulo 3 — Sistemas de numeração decimal, binário e hexadecimal

## 1. Introdução

Os sistemas de numeração são formas organizadas de representar quantidades por meio de símbolos. Eles existem desde as primeiras civilizações, quando as pessoas precisavam registrar animais, objetos, alimentos e outros bens.

Os sistemas mais importantes para a computação são:

* **Decimal** → base 10;
* **Binário** → base 2;
* **Hexadecimal** → base 16.

O sistema binário possui uma importância especial porque os computadores trabalham internamente com dois estados básicos, representados por **0 e 1**.

Além dos sistemas numéricos, a computação utiliza formas de codificação para representar informações, como:

* **BCD**;
* **ASCII**.

---

# 2. Representação analógica e digital

Antes de estudar os sistemas numéricos, é importante compreender a diferença entre representação **analógica** e **digital**.

### Analógico

Uma representação analógica é **contínua**.

Isso significa que uma grandeza pode assumir inúmeros valores dentro de determinado intervalo.

**Exemplo:**

Um termômetro de mercúrio pode indicar uma temperatura entre duas marcações da escala. É necessário interpretar ou aproximar o valor.

### Digital

Uma representação digital é **discreta**.

Os valores são representados por símbolos ou números específicos, em etapas.

**Exemplo:**

Um relógio digital apresenta a hora utilizando números. A representação muda de forma discreta, como:

`10:25 → 10:26 → 10:27`

Enquanto um relógio de ponteiros apresenta o movimento de forma contínua.

### Resumindo

**Analógico = contínuo**

**Digital = discreto**

A representação digital transforma uma grandeza contínua em valores numéricos com determinada precisão.

---

# 3. Sistemas numéricos

A necessidade de contar e medir existe desde as primeiras civilizações.

Os egípcios, por exemplo, utilizavam medidas baseadas em partes do corpo para atividades relacionadas à agricultura e construção.

Algumas medidas utilizadas eram:

* **Dígito** → largura de um dedo;
* **Palmo** → largura de quatro dedos;
* **Cúbito** → distância entre o cotovelo e a ponta do dedo médio.

Os egípcios já utilizavam sistemas numéricos há milhares de anos.

O sistema romano também utilizava uma organização baseada em números decimais, embora fosse diferente do sistema decimal moderno.

Ao longo da história, os números foram estudados e desenvolvidos pela matemática, dando origem a diferentes conjuntos e formas de representação numérica.

---

# 4. Sistema decimal

O sistema decimal é o sistema numérico utilizado normalmente no nosso cotidiano.

Ele possui **base 10**, portanto utiliza dez símbolos:

`{0, 1, 2, 3, 4, 5, 6, 7, 8, 9}`

O valor de cada algarismo depende da posição que ele ocupa.

Cada posição corresponde a uma potência de 10.

### Exemplo

Considere o número:

`234`

Podemos representá-lo como:

`2 × 10² + 3 × 10¹ + 4 × 10⁰`

Calculando:

`2 × 100 + 3 × 10 + 4 × 1`

`200 + 30 + 4 = 234`

Portanto:

`(234)₁₀ = 234`

### Posições

Da direita para a esquerda:

* `10⁰` → unidade;
* `10¹` → dezena;
* `10²` → centena;
* `10³` → milhar.

O algarismo mais à esquerda possui maior peso e é chamado de **MSD (Most Significant Digit)**.

O algarismo mais à direita possui menor peso e é chamado de **LSD (Least Significant Digit)**.

---

# 5. Sistema binário

O sistema binário possui **base 2** e utiliza apenas dois símbolos:

`{0, 1}`

Esses dois valores podem representar dois estados diferentes, como:

* Ligado / desligado;
* Presença / ausência;
* Verdadeiro / falso;
* Corrente / ausência de corrente.

Essa característica torna o sistema binário adequado para a eletrônica digital e para o funcionamento interno dos computadores.

## 5.1 Por que os computadores usam binário?

Os circuitos eletrônicos podem trabalhar com diferentes estados elétricos. De forma simplificada, esses estados podem ser representados por:

* `0` → ausência de sinal;
* `1` → presença de sinal.

Por isso, a linguagem fundamental utilizada internamente pelos computadores é baseada em dois estados.

---

# 6. Potências de 2 no sistema binário

Assim como o sistema decimal utiliza potências de 10, o sistema binário utiliza potências de 2.

As posições são:

`... 2³ 2² 2¹ 2⁰`

E também podem existir posições fracionárias:

`2⁻¹ 2⁻² 2⁻³ ...`

### Exemplo

O número binário:

`1011`

pode ser interpretado como:

`1 × 2³ + 0 × 2² + 1 × 2¹ + 1 × 2⁰`

Calculando:

`8 + 0 + 2 + 1 = 11`

Portanto:

`(1011)₂ = (11)₁₀`

---

# 7. Vantagens do código binário

O código binário apresenta algumas vantagens na computação e nas comunicações digitais.

Entre elas:

* Maior resistência relativa aos efeitos de ruído;
* Facilidade de geração;
* Facilidade de regeneração;
* Representação simples por dois estados.

Além disso, um conjunto de **R bits** consegue representar:

`2ᴿ`

possibilidades diferentes.

### Exemplo

Com 8 bits:

`2⁸ = 256`

Portanto, 8 bits permitem representar **256 combinações diferentes**.

---

# 8. Bit, nibble e byte

O termo **bit** vem de *binary digit* e representa um único dígito binário.

Um bit pode assumir apenas:

`0 ou 1`

Como um único bit representa somente dois estados, os computadores agrupam vários bits.

### Nibble

Um grupo de **4 bits** é chamado de **nibble**.

Exemplo:

`1010`

### Byte

Um grupo de **8 bits** é chamado de **byte**.

Exemplo:

`01000101`

Um byte possui:

`8 bits`

Como existem 8 posições binárias:

`2⁸ = 256`

combinações podem ser representadas.

---

# 9. Outros agrupamentos de bits

Além do nibble e do byte, existem agrupamentos maiores:

* **4 bits** → nibble;
* **8 bits** → byte;
* **16 bits** → word;
* **32 bits** → double word;
* **64 bits** → quad word.

Esses agrupamentos são importantes porque computadores, processadores, memórias e outros componentes trabalham com grupos de bits.

---

# 10. Transferência de bits

Os computadores transferem dados na forma de bits.

Para aumentar a velocidade da transferência, vários bits podem ser transmitidos simultaneamente.

Por exemplo:

* 1 fio → 1 bit por vez;
* 8 fios → 8 bits simultaneamente.

Essa ideia ajuda a compreender por que os computadores trabalham com grupos de bits.

Processadores e outros componentes podem trabalhar com diferentes larguras de dados, como:

* 8 bits;
* 16 bits;
* 32 bits;
* 64 bits.

---

# 11. Unidades de armazenamento

As principais unidades apresentadas são:

### Bit

Representa apenas dois valores:

`0 ou 1`

### Byte

Grupo de 8 bits.

Pode representar:

`2⁸ = 256`

combinações, normalmente correspondentes aos valores de `0 a 255` quando interpretado como um número sem sinal.

Também pode representar caracteres e outros tipos de dados.

### Kilobyte — KB

Aproximadamente:

`1.000 bytes`

Na computação, é comum considerar:

`1 KB = 1.024 bytes`

### Megabyte — MB

Aproximadamente:

`1.000.000 bytes`

### Gigabyte — GB

Aproximadamente:

`1.000.000.000 bytes`

---

# 12. Bits representando caracteres

Os computadores também representam caracteres utilizando códigos binários.

Por exemplo, determinados caracteres podem ser representados por sequências de 8 bits.

Exemplos apresentados no material:

* `A` → `01000001`
* `E` → `01000101`
* `F` → `01000110`

O mais importante não é decorar esses códigos, mas compreender que:

**um caractere pode ser convertido em um código binário e armazenado como bits na memória.**

Por exemplo, quando pressionamos a tecla `E`, o teclado envia ao computador um código que representa esse caractere.

Esse código ocupa 8 bits, ou seja, 1 byte.

---

# 13. Por que 1 KB possui 1.024 bytes?

No uso cotidiano, é comum associar 1 KB a aproximadamente 1.000 bytes.

Entretanto, na convenção binária tradicional apresentada no material:

`1 KB = 1.024 bytes`

Isso ocorre porque:

`1024 = 2¹⁰`

e o número 1024 possui uma representação binária particularmente simples:

`10000000000`

O sistema binário trabalha naturalmente com potências de 2, tornando valores como 1024 convenientes para a computação.

---

# 14. Codificação BCD

**BCD** significa **Binary-Coded Decimal**, ou **Decimal Codificado em Binário**.

É uma forma de representar números decimais usando grupos de **4 bits para cada dígito decimal**.

É importante entender que:

**BCD não é um sistema numérico.**

É uma **codificação**.

Cada algarismo decimal é convertido individualmente para seu equivalente binário de 4 bits.

---

## 14.1 Exemplo de BCD

Considere:

`953`

Cada dígito é convertido separadamente:

* `9` → `1001`
* `5` → `0101`
* `3` → `0011`

Então:

`953₁₀ → 1001 0101 0011 BCD`

---

# 15. BCD não é igual à conversão binária

Essa diferença é muito importante.

### Conversão binária normal

O número inteiro é convertido para binário.

Exemplo:

`137₁₀ = 10001001₂`

### Codificação BCD

Cada dígito decimal é convertido individualmente:

`1 → 0001`

`3 → 0011`

`7 → 0111`

Portanto:

`137₁₀ = 0001 0011 0111 BCD`

Logo:

**Binário normal ≠ BCD**

---

# 16. Decodificação BCD

Para transformar BCD novamente em decimal, basta separar os bits em grupos de 4.

Exemplo:

`1001 0011 1000 0001`

Separando:

* `1001` → 9
* `0011` → 3
* `1000` → 8
* `0001` → 1

Resultado:

`9381`

---

# 17. Sistema hexadecimal

O sistema hexadecimal possui **base 16**.

Ele utiliza 16 símbolos:

`0 1 2 3 4 5 6 7 8 9 A B C D E F`

As letras representam valores maiores que 9:

| Hexadecimal | Decimal |
| ----------- | ------: |
| 0           |       0 |
| 1           |       1 |
| 2           |       2 |
| 3           |       3 |
| 4           |       4 |
| 5           |       5 |
| 6           |       6 |
| 7           |       7 |
| 8           |       8 |
| 9           |       9 |
| A           |      10 |
| B           |      11 |
| C           |      12 |
| D           |      13 |
| E           |      14 |
| F           |      15 |

---

# 18. Relação entre hexadecimal e binário

Cada algarismo hexadecimal corresponde exatamente a **4 bits**.

Isso torna o hexadecimal muito útil na computação.

### Exemplos

`0` → `0000`

`1` → `0001`

`5` → `0101`

`A` → `1010`

`F` → `1111`

Como:

**1 hexadecimal = 4 bits**

e:

**1 byte = 8 bits**

então:

**1 byte = 2 algarismos hexadecimais**

---

# 19. Potências de 16

Assim como o decimal utiliza potências de 10 e o binário utiliza potências de 2, o hexadecimal utiliza potências de 16.

Exemplo:

`210₁₆`

Pode ser representado como:

`2 × 16² + 1 × 16¹ + 0 × 16⁰`

Calculando:

`2 × 256 + 1 × 16 + 0`

`512 + 16`

`528`

Portanto:

`(210)₁₆ = (528)₁₀`

---

# 20. Vantagens do hexadecimal

O hexadecimal facilita bastante a representação de valores binários porque permite escrever muitos bits usando poucos caracteres.

### Nibble

Um nibble possui 4 bits.

Portanto, pode ser representado por:

**1 algarismo hexadecimal**

Exemplo:

`1111₂ = F₁₆`

### Byte

Um byte possui 8 bits.

Portanto, pode ser representado por:

**2 algarismos hexadecimais**

Exemplo:

`01011111₂ = 5F₁₆`

Isso torna o hexadecimal mais compacto e fácil de ler do que longas sequências de zeros e uns.

---

# 21. Aplicações práticas do hexadecimal

O hexadecimal aparece frequentemente na área de computação.

### Endereços MAC

Um endereço MAC pode ser representado utilizando hexadecimal.

Exemplo:

`00-5F-FF-E0-AA-FF`

Essa representação é muito mais compacta do que escrever os valores equivalentes em decimal.

### Cores RGB

Cores também podem ser representadas em hexadecimal.

Exemplo:

`RGB(255, 0, 204)`

pode ser representado como:

`#FF00CC`

Cada par hexadecimal representa um componente da cor:

* `FF` → vermelho;
* `00` → verde;
* `CC` → azul.

---

# 22. Comparação entre decimal, binário e hexadecimal

| Sistema     | Base | Símbolos  |
| ----------- | ---: | --------- |
| Decimal     |   10 | 0–9       |
| Binário     |    2 | 0–1       |
| Hexadecimal |   16 | 0–9 e A–F |

### Relação com bits

* **Binário** → 1 dígito = 1 bit;
* **Hexadecimal** → 1 dígito = 4 bits;
* **Hexadecimal** → 2 dígitos = 1 byte.

---

# 23. ASCII

**ASCII** significa:

**American Standard Code for Information Interchange**

Em português:

**Código Padrão Americano para Intercâmbio de Informações.**

É um padrão utilizado para representar caracteres e funções por meio de códigos numéricos.

O ASCII utiliza **7 bits**.

Como:

`2⁷ = 128`

é possível representar **128 combinações de códigos**.

O padrão foi utilizado para representar elementos como:

* Letras maiúsculas;
* Letras minúsculas;
* Números;
* Sinais de pontuação;
* Outros caracteres e funções.

O ASCII também pode ser utilizado na comunicação entre:

* Computadores;
* Computadores e impressoras;
* Sistemas de armazenamento.

O objetivo principal é estabelecer uma forma padronizada para representar caracteres digitalmente.

---

# 24. Relação entre os principais conceitos

Podemos organizar o conteúdo do capítulo da seguinte maneira:

**Decimal**
→ base 10
→ uso cotidiano

**Binário**
→ base 2
→ 0 e 1
→ funcionamento digital dos computadores

**Hexadecimal**
→ base 16
→ 0–9 e A–F
→ representação compacta do binário

**Bit**
→ 1 dígito binário

**Nibble**
→ 4 bits

**Byte**
→ 8 bits

**BCD**
→ cada dígito decimal representado por 4 bits

**ASCII**
→ código para representação de caracteres

---

# 25. Resumo final

Os sistemas de numeração são fundamentais para compreender como os computadores representam e processam informações.

O **decimal** utiliza dez símbolos e é o sistema usado normalmente pelas pessoas.

O **binário** utiliza apenas `0` e `1`, sendo fundamental para a computação digital.

O **hexadecimal** utiliza 16 símbolos e permite representar grandes sequências binárias de maneira mais compacta.

Os bits são agrupados em unidades maiores:

**4 bits = nibble**

**8 bits = byte**

**16 bits = word**

**32 bits = double word**

**64 bits = quad word**

Além dos sistemas numéricos, existem codificações como **BCD**, que representa cada dígito decimal usando 4 bits, e **ASCII**, que utiliza códigos para representar caracteres.

A principal ideia para o estudo é compreender **como os diferentes sistemas representam os mesmos valores e por que cada um deles é útil na computação**.

---

📌 **Observação:** Este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo foi reorganizado e escrito em linguagem simples para facilitar a compreensão e a revisão. Não substitui o material oficial da disciplina.

