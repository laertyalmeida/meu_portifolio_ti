<<<<<<< HEAD
# LPIC-1 - Módulo 01

## 1. CPU e Arquitetura — Tópicos para Revisão

### 1.1 CPU

* **CPU — Central Processing Unit**

  * Unidade Central de Processamento.
  * Também chamada de processador.
  * Executa as instruções dos programas.

### 1.2 Arquitetura

* Conjunto de regras que define como a CPU:

  * interpreta instruções;
  * processa dados;
  * utiliza registradores;
  * acessa a memória;
  * trabalha com endereços;
  * organiza seu funcionamento interno.

### 1.3 Elementos relacionados à CPU

* **Instruções**

  * Operações que a CPU consegue executar.
* **Registradores**

  * Pequenas áreas de armazenamento dentro da CPU.
  * Extremamente rápidas.
* **Cache**

  * Memória muito rápida.
  * Reduz o tempo de acesso a dados e instruções.
* **RAM**

  * Memória principal.
  * Armazena temporariamente programas e dados em uso.
* **Núcleos (Cores)**

  * Unidades de processamento dentro da CPU.
  * Permitem executar tarefas em paralelo.

### 1.4 Arquitetura x86

* Família de arquiteturas de processadores.
* Evolução:

  * **16 bits**
  * **32 bits → IA-32 / i386**
  * **64 bits → x86-64 / AMD64**

### 1.5 x86-64 / AMD64

* Arquitetura x86 de 64 bits.
* **AMD — Advanced Micro Devices**

  * Empresa que desenvolveu a extensão x86 para 64 bits.
* Também encontrada como:

  * `x86_64`
  * `x86-64`
  * `AMD64`
* Não é exclusiva de processadores AMD.

  * Processadores Intel também utilizam x86-64.

### 1.6 Arquitetura ARM

* Família de arquiteturas baseada na filosofia **RISC**.
* **RISC — Reduced Instruction Set Computer**

  * Computador com conjunto reduzido de instruções.
* Características:

  * instruções mais simples;
  * eficiência;
  * menor consumo de energia;
  * menor geração de calor.

### 1.7 ARM32 e AArch64

* **ARM**

  * Arquitetura de 32 bits.
* **AArch64 / ARM64**

  * Arquitetura ARM de 64 bits.

### 1.8 32 bits x 64 bits

* Relacionado à forma como a arquitetura trabalha com:

  * dados;
  * registradores;
  * endereços de memória.
* **64 bits**

  * Permite trabalhar com endereços de memória muito maiores.
  * Não significa simplesmente "duas vezes mais rápido".

### 1.9 Fluxo básico

```text
Programa
   ↓
Sistema Operacional
   ↓
Instruções
   ↓
Arquitetura
   ↓
CPU interpreta
   ↓
CPU executa
```

### 1.10 Bits e instruções

```text
Bits
 ↓
010101...
 ↓
Instrução
 ↓
Arquitetura interpreta
 ↓
CPU executa
```

### 1.11 Comparação das principais arquiteturas

```text
x86
 ├── i386 / i686 → 32 bits
 └── x86-64 / AMD64 → 64 bits

ARM
 ├── ARM32 → 32 bits
 └── AArch64 / ARM64 → 64 bits
```

### 1.12 Conceito principal

* **Arquitetura = regras**
* **Instrução = operação**
* **CPU = executa**
* **Registrador = armazenamento rápido dentro da CPU**
* **Cache = armazenamento muito rápido próximo da CPU**
* **RAM = memória principal temporária**
* **Core = unidade de processamento**
* **Bits = representação básica das informações**

### 📌 Para memorizar

> **A arquitetura define as regras; as instruções seguem essas regras; e a CPU executa as instruções.**

=======
# LPIC-1 — Módulo 01

## 1. Arquitetura do Sistema
- CPU e arquitetura
- BIOS/UEFI
- Dispositivos
- Periféricos
- `/proc`
- `/sys`
- `/dev`

## 2. Instalação e Gerenciamento de Pacotes
- Debian e `dpkg`
- `apt`
- Repositórios
- Dependências
- Pacotes `.deb`

## 3. Comandos GNU e Unix
- `ls`
- `cd`
- `cp`
- `mv`
- `rm`
- `find`
- `grep`
- `sort`
- `cut`
- `sed`
- `awk`
- `xargs`
- Redirecionamento
- Pipes

## 4. Dispositivos, Sistemas de Arquivos e Hierarquia
- `/`
- `/boot`
- `/etc`
- `/home`
- `/var`
- `/usr`
- `/tmp`
- `/dev`
- `/proc`
- `/sys`
- `/mnt`
- `/media`

## 5. Gerenciamento de Arquivos
- Inodes
- Links físicos
- Links simbólicos
- Permissões
- `chmod`
- `chown`
- `chgrp`

## 6. Shell e Scripts
- Bash
- Variáveis
- `PATH`
- Comandos internos e externos
- Histórico
- Aliases
- Expansões
- Variáveis de ambiente

## 7. Processos
- `ps`
- `top`
- `pgrep`
- `kill`
- `killall`
- `jobs`
- `bg`
- `fg`
- Processos em primeiro e segundo plano

## 8. Expressões Regulares
- `grep`
- Regex básica
- `^`
- `$`
- `.`
- `*`
- `[]`
- `[^]`

## Método de Estudo

Para cada tópico:

1. Teoria
2. Exemplos práticos no Debian
3. Comandos para praticar
4. Pegadinhas da prova
5. Questões LPIC-1
6. Mini simulado ao final do bloco
>>>>>>> 5fc8a47 (Continua resumo jonas)
