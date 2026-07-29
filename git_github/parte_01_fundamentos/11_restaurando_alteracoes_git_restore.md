# Capítulo 11 - Restaurando arquivos com `git restore`

**Capítulo:** 11  
**Sistema Operacional:** Debian 13 (Trixie)  
**Terminal:** Bash  
**Última atualização:** Julho/2026

---

# Objetivo

Aprender a utilizar o comando `git restore` para desfazer alterações em arquivos, restaurar arquivos removidos e remover arquivos da área de preparação (Staging Area).

Esse comando permite recuperar arquivos sem a necessidade de navegar pelo histórico de commits, tornando o processo mais simples e seguro.

---

# O que significa `restore`?

A palavra **restore** significa:

> **restore = restaurar**

No Git, o comando `git restore` devolve um arquivo ao estado desejado.

Dependendo das opções utilizadas, ele pode:

- descartar alterações locais;
- restaurar arquivos removidos;
- remover arquivos da Staging Area;
- recuperar a versão de outro commit.

---

# Quando utilizar?

Algumas situações comuns:

- alterei um arquivo por engano;
- removi um arquivo acidentalmente;
- quero voltar para a última versão salva;
- adicionei um arquivo à Staging Area e mudei de ideia.

---

# Restaurando alterações de um arquivo

Suponha que o arquivo `README.md` tenha sido modificado.

Antes:

```bash
git status
```

Saída:

```text
modified: README.md
```

Para descartar todas as alterações feitas nesse arquivo:

```bash
git restore README.md
```

Resultado:

- todas as alterações locais serão descartadas;
- o arquivo voltará exatamente ao estado do último commit.

> **Atenção:** essa operação não pode ser desfeita.

---

# Restaurando vários arquivos

É possível restaurar diversos arquivos ao mesmo tempo.

```bash
git restore arquivo1.md arquivo2.md
```

Ou restaurar todos os arquivos modificados:

```bash
git restore .
```

O ponto (`.`) representa todos os arquivos rastreados pelo Git no diretório atual.

---

# Restaurando um arquivo removido

Imagine que o arquivo foi apagado utilizando o comando:

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

O arquivo será restaurado exatamente como estava no último commit.

---

# Removendo um arquivo da Staging Area

Suponha que você executou:

```bash
git add README.md
```

Depois percebeu que ainda não deseja incluí-lo no próximo commit.

Para removê-lo da Staging Area:

```bash
git restore --staged README.md
```

Resultado:

- o arquivo continua modificado;
- ele deixa de estar preparado para o próximo commit.

---

# Restaurando a versão de outro commit

Também é possível restaurar a versão de um arquivo existente em outro commit.

Exemplo:

```bash
git restore --source=HEAD~1 README.md
```

Nesse caso, o arquivo será restaurado utilizando a versão presente no commit anterior.

---

# Boas práticas

✔ Sempre execute `git status` antes de utilizar `git restore`.

✔ Tenha certeza de que deseja descartar as alterações.

✔ Antes de realizar mudanças importantes, faça um commit. Assim, caso algo dê errado, será possível recuperar facilmente seu trabalho.

✔ Utilize branches para testar alterações sem comprometer a branch principal.

---

# Resumo dos comandos

| Comando | Função |
|---------|--------|
| `git restore arquivo` | Descarta as alterações locais do arquivo |
| `git restore .` | Descarta alterações de todos os arquivos rastreados |
| `git restore --staged arquivo` | Remove o arquivo da Staging Area |
| `git restore --source=HEAD~1 arquivo` | Recupera a versão de um commit anterior |

---

# Observação

O comando `git restore` funciona apenas com arquivos já conhecidos pelo Git.

Arquivos novos, que ainda não passaram por `git add`, não poderão ser recuperados utilizando esse comando.

---

# Conclusão

O `git restore` é uma ferramenta essencial para recuperar arquivos e desfazer alterações antes da criação de um novo commit.

Seu uso reduz erros durante o desenvolvimento e proporciona mais segurança ao trabalhar com arquivos modificados ou removidos.
