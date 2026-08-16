
## 2. Tópicos e subtópicos — super resumido

```markdown
# Capítulo 5 — Álgebra de Boole e funções booleanas

## 1. Álgebra de Boole
- Valores:
  - `0` → falso/desligado
  - `1` → verdadeiro/ligado
- Criada a partir dos estudos de George Boole.
- Base da lógica dos circuitos digitais.

## 2. Aplicação
- Circuitos digitais.
- Processadores.
- ULA.
- Somadores.
- Subtratores.
- Comparadores.
- Síntese de circuitos lógicos.

## 3. Conceitos
- Variável booleana → assume `0` ou `1`.
- Função booleana → entradas → uma saída.
- Portas lógicas → implementam operações booleanas.
- Tabela-verdade → mostra todas as combinações de entradas e saídas.

## 4. Portas lógicas

### OR
- `S = X1 + X2`
- Saída `1` se qualquer entrada for `1`.
- `0` somente quando todas forem `0`.

### AND
- `S = X1 × X2`
- Saída `1` somente quando todas forem `1`.

### NOT
- Inverte a entrada.
- `0 → 1`
- `1 → 0`

### XOR
- OU exclusivo.
- Saída `1` quando entradas são diferentes.
- Usada em verificação de paridade.

### NAND
- AND invertida.
- Saída `0` somente quando todas forem `1`.
- Nos demais casos → `1`.

### NOR
- OR invertida.
- Saída `1` somente quando todas forem `0`.

### XNOR
- XOR invertida.
- Saída `1` quando entradas são iguais.

## 5. Paridade
- Utilizada para detectar determinados erros de transmissão.
- XOR pode ser usada em geradores e verificadores de paridade.
- Paridade par:
  - `E = 0` → sem erro detectado.
  - `E = 1` → erro detectado.

## 6. Teoremas de De Morgan
- Usados para simplificar expressões booleanas.
- Auxiliam no desenvolvimento de circuitos digitais.
- `NOT(AND) = OR dos negados`
- `NOT(OR) = AND dos negados`

## 7. Memorização rápida
- OR → qualquer `1`.
- AND → todos `1`.
- NOT → inverte.
- XOR → diferentes.
- NAND → AND invertida.
- NOR → OR invertida.
- XNOR → iguais.

## 8. Importância
- Análise de circuitos.
- Projeto de circuitos.
- Simplificação lógica.
- Processadores.
- Sistemas digitais.
- Comunicação de dados.
- Detecção de erros.

---

## 📌 Observação

Este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo foi reorganizado e escrito em linguagem simples para facilitar a compreensão e a revisão. Não substitui o material oficial da disciplina.
