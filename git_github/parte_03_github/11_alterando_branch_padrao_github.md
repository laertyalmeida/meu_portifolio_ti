## Tempo estimado de leitura

**20 minutos**

**Nível:** Intermediário

# Capítulo 11 – Alterando a Branch Padrão no GitHub

---

# Neste capítulo você aprenderá

- O que é uma branch padrão.
- Por que o GitHub utiliza uma branch padrão.
- Como alterar a branch padrão de um repositório.
- O que acontece após essa alteração.
- Boas práticas para definir a branch principal de um projeto.

---

# Objetivo

Ao criar um repositório no GitHub, uma das branches é definida como **branch padrão** (*Default Branch*).

Essa branch é considerada a principal do projeto e será utilizada como referência para diversas operações, como abertura de Pull Requests, exibição do código na página inicial do repositório e clonagem por outros desenvolvedores.

Neste capítulo aprenderemos como alterar essa configuração para que o GitHub passe a utilizar a branch desejada como principal.

---

# O que é uma Branch?

Antes de entender o conceito de branch padrão, é importante recordar o significado de uma branch.

Uma **branch** representa uma linha de desenvolvimento independente dentro do projeto.

Ela permite criar novas funcionalidades, corrigir erros ou realizar experimentos sem modificar diretamente a linha principal de desenvolvimento.

---

# O que é uma Branch Padrão?

A **branch padrão** é a branch principal do repositório.

Ela é utilizada pelo GitHub como referência para diversas operações.

Quando alguém acessa um repositório pela primeira vez, é essa branch que será exibida automaticamente.

Também é ela que será utilizada como destino padrão ao criar um Pull Request.

---

# Quando alterar a Branch Padrão?

Em muitos projetos é comum criar uma nova branch para organizar melhor o desenvolvimento.

Após essa nova branch tornar-se a principal do projeto, pode ser interessante defini-la como branch padrão.

No desenvolvimento deste portfólio, a branch:

```text
padronizacao_documentacao
```

passou a concentrar todo o trabalho de documentação e, por esse motivo, foi definida como branch principal do repositório.

---

# Alterando a Branch Padrão

No GitHub, acesse o repositório.

Em seguida, siga o caminho:

```text
Settings → Default branch
```

---

## Settings

Significa:

> **Configurações**

É a área onde ficam disponíveis as configurações gerais do repositório.

---

## Default branch

Significa:

> **Branch padrão**

É a configuração responsável por definir qual será a principal branch do projeto.

---

# Escolhendo a nova Branch

Na opção **Default branch**, selecione a branch desejada.

No projeto deste portfólio foi selecionada:

```text
padronizacao_documentacao
```

Após selecionar a nova branch, confirme a alteração clicando em:

```text
Update
```

---

## Update

Significa:

> **Atualizar**

Ao confirmar essa opção, o GitHub passará a considerar a nova branch como principal.

---

# O que muda após a alteração?

Depois da mudança:

- a nova branch será exibida na página inicial do repositório;
- os novos Pull Requests terão essa branch como destino padrão;
- novos colaboradores visualizarão essa branch ao acessar o projeto;
- a clonagem do repositório utilizará essa branch como referência.

A alteração da branch padrão **não remove** as demais branches existentes.

Todas continuam disponíveis normalmente.

---

# Posso alterar novamente?

Sim.

A branch padrão pode ser alterada sempre que necessário.

Em projetos maiores é comum que essa configuração seja modificada conforme a evolução do fluxo de desenvolvimento.

---

# Integração com o Projeto Linux

Neste capítulo foi apresentada uma configuração administrativa realizada diretamente na interface do GitHub.

Embora não envolva comandos executados no terminal Linux, essa configuração faz parte da administração de projetos hospedados em servidores Git.

No **Projeto Linux**, serão estudados servidores Git auto-hospedados, permissões de acesso, autenticação e administração de serviços, permitindo compreender como plataformas semelhantes ao GitHub organizam seus repositórios internamente.

---

# Boas práticas

- Defina como branch padrão aquela que representa a versão principal do projeto.
- Evite alterar a branch padrão sem necessidade.
- Antes de alterar essa configuração, verifique se todos os colaboradores estão cientes da mudança.
- Mantenha um fluxo de trabalho organizado entre branches de desenvolvimento e branch principal.

---

# Resumo

Neste capítulo você aprendeu:

- o que é uma branch padrão;
- qual a função da configuração **Default branch**;
- como alterar a branch principal de um repositório;
- quais mudanças ocorrem após essa alteração;
- boas práticas para organização das branches.

Seu repositório agora possui uma branch principal definida de acordo com a organização do projeto.

---

# O que foi realizado na prática

Durante este capítulo foram realizadas as seguintes atividades:

- ✔ Identificação da branch padrão do repositório.
- ✔ Alteração da configuração **Default branch**.
- ✔ Definição da branch `padronizacao_documentacao` como principal.
- ✔ Validação da nova configuração no GitHub.

---

# Próximo capítulo

## Capítulo 12 – Excluindo uma Branch Remota no GitHub

No próximo capítulo você aprenderá como remover uma branch remota que não será mais utilizada, compreendendo o comando `git push origin --delete` e as boas práticas para manter o repositório organizado.
