# Git e GitHub — Guia de Estudos

## Capítulo 06 — Consultando o Histórico de Alterações

**Tempo estimado de leitura:** 8 minutos
**Nível:** Iniciante

---

## Neste capítulo você aprenderá

* Visualizar o histórico de *commits*.
* Entender as principais informações exibidas pelo Git.
* Consultar o histórico de forma resumida.
* Limitar a quantidade de *commits* exibidos.
* Exibir informações sobre os arquivos alterados.
* Conhecer algumas opções do comando `git log`.

---

# Informações do capítulo

| Campo                   | Informação                            |
| ----------------------- | ------------------------------------- |
| **Capítulo**            | 06                                    |
| **Título**              | Consultando o Histórico de Alterações |
| **Autor**               | Laerte Costa                          |
| **Sistema Operacional** | Debian GNU/Linux                      |
| **Terminal**            | Bash                                  |
| **Última atualização**  | Agosto de 2026                        |

---

# Objetivo deste capítulo

Neste capítulo, você vai aprender a consultar o histórico do seu repositório Git.

Vamos utilizar o comando `git log` para visualizar os *commits* realizados e entender as principais informações apresentadas pelo Git.

---

# Pré-requisitos

É recomendado ter concluído os capítulos anteriores, principalmente o capítulo sobre criação de *commits*.

Para acompanhar os exemplos, é importante ter pelo menos um *commit* no repositório.

---

# 1. O que é o histórico de commits?

Sempre que criamos um *commit*, o Git registra um ponto na evolução do projeto.

Com vários *commits*, podemos acompanhar as mudanças realizadas ao longo do tempo.

Por exemplo:

```text
Commit 1 → primeira versão
    ↓
Commit 2 → adicionada documentação
    ↓
Commit 3 → corrigido um arquivo
    ↓
Commit 4 → adicionada uma nova funcionalidade
```

Esses registros formam o **histórico do repositório**.

Para consultar esse histórico, usamos o comando:

```bash
git log
```

---

# 2. Visualizando o histórico

### Comando

```bash
git log
```

### O que esse comando faz?

O `git log` mostra os *commits* realizados no repositório.

Por padrão, os registros aparecem do **mais recente para o mais antigo**.

Um resultado parecido com este pode aparecer:

```text
commit 9c3f4d7b1b3d8f4d9f7b2c5e8a6d7f3c2a1b4e5
Author: Laerte Costa <laerte@email.com>
Date:   Wed Jul 22 20:15:30 2026 -0300

    Primeiro commit
```

O conteúdo exato será diferente no seu computador.

---

# 3. Entendendo as informações do commit

Cada *commit* apresenta algumas informações importantes.

## Commit

```text
commit 9c3f4d7b1b3d8f4d9f7b2c5e8a6d7f3c2a1b4e5
```

Esse é o identificador do *commit*.

O Git utiliza esse identificador para localizar e diferenciar cada registro do histórico.

Normalmente, você verá apenas uma parte desse identificador quando utilizar opções resumidas.

---

## Author

```text
Author: Laerte Costa <laerte@email.com>
```

Mostra o nome e o e-mail configurados como autor do *commit*.

Essas informações são definidas por meio das configurações do Git, por exemplo:

```bash
git config --global user.name "Laerte Costa"
git config --global user.email "laerte@email.com"
```

---

## Date

```text
Date:   Wed Jul 22 20:15:30 2026 -0300
```

Mostra a data e o horário em que o *commit* foi criado.

---

## Mensagem do commit

```text
Primeiro commit
```

É a mensagem informada no momento em que o *commit* foi criado.

Por exemplo:

```bash
git commit -m "Primeiro commit"
```

É importante utilizar mensagens que expliquem de forma simples o que foi feito.

---

# 4. Histórico resumido

Quando o repositório possui muitos *commits*, o `git log` pode apresentar bastante informação.

Para visualizar o histórico de uma forma mais compacta, podemos utilizar:

### Comando

```bash
git log --oneline
```

### Explicação

A opção `--oneline` mostra cada *commit* em apenas uma linha.

Exemplo:

```text
9c3f4d7 Primeiro commit
72a4c81 Adiciona documentação do projeto
3b92e10 Cria estrutura inicial
```

Assim, fica mais fácil visualizar rapidamente a sequência de *commits*.

### Entendendo

**`--oneline`** → apresenta cada *commit* em uma única linha.

> **Dica**
>
> Para consultar rapidamente o histórico de um projeto, `git log --oneline` é um dos comandos mais úteis.

---

# 5. Limitando a quantidade de commits

Também podemos escolher quantos *commits* queremos visualizar.

### Comando

```bash
git log -2
```

Nesse exemplo, o Git exibirá apenas os **dois *commits* mais recentes**.

Podemos alterar o número conforme a necessidade.

Por exemplo:

```bash
git log -5
```

Mostra os cinco *commits* mais recentes.

Ou:

```bash
git log -10
```

Mostra os dez mais recentes.

---

# 6. Combinando opções

As opções do `git log` também podem ser combinadas.

Por exemplo:

```bash
git log --oneline -5
```

Esse comando mostra os **cinco *commits* mais recentes**, utilizando o formato resumido.

Exemplo:

```text
9c3f4d7 Primeiro commit
72a4c81 Adiciona documentação
3b92e10 Cria estrutura inicial
a82f991 Configura projeto
c41d220 Inicia repositório
```

Essa combinação é bastante prática para consultar rapidamente o histórico.

---

# 7. Visualizando estatísticas

Também podemos utilizar o `git log` para visualizar informações sobre os arquivos alterados.

### Comando

```bash
git log --stat
```

A opção `--stat` apresenta estatísticas relacionadas às alterações de cada *commit*.

Ela pode mostrar:

* arquivos modificados;
* quantidade de linhas adicionadas;
* quantidade de linhas removidas.

Exemplo simplificado:

```text
 README.md | 10 ++++++++++
 1 file changed, 10 insertions(+)
```

### Entendendo

**`--stat`** → mostra um resumo estatístico das alterações.

Essa opção pode ser útil quando queremos entender rapidamente o impacto de um *commit*.

---

# 8. Uma combinação útil

Também podemos combinar `--oneline` com outras opções do `git log`.

Por exemplo:

```bash
git log --oneline --stat
```

Isso permite consultar o histórico de forma resumida e também visualizar informações sobre os arquivos alterados.

As opções disponíveis podem ser combinadas de diferentes maneiras, dependendo do que você deseja consultar.

---

# 9. Curiosidade sobre o identificador do commit

O identificador apresentado pelo Git é baseado em uma função de hash.

Em muitos repositórios Git, os identificadores históricos são baseados em **SHA-1**.

Por exemplo:

```text
9c3f4d7b1b3d8f4d9f7b2c5e8a6d7f3c2a1b4e5
```

Esse identificador permite ao Git diferenciar os registros do histórico.

> **Importante**
>
> Para quem está começando, não é necessário decorar como o SHA-1 funciona. Neste momento, basta entender que o Git utiliza esse identificador para localizar e diferenciar os *commits*.

---

# 10. Comandos vistos neste capítulo

| Comando                | O que faz                                                  |
| ---------------------- | ---------------------------------------------------------- |
| `git log`              | Mostra o histórico de *commits*.                           |
| `git log --oneline`    | Mostra o histórico de forma resumida.                      |
| `git log -2`           | Mostra os dois *commits* mais recentes.                    |
| `git log --stat`       | Mostra estatísticas das alterações.                        |
| `git log --oneline -5` | Mostra os cinco *commits* mais recentes de forma resumida. |

---

# Boas práticas

Ao consultar o histórico do Git:

* Use `git log` quando precisar de informações detalhadas.
* Use `git log --oneline` para uma visão rápida.
* Utilize mensagens de *commit* claras.
* Use `git log -n` quando quiser limitar a quantidade de registros.
* Use `git log --stat` quando quiser entender quais arquivos foram alterados.

---

# Resumo

Neste capítulo, você aprendeu a consultar o histórico do Git utilizando o comando `git log`.

Você também aprendeu que cada *commit* possui informações como:

* identificador;
* autor;
* data;
* mensagem.

Além disso, conheceu algumas opções úteis:

```bash
git log
git log --oneline
git log -2
git log --stat
```

Esses comandos ajudam a entender a evolução do projeto e a consultar os registros realizados anteriormente.

---

# O que você aprendeu

Ao concluir este capítulo, você consegue:

* ✅ Visualizar o histórico de *commits*.
* ✅ Entender as principais informações de um *commit*.
* ✅ Utilizar `git log`.
* ✅ Utilizar `git log --oneline`.
* ✅ Limitar a quantidade de *commits* exibidos.
* ✅ Utilizar `git log --stat`.
* ✅ Combinar algumas opções do `git log`.

---

# Próximo capítulo

## Capítulo 07 — Comparando Alterações com git diff

No próximo capítulo, você aprenderá a utilizar o comando:

```bash
git diff
```

Esse comando permite visualizar as diferenças entre as versões dos arquivos e entender exatamente o que foi alterado antes de criar um novo *commit*.

---

# 📚 Fonte de estudo

Este resumo foi elaborado a partir dos estudos e da prática do autor sobre **Git e GitHub**, utilizando os conteúdos da disciplina e materiais de estudo como referência.

**Observação:** este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo original das disciplinas e materiais utilizados como referência não deve ser reproduzido ou disponibilizado integralmente neste repositório.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

