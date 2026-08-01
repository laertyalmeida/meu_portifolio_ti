# Tempo estimado de leitura

**12 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* O que é o arquivo `.gitignore`.
* Por que alguns arquivos não devem ser versionados.
* Criar um arquivo `.gitignore`.
* Ignorar arquivos e diretórios.
* Ignorar arquivos em subdiretórios.
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

Crie um arquivo chamado `.gitignore` no diretório raiz do repositório.

### Comando

```bash
touch .gitignore
```

---

# Significado do comando

**touch** → tocar.

Originalmente, o comando `touch` foi criado para atualizar a data e hora de modificação de um arquivo.

Caso o arquivo não exista, ele será criado.

Por esse motivo, é muito utilizado no Linux para criar arquivos vazios.

---

# Onde criar o arquivo `.gitignore`?

Na maioria dos projetos existe apenas um arquivo `.gitignore`, localizado na raiz do repositório, ou seja, no mesmo diretório onde está a pasta `.git`.

Exemplo:

```text
meu_projeto/
├── .git/
├── .gitignore
├── README.md
├── docs/
├── src/
└── imagens/
```

Quando o `.gitignore` está na raiz, suas regras são válidas para todo o repositório, incluindo todos os seus subdiretórios.

Na maioria dos projetos pessoais e profissionais, um único arquivo `.gitignore` é suficiente.

Embora seja possível criar outros arquivos `.gitignore` em subdiretórios, essa prática normalmente é utilizada apenas em projetos maiores, nos quais diferentes módulos possuem regras específicas.

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

# Ignorando arquivos em subdiretórios

Além de utilizar regras genéricas, também é possível ignorar arquivos e diretórios específicos informando seu caminho relativo no arquivo `.gitignore`.

Exemplo:

```text
parte1/teste.txt
```

Ignora apenas o arquivo:

```text
parte1/teste.txt
```

---

Também é possível ignorar todos os arquivos de uma determinada extensão dentro de um único diretório.

Exemplo:

```text
parte1/*.txt
```

Nesse caso, somente os arquivos `.txt` existentes dentro da pasta `parte1` serão ignorados.

Arquivos `.txt` existentes em outros diretórios continuarão sendo rastreados normalmente.

---

Para ignorar um diretório específico:

```text
parte1/cache/
```

Apenas a pasta `cache` localizada dentro de `parte1` será ignorada.

---

Essa abordagem permite centralizar todas as regras em um único arquivo `.gitignore`, facilitando sua manutenção e evitando a criação de vários arquivos `.gitignore` espalhados pelo projeto.

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

O Git possui um comando para descobrir qual regra do `.gitignore` está sendo aplicada a um determinado arquivo.

### Comando

```bash
git check-ignore -v teste.log
```

---

# Significado do comando

**git** → sistema de controle de versão.

**check** → verificar.

**ignore** → ignorar.

**check-ignore** → verificar se um arquivo está sendo ignorado e identificar qual regra do `.gitignore` foi responsável por isso.

**-v** → *verbose* (detalhado).

Exibe informações completas sobre a regra aplicada, informando:

* qual arquivo `.gitignore` foi utilizado;
* em qual linha a regra foi encontrada;
* qual padrão fez com que o arquivo fosse ignorado.

---

Exemplo de saída:

```text
.gitignore:1:*.log    teste.log
```

Significado:

* `.gitignore` → arquivo onde a regra foi encontrada;
* `1` → número da linha no arquivo `.gitignore`;
* `*.log` → padrão responsável por ignorar o arquivo;
* `teste.log` → arquivo afetado pela regra.

Esse comando é muito útil quando um arquivo está sendo ignorado e você deseja descobrir exatamente qual regra do `.gitignore` está causando esse comportamento.

---

# Como funciona o `.gitignore`?

O Git utiliza as regras definidas no `.gitignore` para determinar quais arquivos não devem aparecer como arquivos não rastreados (*untracked*) no repositório.

Quando um arquivo corresponde a uma regra, ele não será exibido normalmente pelo `git status` e também não será adicionado ao utilizar comandos como:

```bash
git add .
```

---

# Atenção

O `.gitignore` ignora apenas arquivos que **ainda não estão sendo controlados pelo Git**.

Se um arquivo já foi adicionado anteriormente com `git add` e registrado em um commit, apenas incluí-lo no `.gitignore` não fará com que ele deixe de ser versionado.

Para que ele passe a ser ignorado, primeiro é necessário removê-lo do índice do Git.

### Comando

```bash
git rm --cached nome_do_arquivo
```

---

# Significado do comando

**git** → sistema de controle de versão.

**rm** → *remove* (remover).

**--cached** → remove o arquivo apenas do índice (cache) do Git, mantendo-o no diretório de trabalho.

Esse comando faz com que o Git deixe de controlar o arquivo, mas o arquivo continua existindo normalmente no computador.

Após essa remoção, o `.gitignore` passará a ignorá-lo normalmente.

---

# O que foi aprendido

* o arquivo `.gitignore` define quais arquivos o Git deve ignorar;
* normalmente existe apenas um `.gitignore` na raiz do repositório;
* um único `.gitignore` pode controlar todo o repositório;
* é possível ignorar arquivos e diretórios específicos utilizando caminhos relativos;
* arquivos temporários normalmente não devem ser versionados;
* `touch` cria o arquivo `.gitignore`;
* `git check-ignore` identifica qual regra está ignorando um arquivo;
* a flag `-v` exibe informações detalhadas sobre a regra aplicada;
* `git status` permite verificar se uma regra está funcionando;
* `git rm --cached` remove um arquivo do controle de versão sem apagá-lo do computador.

---

# Resumo

Neste capítulo você aprendeu a utilizar o arquivo `.gitignore` para impedir que arquivos desnecessários sejam adicionados ao repositório.

Também aprendeu que, na maioria dos projetos, existe apenas um arquivo `.gitignore` localizado na raiz do repositório, responsável por controlar quais arquivos e diretórios devem ser ignorados em todo o projeto.

Além disso, viu como criar regras específicas para subdiretórios, como identificar a regra responsável por ignorar um arquivo utilizando o comando `git check-ignore -v` e entendeu por que arquivos que já estão sendo versionados precisam ser removidos do índice do Git antes que passem a ser ignorados.

Essas práticas ajudam a manter o projeto organizado, facilitam a manutenção do repositório e evitam que arquivos temporários ou desnecessários façam parte do histórico de commits.

---

# Próximo capítulo

## 10 - Renomeando e Removendo Arquivos

No próximo capítulo você aprenderá como renomear e remover arquivos utilizando os comandos `git mv` e `git rm`, mantendo o histórico do projeto organizado.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

