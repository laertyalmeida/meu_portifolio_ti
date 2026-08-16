# Capítulo 6 — Álgebra de Boole e postulados

## 1. Álgebra de Boole

A Álgebra de Boole é utilizada para representar, manipular e simplificar expressões lógicas e circuitos digitais. Ela é fundamental para reduzir a complexidade dos circuitos, permitindo utilizar menos portas lógicas e, consequentemente, economizar componentes.

Diferentemente da álgebra tradicional, que trabalha com diversos valores numéricos, a álgebra booleana utiliza apenas dois valores:

- `0` → falso, desligado, baixo, não, aberto.
- `1` → verdadeiro, ligado, alto, sim, fechado.

As variáveis booleanas representam estados lógicos, podendo também representar níveis de tensão em circuitos digitais.

Uma expressão booleana é uma expressão matemática formada por variáveis booleanas, cujo resultado sempre será `0` ou `1`.

### Simplificação de expressões

Uma mesma tabela-verdade pode ser representada por diferentes expressões booleanas. O objetivo da simplificação é encontrar uma expressão equivalente, porém menos complexa.

Quanto mais simples a expressão:

- menor pode ser o número de portas lógicas;
- menor pode ser a quantidade de componentes;
- mais compacto pode ser o circuito;
- menor pode ser o custo de implementação.

A fatoração é uma das técnicas utilizadas para simplificar expressões booleanas, utilizando postulados, propriedades, teoremas e identidades da Álgebra de Boole.

---

## 2. Postulado da complementação

O complemento de uma variável representa o seu valor inverso.

Se:

- `A = 0` → `A̅ = 1`
- `A = 1` → `A̅ = 0`

O circuito responsável pela complementação é o inversor, ou porta NOT.

### Dupla negação

Quando uma variável é complementada duas vezes, retorna ao seu valor original:

`A̿ = A`

Portanto:

- se `A = 0`, duas negações resultam em `0`;
- se `A = 1`, duas negações resultam em `1`.

Essa propriedade mostra que duas inversões sucessivas anulam uma à outra.

---

## 3. Postulado da adição

Na Álgebra de Boole, a adição corresponde à operação lógica OR.

As principais regras são:

- `0 + 0 = 0`
- `0 + 1 = 1`
- `1 + 0 = 1`
- `1 + 1 = 1`

Diferentemente da soma matemática convencional, `1 + 1` na lógica booleana resulta em `1`.

### Principais identidades da adição

#### Identidade

`A + 0 = A`

Somar `0` não altera o valor da variável.

#### Dominação

`A + 1 = 1`

Qualquer variável somada a `1` resulta em `1`.

#### Idempotência

`A + A = A`

Somar uma variável a ela mesma mantém o próprio valor.

#### Complementação

`A + A̅ = 1`

Uma variável somada ao seu complemento sempre resulta em `1`.

---

## 4. Postulado da multiplicação

Na Álgebra de Boole, a multiplicação corresponde à operação lógica AND.

As regras básicas são:

- `0 × 0 = 0`
- `0 × 1 = 0`
- `1 × 0 = 0`
- `1 × 1 = 1`

Para que uma operação AND resulte em `1`, todas as entradas precisam estar em `1`.

### Principais identidades da multiplicação

#### Elemento nulo

`A × 0 = 0`

Qualquer variável multiplicada por `0` resulta em `0`.

#### Identidade

`A × 1 = A`

Multiplicar uma variável por `1` mantém seu valor.

#### Idempotência

`A × A = A`

Uma variável multiplicada por ela mesma resulta nela própria.

#### Complementação

`A × A̅ = 0`

Uma variável multiplicada pelo seu complemento sempre resulta em `0`.

---

## 5. Propriedades algébricas

As propriedades algébricas permitem reorganizar e simplificar expressões booleanas.

### 5.1 Propriedade comutativa

A ordem das variáveis pode ser alterada sem modificar o resultado.

#### Adição

`A + B = B + A`

#### Multiplicação

`A × B = B × A`

---

### 5.2 Propriedade associativa

Permite alterar a forma de agrupamento das variáveis sem alterar o resultado.

#### Adição

`A + (B + C) = (A + B) + C`

#### Multiplicação

`A × (B × C) = (A × B) × C`

---

### 5.3 Propriedade distributiva

Permite distribuir uma operação sobre outra.

Um exemplo importante é:

`A × (B + C) = A × B + A × C`

Essa propriedade é utilizada frequentemente na manipulação e simplificação de expressões booleanas.

---

# 6. Teoremas de De Morgan

Os teoremas de De Morgan são importantes para simplificar e transformar circuitos lógicos.

Eles permitem converter operações:

- OR em AND;
- AND em OR;

sempre considerando os complementos das variáveis ou termos envolvidos.

Essa transformação é útil para otimizar circuitos e implementar uma mesma função utilizando diferentes tipos de portas lógicas.

---

## 6.1 Primeiro teorema de De Morgan

O primeiro teorema estabelece que:

> O complemento de um produto é igual à soma dos complementos.

Em expressão:

`(A × B)̅ = A̅ + B̅`

Ou seja:

1. uma operação AND é transformada em OR;
2. cada variável é complementada.

Para várias variáveis:

`(A × B × C × ... × N)̅ = A̅ + B̅ + C̅ + ... + N̅`

---

## 6.2 Segundo teorema de De Morgan

O segundo teorema estabelece que:

> O complemento de uma soma é igual ao produto dos complementos.

Em expressão:

`(A + B)̅ = A̅ × B̅`

Ou seja:

1. uma operação OR é transformada em AND;
2. cada variável é complementada.

Para várias variáveis:

`(A + B + C + ... + N)̅ = A̅ × B̅ × C̅ × ... × N̅`

---

## 6.3 Regra geral dos teoremas de De Morgan

Para aplicar De Morgan, podemos seguir uma regra simples:

1. Trocar a operação:
   - OR → AND
   - AND → OR

2. Complementar individualmente cada variável ou termo.

3. Complementar a expressão resultante de acordo com a transformação.

### Exemplo conceitual

Uma expressão com OR, como:

`A + B + C + D`

pode ser transformada utilizando De Morgan em uma expressão equivalente envolvendo AND e os complementos das variáveis.

É importante observar que uma expressão pode possuir várias variáveis, mas diferentes quantidades de termos.

Por exemplo:

`A + BC + D`

possui quatro variáveis:

- `A`
- `B`
- `C`
- `D`

mas possui três termos:

- `A`
- `BC`
- `D`

O teorema pode ser aplicado à expressão inteira ou a termos específicos, dependendo da simplificação desejada.

---

# 7. Circuitos integrados

As portas lógicas podem ser reunidas em circuitos integrados.

Um circuito integrado é um pequeno bloco de material semicondutor, conhecido como chip, que reúne diversos componentes e circuitos em um único dispositivo.

Esses chips podem conter:

- portas lógicas;
- contadores;
- codificadores;
- decodificadores;
- outros circuitos digitais.

Essa integração permite construir circuitos complexos de forma compacta.

---

# 8. Importância da Álgebra de Boole

A Álgebra de Boole é fundamental para o desenvolvimento e funcionamento dos sistemas digitais.

Por meio dos postulados, propriedades e teoremas, especialmente os teoremas de De Morgan, é possível:

- simplificar expressões booleanas;
- reduzir circuitos;
- diminuir a quantidade de portas lógicas;
- otimizar componentes;
- criar circuitos digitais mais compactos.

Esses conceitos estão presentes em diversos equipamentos digitais, incluindo computadores, processadores, unidades lógicas e aritméticas (ULA), eletrodomésticos e sistemas eletrônicos de automóveis.

## Resumo final

A Álgebra de Boole trabalha com os valores `0` e `1` e fornece regras para representar e simplificar circuitos digitais.

Os principais pontos são:

- Complementação → inversão da variável.
- Adição → operação OR.
- Multiplicação → operação AND.
- Comutativa → permite trocar a ordem.
- Associativa → permite alterar agrupamentos.
- Distributiva → permite distribuir operações.
- De Morgan → permite trocar OR por AND e AND por OR, aplicando complementos.

O principal objetivo dessas regras é simplificar expressões e tornar os circuitos digitais mais eficientes e compactos.

📌 **Observação:** Este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo foi reorganizado e escrito em linguagem simples para facilitar a compreensão e a revisão. Não substitui o material oficial da disciplina.
