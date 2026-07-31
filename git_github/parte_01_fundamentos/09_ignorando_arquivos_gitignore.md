# Tempo estimado de leitura

**10 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* O que é o arquivo `.gitignore`.
* Por que alguns arquivos não devem ser versionados.
* Criar um arquivo `.gitignore`.
* Ignorar arquivos e diretórios.
* Verificar o efeito do `.gitignore` no repositório.

---

# Git e GitHub — Guia de Estudos

---

# Informações do capítulo

| Campo                   | Informação                          |
| ----------------------- | ----------------------------------- |
| **Capítulo**            | 09                                  |
| **Título**              | Ignorando Arquivos com `.gitignore` |
| **Autor**               | Laerte Costa                        |
| **Sistema Operacional** | Debian GNU/Linux                    |
| **Terminal**            | Bash                                |
| **Última atualização**  | Julho de 2026                       |

---

# Pré-requisitos

Recomenda-se ter concluído os capítulos anteriores.

---

# Conceito teórico

## O que é o `.gitignore`?

Nem todos os arquivos de um projeto precisam ser registrados pelo Git.

Arquivos temporários, logs, caches, arquivos compilados e configurações específicas da máquina normalmente não fazem parte do código-fonte e, por isso, não devem ser versionados.

Para informar ao Git quais arquivos devem ser ignorados, utiliza-se o arquivo `.gitignore`.

---

# Por que utilizar o `.gitignore`?

Imagine que, durante o desenvolvimento, um programa gere arquivos temporários automaticamente.

Esses arquivos podem mudar constantemente e não fazem parte do projeto.

Se forem versionados, o histórico ficará desorganizado com alterações desnecessárias.

O `.gitignore` evita que esses arquivos sejam adicionados ao controle de versão.

---

# Criando o arquivo

Crie um arquivo chamado `.gitignore` no diretório do projeto.

### Comando

```bash
touch .gitignore
```

---

# Significado do comando

**touch** → tocar

Originalmente, o comando `touch` foi criado para atualizar a data e hora de modificação de um arquivo.

Caso o arquivo não exista, ele será criado.

Por esse motivo, é muito utilizado no Linux para criar arquivos vazios.

---

# Editando o arquivo

Abra o arquivo `.gitignore` com o editor de sua preferência e adicione algumas regras.

Exemplo:

```text
*.log
*.tmp
cache/
```

Nesse exemplo:

* `*.log` → ignora todos os arquivos com extensão `.log`;
* `*.tmp` → ignora todos os arquivos com extensão `.tmp`;
* `cache/` → ignora todo o diretório `cache`.

---

# Testando o funcionamento

Crie um arquivo chamado:

```text
teste.log
```

Agora execute:

### Comando

```bash
git status
```

O arquivo `teste.log` não será exibido como arquivo novo (*untracked*), pois corresponde a uma regra definida no `.gitignore`.

---

# Verificando qual regra ignorou o arquivo

O Git possui um comando para descobrir qual regra do `.gitignore` está sendo aplicada.

### Comando

```bash
git check-ignore -v teste.log
```

Exemplo:

```text
.gitignore:1:*.log    teste.log
```

Significado:

* `.gitignore:1` → regra encontrada na linha 1 do arquivo `.gitignore`;
* `*.log` → padrão responsável por ignorar o arquivo;
* `teste.log` → arquivo afetado pela regra.

---

# Como funciona o `.gitignore`?

O Git utiliza as regras definidas no `.gitignore` para determinar quais arquivos não devem aparecer como arquivos não rastreados (*untracked*) no repositório.

Quando um arquivo corresponde a uma regra, ele não será exibido normalmente pelo `git status` e não será adicionado com `git add .`.

---

# Atenção

O `.gitignore` ignora apenas arquivos que **ainda não estão sendo controlados pelo Git**.

Se um arquivo já foi adicionado anteriormente com:

```bash
git add
```

e registrado em um commit, apenas incluí-lo no `.gitignore` não será suficiente para que ele deixe de ser versionado.

Será necessário removê-lo da Área de Preparação e do controle do Git utilizando comandos específicos.

Esse procedimento será estudado em capítulos mais avançados.

---

# O que foi aprendido

* o arquivo `.gitignore` define quais arquivos o Git deve ignorar;
* arquivos temporários normalmente não devem ser versionados;
* `touch` cria o arquivo `.gitignore`;
* o `git status` permite verificar se uma regra está funcionando;
* `git check-ignore` mostra qual regra ignorou determinado arquivo.

---

# Resumo

Neste capítulo você aprendeu a utilizar o arquivo `.gitignore` para impedir que arquivos desnecessários sejam adicionados ao repositório.

Essa prática ajuda a manter o projeto mais organizado e evita que arquivos temporários façam parte do histórico de commits.

---

# Próximo capítulo

## 10 - Renomeando e Removendo Arquivos

No próximo capítulo você aprenderá como renomear e remover arquivos utilizando os comandos `git mv` e `git rm`, mantendo o histórico do projeto organizado.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

