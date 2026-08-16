# Arquitetura de Computador – Hardware

## 1. Hardware

* Parte física do computador.
* Executa operações lógicas, aritméticas e manipulação de dados.
* Depende de instruções precisas.

### Componentes principais

* CPU
* Memória
* E/S (I/O)
* Barramentos

## 2. CPU

* Unidade Central de Processamento.
* Processa dados e instruções.
* Controla operações do computador.

### Componentes

* **ULA/ALU:** cálculos e operações lógicas.
* **UC:** busca, interpreta e controla instruções.
* **Registradores:** armazenamento temporário interno.

### Unidades do computador

* Entrada → recebe dados.
* Memória → armazena dados/instruções.
* UC → interpreta e controla.
* ULA → processa.
* Saída → apresenta resultados.

## 3. Memória

* Retém informações.
* Pode ser temporária ou permanente.

### Hierarquia

1. Registradores
2. Cache
3. RAM
4. Armazenamento externo
5. Mídias removíveis

### Conceitos

* **Palavra:** conjunto de bits associado à arquitetura.
* **Unidade endereçável:** menor unidade identificada por endereço.
* **Unidade de transferência:** quantidade transferida por operação.

### Tipos

* **Volátil:** perde dados sem energia.

  * RAM
  * Cache
  * Registradores
* **Não volátil:** mantém dados sem energia.

  * Flash
  * HD

### Memórias

* **Principal:** RAM; usada diretamente durante o processamento.
* **Secundária:** armazenamento permanente e de grande capacidade.

## 4. Entrada/Saída – E/S ou I/O

* Interface entre computador e dispositivos externos.
* Gerencia transferência de dados.

### Tipos

* E/S programada.
* E/S por interrupção.
* DMA → acesso direto à memória.

### Funções

* Comunicação com CPU.
* Controle e temporização.
* Comunicação com dispositivos.
* Transferência de dados.
* Detecção de erros.

## 5. Barramentos

* Comunicação entre componentes.
* Transportam dados, endereços e sinais.

### Controladores

* Controlam dispositivos de E/S.
* Permitem acesso ao barramento.
* Podem utilizar DMA.
* Podem gerar interrupções.

### Árbitro

* Organiza o acesso ao barramento.
* Evita conflitos entre componentes.

## 6. PCI e PCIe

* **PCI:** barramento para componentes periféricos.
* **PCIe:** evolução com comunicação serial.
* Utiliza **lanes** para aumentar a largura de banda.
* Muito utilizado em placas gráficas e outros periféricos.

## 7. Fluxo básico

**Entrada → Memória → CPU → Processamento → Memória/Saída**

* UC busca e interpreta.
* ULA processa.
* Registradores armazenam temporariamente.
* Barramentos interligam.
* E/S comunica com dispositivos externos.

📌 **Observação:** Este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo foi reorganizado e escrito em linguagem simples para facilitar a compreensão e a revisão. Não substitui o material oficial da disciplina.

