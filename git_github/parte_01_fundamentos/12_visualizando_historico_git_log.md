# Tempo estimado de leitura

**12 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* O que é o comando `git log`.
* Consultar o histórico de commits.
* Entender as informações exibidas pelo Git.
* Utilizar opções para melhorar a visualização do histórico.
* Encontrar informações importantes sobre alterações realizadas no projeto.

---

# Git e GitHub — Guia de Estudos

---

# Informações do capítulo

| Campo                   | Informação                             |
| ----------------------- | -------------------------------------- |
| **Capítulo**            | 12                                     |
| **Título**              | Visualizando o Histórico com `git log` |
| **Autor**               | Laerte Costa                           |
| **Sistema Operacional** | Debian GNU/Linux                       |
| **Terminal**            | Bash                                   |
| **Última atualização**  | Julho de 2026                          |

---

# Pré-requisitos

Recomenda-se ter concluído os capítulos anteriores.

---

# Conceito teórico

## O que é o histórico do Git?

Uma das principais características do Git é registrar todas as alterações importantes realizadas em um projeto.

Cada vez que um commit é criado, o Git salva informações como:

* quem realizou a alteração;
* quando ela aconteceu;
* qual mensagem foi registrada;
* quais arquivos foram modificados.

Esse conjunto de registros forma o histórico do projeto.

---

# O que é o `git log`?

O comando:

```bash
git log
```

permite visualizar o histórico de commits de um repositório.

Ele mostra a evolução do projeto desde o commit mais recente até os commits mais antigos.

---

# Visualizando o histórico

Execute:

### Comando

```bash
git log
```

Exemplo:

```text
commit a84f91c2d8e7f6a5b4
Author: Laerte Costa
Date:   Jul 30 2026

    Adiciona documentação do capítulo 11
```

---

# Entendendo a saída do `git log`

## Commit

Exemplo:

```text
commit a84f91c2d8e7f6a5b4
```

O valor exibido é o identificador único do commit (*hash*).

O Git utiliza esse código para localizar exatamente uma versão registrada do projeto.

---

## Author

Exemplo:

```text
Author: Laerte Costa
```

Mostra o autor responsável pelo commit.

Essa informação vem da configuração definida anteriormente:

```bash
git config --global user.name
```

---

## Date

Exemplo:

```text
Date: Jul 30 2026
```

Mostra a data em que o commit foi criado.

---

## Mensagem do commit

Exemplo:

```text
Adiciona documentação do capítulo 11
```

É a descrição informada no momento do commit:

```bash
git commit -m "mensagem"
```

Uma boa mensagem ajuda a entender a evolução do projeto.

---

# Navegando pelo histórico

Assim como no `git diff`, o Git utiliza o paginador `less`.

Comandos:

```text
Espaço → próxima página

b → página anterior

/texto → pesquisar

n → próxima ocorrência

q → sair
```

---

# Visualização resumida

O histórico completo pode gerar muitas informações.

Para visualizar apenas uma linha por commit:

### Comando

```bash
git log --oneline
```

Exemplo:

```text
a84f91c Adiciona documentação do capítulo 11
7c921aa Adiciona capítulo sobre git restore
3bd82ef Cria estrutura inicial do projeto
```

---

# Entendendo o `--oneline`

**oneline** → uma linha

Essa opção reduz a saída mostrando:

* hash resumido do commit;
* mensagem do commit.

É muito utilizado para consultar rapidamente o histórico.

---

# Exibindo mais detalhes

Para visualizar informações resumidas e arquivos alterados:

### Comando

```bash
git log --stat
```

Exemplo:

```text
3 files changed, 120 insertions(+), 5 deletions(-)
```

Mostra:

* quantidade de arquivos modificados;
* linhas adicionadas;
* linhas removidas.

---

# Mostrando as alterações de cada commit

Para visualizar o conteúdo alterado em cada commit:

### Comando

```bash
git log -p
```

O parâmetro:

```text
-p
```

vem de:

```text
patch
```

e mostra as diferenças (*diff*) introduzidas por cada commit.

---

# Limitando a quantidade de commits

Para mostrar apenas os últimos commits:

### Comando

```bash
git log -5
```

Nesse exemplo:

```text
-5
```

significa:

mostrar os últimos 5 commits.

---

# Filtrando commits por autor

É possível pesquisar commits realizados por determinado autor.

### Comando

```bash
git log --author="Laerte"
```

O Git exibirá somente commits relacionados ao autor informado.

---

# Pesquisando mensagens de commits

Para procurar uma palavra dentro das mensagens:

### Comando

```bash
git log --grep="capítulo"
```

Exemplo:

O Git mostrará somente commits que possuem a palavra "capítulo" na mensagem.

---

# Consultando um commit específico

Cada commit possui um identificador único.

Exemplo:

```bash
git show a84f91c
```

O comando:

```text
git show
```

mostra os detalhes de um commit específico.

Ele apresenta:

* autor;
* data;
* mensagem;
* alterações realizadas.

---

# Boas práticas

✔ Utilize mensagens claras nos commits.

Exemplo:

Evite:

```text
alterações
```

Prefira:

```text
Adiciona documentação do capítulo 12
```

---

✔ Consulte o histórico antes de modificar arquivos importantes.

O histórico funciona como uma linha do tempo do projeto.

---

✔ Faça commits pequenos e organizados.

Isso facilita encontrar alterações no futuro.

---

# O que foi aprendido

* `git log` exibe o histórico de commits;
* cada commit possui um identificador único (*hash*);
* mensagens de commit ajudam a entender mudanças;
* `--oneline` apresenta um resumo do histórico;
* `git show` permite analisar um commit específico;
* o histórico ajuda a acompanhar a evolução do projeto.

---

# Resumo

Neste capítulo você aprendeu a consultar o histórico do Git utilizando o comando `git log`.

Também aprendeu como visualizar commits de diferentes formas, encontrar informações específicas e utilizar o histórico como uma ferramenta de organização e segurança.

---

# Próximo capítulo

## 13 - Trabalhando com Branches

No próximo capítulo você aprenderá como criar, visualizar e alternar entre branches, permitindo desenvolver novas funcionalidades sem comprometer a versão principal do projeto.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

