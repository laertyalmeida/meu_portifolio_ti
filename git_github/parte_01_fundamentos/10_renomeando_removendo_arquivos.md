# Git e GitHub — Guia de Estudos

## Capítulo 10 — Renomeando e Removendo Arquivos

**Tempo estimado de leitura:** 12 minutos
**Nível:** Iniciante

---

## Neste capítulo você aprenderá

* Renomear arquivos utilizando `git mv`.
* Remover arquivos utilizando `git rm`.
* Entender a diferença entre `mv` e `git mv`.
* Entender a diferença entre `rm` e `git rm`.
* Verificar alterações utilizando `git status`.
* Registrar alterações com `git commit`.
* Entender como o Git acompanha renomeações e remoções.

---

# Informações do capítulo

| Campo                   | Informação                      |
| ----------------------- | ------------------------------- |
| **Capítulo**            | 10                              |
| **Título**              | Renomeando e Removendo Arquivos |
| **Autor**               | Laerte Costa                    |
| **Sistema Operacional** | Debian GNU/Linux                |
| **Terminal**            | Bash                            |
| **Última atualização**  | Agosto de 2026                  |

---

# Objetivo deste capítulo

Neste capítulo, você vai aprender como renomear e remover arquivos utilizando comandos específicos do Git.

Também vamos entender a diferença entre utilizar os comandos comuns do Linux e os comandos oferecidos pelo Git para essas tarefas.

---

# Pré-requisitos

É recomendado ter concluído os capítulos anteriores, principalmente os capítulos sobre:

* `git status`;
* `git add`;
* `git commit`;
* Área de Trabalho;
* Área de Preparação;
* `.gitignore`.

---

# 1. Por que utilizar comandos do Git?

No Linux, podemos renomear e remover arquivos utilizando comandos como:

```bash
mv
```

e:

```bash
rm
```

O Git também possui comandos próprios para essas operações:

```bash
git mv
```

e:

```bash
git rm
```

A principal vantagem é que esses comandos realizam a operação no sistema de arquivos e, ao mesmo tempo, preparam a alteração para o próximo *commit*.

---

# 2. Renomeando um arquivo com `git mv`

Imagine que o projeto tenha o arquivo:

```text
README.md
```

Queremos mudar seu nome para:

```text
APRESENTACAO.md
```

Podemos utilizar:

```bash
git mv README.md APRESENTACAO.md
```

O arquivo será renomeado.

---

# 3. Entendendo o `git mv`

A palavra `mv` vem de **move**, que significa **mover**.

O comando:

```bash
git mv README.md APRESENTACAO.md
```

faz duas coisas:

1. Renomeia ou move o arquivo.
2. Coloca essa alteração na Área de Preparação (*Staging Area*).

Podemos pensar no processo assim:

```text
README.md
    │
    │ git mv
    ↓
APRESENTACAO.md
    │
    ↓
Staging Area
```

---

# 4. O que acontece internamente?

Uma operação como:

```bash
git mv README.md APRESENTACAO.md
```

é equivalente, de forma simplificada, a:

```bash
mv README.md APRESENTACAO.md
git add APRESENTACAO.md
git rm README.md
```

Ou seja, o Git registra a mudança de nome como uma alteração preparada.

> **Importante**
>
> O `git mv` facilita o processo, mas o Git também consegue identificar renomeações feitas usando os comandos comuns do Linux.

---

# 5. Verificando a renomeação

Depois de executar:

```bash
git mv README.md APRESENTACAO.md
```

utilize:

```bash
git status
```

O Git poderá mostrar:

```text
Changes to be committed:

    renamed: README.md -> APRESENTACAO.md
```

Isso significa que a alteração está preparada para o próximo *commit*.

---

# 6. Como o Git identifica uma renomeação?

É importante entender que o Git não precisa necessariamente registrar uma operação chamada "renomear".

Ele analisa as alterações e pode identificar que um arquivo antigo e um arquivo novo possuem conteúdo semelhante.

Por isso, uma alteração pode aparecer no histórico como:

```text
renamed: README.md -> APRESENTACAO.md
```

Essa identificação é feita pelo Git com base na similaridade dos arquivos.

---

# 7. Movendo um arquivo para outro diretório

O `git mv` também pode ser utilizado para mover um arquivo para outra pasta.

Por exemplo:

```bash
git mv APRESENTACAO.md docs/APRESENTACAO.md
```

Nesse caso, o arquivo será movido para o diretório `docs`.

Depois podemos verificar:

```bash
git status
```

O Git poderá mostrar algo semelhante a:

```text
renamed: APRESENTACAO.md -> docs/APRESENTACAO.md
```

---

# 8. Removendo um arquivo com `git rm`

Agora imagine que queremos remover:

```text
APRESENTACAO.md
```

Podemos utilizar:

```bash
git rm APRESENTACAO.md
```

O arquivo será removido do diretório de trabalho e a remoção será preparada para o próximo *commit*.

---

# 9. Entendendo o `git rm`

A palavra `rm` vem de **remove**, que significa **remover**.

O comando:

```bash
git rm APRESENTACAO.md
```

realiza duas ações:

1. Remove o arquivo do diretório de trabalho.
2. Coloca a remoção na Área de Preparação.

O fluxo fica:

```text
APRESENTACAO.md
       │
       │ git rm
       ↓
Arquivo removido
       │
       ↓
Staging Area
```

---

# 10. Diferença entre `rm` e `git rm`

No Linux, podemos remover um arquivo utilizando:

```bash
rm arquivo.txt
```

Nesse caso, o Linux remove o arquivo.

O Git perceberá a alteração quando você consultar:

```bash
git status
```

Por exemplo:

```text
Changes not staged for commit:

    deleted: arquivo.txt
```

Ainda será necessário preparar essa alteração:

```bash
git add arquivo.txt
```

---

Já utilizando:

```bash
git rm arquivo.txt
```

o arquivo é removido e a alteração já fica preparada.

Podemos comparar:

| Comando              | O que acontece                                        |
| -------------------- | ----------------------------------------------------- |
| `rm arquivo.txt`     | Remove o arquivo do sistema.                          |
| `git rm arquivo.txt` | Remove o arquivo e prepara a remoção para o *commit*. |

---

# 11. Verificando a remoção

Depois de executar:

```bash
git rm APRESENTACAO.md
```

utilize:

```bash
git status
```

O Git poderá mostrar:

```text
Changes to be committed:

    deleted: APRESENTACAO.md
```

Isso significa que a remoção está preparada para o próximo *commit*.

---

# 12. Registrando as alterações

Depois de verificar as alterações, podemos criar um *commit*.

Por exemplo:

```bash
git commit -m "Renomeia e remove arquivos de exemplo"
```

A partir desse momento, a alteração passa a fazer parte do histórico do projeto.

Podemos verificar o histórico com:

```bash
git log --oneline
```

---

# 13. Exemplo completo

Imagine que temos:

```text
README.md
```

Queremos renomeá-lo para:

```text
APRESENTACAO.md
```

Executamos:

```bash
git mv README.md APRESENTACAO.md
```

Depois verificamos:

```bash
git status
```

O Git mostrará a renomeação preparada.

Depois criamos o *commit*:

```bash
git commit -m "Renomeia README"
```

---

Agora imagine que queremos remover o arquivo:

```text
APRESENTACAO.md
```

Executamos:

```bash
git rm APRESENTACAO.md
```

Verificamos:

```bash
git status
```

E registramos:

```bash
git commit -m "Remove arquivo de apresentação"
```

---

# 14. `git mv` e `git rm` no fluxo do Git

Os comandos podem ser visualizados desta forma:

```text
┌───────────────────────────┐
│      Área de Trabalho     │
└─────────────┬─────────────┘
              │
       git mv / git rm
              ↓
┌───────────────────────────┐
│     Área de Preparação    │
└─────────────┬─────────────┘
              │
         git commit
              ↓
┌───────────────────────────┐
│        Repositório         │
└───────────────────────────┘
```

Isso mostra que `git mv` e `git rm` já preparam as alterações.

---

# 15. E se eu usar `mv` ou `rm`?

Também é possível trabalhar utilizando os comandos tradicionais do Linux.

Por exemplo:

```bash
mv README.md APRESENTACAO.md
```

Depois:

```bash
git status
```

O Git poderá identificar:

```text
deleted: README.md
untracked: APRESENTACAO.md
```

Nesse caso, será necessário preparar a alteração.

Uma forma simples seria:

```bash
git add -A
```

Depois:

```bash
git status
```

O Git poderá reconhecer a alteração como uma renomeação.

Por isso, quando o objetivo é realizar uma operação de arquivo dentro de um repositório Git, utilizar `git mv` e `git rm` torna o processo mais direto.

---

# 16. Boa prática

Quando estiver trabalhando dentro de um repositório Git, prefira:

```bash
git mv
```

para renomear ou mover arquivos e:

```bash
git rm
```

para remover arquivos.

Isso deixa claro que a operação está sendo realizada dentro do contexto do Git e já prepara a alteração para o próximo *commit*.

> **Importante**
>
> Isso não significa que `mv` e `rm` sejam comandos errados. Eles continuam sendo comandos normais e importantes do Linux.
>
> A diferença é que `git mv` e `git rm` também atualizam a Área de Preparação do Git.

---

# Comandos vistos neste capítulo

| Comando                    | Função                                                            |
| -------------------------- | ----------------------------------------------------------------- |
| `mv arquivo novo_nome`     | Renomeia ou move um arquivo no Linux.                             |
| `rm arquivo`               | Remove um arquivo no Linux.                                       |
| `git mv arquivo novo_nome` | Renomeia ou move e prepara a alteração.                           |
| `git rm arquivo`           | Remove e prepara a remoção.                                       |
| `git status`               | Mostra o estado do repositório.                                   |
| `git add -A`               | Prepara alterações de arquivos, incluindo renomeações e remoções. |
| `git commit -m "mensagem"` | Registra as alterações no histórico.                              |
| `git log --oneline`        | Mostra o histórico resumido.                                      |

---

# Boas práticas

Ao renomear ou remover arquivos:

* Use `git mv` para renomear ou mover arquivos dentro do projeto.
* Use `git rm` para remover arquivos que estão sendo controlados pelo Git.
* Execute `git status` depois da operação.
* Revise as alterações antes do *commit*.
* Utilize mensagens de *commit* claras.
* Lembre-se de que `mv` e `rm` do Linux também podem ser usados, mas exigem que o Git identifique e prepare as alterações posteriormente.

---

# Resumo

Neste capítulo, você aprendeu a renomear e remover arquivos utilizando os comandos do Git.

Para renomear:

```bash
git mv arquivo antigo_nome
```

Para remover:

```bash
git rm arquivo
```

Esses comandos realizam a alteração no sistema de arquivos e também preparam a mudança para o próximo *commit*.

Você também aprendeu que é possível utilizar os comandos tradicionais do Linux:

```bash
mv
rm
```

mas, nesse caso, será necessário preparar as alterações posteriormente.

O fluxo recomendado é:

```text
Renomear ou remover
        ↓
   git mv / git rm
        ↓
    git status
        ↓
    git commit
```

---

# O que você aprendeu

Ao concluir este capítulo, você consegue:

* ✅ Renomear arquivos com `git mv`.
* ✅ Mover arquivos com `git mv`.
* ✅ Remover arquivos com `git rm`.
* ✅ Diferenciar `git mv` de `mv`.
* ✅ Diferenciar `git rm` de `rm`.
* ✅ Verificar alterações usando `git status`.
* ✅ Entender que `git mv` e `git rm` já preparam as alterações.
* ✅ Registrar renomeações e remoções com `git commit`.

---

# Próximo capítulo

## Capítulo 11 — Restaurando Alterações com `git restore`

No próximo capítulo, você aprenderá a desfazer alterações feitas nos arquivos utilizando o comando:

```bash
git restore
```

Esse comando será útil quando você modificar um arquivo e perceber que deseja voltar ao estado anterior.

---

# 📚 Fonte de estudo

Este resumo foi elaborado a partir dos estudos e da prática do autor sobre **Git e GitHub**, utilizando os conteúdos da disciplina e materiais de estudo como referência.

**Observação:** este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo original das disciplinas e materiais utilizados como referência não deve ser reproduzido ou disponibilizado integralmente neste repositório.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

