## Tempo estimado de leitura

**20 minutos**

**Nível:** Intermediário

# Capítulo 12 – Excluindo uma Branch Remota no GitHub

---

# Neste capítulo você aprenderá

- O que é uma branch remota.
- Quando remover uma branch do GitHub.
- Como excluir uma branch remota utilizando o Git.
- O significado do comando `git push origin --delete`.
- Boas práticas para manter o repositório organizado.

---

# Objetivo

Durante o desenvolvimento de um projeto, é comum criar diversas branches para desenvolver funcionalidades, corrigir problemas ou organizar a documentação.

Após a conclusão do trabalho e, principalmente, depois da união (*merge*) com a branch principal, algumas dessas branches deixam de ser necessárias.

Neste capítulo aprenderemos como remover uma branch do repositório remoto hospedado no GitHub, mantendo o projeto mais organizado.

---

# O que é uma Branch Remota?

Uma **branch remota** é uma branch armazenada no servidor Git, como o GitHub.

Ela fica disponível para todos os colaboradores que possuem acesso ao repositório.

Diferentemente da branch local, a branch remota existe no servidor e pode ser acessada por qualquer pessoa autorizada.

---

# Quando excluir uma Branch?

Normalmente uma branch pode ser removida quando:

- o trabalho foi concluído;
- seu conteúdo já foi incorporado à branch principal;
- ela não será mais utilizada;
- deseja-se manter o repositório mais limpo e organizado.

Excluir branches antigas facilita a navegação e reduz a quantidade de branches desnecessárias.

---

# Comando para excluir uma Branch Remota

```bash
git push origin --delete nome_da_branch
```

Exemplo:

```bash
git push origin --delete master
```

---

# Entendendo o comando

```bash
git push origin --delete master
```

---

## git

Significa:

> Sistema de controle de versões.

É o programa responsável por executar o comando.

---

## push

Significa:

> Enviar alterações para o repositório remoto.

Nesse caso, envia uma solicitação para remover uma branch existente no servidor.

---

## origin

Significa:

> Repositório remoto padrão.

É o servidor onde o projeto está hospedado.

No nosso caso, corresponde ao repositório no GitHub.

---

## --delete

Significa:

> Excluir.

Esta opção informa ao Git que a operação desejada é remover uma branch do repositório remoto.

---

## master

É o nome da branch que será removida.

No seu projeto, essa branch deixou de ser utilizada após a definição da branch:

```text
padronizacao_documentacao
```

como branch principal.

---

# O que acontece após a exclusão?

Depois da execução do comando:

- a branch deixa de existir no GitHub;
- ela não aparecerá mais na lista de branches remotas;
- os commits continuam preservados caso estejam presentes em outra branch;
- apenas a referência da branch é removida.

Excluir uma branch **não significa apagar automaticamente os commits**, desde que eles já estejam presentes em outra branch.

---

# Como verificar as Branches Remotas

Para visualizar as branches existentes no servidor utilize:

```bash
git branch -r
```

---

## Entendendo o comando

```bash
git branch -r
```

### git

Sistema de controle de versões.

### branch

Lista ou manipula branches.

### -r

Significa:

> **Remote**

Mostra apenas as branches existentes no repositório remoto.

Exemplo de saída:

```text
origin/main
origin/padronizacao_documentacao
```

Após excluir uma branch, ela deixará de aparecer nessa lista.

---

# Atualizando as referências locais

Após remover uma branch remota, é possível atualizar as referências locais com:

```bash
git fetch --prune
```

---

## Entendendo o comando

```bash
git fetch --prune
```

### fetch

Busca informações atualizadas do repositório remoto.

Não altera seus arquivos locais.

---

### --prune

Significa:

> Limpar referências antigas.

Remove da máquina local as referências para branches remotas que já foram excluídas no servidor.

---

# Atenção

Uma branch remota só poderá ser excluída se:

- ela não for a branch padrão do repositório;
- você possuir permissão para realizar essa alteração.

Caso tente remover a branch padrão, o GitHub impedirá a operação.

---

# Integração com o Projeto Linux

Neste capítulo utilizamos comandos Git para administrar um repositório remoto.

Embora a operação seja realizada através do GitHub, o comando funciona com qualquer servidor Git compatível.

No **Projeto Linux**, esse conhecimento será útil para administrar servidores Git próprios, compreender permissões de acesso e manter repositórios organizados em ambientes corporativos.

---

# Boas práticas

- Exclua apenas branches que realmente não serão mais utilizadas.
- Certifique-se de que o trabalho da branch já foi incorporado à branch principal.
- Nunca exclua uma branch sem verificar se outros colaboradores ainda a utilizam.
- Atualize as referências locais utilizando `git fetch --prune`.
- Mantenha apenas branches úteis para facilitar a manutenção do projeto.

---

# Resumo

Neste capítulo você aprendeu:

- o que é uma branch remota;
- quando uma branch pode ser removida;
- como utilizar `git push origin --delete`;
- como listar branches remotas;
- como atualizar as referências locais após a exclusão;
- boas práticas para manter o repositório organizado.

Agora seu repositório permanece mais limpo, facilitando a organização do desenvolvimento.

---

# O que foi realizado na prática

Durante este capítulo foram realizadas as seguintes atividades:

- ✔ Identificação das branches remotas.
- ✔ Exclusão de uma branch remota utilizando `git push origin --delete`.
- ✔ Verificação das branches existentes no servidor.
- ✔ Atualização das referências locais com `git fetch --prune`.

---

# Próximo capítulo

## Capítulo 13 – Renomeando uma Branch Local e Remota

No próximo capítulo você aprenderá como renomear uma branch utilizando `git branch -m`, atualizar o repositório remoto e ajustar a branch de acompanhamento (*upstream*), mantendo a organização do projeto.
