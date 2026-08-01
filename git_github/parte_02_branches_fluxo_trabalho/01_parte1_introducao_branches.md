# Tempo estimado de leitura

**15 minutos**

**Nível:** Iniciante

---

# Pré-requisitos

Antes de iniciar este capítulo é recomendado que você tenha concluído toda a Parte 1 — Fundamentos do Git.

É importante compreender os seguintes conceitos da parte 1 (Fundamentos do Git):

- Repositório Git.
- Área de Trabalho (Working Tree).
- Área de Preparação (Staging Area).
- Commit.
- Histórico de commits.

---

# Neste capítulo você aprenderá

- O que é uma Branch.
- Por que as Branches existem.
- Como o Git organiza as Branches.
- O que é a Branch principal.
- O conceito de HEAD.
- Como visualizar as Branches existentes.
- O primeiro comando relacionado às Branches.
- Boas práticas utilizadas profissionalmente.

---

# Introdução

Durante toda a Parte 1 (Fundamentos do Git) trabalhamos diretamente na branch principal do repositório.

Isso foi suficiente para aprender os conceitos básicos do Git, como criar commits, visualizar o histórico e acompanhar as alterações realizadas no projeto.

No entanto, imagine a seguinte situação:

Você está desenvolvendo um sistema utilizado por milhares de pessoas.

Seu chefe pede para criar uma nova funcionalidade.

Ao mesmo tempo, um cliente informa que existe um erro grave que precisa ser corrigido imediatamente.

Como desenvolver a nova funcionalidade sem colocar em risco a versão que já está funcionando?

É exatamente para resolver esse problema que existem as **Branches**.

As Branches permitem criar linhas independentes de desenvolvimento dentro do mesmo repositório.

Dessa forma é possível desenvolver novas funcionalidades, corrigir erros ou realizar testes sem modificar diretamente a versão principal do projeto.

Esse é um dos recursos mais importantes do Git e também um dos mais utilizados por equipes profissionais.

---

# Conceito teórico

## O que é uma Branch?

A palavra **Branch** significa, em inglês:

> **Galho** ou **Ramificação**.

O nome foi escolhido porque representa exatamente a ideia de um galho surgindo a partir do tronco principal de uma árvore.

No Git, uma Branch é uma linha independente de desenvolvimento.

Isso significa que ela possui seu próprio histórico de commits, permitindo que diferentes alterações sejam realizadas de forma isolada.

Enquanto você trabalha em uma Branch, a Branch principal permanece intacta.

Quando o trabalho estiver concluído, as alterações poderão ser unidas novamente.

---

# Exemplo do mundo real

Imagine que você está escrevendo um livro.

A versão publicada representa a Branch principal.

Agora imagine que você deseja escrever um novo capítulo.

Em vez de alterar diretamente o livro publicado, você faz uma cópia apenas para escrever esse novo conteúdo.

Quando terminar a revisão, basta incorporar as alterações ao livro original.

É exatamente isso que uma Branch faz.

Ela cria um ambiente separado para trabalhar com segurança.

---

# Representação visual

Sem Branches:

Projeto

A ─── B ─── C


Todo novo commit será realizado na mesma linha.

---

Com Branches:

A ─── B ─── C (main, master)
│
│
└──── D ─── E (nova-funcionalidade)


Observe que:

- A Branch principal continua existindo.
- A nova funcionalidade possui seus próprios commits.
- Nenhuma alteração interfere na outra.

---

Outro exemplo:

main, master
│
├── login
│
├── cadastro
│
├── relatorios
│
└── correcao-bug


Cada Branch representa um trabalho diferente.

---

# Por que utilizar Branches?

Sem Branches:

- todas as alterações acontecem no mesmo lugar;
- aumenta o risco de erros;
- dificulta desfazer alterações;
- vários desenvolvedores podem modificar os mesmos arquivos simultaneamente.

Com Branches:

- cada funcionalidade possui seu próprio espaço;
- o código principal permanece estável;
- facilita testes;
- facilita revisões;
- reduz conflitos;
- permite que várias pessoas trabalhem ao mesmo tempo.

Por esse motivo, praticamente todas as empresas utilizam Branches em seus projetos.

---

# O que é a Branch principal?

Quando um repositório é criado, o Git define uma Branch principal.

Dependendo da configuração do Git ou da plataforma utilizada, ela poderá receber um dos seguintes nomes:

- `main`
- `master`

Atualmente, o padrão mais utilizado é:

main


Ela representa a versão principal do projeto.

Em ambientes profissionais, normalmente evita-se trabalhar diretamente na Branch principal.

O mais comum é criar uma nova Branch para cada tarefa.

Depois que o trabalho é concluído e revisado, ele é incorporado à Branch principal.

Essa prática reduz significativamente o risco de introduzir erros na versão principal do projeto.

---

# Glossário

| Termo      | Tradução    | Significado no Git                    |
|------------|-------------|---------------------------------------|
| Branch     | Ramificação | Linha independente de desenvolvimento |
| Main       | Principal   | Branch principal do projeto           |
| Master     | Mestre      | Antigo nome da Branch principal       |
| Commit     | Registro    | Ponto salvo no histórico do Git       |
| Repository | Repositório | Local onde o Git armazena o projeto   |
| History    | Histórico   | Sequência de commits realizados       |

---

# O que é o HEAD?

Ao estudar Branches, um novo termo aparece com bastante frequência:

**HEAD**

Esse nome pode parecer estranho no início, mas seu conceito é bastante simples.

Em inglês, **Head** significa:

> Cabeça.

No Git, o **HEAD** é um ponteiro especial que indica onde você está trabalhando naquele momento.

Na maioria das situações, o HEAD aponta para a Branch atualmente selecionada.

Exemplo:

HEAD
│
▼
nova-feature

A ─── B ─── C
│
└──── D


Agora todos os novos commits serão registrados na Branch `nova-feature`.

Podemos imaginar o HEAD como um marcador de página em um livro.

Ele sempre indica exatamente onde você está trabalhando.

---

# Curiosidade

Ao contrário do que muitos iniciantes imaginam, uma Branch **não é uma cópia completa do projeto**.

Internamente, o Git cria apenas uma nova referência para o commit atual.

Isso torna a criação de Branches extremamente rápida e eficiente, mesmo em projetos muito grandes.

Essa é uma das razões pelas quais o Git consegue trabalhar com centenas ou até milhares de Branches sem comprometer significativamente o desempenho.

Esse é o Capítulo 1 (Parte 1) – Nele ainda não executamos nenhum comando porque seguimos um princípio importante: primeiro entender o conceito, depois utilizar a ferramenta.

---

# Próximo capítulo

## Parte 2 — Trabalhando com Branches

No próximo capítulo você aprenderá como criar novas **Branches**, compreenderá as diferentes formas de criar uma ramificação e descobrirá como esse recurso permite desenvolver novas funcionalidades de forma organizada, segura e independente da branch principal.

Também conhecerá as boas práticas utilizadas por desenvolvedores e equipes profissionais para organizar o fluxo de trabalho utilizando Branches.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

