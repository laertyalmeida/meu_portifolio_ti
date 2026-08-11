# Git e GitHub — Guia de Estudos

## Capítulo 11 — Restaurando Alterações com `git restore`

**Tempo estimado de leitura:** 12 minutos
**Nível:** Iniciante

---

## Neste capítulo você aprenderá

* O que é o comando `git restore`.
* Desfazer alterações realizadas em arquivos.
* Restaurar arquivos removidos.
* Remover arquivos da Área de Preparação (*Staging Area*).
* Recuperar o conteúdo de arquivos de commits anteriores.
* Entender a diferença entre restaurar um arquivo e alterar o histórico de commits.

---

# Informações do capítulo

| Campo                   | Informação                               |
| ----------------------- | ---------------------------------------- |
| **Capítulo**            | 11                                       |
| **Título**              | Restaurando Alterações com `git restore` |
| **Autor**               | Laerte Costa                             |
| **Sistema Operacional** | Debian GNU/Linux                         |
| **Terminal**            | Bash                                     |
| **Última atualização**  | Agosto de 2026                           |

---

# Objetivo deste capítulo

Neste capítulo, você vai aprender a utilizar o comando `git restore` para desfazer alterações realizadas nos arquivos e recuperar versões conhecidas pelo Git.

Também vamos entender como retirar arquivos da Área de Preparação sem perder as alterações feitas neles.

---

# Pré-requisitos

É recomendado ter concluído os capítulos anteriores, principalmente os capítulos sobre:

* `git status`;
* `git add`;
* `git commit`;
* Área de Trabalho;
* Área de Preparação;
* `git diff`.

---

# 1. O que é o `git restore`?

Durante o desenvolvimento, podemos alterar um arquivo e depois perceber que a alteração não deveria permanecer.

Por exemplo:

```text
README.md
```

foi modificado, mas queremos voltar ao estado anterior.

O comando:

```bash
git restore
```

permite restaurar arquivos para um estado conhecido pelo Git.

Ele pode ser utilizado para:

* descartar alterações na Área de Trabalho;
* recuperar arquivos removidos;
* retirar arquivos da Área de Preparação;
* restaurar o conteúdo de um arquivo a partir de outro commit.

---

# 2. O que significa `restore`?

A palavra:

```text
restore
```

significa:

> restaurar

No Git, o comando `git restore` trabalha principalmente com o **conteúdo dos arquivos**.

Dependendo da opção utilizada, ele pode atuar na Área de Trabalho ou na Área de Preparação.

---

# 3. Quando utilizar o `git restore`?

Algumas situações comuns são:

* alterei um arquivo por engano;
* removi um arquivo acidentalmente;
* quero recuperar a última versão registrada;
* adicionei um arquivo com `git add` e quero retirá-lo da Área de Preparação;
* quero recuperar o conteúdo de um arquivo de um commit anterior.

---

# 4. Descartando alterações de um arquivo

Imagine que o arquivo:

```text
README.md
```

já esteja sendo controlado pelo Git e tenha sido modificado.

Primeiro, verifique:

```bash
git status
```

O Git poderá mostrar:

```text
modified: README.md
```

Para descartar a alteração:

```bash
git restore README.md
```

O arquivo voltará para o conteúdo registrado no `HEAD`, ou seja, para a versão que está no commit atualmente apontado pelo `HEAD`.

---

# 5. Atenção ao utilizar `git restore`

Este comando pode descartar alterações que ainda não foram registradas em um commit.

Por exemplo:

```text
Versão do commit
       ↓
README.md
       ↓
Você modifica o arquivo
       ↓
git restore README.md
       ↓
Alteração descartada
```

Por isso, antes de utilizar o comando, é uma boa prática verificar:

```bash
git diff
```

Assim você consegue visualizar o que será perdido.

> ⚠️ **Atenção**
>
> Se você utilizar `git restore` para descartar uma alteração que ainda não foi registrada em um commit, essa alteração pode ser perdida.

---

# 6. Restaurando vários arquivos

Também podemos informar vários arquivos:

```bash
git restore arquivo1.md arquivo2.md
```

Nesse caso, somente os arquivos informados serão restaurados.

---

# 7. Restaurando todos os arquivos modificados

Também podemos utilizar:

```bash
git restore .
```

O ponto:

```text
.
```

representa o diretório atual.

Esse comando restaura os arquivos rastreados que possuem alterações na Área de Trabalho.

> **Cuidado**
>
> Antes de utilizar `git restore .`, verifique as alterações com `git status` e `git diff`. Alterações não salvas em commits podem ser descartadas.

---

# 8. Restaurando um arquivo removido

Imagine que o arquivo:

```text
README.md
```

foi removido utilizando:

```bash
rm README.md
```

Agora execute:

```bash
git status
```

O Git poderá mostrar:

```text
deleted: README.md
```

Como o arquivo ainda está registrado no Git, podemos recuperá-lo utilizando:

```bash
git restore README.md
```

O arquivo será recriado com o conteúdo da versão registrada no `HEAD`.

---

# 9. Retirando um arquivo da Área de Preparação

Agora imagine que modificamos:

```text
README.md
```

e executamos:

```bash
git add README.md
```

O arquivo está agora na Área de Preparação.

Mas percebemos que ainda não queremos incluí-lo no próximo commit.

Podemos utilizar:

```bash
git restore --staged README.md
```

---

# 10. O que acontece com `git restore --staged`?

Esse comando retira o arquivo da Área de Preparação.

Importante:

> **As alterações do arquivo não são apagadas.**

O fluxo fica:

```text
Arquivo modificado
       ↓
   git add
       ↓
Staging Area
       ↓
git restore --staged
       ↓
Arquivo volta para
a Área de Trabalho
```

Depois disso, o arquivo continuará modificado.

Podemos confirmar com:

```bash
git status
```

O Git poderá mostrar:

```text
Changes not staged for commit:
    modified: README.md
```

---

# 11. Diferença entre `git restore` e `git restore --staged`

Essa diferença é muito importante.

### `git restore arquivo`

Descarta a alteração da **Área de Trabalho**.

```bash
git restore README.md
```

Resultado:

```text
Alteração local
      ↓
   descartada
```

---

### `git restore --staged arquivo`

Retira o arquivo da **Área de Preparação**, mas mantém sua alteração.

```bash
git restore --staged README.md
```

Resultado:

```text
Staging Area
     ↓
Área de Trabalho
```

A alteração continua existindo.

---

# 12. Restaurando conteúdo de outro commit

O Git também permite restaurar o conteúdo de um arquivo a partir de outro commit.

Por exemplo:

```bash
git restore --source=HEAD~1 README.md
```

Vamos entender:

### `--source`

Define de onde o Git deve obter o conteúdo.

### `HEAD~1`

Representa o commit anterior ao `HEAD`.

### `README.md`

É o arquivo que receberá o conteúdo dessa versão.

Nesse exemplo, o Git pega o conteúdo de `README.md` do commit anterior e coloca esse conteúdo na Área de Trabalho.

> **Importante**
>
> Isso não cria automaticamente um novo commit e também não apaga o commit anterior. O conteúdo do arquivo é apenas restaurado na Área de Trabalho.

Depois disso, podemos verificar a alteração com:

```bash
git status
```

e:

```bash
git diff
```

---

# 13. Restaurando e preparando ao mesmo tempo

Também existe uma forma de restaurar um arquivo a partir de uma fonte e atualizar a Área de Preparação.

Por exemplo:

```bash
git restore --source=HEAD~1 --staged README.md
```

Nesse caso, o conteúdo de `README.md` será obtido do commit anterior e colocado na Área de Preparação.

Esse uso é mais avançado e será mais fácil de entender depois que você estiver confortável com `git add`, `git commit` e `git diff`.

---

# 14. `git restore` não apaga commits

É importante não confundir:

```bash
git restore
```

com comandos que alteram o histórico.

O `git restore` trabalha principalmente com o conteúdo dos arquivos.

Ele não remove commits do histórico.

Existem outros comandos para trabalhar com o histórico, como:

```bash
git reset
```

e:

```bash
git revert
```

Esses comandos serão estudados posteriormente.

---

# 15. Comparando os principais usos

| Comando                               | O que acontece                                                  |
| ------------------------------------- | --------------------------------------------------------------- |
| `git restore arquivo`                 | Descarta alterações do arquivo na Área de Trabalho.             |
| `git restore .`                       | Descarta alterações dos arquivos rastreados no diretório atual. |
| `git restore --staged arquivo`        | Retira o arquivo da Área de Preparação, mantendo a alteração.   |
| `git restore --source=HEAD~1 arquivo` | Recupera o conteúdo do arquivo a partir do commit anterior.     |

---

# 16. Exemplo prático completo

Imagine que o arquivo:

```text
README.md
```

está no projeto.

Faça uma alteração nele.

Depois execute:

```bash
git status
```

O arquivo aparecerá como modificado.

Agora veja a alteração:

```bash
git diff
```

Se você decidir que quer manter a alteração:

```bash
git add README.md
```

Se mudar de ideia e quiser retirar o arquivo da Área de Preparação:

```bash
git restore --staged README.md
```

A alteração continuará no arquivo.

Se depois decidir que realmente não quer mais a alteração:

```bash
git restore README.md
```

Agora o arquivo voltará para a versão registrada no `HEAD`.

---

# 17. Fluxo visual

O funcionamento pode ser representado assim:

```text
             Arquivo modificado
                    │
                    ▼
              git status
                    │
                    ▼
                git diff
                    │
          ┌─────────┴─────────┐
          │                   │
      git add            git restore
          │                   │
          ▼                   ▼
   Staging Area          Alteração
          │                descartada
          ▼
git restore --staged
          │
          ▼
Arquivo volta para
Área de Trabalho
```

---

# 18. Boas práticas

Antes de utilizar `git restore`:

* Execute `git status`.
* Utilize `git diff` para verificar as alterações.
* Tenha certeza de que deseja descartar o conteúdo.
* Faça commits frequentes de alterações importantes.
* Evite utilizar `git restore .` sem verificar antes o que será descartado.

Uma boa prática é:

```bash
git status
git diff
```

e somente depois decidir se deve utilizar:

```bash
git restore arquivo
```

---

# Comandos vistos neste capítulo

| Comando                               | Função                                                          |
| ------------------------------------- | --------------------------------------------------------------- |
| `git restore arquivo`                 | Descarta alterações do arquivo.                                 |
| `git restore .`                       | Descarta alterações dos arquivos rastreados no diretório atual. |
| `git restore --staged arquivo`        | Retira o arquivo da Área de Preparação.                         |
| `git restore --source=HEAD~1 arquivo` | Recupera o conteúdo de um commit anterior.                      |
| `git status`                          | Mostra o estado do repositório.                                 |
| `git diff`                            | Mostra alterações que ainda não foram preparadas.               |

---

# O que foi aprendido

Ao concluir este capítulo, você consegue:

* ✅ Entender o que é `git restore`.
* ✅ Descartar alterações feitas em arquivos.
* ✅ Recuperar arquivos removidos.
* ✅ Retirar arquivos da Área de Preparação.
* ✅ Manter uma alteração ao removê-la da Staging Area.
* ✅ Recuperar o conteúdo de um arquivo de outro commit.
* ✅ Diferenciar `git restore` de comandos que alteram o histórico.
* ✅ Utilizar `git status` e `git diff` antes de descartar alterações.

---

# Resumo

O comando `git restore` é utilizado principalmente para restaurar o conteúdo de arquivos.

Para descartar uma alteração local:

```bash
git restore arquivo
```

Para retirar um arquivo da Área de Preparação sem perder sua alteração:

```bash
git restore --staged arquivo
```

Para recuperar o conteúdo de uma versão anterior:

```bash
git restore --source=HEAD~1 arquivo
```

A principal diferença é:

```text
git restore arquivo
        ↓
descarta a alteração

git restore --staged arquivo
        ↓
remove da Staging Area,
mas mantém a alteração
```

Antes de descartar qualquer alteração, lembre-se de verificar:

```bash
git status
git diff
```

Assim você reduz o risco de perder trabalho por engano.

---

# Próximo capítulo

## Capítulo 12 — Revisão Prática da Parte 1

Neste capítulo, você vai revisar os principais conceitos aprendidos até aqui e praticar o fluxo básico do Git:

```text
criar/modificar
      ↓
git status
      ↓
git add
      ↓
git diff --staged
      ↓
git commit
      ↓
git log
```

A revisão ajudará a fixar os comandos antes de avançar para os próximos assuntos do Git.

---

# 📚 Fonte de estudo

Este resumo foi elaborado a partir dos estudos e da prática do autor sobre **Git e GitHub**, utilizando os conteúdos da disciplina e materiais de estudo como referência.

**Observação:** este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo original das disciplinas e materiais utilizados como referência não deve ser reproduzido ou disponibilizado integralmente neste repositório.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

