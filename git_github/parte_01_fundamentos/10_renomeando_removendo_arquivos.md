# Tempo estimado de leitura

**12 minutos**

**Nível:** Iniciante

## Neste capítulo você aprenderá

* Renomear arquivos com `git mv`.
* Remover arquivos com `git rm`.
* Entender por que utilizar os comandos do Git.
* Verificar as alterações utilizando `git status`.
* Entender como o Git acompanha alterações estruturais.

---

# Git e GitHub — Guia de Estudos

---

# Informações do capítulo

| Campo                   | Informação                      |
| ----------------------- | ------------------------------- |
| **Capítulo**            | 10                              |
| **Título**              | Renomeando e Removendo Arquivos |
| **Autor**               | Laerte Costa                    |
| **Sistema Operacional** | Debian GNU/Linux                |
| **Terminal**            | Bash                            |
| **Última atualização**  | Julho de 2026                   |

---

# Pré-requisitos

Recomenda-se ter concluído os capítulos anteriores.

---

# Conceito teórico

## Por que utilizar os comandos do Git?

Arquivos podem ser renomeados ou removidos utilizando comandos do próprio sistema operacional, como:

```bash
mv
```

e

```bash
rm
```

No entanto, o Git também oferece comandos específicos para essas tarefas.

Além de realizar a alteração no arquivo, esses comandos informam imediatamente ao Git o que aconteceu, facilitando o acompanhamento das mudanças no projeto.

---

# Renomeando um arquivo

Suponha que exista um arquivo chamado:

```text
README.md
```

Para renomeá-lo, utilize:

### Comando

```bash
git mv README.md APRESENTACAO.md
```

O arquivo passará a ter o novo nome.

---

# Significado do comando

**mv** → *move* → mover

O comando `git mv` utiliza a palavra **move**, pois renomear um arquivo também é uma forma de movê-lo dentro do sistema de arquivos.

Quando utilizamos:

```bash
git mv
```

o Git realiza duas ações:

1. Move ou renomeia o arquivo no sistema.
2. Adiciona essa alteração à Área de Preparação (*Staging Area*).

Internamente, seria semelhante a executar:

```bash
mv README.md APRESENTACAO.md
git add APRESENTACAO.md
```

---

# Verificando a alteração

Após renomear o arquivo, execute:

### Comando

```bash
git status
```

Exemplo:

```text
Changes to be committed:

    renamed: README.md -> APRESENTACAO.md
```

O Git identifica que o arquivo foi renomeado e que essa alteração está preparada para o próximo commit.

---

# Como o Git identifica uma renomeação?

O Git não guarda uma operação chamada "renomear arquivo".

Ele identifica uma possível renomeação comparando o conteúdo dos arquivos.

Quando percebe que um arquivo removido possui grande semelhança com um arquivo criado, o Git apresenta essa alteração como:

```text
renamed:
```

---

# Removendo um arquivo

Para remover um arquivo do projeto, utilize:

### Comando

```bash
git rm APRESENTACAO.md
```

O arquivo será removido do diretório e a remoção será preparada para o próximo commit.

---

# Significado do comando

**rm** → *remove* → remover

O comando `git rm` realiza duas ações:

1. Remove o arquivo do diretório.
2. Informa ao Git que essa remoção deverá ser registrada.

---

# Diferença entre `rm` e `git rm`

Utilizando somente:

```bash
rm arquivo.txt
```

o arquivo será removido apenas do sistema operacional.

O Git perceberá a alteração posteriormente através do:

```bash
git status
```

Já utilizando:

```bash
git rm arquivo.txt
```

a remoção já será preparada automaticamente para o próximo commit.

---

# Verificando a remoção

Após remover o arquivo, execute:

### Comando

```bash
git status
```

Exemplo:

```text
Changes to be committed:

    deleted: APRESENTACAO.md
```

O Git informa que o arquivo será removido no próximo commit.

---

# Registrando as alterações

Depois de verificar as mudanças, registre-as no histórico.

### Comando

```bash
git commit -m "Renomeia e remove arquivos de exemplo"
```

A partir desse momento, as alterações passam a fazer parte do histórico do projeto.

---

# Boa prática

Sempre que possível, utilize os comandos:

```bash
git mv
```

e

```bash
git rm
```

em vez dos comandos comuns do sistema operacional.

Embora o Git consiga identificar muitas dessas alterações posteriormente, utilizar seus próprios comandos torna o fluxo de trabalho mais claro e facilita a compreensão do histórico do projeto.

---

*Sempre que um arquivo for modificado com mv ou removido (deleted) com rm, as mudanças vão aparecer no status com git status, basta adicionar com git add e registrar com commit -m para armazenar os registros dessas mudanças.*


# O que foi aprendido

* `git mv` renomeia ou move arquivos;
* `git rm` remove arquivos do projeto;
* `git mv` e `git rm` já preparam alterações para o próximo commit;
* `git status` permite verificar as alterações realizadas;
* as alterações devem ser registradas com um novo commit.

---

# Resumo

Neste capítulo você aprendeu como renomear e remover arquivos utilizando os comandos do Git.

Também conheceu a importância de utilizar essas ferramentas para manter o histórico do projeto organizado e facilitar o acompanhamento das alterações.

---

# Próximo capítulo

## 11 - Restaurando Alterações com Git Restore

No próximo capítulo você aprenderá a restaurar arquivos modificados utilizando o comando `git restore`, recuperando versões anteriores antes de criar um commit.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

