# 01 - Início dos estudos Git

## Objetivo

Iniciar os estudos sobre Git, compreendendo o conceito de controle de versão e realizando a criação do primeiro repositório Git local.

---

## Ambiente utilizado

**Sistema operacional:**

Debian Linux

**Terminal utilizado:**

Bash

---

# Conceito aprendido

## O que é Git?

O Git é um sistema de controle de versão distribuído utilizado para acompanhar alterações realizadas em arquivos e projetos.

Ele permite registrar o histórico das modificações, possibilitando:

- acompanhar alterações realizadas;
- recuperar versões anteriores de arquivos;
- criar diferentes linhas de desenvolvimento através de branches;
- organizar projetos;
- facilitar o trabalho colaborativo.

O Git é uma ferramenta muito utilizada no desenvolvimento de software, administração de sistemas e organização de documentação técnica.

---

# Primeiro comando aprendido

## git init

Comando utilizado:

```bash
git init
```

## Função do comando

O comando `git init` é utilizado para transformar um diretório comum em um repositório Git local.

Antes da execução do comando, o diretório funciona apenas como uma pasta comum do sistema.

Após executar:

```bash
git init
```

o Git cria uma estrutura interna responsável pelo gerenciamento do repositório.

---

# Estrutura criada pelo Git

Após inicializar um repositório, é criada uma pasta oculta chamada:

```bash
.git
```

Exemplo:

```
meu_projeto/
├── arquivos_do_projeto
└── .git/
```

A pasta `.git` contém todas as informações internas necessárias para o funcionamento do Git, como:

- histórico de alterações;
- informações dos commits;
- configurações do repositório;
- referências de branches;
- banco de objetos do Git.

A pasta `.git` não deve ser modificada manualmente, pois qualquer alteração incorreta pode comprometer o funcionamento do repositório.

---

# Primeiro teste realizado

Foi criado um diretório para estudos e executado o comando:

```bash
git init
```

Após a execução, foi observado que o diretório passou a ser reconhecido pelo Git como um repositório local.

---

# Conceito importante aprendido

Um diretório comum e um repositório Git possuem diferenças:

## Diretório comum

É apenas uma pasta contendo arquivos.

Exemplo:

```
projeto/
├── arquivo1.txt
└── arquivo2.txt
```

## Repositório Git

É uma pasta que possui a estrutura adicional criada pelo Git:

```
projeto/
├── arquivo1.txt
├── arquivo2.txt
└── .git/
```

A presença da pasta `.git` indica que aquele diretório está sendo gerenciado pelo Git.

---
# Obs:

Veremos na prática no registro 04.

# Observações do aprendizado

Este foi o primeiro registro dos estudos sobre Git.

Neste momento foi compreendido que o Git não é apenas uma ferramenta para armazenar arquivos, mas um sistema capaz de registrar toda a evolução de um projeto.

Este documento faz parte da construção do portfólio técnico de estudos envolvendo Linux, Git, redes e desenvolvimento.

A documentação será utilizada como histórico de aprendizado e também como material de consulta futura.
