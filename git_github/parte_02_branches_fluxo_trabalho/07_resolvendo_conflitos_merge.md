**Tempo estimado:** 25 minutos

**Nível:** Intermediário

# Capítulo 07 — Resolvendo Conflitos de Merge

---

# Pré-requisitos

Antes de iniciar este capítulo é recomendado compreender o funcionamento do comando `git merge`.

---

# Neste capítulo você aprenderá

* O que é um conflito de merge.
* Por que os conflitos acontecem.
* Como identificar arquivos em conflito.
* Como resolver um conflito de forma segura.
* Como concluir um merge após a resolução.

---

# O que é um conflito de Merge?

Um conflito ocorre quando o Git não consegue decidir automaticamente qual alteração deve ser mantida durante a mesclagem de duas Branches.

Isso normalmente acontece quando o mesmo trecho de um arquivo foi modificado em Branches diferentes.

Exemplo:

```text
main

A ─── B ─── C
             \
login         D
```

Se os commits `C` e `D` modificarem a mesma linha de um arquivo, o Git solicitará que o usuário resolva o conflito manualmente.

---

# Representação visual

Antes do merge:

```text
main

A ─── B ─── C
             \
login         D
```

Durante o merge:

```text
main

A ─── B ─── C
             X
login         D
```

O símbolo `X` representa o conflito que precisa ser resolvido antes da conclusão da mesclagem.

---

# Comando

Inicie a mesclagem normalmente:

```bash
git switch main
git merge login
```

---

# Significado do comando

## `git`

Sistema de controle de versão distribuído.

### `merge`

**Tradução:** Mesclar.

Integra outra Branch à Branch atual.

### `login`

Branch que será integrada.

---

# Resultado

Quando ocorre um conflito, o Git apresenta uma saída semelhante a:

```text
Auto-merging login.py
CONFLICT (content): Merge conflict in login.py
Automatic merge failed; fix conflicts and then commit the result.
```

---

# Explicação da saída

### `Auto-merging`

O Git tentou realizar a mesclagem automaticamente.

### `CONFLICT`

Foi encontrado um conflito que precisa ser resolvido manualmente.

### `Automatic merge failed`

A mesclagem foi interrompida até que o conflito seja resolvido.

---

# Arquivo em conflito

Ao abrir o arquivo, você verá marcações semelhantes às seguintes:

```text
<<<<<<< HEAD
print("Versão da main")
=======
print("Versão da login")
>>>>>>> login
```

### `<<<<<<< HEAD`

Início da versão da Branch atual.

### `=======`

Separador entre as duas versões.

### `>>>>>>> login`

Fim da versão proveniente da Branch `login`.

O desenvolvedor deve editar o arquivo, escolher a versão desejada (ou combinar ambas) e remover essas marcações.

---

# Concluindo a mesclagem

Após resolver o conflito:

Adicione o arquivo:

```bash
git add login.py
```

Conclua o merge:

```bash
git commit
```

O Git criará o commit de merge utilizando a mensagem padrão ou outra informada pelo usuário.

---

# O que aconteceu internamente?

Quando ocorreu o conflito, o Git interrompeu a mesclagem para evitar perda de informações.

Após a resolução e o commit, o histórico volta a ficar consistente e as duas Branches passam a compartilhar as alterações integradas.

---

# Atenção

Nunca remova as marcações de conflito sem revisar cuidadosamente o conteúdo.

Escolher a versão incorreta pode eliminar alterações importantes realizadas em uma das Branches.

---

# Resumo

Neste capítulo você aprendeu que conflitos de merge acontecem quando o Git encontra alterações incompatíveis no mesmo trecho de um arquivo. Também aprendeu como identificar os conflitos, editar os arquivos, concluir a resolução e finalizar a mesclagem com segurança.

---

# Próximo capítulo

## Capítulo 08 — Excluindo Branches

No próximo capítulo você aprenderá como remover Branches que já foram integradas ao projeto, mantendo o repositório organizado e facilitando o gerenciamento do histórico.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

