1. Resumo completo — pronto para seu .md
# Capítulo 5 — Álgebra de Boole e funções booleanas


## 1. Introdução à Álgebra de Boole


A **Álgebra de Boole** é uma forma de representar e trabalhar com valores lógicos, normalmente utilizando apenas dois estados:


- `0` → falso, desligado ou ausência de sinal;
- `1` → verdadeiro, ligado ou presença de sinal.


Os computadores utilizam circuitos digitais que trabalham justamente com a presença ou ausência de sinais elétricos. Dessa forma, as operações lógicas realizadas sobre esses sinais são fundamentais para o funcionamento dos computadores.


A lógica utilizada para processar informações digitais é chamada de **lógica booleana**, e os componentes físicos responsáveis por executar essas operações são chamados de **portas lógicas**.


A base da Álgebra de Boole foi desenvolvida pelo matemático **George Boole**, que, em 1854, estudou como decisões lógicas poderiam ser representadas a partir de situações verdadeiras ou falsas.


Na computação, a Álgebra de Boole é importante porque permite representar, analisar, simplificar e projetar circuitos digitais.


---


## 2. Aplicação da Álgebra de Boole na computação


Os circuitos digitais são responsáveis pela implementação da lógica utilizada pelos computadores.


Um exemplo importante está dentro do processador, na **Unidade Lógica e Aritmética (ULA)**. A ULA realiza operações aritméticas e lógicas e utiliza diversos circuitos para executar suas funções.


Entre esses circuitos podemos destacar:


- **Somadores:** realizam operações de soma;
- **Subtratores:** realizam operações de subtração;
- **Comparadores:** comparam sinais ou valores provenientes de diferentes origens.


A Álgebra de Boole não serve apenas para analisar circuitos já existentes. Ela também pode ser utilizada para **projetar circuitos**, definindo como determinadas entradas devem produzir determinadas saídas.


Esse processo de criação de circuitos lógicos a partir de relações entre entradas e saídas é chamado de **síntese de circuitos lógicos**.


---


## 3. Variáveis booleanas e funções booleanas


### 3.1 Variável booleana


Uma **variável booleana** é uma quantidade que pode assumir apenas dois valores:


- `0`;
- `1`.


Por exemplo:


```text
X = 0

ou

X = 1
3.2 Função booleana

Uma função booleana relaciona uma ou mais variáveis de entrada a uma única saída.

Por exemplo:

S = X1 + X2

Nesse caso:

X1 e X2 são entradas;
S é a saída.

A saída depende dos valores recebidos pelas entradas.

4. Portas lógicas

As portas lógicas são componentes eletrônicos responsáveis por realizar operações booleanas sobre sinais elétricos.

Na prática, essas portas são implementadas em componentes eletrônicos, como chips, e combinadas para formar circuitos digitais mais complexos.

As principais portas lógicas estudadas são:

OR;
AND;
NOT;
XOR;
NAND;
NOR;
XNOR.

Cada porta possui:

uma função lógica;
entradas;
uma saída;
uma expressão booleana;
uma tabela-verdade;
uma representação gráfica.
5. Tabela-verdade

A tabela-verdade organiza todas as combinações possíveis das entradas de uma função lógica e mostra o resultado correspondente na saída.

Para duas entradas, existem quatro combinações possíveis:

00
01
10
11

A tabela-verdade permite entender exatamente como uma porta lógica se comporta para cada combinação de entradas.

Ela é utilizada na análise, documentação e projeto de circuitos digitais.

6. Operações básicas da Álgebra de Boole

A Álgebra de Boole possui três operações básicas:

OR;
AND;
NOT.

Outras portas, como XOR, NAND, NOR e XNOR, também são importantes e podem ser construídas a partir das operações booleanas básicas.

7. Porta OR — OU booleano

A porta OR produz saída 1 quando pelo menos uma das entradas for 1.

A saída será 0 somente quando todas as entradas forem 0.

Para duas entradas:

S = X1 + X2

O símbolo + representa a operação lógica OR, e não uma soma aritmética convencional.

Tabela-verdade OR
X1	X2	S
0	0	0
0	1	1
1	0	1
1	1	1
Regra principal

Se qualquer entrada for 1, a saída será 1.

Exemplo prático

Imagine um sistema industrial que precisa ativar um alarme quando:

a temperatura ultrapassar o limite; OU
a pressão ultrapassar o limite.

Nesse caso, qualquer uma dessas condições pode ativar o alarme.

A lógica pode ser representada por:

Alarme = Temperatura + Pressão

Portanto, a porta OR é adequada quando qualquer uma de várias condições pode provocar uma ação.

8. Porta AND — E booleano

A porta AND realiza uma operação semelhante à multiplicação lógica.

A saída será 1 somente quando todas as entradas forem 1.

Para duas entradas:

S = X1 × X2
Tabela-verdade AND
X1	X2	S
0	0	0
0	1	0
1	0	0
1	1	1
Regra principal

Todas as entradas precisam ser 1 para que a saída seja 1.

Por exemplo, se uma máquina só puder funcionar quando dois sensores estiverem ativados:

Máquina = Sensor1 AND Sensor2

Se qualquer um dos sensores estiver desligado, a saída será 0.

9. Porta NOT — NÃO booleano

A porta NOT realiza a negação de uma entrada.

Ela possui uma única entrada e produz o valor contrário:

entrada 0 → saída 1;
entrada 1 → saída 0.

A expressão pode ser representada como:

S = NOT X1

ou utilizando a barra sobre a variável:

S = X1̅
Tabela-verdade NOT
X1	S
0	1
1	0
Regra principal

A saída sempre será o oposto da entrada.

10. Porta XOR — OU exclusivo

A porta XOR significa OU exclusivo.

Ela produz 1 quando as entradas são diferentes.

Quando as entradas são iguais, a saída será 0.

Tabela-verdade XOR
X1	X2	S
0	0	0
0	1	1
1	0	1
1	1	0
Regra principal

XOR produz 1 quando as entradas são diferentes.

Podemos pensar assim:

Diferentes → 1
Iguais     → 0
11. Aplicação da XOR em sistemas digitais

Uma aplicação importante da porta XOR está nos sistemas de transmissão de dados e verificação de erros.

Informações digitais são transmitidas constantemente por redes e sistemas de comunicação. Durante uma transmissão, pode ocorrer alteração de algum bit.

Para ajudar a identificar erros, pode ser utilizado um bit de paridade.

O transmissor acrescenta esse bit aos dados originais. O receptor utiliza um circuito de verificação para verificar se a quantidade de bits 1 está de acordo com o critério de paridade utilizado.

A porta XOR é especialmente útil nesse processo porque permite verificar diferenças e calcular a paridade dos bits.

12. Gerador de paridade

Em um sistema de paridade par, o transmissor recebe os bits dos dados e calcula um bit adicional chamado bit de paridade (P).

Por exemplo, podemos ter quatro bits de dados:

D3 D2 D1 D0

O circuito calcula o bit de paridade e envia:

D3 D2 D1 D0 P

O receptor recebe esses bits e utiliza um circuito de verificação.

13. Verificador de paridade

O circuito verificador analisa os bits recebidos e produz uma saída de erro:

E = 0 → não foi detectado erro
E = 1 → erro detectado

No critério de paridade par, a saída E será 1 quando a quantidade de bits 1 recebidos for ímpar.

Assim:

E = 0 → quantidade de 1s compatível com paridade par
E = 1 → quantidade de 1s indica possível erro

Esse mecanismo é capaz de detectar determinados erros, principalmente aqueles relacionados à alteração de um único bit.

Exemplo

Considere uma transmissão:

P  D3 D2 D1 D0
0  1  0  1  0

Os bits de dados possuem duas ocorrências de 1, portanto a paridade já é par. O bit P é 0.

O verificador calcula a combinação dos bits utilizando XOR. Se o resultado final for 0, não será indicado erro.

14. Porta NAND — NÃO E

A porta NAND é uma operação AND seguida de uma negação.

Ou seja:

NAND = NOT(AND)

Para duas entradas:

S = (X1 × X2)̅

A saída será 0 somente quando todas as entradas forem 1.

Em todos os outros casos, a saída será 1.

Tabela-verdade NAND
X1	X2	S
0	0	1
0	1	1
1	0	1
1	1	0
Regra principal

NAND é o contrário da AND.

Podemos comparar:

AND:
1 AND 1 = 1


NAND:
1 NAND 1 = 0
15. Teoremas de De Morgan

Os teoremas de De Morgan foram desenvolvidos pelo matemático Augustus De Morgan e são importantes para simplificar expressões booleanas e desenvolver circuitos digitais.

Eles ajudam a transformar expressões envolvendo AND, OR e negação.

Uma relação importante é:

NOT(X1 AND X2) = NOT X1 OR NOT X2

Outra é:

NOT(X1 OR X2) = NOT X1 AND NOT X2

Essas relações são muito utilizadas na simplificação de circuitos e expressões booleanas.

16. Porta NOR — NÃO OU

A porta NOR é uma operação OR seguida de uma negação.

Ou seja:

NOR = NOT(OR)

Para duas entradas:

S = (X1 + X2)̅

A saída será 1 somente quando todas as entradas forem 0.

Tabela-verdade NOR
X1	X2	S
0	0	1
0	1	0
1	0	0
1	1	0
Regra principal

NOR é o contrário da OR.

Comparando:

OR:
0 OR 0 = 0


NOR:
0 NOR 0 = 1
17. Porta XNOR — OU exclusivo por coincidência

A porta XNOR é relacionada à XOR, porém apresenta o comportamento inverso.

Enquanto a XOR produz 1 quando as entradas são diferentes, a XNOR produz 1 quando as entradas são iguais.

Tabela-verdade XNOR
X1	X2	S
0	0	1
0	1	0
1	0	0
1	1	1
Regra principal

XNOR produz 1 quando as entradas são iguais.

Podemos memorizar:

XOR:
iguais → 0
diferentes → 1


XNOR:
iguais → 1
diferentes → 0

Por isso, a XNOR também pode ser entendida como uma porta de coincidência.

18. Comparação entre as principais portas lógicas
Porta	Regra principal	Saída 1 quando...
OR	OU	Pelo menos uma entrada é 1
AND	E	Todas as entradas são 1
NOT	NÃO	A entrada é invertida
XOR	OU exclusivo	As entradas são diferentes
NAND	NÃO E	Pelo menos uma entrada é 0
NOR	NÃO OU	Todas as entradas são 0
XNOR	Coincidência	As entradas são iguais
19. Forma rápida de memorizar

Uma forma simples de lembrar o funcionamento é:

OR   → basta uma entrada 1
AND  → todas precisam ser 1
NOT  → inverte
XOR  → diferentes = 1
NAND → AND invertida
NOR  → OR invertida
XNOR → iguais = 1

Outra maneira é observar as condições que produzem 1:

OR   → qualquer 1
AND  → todos 1
NOT  → contrário
XOR  → diferentes
NAND → qualquer 0
NOR  → todos 0
XNOR → iguais
20. Importância da Álgebra de Boole

A Álgebra de Boole é fundamental para a computação porque permite representar matematicamente decisões e relações entre sinais digitais.

Ela é utilizada para:

analisar circuitos;
projetar circuitos;
simplificar circuitos;
representar relações entre entradas e saídas;
implementar operações lógicas;
verificar condições;
detectar determinados erros na transmissão de dados.

Os conceitos estudados servem de base para compreender o funcionamento interno dos computadores e de diversos equipamentos digitais.

21. Conclusão

A Álgebra de Boole utiliza valores binários, normalmente representados por 0 e 1, para representar estados lógicos.

As portas lógicas implementam fisicamente essas operações em circuitos digitais.

As sete principais portas estudadas são:

OR
AND
NOT
XOR
NAND
NOR
XNOR

Cada uma possui um comportamento específico, que pode ser representado por uma expressão booleana, uma tabela-verdade e um símbolo lógico.

A compreensão dessas portas é importante para estudar circuitos digitais, processadores, sistemas de comunicação, dispositivos eletrônicos e outros componentes da computação.

📌 Observação

Este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo foi reorganizado e escrito em linguagem simples para facilitar a compreensão e a revisão. Não substitui o material oficial da disciplina.
