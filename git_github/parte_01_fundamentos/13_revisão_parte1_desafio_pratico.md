# Tempo estimado de leitura

**15 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* Revisar os principais conceitos aprendidos na Parte 1.
* Identificar a função dos principais comandos Git estudados.
* Relembrar o fluxo básico de trabalho do Git.
* Praticar os comandos em um pequeno projeto.
* Testar a criação, alteração, preparação, registro e restauração de arquivos.

---

# Git e GitHub — Guia de Estudos

---

# Informações do capítulo

| Campo                   | Informação                           |
| ----------------------- | ------------------------------------ |
| **Capítulo**            | 13                                   |
| **Título**              | Revisão da Parte 1 e Desafio Prático |
| **Autor**               | Laerte Costa                         |
| **Sistema Operacional** | Debian GNU/Linux                     |
| **Terminal**            | Bash                                 |
| **Última atualização**  | Agosto de 2026                       |

---

# Objetivo deste capítulo

Este capítulo encerra a **Parte 1 — Fundamentos do Git**.

Aqui você vai revisar os principais comandos estudados e realizar um pequeno desafio prático utilizando o fluxo básico do Git.

A ideia não é apenas memorizar comandos, mas entender **quando e por que utilizar cada um deles**.

---

# Pré-requisitos

É recomendado ter concluído os capítulos anteriores da Parte 1.

---

# Revisão da Parte 1

Durante esta primeira parte, você aprendeu os conceitos básicos necessários para começar a trabalhar com Git.

O principal objetivo foi entender como o Git acompanha as alterações de um projeto, desde a criação dos arquivos até o registro dessas alterações no histórico.

---

# Principais comandos estudados

## Criando um repositório

```bash
git init
```

Cria um novo repositório Git dentro do diretório atual.

---

## Configurando a identidade

```bash
git config
```

Permite configurar informações utilizadas pelo Git.

Exemplo:

```bash
git config --global user.name
git config --global user.email
```

Essas informações são utilizadas nos commits.

---

## Verificando o estado do repositório

```bash
git status
```

Mostra o estado atual dos arquivos.

Com ele, podemos identificar:

* arquivos novos;
* arquivos modificados;
* arquivos preparados para commit;
* arquivos removidos.

---

## Comparando alterações

```bash
git diff
```

Mostra alterações que estão na Área de Trabalho e ainda não foram adicionadas à Área de Preparação.

Para visualizar alterações que já foram preparadas:

```bash
git diff --staged
```

---

## Preparando arquivos

```bash
git add arquivo
```

Adiciona um arquivo à Área de Preparação (*Staging Area*).

Também podemos utilizar:

```bash
git add .
```

para adicionar os arquivos do diretório atual.

---

## Registrando alterações

```bash
git commit -m "mensagem"
```

Registra as alterações que estão na Área de Preparação no histórico do projeto.

---

## Ignorando arquivos

O arquivo:

```text
.gitignore
```

define arquivos e diretórios que não devem ser adicionados ao repositório.

Exemplo:

```text
*.log
*.tmp
cache/
```

---

## Renomeando arquivos

```bash
git mv arquivo_antigo arquivo_novo
```

Renomeia ou move um arquivo e prepara essa alteração para o próximo commit.

---

## Removendo arquivos

```bash
git rm arquivo
```

Remove um arquivo do projeto e prepara essa remoção para o próximo commit.

---

## Restaurando alterações

Para descartar uma alteração realizada em um arquivo:

```bash
git restore arquivo
```

Para retirar um arquivo da Área de Preparação sem perder sua alteração:

```bash
git restore --staged arquivo
```

---

## Consultando o histórico

```bash
git log
```

Mostra o histórico de commits do projeto.

Para uma visualização resumida:

```bash
git log --oneline
```

Para visualizar detalhes de um commit específico:

```bash
git show <commit>
```

---

# As três áreas do Git

Durante a Parte 1, você também aprendeu que o Git organiza o trabalho em três áreas principais:

```text
Área de Trabalho
       │
       │ git add
       ▼
Área de Preparação
       │
       │ git commit
       ▼
Repositório
```

### Área de Trabalho

Onde os arquivos são criados e modificados.

### Área de Preparação

Onde você escolhe quais alterações farão parte do próximo commit.

### Repositório

Onde os commits ficam registrados no histórico.

---

# O fluxo básico aprendido

O fluxo principal estudado nesta primeira parte pode ser representado assim:

```text
Criar ou modificar
        ↓
   git status
        ↓
     git diff
        ↓
      git add
        ↓
git diff --staged
        ↓
    git commit
        ↓
     git log
```

Quando necessário, também podemos utilizar:

```text
git restore
```

para desfazer alterações ou recuperar arquivos.

---

# A importância da prática

Aprender Git não significa apenas decorar comandos.

É importante entender:

* qual problema cada comando resolve;
* em qual área do Git ele atua;
* o que acontece depois de executá-lo;
* como verificar o resultado.

A prática ajuda a transformar os comandos em conhecimento.

Por isso, agora vamos colocar em prática o que foi estudado.

---

# Desafio prático

O objetivo deste exercício é criar um pequeno projeto e utilizar o fluxo básico do Git.

Você deverá:

1. criar um diretório;
2. inicializar um repositório;
3. criar um arquivo;
4. verificar o estado;
5. criar um commit;
6. modificar o arquivo;
7. revisar a alteração;
8. preparar a alteração;
9. criar outro commit;
10. consultar o histórico;
11. testar a restauração de uma alteração.

---

# 1. Criando o diretório do projeto

No terminal, execute:

```bash
mkdir projeto_git
```

Depois entre no diretório:

```bash
cd projeto_git
```

---

# 2. Inicializando o repositório

Execute:

```bash
git init
```

O Git criará o diretório oculto:

```text
.git/
```

Esse diretório contém as informações necessárias para o Git controlar o projeto.

---

# 3. Criando o primeiro arquivo

Crie o arquivo:

```bash
touch README.md
```

Depois abra o arquivo no editor de sua preferência e coloque:

```text
# Meu Projeto

Primeira versão do projeto.
```

Salve o arquivo.

---

# 4. Verificando o estado

Execute:

```bash
git status
```

Observe como o Git apresenta o arquivo `README.md`.

Ele deverá aparecer como um arquivo **não rastreado** (*untracked*).

---

# 5. Preparando o arquivo

Adicione o arquivo à Área de Preparação:

```bash
git add README.md
```

Depois verifique novamente:

```bash
git status
```

Agora o arquivo deverá aparecer como preparado para o próximo commit.

---

# 6. Criando o primeiro commit

Registre a primeira versão:

```bash
git commit -m "Cria arquivo inicial do projeto"
```

Depois verifique:

```bash
git status
```

O esperado é:

```text
nothing to commit, working tree clean
```

---

# 7. Modificando o arquivo

Abra novamente o `README.md` e altere seu conteúdo para:

```text
# Meu Projeto

Primeira versão do projeto.

Nova alteração realizada.
```

Salve o arquivo.

---

# 8. Verificando a alteração

Execute:

```bash
git status
```

Agora o arquivo deverá aparecer como modificado.

Depois utilize:

```bash
git diff
```

Observe quais linhas foram adicionadas.

Você deverá identificar o conteúdo que existia antes e o novo conteúdo.

---

# 9. Preparando a alteração

Adicione o arquivo:

```bash
git add README.md
```

Agora verifique o que está preparado:

```bash
git diff --staged
```

Esse comando mostra as alterações que serão incluídas no próximo commit.

---

# 10. Criando o segundo commit

Registre a alteração:

```bash
git commit -m "Atualiza documentação do projeto"
```

Depois execute:

```bash
git status
```

O diretório deverá estar novamente limpo.

---

# 11. Consultando o histórico

Agora consulte os commits criados:

```bash
git log --oneline
```

Você deverá encontrar algo parecido com:

```text
b7a82c1 Atualiza documentação do projeto
a3f91d2 Cria arquivo inicial do projeto
```

Os hashes serão diferentes no seu computador.

O importante é identificar os dois commits realizados.

---

# 12. Testando o `git restore`

Agora faça uma nova alteração no `README.md`.

Por exemplo, adicione:

```text
Esta alteração será descartada.
```

Salve o arquivo.

Verifique:

```bash
git status
```

Depois visualize a alteração:

```bash
git diff
```

Agora descarte a alteração:

```bash
git restore README.md
```

Verifique novamente:

```bash
git status
```

O arquivo deverá voltar ao estado do último commit.

---

# 13. Conferindo o resultado

Execute:

```bash
git status
```

O resultado esperado é semelhante a:

```text
nothing to commit, working tree clean
```

Depois consulte novamente:

```bash
git log --oneline
```

Os dois commits realizados anteriormente continuarão no histórico.

Isso mostra uma característica importante do Git:

> Uma alteração descartada com `git restore` não altera os commits que já foram registrados.

---

# 14. Desafio extra

Se quiser praticar um pouco mais, tente realizar as seguintes tarefas sem consultar os capítulos anteriores:

### Tarefa 1

Crie um arquivo:

```text
notas.txt
```

Depois verifique seu estado com:

```bash
git status
```

### Tarefa 2

Adicione o arquivo à Área de Preparação:

```bash
git add notas.txt
```

### Tarefa 3

Crie um commit.

Escolha uma mensagem que explique o que foi feito.

### Tarefa 4

Modifique o arquivo novamente.

Use:

```bash
git diff
```

para visualizar a alteração.

### Tarefa 5

Adicione a alteração:

```bash
git add notas.txt
```

Depois utilize:

```bash
git diff --staged
```

### Tarefa 6

Crie outro commit.

### Tarefa 7

Consulte o histórico:

```bash
git log --oneline
```

---

# Teste seus conhecimentos

Antes de avançar para a Parte 2, tente responder às perguntas abaixo sem consultar os capítulos anteriores.

| Comando             | Pergunta                       |
| ------------------- | ------------------------------ |
| `git init`          | Para que serve?                |
| `git status`        | O que ele mostra?              |
| `git diff`          | O que ele permite visualizar?  |
| `git add`           | Para onde o arquivo é enviado? |
| `git diff --staged` | O que ele mostra?              |
| `git commit`        | O que ele registra?            |
| `git log`           | Para que serve?                |
| `git restore`       | O que ele pode desfazer?       |
| `.gitignore`        | Para que serve?                |
| `git mv`            | O que ele faz?                 |
| `git rm`            | O que ele faz?                 |

---

# Gabarito para revisão

Se você conseguiu responder sozinho, ótimo.

Caso tenha dificuldade, utilize esta tabela para revisar:

| Comando             | Função                                                |
| ------------------- | ----------------------------------------------------- |
| `git init`          | Cria um repositório Git.                              |
| `git status`        | Mostra o estado atual do repositório.                 |
| `git diff`          | Mostra alterações ainda não preparadas.               |
| `git add`           | Adiciona alterações à Área de Preparação.             |
| `git diff --staged` | Mostra alterações que estão na Área de Preparação.    |
| `git commit`        | Registra as alterações no histórico.                  |
| `git log`           | Mostra o histórico de commits.                        |
| `git restore`       | Restaura arquivos e pode descartar alterações locais. |
| `.gitignore`        | Define arquivos que devem ser ignorados pelo Git.     |
| `git mv`            | Renomeia ou move arquivos.                            |
| `git rm`            | Remove arquivos e prepara a remoção.                  |

---

# O que foi aprendido

Ao concluir este capítulo, você revisou:

* ✅ Criação de um repositório com `git init`.
* ✅ Verificação do estado com `git status`.
* ✅ Comparação de alterações com `git diff`.
* ✅ Preparação de arquivos com `git add`.
* ✅ Revisão da Área de Preparação com `git diff --staged`.
* ✅ Criação de commits com `git commit`.
* ✅ Consulta do histórico com `git log`.
* ✅ Restauração de arquivos com `git restore`.
* ✅ Uso básico do `.gitignore`.
* ✅ Renomeação com `git mv`.
* ✅ Remoção com `git rm`.
* ✅ Relação entre Área de Trabalho, Área de Preparação e Repositório.

---

# Resumo da Parte 1

Nesta primeira parte, você construiu a base para começar a trabalhar com Git.

Você aprendeu que o Git não serve apenas para salvar arquivos, mas para **acompanhar a evolução de um projeto**.

O fluxo principal pode ser resumido assim:

```text
Criar
  ↓
Modificar
  ↓
Verificar
  ↓
Revisar
  ↓
Preparar
  ↓
Registrar
  ↓
Consultar histórico
  ↓
Restaurar quando necessário
```

Agora você já conhece os principais comandos necessários para trabalhar com um repositório Git de forma básica.

---

# Próxima etapa

## Parte 2 — Trabalhando com Branches

Na próxima parte, você aprenderá um dos recursos mais importantes do Git: as **branches**.

Você aprenderá a:

* criar branches;
* alternar entre branches;
* desenvolver alterações separadamente;
* organizar diferentes linhas de trabalho;
* entender como branches ajudam no desenvolvimento de projetos.

O fluxo de estudo continuará evoluindo:

```text
Parte 1
Fundamentos
    ↓
Parte 2
Branches
    ↓
Parte 3
GitHub
```

---

# 📚 Fonte de estudo

Este resumo foi elaborado a partir dos estudos e da prática do autor sobre **Git e GitHub**, utilizando os conteúdos da disciplina e materiais de estudo como referência.

**Observação:** este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo original das disciplinas e materiais utilizados como referência não deve ser reproduzido ou disponibilizado integralmente neste repositório.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

