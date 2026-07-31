# Tempo estimado de leitura

**15 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* Revisar os principais conceitos aprendidos na Parte 1.
* Identificar a função de cada comando Git estudado.
* Entender a importância da prática no aprendizado.
* Realizar um desafio utilizando o fluxo completo de trabalho com Git.

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
| **Última atualização**  | Julho de 2026                        |

---

# Pré-requisitos

Recomenda-se ter concluído os capítulos anteriores.

---

# Revisão da Parte 1

Durante a primeira parte deste guia, você aprendeu os fundamentos essenciais para trabalhar com Git.

O objetivo principal foi compreender como o Git acompanha as alterações de um projeto, desde a criação de arquivos até o registro no histórico.

---

# Conceitos fundamentais aprendidos

## Criando um repositório

```bash
git init
```

Cria um novo repositório Git dentro de um diretório.

---

## Configurando a identidade

```bash
git config
```

Define informações do usuário utilizadas nos commits.

Exemplo:

```bash
git config --global user.name
git config --global user.email
```

---

## Verificando alterações

```bash
git status
```

Mostra o estado atual dos arquivos.

Permite identificar:

* arquivos novos;
* arquivos modificados;
* arquivos preparados para commit.

---

## Comparando alterações

```bash
git diff
```

Mostra diferenças entre a versão atual do arquivo e a versão preparada.

Utilizado para revisar alterações antes de adicioná-las.

---

```bash
git diff --staged
```

Mostra alterações que já estão na Área de Preparação (*Staging Area*).

---

## Preparando arquivos

```bash
git add
```

Envia arquivos da Área de Trabalho para a Área de Preparação.

---

## Registrando alterações

```bash
git commit -m "mensagem"
```

Cria um registro permanente das alterações no histórico do projeto.

---

## Ignorando arquivos

```text
.gitignore
```

Define arquivos e diretórios que não devem ser adicionados ao repositório.

Exemplos:

```text
*.log
*.tmp
cache/
```

---

## Renomeando e removendo arquivos

```bash
git mv
```

Renomeia ou move arquivos informando essa alteração ao Git.

---

```bash
git rm
```

Remove arquivos do projeto e prepara essa remoção para o próximo commit.

---

## Restaurando alterações

```bash
git restore arquivo
```

Descarta alterações realizadas em arquivos.

---

```bash
git restore --staged arquivo
```

Remove arquivos da Área de Preparação sem perder as alterações.

---

## Consultando o histórico

```bash
git log
```

Exibe os commits realizados no projeto.

Permite acompanhar a evolução dos arquivos.

---

```bash
git show
```

Exibe detalhes de um commit específico.

---

# O fluxo básico aprendido

Durante a Parte 1, você aprendeu o ciclo principal de trabalho do Git:

```text
Criar arquivo
      ↓
Modificar arquivo
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

Esse fluxo representa o processo básico de controle de versão.

---

# A importância da prática

Aprender Git não significa apenas memorizar comandos.

O conhecimento verdadeiro acontece quando você entende:

* qual problema cada comando resolve;
* em qual etapa do Git ele atua;
* quais alterações ele realiza;
* como ele influencia o histórico do projeto.

A prática transforma comandos em habilidade.

Quanto mais você utiliza o Git em situações reais, mais natural se torna identificar qual ferramenta utilizar.

---

# Desafio prático

Agora coloque em prática tudo que foi aprendido na Parte 1.

O objetivo é criar um pequeno projeto e acompanhar todo o ciclo de alterações.

---

# 1 - Criar um diretório do projeto

Execute:

```bash
mkdir projeto_git
cd projeto_git
```

---

# 2 - Inicializar o repositório

Execute:

```bash
git init
```

Observe que o diretório agora possui controle de versão.

---

# 3 - Criar um arquivo

Crie um arquivo:

```text
README.md
```

Adicione um conteúdo inicial:

```text
# Meu Projeto

Primeira versão do projeto.
```

---

# 4 - Verificar o estado

Execute:

```bash
git status
```

Identifique como o Git apresenta o arquivo.

---

# 5 - Adicionar e criar o primeiro commit

Execute:

```bash
git add README.md
```

Depois:

```bash
git commit -m "Cria arquivo inicial do projeto"
```

---

# 6 - Modificar o arquivo

Altere o conteúdo:

```text
# Meu Projeto

Primeira versão do projeto.

Nova alteração realizada.
```

---

# 7 - Revisar a alteração

Execute:

```bash
git diff
```

Identifique:

* conteúdo antigo;
* conteúdo novo;
* linhas adicionadas.

---

# 8 - Preparar a alteração

Execute:

```bash
git add README.md
```

Depois:

```bash
git diff --staged
```

Observe a diferença entre a Área de Trabalho e a Área de Preparação.

---

# 9 - Registrar a alteração

Execute:

```bash
git commit -m "Atualiza documentação do projeto"
```

---

# 10 - Consultar o histórico

Execute:

```bash
git log --oneline
```

Identifique os commits criados.

---

# 11 - Testar restauração

Faça uma nova alteração no arquivo.

Depois execute:

```bash
git restore README.md
```

Observe o arquivo retornando para a última versão registrada.

---

# 12 - Identificar a função dos comandos

Ao finalizar o desafio, responda:

| Comando       | Pergunta                                                 |
| ------------- | -------------------------------------------------------- |
| `git init`    | Para que serve criar um repositório?                     |
| `git status`  | Como verificar o estado dos arquivos?                    |
| `git diff`    | Como visualizar alterações?                              |
| `git add`     | O que acontece ao enviar um arquivo para a Staging Area? |
| `git commit`  | Onde a alteração fica registrada?                        |
| `git log`     | Como consultar o histórico?                              |
| `git restore` | Como desfazer uma alteração?                             |

---

# O que foi aprendido

* O fluxo básico de trabalho com Git.
* A função dos principais comandos da Parte 1.
* A relação entre Área de Trabalho, Área de Preparação e Repositório.
* A importância da prática para consolidar o aprendizado.

---

# Resumo

Nesta primeira parte do guia, você construiu a base necessária para trabalhar com Git.

Mais importante do que decorar comandos é compreender o fluxo:

```text
Alterar
 ↓
Revisar
 ↓
Preparar
 ↓
Registrar
 ↓
Consultar
 ↓
Recuperar quando necessário
```

Com essa base consolidada, você está preparado para avançar para a Parte 2, onde aprenderá a trabalhar com branches e desenvolver diferentes versões de um projeto.

---

# Próximo capítulo

## Parte 2 - Trabalhando com Branches

Na próxima etapa você aprenderá como criar ramificações, desenvolver novas funcionalidades e organizar diferentes linhas de trabalho dentro do Git.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

