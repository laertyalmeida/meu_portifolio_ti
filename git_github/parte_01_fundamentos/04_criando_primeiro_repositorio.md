# Git e GitHub — Guia de Estudos

> **"Conhecimento só tem valor quando é compartilhado."**

---

## Sobre esta documentação

Este material foi desenvolvido durante minha jornada de aprendizado em **Git** e **GitHub**.

O objetivo desta documentação não é apenas registrar comandos, mas compreender o funcionamento do Git de forma gradual, explicando os conceitos, os motivos de cada comando existir e como eles são utilizados no dia a dia.

Cada capítulo foi escrito com linguagem simples, exemplos práticos e explicações detalhadas, servindo tanto como material de estudo quanto como documentação de referência para consultas futuras.

---

# Informações do capítulo

| Campo                   | Informação                         |
| ----------------------- | ---------------------------------- |
| **Capítulo**            | 04                                 |
| **Título**              | Criando o Primeiro Repositório Git |
| **Autor**               | Laerte Costa                       |
| **Sistema Operacional** | Debian GNU/Linux                   |
| **Terminal**            | Bash                               |
| **Distribuição**        | Debian                             |
| **Nível**               | Iniciante                          |
| **Última atualização**  | Julho de 2026                      |

---

# Objetivo

Neste capítulo será criado o primeiro repositório Git.

Ao final deste estudo você será capaz de:

* compreender o que é um repositório Git;
* diferenciar projeto e repositório;
* criar um diretório para um novo projeto;
* navegar entre diretórios utilizando o terminal;
* inicializar um repositório utilizando `git init`;
* visualizar a pasta oculta `.git`;
* interpretar a saída do comando `git status`;
* compreender o significado de arquivos **Untracked** (Não Rastreados).

---

# Pré-requisitos

Para acompanhar este capítulo é recomendado possuir conhecimentos básicos sobre:

* Estrutura de diretórios do Linux;
* Navegação entre diretórios utilizando `cd`;
* Criação de diretórios utilizando `mkdir`;
* Visualização de arquivos utilizando `ls`;
* Git instalado e configurado no sistema.

---

# Estrutura padrão da documentação

Todos os capítulos deste guia seguirão a mesma organização para facilitar o estudo, a revisão e futuras consultas.

1. Informações do capítulo
2. Objetivo
3. Pré-requisitos *(quando necessário)*
4. Conceito teórico
5. Explicação detalhada dos comandos
6. Entendendo cada parâmetro
7. Exemplo prático passo a passo
8. Explicação da saída do terminal
9. Boas práticas
10. Cuidados e erros comuns
11. Curiosidades técnicas
12. Resumo
13. Revisão rápida
14. Palavras-chave
15. Próximo capítulo

Essa padronização permite que qualquer capítulo possa ser estudado de forma organizada e previsível.

---

# Convenções utilizadas

Sempre que um comando, termo técnico ou palavra em inglês aparecer pela primeira vez, será apresentado também o seu significado em português.

Exemplos:

| Inglês                              | Português                                          |
| ----------------------------------- | -------------------------------------------------- |
| **Repository**                      | Repositório                                        |
| **Project**                         | Projeto                                            |
| **Version Control**                 | Controle de Versão                                 |
| **Working Directory**               | Diretório de Trabalho                              |
| **Current Directory**               | Diretório Atual                                    |
| **Hidden Files**                    | Arquivos Ocultos                                   |
| **Untracked**                       | Não Rastreado                                      |
| **Tracked**                         | Rastreado                                          |
| **Staging Area**                    | Área de Preparação                                 |
| **Working Tree**                    | Árvore de Trabalho                                 |
| **Commit**                          | Registro permanente de alterações                  |
| **Branch**                          | Ramificação                                        |
| **Merge**                           | Mesclar                                            |
| **Clone**                           | Clonar                                             |
| **Push**                            | Enviar alterações para o repositório remoto        |
| **Pull**                            | Buscar e integrar alterações do repositório remoto |
| **Fetch**                           | Buscar alterações do repositório remoto            |
| **Checkout**                        | Alternar entre branches ou restaurar arquivos      |
| **Initialize (`init`)**             | Inicializar                                        |
| **Status**                          | Estado ou Situação                                 |
| **Make Directory (`mkdir`)**        | Criar Diretório                                    |
| **Change Directory (`cd`)**         | Alterar Diretório                                  |
| **Print Working Directory (`pwd`)** | Exibir o Diretório de Trabalho Atual               |
| **List (`ls`)**                     | Listar Arquivos e Diretórios                       |
| **Hidden (`-a`)**                   | Mostrar Arquivos Ocultos                           |
| **Long Format (`-l`)**              | Exibir Informações Detalhadas                      |

---

# Filosofia deste material

Este guia foi desenvolvido seguindo alguns princípios.

* Aprender antes de decorar.
* Compreender antes de executar.
* Documentar tudo o que for aprendido.
* Explicar os conceitos de forma simples e objetiva.
* Relacionar teoria e prática.
* Construir uma base sólida para estudos futuros, certificações e projetos profissionais.

O objetivo é formar conhecimento consistente, e não apenas memorizar comandos.

---

# Índice da coleção

## Fundamentos

* 01 - Início do Git
* 02 - Instalação do Git no Debian
* 03 - Configuração da Identidade do Git
* 04 - Criando o Primeiro Repositório

## Controle de versões

* 05 - Git Add
* 06 - Git Commit
* 07 - Git Log
* 08 - Git Diff
* 09 - Git Restore
* 10 - Git Reset

## Branches

* 11 - Branches
* 12 - Merge
* 13 - Conflitos de Merge
* 14 - Rebase *(opcional para iniciantes)*

## GitHub

* 15 - Criando uma Conta no GitHub
* 16 - Criando um Repositório Remoto
* 17 - Git Clone
* 18 - Git Push
* 19 - Git Pull
* 20 - Git Fetch

## Projetos Práticos

* Versionando um Projeto Real
* Trabalhando com Branches
* Simulando Trabalho em Equipe
* Fluxo de Trabalho Completo com Git e GitHub

---

# Observação

Este material encontra-se em constante evolução.

Novos capítulos serão adicionados conforme o avanço dos estudos, mantendo sempre a mesma organização, linguagem e padrão de documentação.

---

**"Conhecimento só tem valor quando é compartilhado."**
— Laerte Costa

