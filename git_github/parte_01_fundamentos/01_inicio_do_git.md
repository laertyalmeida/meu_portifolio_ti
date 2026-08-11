# 📚 Capítulo 01 — Início dos Estudos com Git

## 🎯 Objetivo

Neste capítulo, vamos entender:

* O que é Git;
* O que é controle de versão;
* O que significa Git ser distribuído;
* Qual a diferença entre Git e GitHub;
* Onde o Git pode ser usado;
* Por que aprender Git.

---

# 1. O que é Git?

O **Git** é uma ferramenta usada para **controlar as mudanças de um projeto ao longo do tempo**.

Imagine que você está criando um projeto e modifica vários arquivos.

Sem o Git, você poderia acabar criando vários arquivos:

```text
projeto_final
projeto_final_2
projeto_final_agora_vai
projeto_final_definitivo
```

😅 Isso pode virar uma bagunça.

Com o Git, as alterações ficam registradas em um **histórico**.

Assim, você pode:

* Ver o que mudou;
* Saber quando uma alteração foi feita;
* Comparar versões;
* Voltar para uma versão anterior;
* Trabalhar em diferentes partes do projeto;
* Trabalhar com outras pessoas.

📌 **Para lembrar:**

> **Git = ferramenta para controlar as versões de um projeto.**

---

# 2. O que é controle de versão?

**Controle de versão** é uma forma de acompanhar as mudanças que acontecem em um projeto.

Imagine que você começou um arquivo e fez várias alterações:

```text
Versão 1
   ↓
Versão 2
   ↓
Versão 3
   ↓
Versão 4
```

O Git registra essas mudanças.

Se alguma coisa der errado, você consegue consultar o histórico e entender o que aconteceu.

### Exemplo

Você está criando um programa.

Na segunda-feira, ele funciona:

```text
Programa funcionando
```

Na terça-feira, você faz algumas alterações:

```text
Programa com novos recursos
```

Na quarta-feira, uma alteração causa um problema:

```text
Programa com erro
```

Com o Git, você pode consultar o histórico para descobrir **qual alteração causou o problema** e, quando necessário, voltar para uma versão anterior.

📌 **Para lembrar:**

> **Controle de versão = registrar e acompanhar as mudanças de um projeto.**

---

# 3. O que significa Git ser distribuído?

O Git é um sistema de controle de versão **distribuído**.

Isso significa que cada computador que possui uma cópia do repositório Git pode ter **o projeto e seu histórico de alterações**.

Por exemplo:

```text
Computador 1
     │
     ├── Projeto
     └── Histórico

Computador 2
     │
     ├── Projeto
     └── Histórico
```

Isso permite trabalhar em várias operações sem depender o tempo todo da internet.

📌 **Para lembrar:**

> **Distribuído = cada cópia do repositório pode possuir o projeto e seu histórico.**

---

# 4. Git e GitHub são a mesma coisa?

Não.

Eles trabalham juntos, mas são coisas diferentes.

## Git

O **Git** é o programa de controle de versão que você instala no computador.

Ele funciona principalmente pelo terminal.

Exemplo:

```bash
git status
```

---

## GitHub

O **GitHub** é uma plataforma online onde podemos armazenar e compartilhar repositórios Git.

Ele também facilita:

* Compartilhar projetos;
* Trabalhar em equipe;
* Guardar uma cópia do projeto online;
* Criar um portfólio;
* Acompanhar projetos.

Uma forma simples de entender:

```text
Git
↓
Controla as versões no computador

GitHub
↓
Hospeda e compartilha o repositório online
```

📌 **Para lembrar:**

> **Git = ferramenta de controle de versão.**

> **GitHub = plataforma online que trabalha com repositórios Git.**

---

# 5. Onde o Git pode ser usado?

O Git ficou muito conhecido no desenvolvimento de software, mas ele não serve apenas para programadores.

Podemos utilizá-lo para controlar diferentes tipos de arquivos e projetos.

Por exemplo:

* 🐍 Programas em Python;
* 💻 Scripts;
* 🐧 Configurações do Linux;
* 🌐 Projetos de redes;
* 📚 Documentação;
* 📝 Arquivos Markdown;
* ⚙️ Automação;
* 🏗️ Projetos de infraestrutura;
* 🎓 Estudos pessoais.

No meu caso, posso utilizar o Git para organizar meus estudos e manter meu **portfólio de tecnologia**.

---

# 6. Por que aprender Git?

O Git ajuda a organizar melhor nossos projetos.

Mesmo quando estamos estudando sozinhos, ele pode ser muito útil.

Com ele podemos:

* Acompanhar nossa evolução;
* Guardar o histórico dos projetos;
* Testar mudanças com mais segurança;
* Recuperar versões anteriores;
* Organizar nossos arquivos;
* Compartilhar nossos projetos.

Além disso, Git é muito utilizado no mercado de tecnologia.

Por isso, aprender Git é importante para quem trabalha ou pretende trabalhar com:

* Desenvolvimento;
* Linux;
* Redes;
* DevOps;
* Infraestrutura;
* Automação;
* Administração de sistemas.

---

# 7. Git no Linux

No Linux, o Git pode ser utilizado diretamente pelo **terminal**.

Depois de instalado, podemos executar comandos como:

```bash
git --version
```

Esse comando mostra a versão do Git instalada no computador.

Exemplo:

```text
git version 2.x.x
```

📌 **Significado do comando:**

```text
git
```

Executa o Git.

```text
--version
```

Pede para o Git mostrar sua versão.

---

# 8. Curiosidade

O Git foi criado em **2005 por Linus Torvalds**, conhecido principalmente por ter criado o kernel Linux.

O Git foi desenvolvido para ajudar no controle do desenvolvimento do kernel Linux.

---

# 🧠 Resumo rápido

```text
GIT
│
├── 📚 Controle de versão
│   └── Registra as alterações
│
├── 💻 Distribuído
│   └── Cada cópia pode possuir o histórico
│
├── 🌐 GitHub
│   └── Hospeda e compartilha repositórios
│
├── 🐧 Linux
│   └── Pode ser usado pelo terminal
│
└── 🚀 Utilização
    ├── Programação
    ├── Scripts
    ├── Documentação
    ├── Estudos
    ├── Redes
    └── Infraestrutura
```

---

# 🎯 O que você aprendeu

Neste capítulo você aprendeu que:

* **Git** é uma ferramenta de controle de versão;
* O controle de versão registra as alterações de um projeto;
* Git é um sistema distribuído;
* **Git e GitHub não são a mesma coisa**;
* O Git pode ser usado em vários tipos de projetos;
* No Linux, o Git pode ser utilizado pelo terminal;
* Git é uma ferramenta importante para quem trabalha ou pretende trabalhar com tecnologia.

---

# 📌 Próximo capítulo

## Capítulo 02 — Instalação do Git no Debian

No próximo capítulo, vamos instalar o Git no Debian, verificar se ele está funcionando e preparar o ambiente para começar a utilizá-lo na prática.

---

## 📚 Fonte de estudo

Este material foi elaborado a partir dos meus estudos sobre **Git e controle de versão**, combinando o conteúdo estudado com **práticas realizadas por mim no Debian GNU/Linux**.

Os exemplos e comandos apresentados foram utilizados durante meus estudos para facilitar a compreensão e registrar minha evolução.

> **Observação:** este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo original da disciplina/material de referência não foi reproduzido integralmente.

