## Tempo estimado de leitura

**25 minutos**

**Nível:** Intermediário

# Capítulo 13 – Renomeando uma Branch Local e Remota

---

# Neste capítulo você aprenderá

- Como renomear uma branch local.
- Como enviar a nova branch para o GitHub.
- Como remover a branch antiga do repositório remoto.
- Como configurar a nova branch para acompanhar o repositório remoto (*upstream*).
- Boas práticas ao alterar o nome de uma branch.

---

# Objetivo

Durante o desenvolvimento de um projeto pode surgir a necessidade de alterar o nome de uma branch.

Isso pode acontecer para padronizar a nomenclatura, corrigir erros de digitação ou tornar o nome mais descritivo.

Neste capítulo aprenderemos como renomear uma branch local, atualizar o repositório remoto e configurar corretamente a nova branch para continuar sincronizada com o GitHub.

---

# Quando renomear uma Branch?

Renomear uma branch é recomendado quando:

- o nome foi criado incorretamente;
- deseja-se seguir um padrão de nomenclatura;
- a branch passou a representar outro objetivo;
- o projeto adotou uma convenção de nomes.

Exemplo:

Antes:

```text
teste
```

Depois:

```text
documentacao_git
```

---

# Renomeando a Branch Local

Para alterar o nome da branch atual utilize:

```bash
git branch -m novo_nome
```

Exemplo:

```bash
git branch -m documentacao_git
```

---

# Entendendo o comando

```bash
git branch -m documentacao_git
```

---

## git

Sistema de controle de versões.

---

## branch

Manipula as branches do repositório.

---

## -m

Significa:

> **Move**

Apesar do nome "Move", essa opção é utilizada para **renomear** uma branch.

---

## documentacao_git

É o novo nome que será atribuído à branch.

---

# Verificando a alteração

Após renomear a branch, utilize:

```bash
git branch
```

Exemplo de saída:

```text
* documentacao_git
  main
```

O símbolo `*` indica a branch atualmente utilizada.

---

# Enviando a nova Branch para o GitHub

Depois de alterar o nome localmente, envie a nova branch para o servidor.

```bash
git push origin documentacao_git
```

---

# Entendendo o comando

```bash
git push origin documentacao_git
```

## push

Envia a nova branch para o repositório remoto.

## origin

Representa o repositório remoto configurado.

## documentacao_git

É a branch que será criada no GitHub.

---

# Configurando o Upstream

Após enviar a branch, configure o acompanhamento automático.

```bash
git push --set-upstream origin documentacao_git
```

Também é possível utilizar a forma abreviada:

```bash
git push -u origin documentacao_git
```

---

# Entendendo o comando

```bash
git push -u origin documentacao_git
```

---

## -u

Significa:

> **--set-upstream**

Cria o vínculo entre a branch local e a branch remota.

Depois dessa configuração, basta utilizar:

```bash
git push
```

ou

```bash
git pull
```

sem informar novamente o nome da branch.

---

# Removendo a Branch Antiga

Após confirmar que a nova branch está funcionando corretamente, a antiga pode ser removida.

```bash
git push origin --delete nome_antigo
```

Exemplo:

```bash
git push origin --delete teste
```

---

# Atualizando as Referências Locais

Depois de remover a branch remota antiga, atualize as referências locais.

```bash
git fetch --prune
```

Isso remove da sua máquina as referências para branches que já não existem no servidor.

---

# Fluxo completo

Na prática, o processo fica assim:

```bash
git branch -m documentacao_git
git push -u origin documentacao_git
git push origin --delete teste
git fetch --prune
```

---

# O que acontece após a renomeação?

Depois desse processo:

- a branch local passa a utilizar o novo nome;
- uma nova branch é criada no GitHub;
- a branch antiga pode ser removida;
- o vínculo (*upstream*) passa a apontar para a nova branch;
- o desenvolvimento continua normalmente.

---

# Integração com o Projeto Linux

Renomear branches é uma atividade comum em projetos colaborativos e servidores Git.

No **Projeto Linux**, esse conhecimento será importante para compreender como equipes organizam fluxos de trabalho em servidores Git auto-hospedados, mantendo padrões de nomenclatura e facilitando a administração de grandes projetos.

---

# Boas práticas

- Utilize nomes claros e descritivos.
- Evite espaços e caracteres especiais.
- Padronize a nomenclatura entre toda a equipe.
- Configure sempre o *upstream* após criar uma nova branch.
- Remova branches antigas apenas após confirmar que não serão mais utilizadas.

---

# Resumo

Neste capítulo você aprendeu:

- como renomear uma branch local;
- como enviar a nova branch ao GitHub;
- como configurar o *upstream*;
- como remover a branch antiga;
- como manter o repositório organizado após a alteração.

Agora você consegue alterar o nome de uma branch sem perder a sincronização com o repositório remoto.

---

# O que foi realizado na prática

Durante este capítulo foram realizadas as seguintes atividades:

- ✔ Renomeação de uma branch local.
- ✔ Envio da nova branch para o GitHub.
- ✔ Configuração do *upstream*.
- ✔ Remoção da branch antiga.
- ✔ Atualização das referências locais.

---

# Próximo capítulo

## Capítulo 14 – Trabalhando com Tags no Git

No próximo capítulo você aprenderá o que são **tags**, quando utilizá-las, como criar versões do projeto com `git tag` e como publicá-las no GitHub para identificar marcos importantes do desenvolvimento.
