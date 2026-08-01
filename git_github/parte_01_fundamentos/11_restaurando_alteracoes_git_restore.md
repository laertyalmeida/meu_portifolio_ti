# Tempo estimado de leitura

**12 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* O que é o comando `git restore`.
* Desfazer alterações realizadas em arquivos.
* Restaurar arquivos removidos.
* Remover arquivos da Área de Preparação (*Staging Area*).
* Recuperar versões de arquivos utilizando commits anteriores.

---

# Git e GitHub — Guia de Estudos

---

# Informações do capítulo

| Campo                   | Informação                               |
| ----------------------- | ---------------------------------------- |
| **Capítulo**            | 11                                       |
| **Título**              | Restaurando Alterações com `git restore` |
| **Autor**               | Laerte Costa                             |
| **Sistema Operacional** | Debian GNU/Linux                         |
| **Terminal**            | Bash                                     |
| **Última atualização**  | Julho de 2026                            |

---

# Pré-requisitos

Recomenda-se ter concluído os capítulos anteriores.

---

# Conceito teórico

## O que é o `git restore`?

Durante o desenvolvimento de um projeto, é comum realizar alterações e depois perceber que determinada modificação não deveria permanecer.

O comando `git restore` permite recuperar arquivos para um estado anterior, desfazendo alterações realizadas na Área de Trabalho ou removendo arquivos da Área de Preparação.

Ele facilita a recuperação de arquivos sem a necessidade de navegar pelo histórico de commits.

---

# O que significa `restore`?

A palavra:

```text
restore
```

significa:

> restaurar

No Git, o comando `git restore` devolve um arquivo para um estado específico.

Dependendo da opção utilizada, ele pode:

* descartar alterações locais;
* recuperar arquivos removidos;
* retirar arquivos da Área de Preparação (*Staging Area*);
* restaurar uma versão existente em outro commit.

---

# Quando utilizar o `git restore`?

Algumas situações comuns:

* alterei um arquivo por engano;
* removi um arquivo acidentalmente;
* quero voltar para a última versão salva no commit;
* adicionei um arquivo com `git add` e quero removê-lo da Área de Preparação.

---

# Restaurando alterações de um arquivo

Suponha que o arquivo:

```text
README.md
```

tenha sido modificado.

Verifique o estado do repositório:

### Comando

```bash
git status
```

Exemplo:

```text
modified: README.md
```

Para descartar as alterações feitas nesse arquivo:

### Comando

```bash
git restore README.md
```

Resultado:

* as alterações realizadas na Área de Trabalho serão descartadas;
* o arquivo retornará ao estado do último commit.

> **Atenção:** as alterações descartadas dessa forma não poderão ser recuperadas facilmente.

---

# Restaurando vários arquivos

É possível restaurar vários arquivos informando seus nomes:

```bash
git restore arquivo1.md arquivo2.md
```

Também é possível restaurar todos os arquivos modificados:

```bash
git restore .
```

O ponto (`.`) representa o diretório atual e seus arquivos rastreados pelo Git.

---

# Restaurando um arquivo removido

Imagine que um arquivo foi removido utilizando o comando:

```bash
rm README.md
```

O Git identificará a remoção:

```bash
git status
```

Saída:

```text
deleted: README.md
```

Para recuperar o arquivo:

```bash
git restore README.md
```

O arquivo será restaurado conforme a última versão registrada no commit.

---

# Removendo um arquivo da Área de Preparação

Imagine que você adicionou um arquivo:

```bash
git add README.md
```

Depois percebeu que ainda não deseja incluí-lo no próximo commit.

Para retirar o arquivo da Área de Preparação:

```bash
git restore --staged README.md
```

Resultado:

* o arquivo continua modificado na Área de Trabalho;
* ele deixa de estar preparado para o próximo commit.

Esse comando desfaz o efeito do `git add`, mas não perde as alterações realizadas.
Ou seja você desfaz o efeito git add, ele volta para o modificado e depois você faz o git restore para voltar como estava.


---

# Restaurando uma versão de outro commit

O Git também permite recuperar o conteúdo de um arquivo presente em outro commit.

Exemplo:

```bash
git restore --source=HEAD~1 README.md
```

Significado:

* `--source` → define a origem da versão que será restaurada;
* `HEAD~1` → representa o commit anterior ao atual;
* `README.md` → arquivo que será restaurado.

Nesse caso, o conteúdo do arquivo será substituído pela versão existente no commit anterior.

---

# Diferença entre restaurar e voltar um commit

O comando:

```bash
git restore
```

atua sobre arquivos.

Ele não remove commits nem altera o histórico do projeto.

Para trabalhar com alterações no histórico de commits existem outros comandos, como:

```bash
git reset
git revert
```

Esses comandos serão estudados futuramente.

---

# Boas práticas

✔ Sempre execute:

```bash
git status
```

antes de utilizar `git restore`.

✔ Utilize:

```bash
git diff
```

para revisar alterações antes de descartá-las.

✔ Antes de realizar mudanças importantes, crie um commit.

Assim, caso algo dê errado, será possível recuperar o trabalho através do histórico.

✔ Utilize branches para testar alterações sem comprometer a branch principal.

---

# Resumo dos comandos

| Comando                               | Função                                              |
| ------------------------------------- | --------------------------------------------------- |
| `git restore arquivo`                 | Descarta alterações locais do arquivo               |
| `git restore .`                       | Descarta alterações de todos os arquivos rastreados |
| `git restore --staged arquivo`        | Remove arquivo da Área de Preparação                |
| `git restore --source=HEAD~1 arquivo` | Recupera conteúdo de uma versão anterior            |

---

# Observação

O comando `git restore` funciona principalmente com arquivos que já são conhecidos pelo Git.

Arquivos novos que ainda não foram adicionados com:

```bash
git add
```

não possuem uma versão registrada no histórico e, por isso, não podem ser recuperados utilizando esse comando.

---

# O que foi aprendido

* `git restore` desfaz alterações em arquivos;
* arquivos removidos podem ser recuperados;
* `git restore --staged` remove arquivos da Área de Preparação;
* o comando trabalha com arquivos, não com o histórico de commits;
* revisar antes de descartar alterações é uma boa prática.

---

# Resumo

Neste capítulo você aprendeu a utilizar o comando `git restore` para recuperar arquivos e desfazer alterações antes da criação de um commit.

Esse comando aumenta a segurança durante o desenvolvimento, permitindo testar mudanças e retornar a estados anteriores quando necessário.

---

# Próximo capítulo

## 12 - Visualizando o Histórico com `git log`

No próximo capítulo você aprenderá como consultar o histórico do projeto, visualizar commits realizados e entender como o Git registra a evolução dos arquivos.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

