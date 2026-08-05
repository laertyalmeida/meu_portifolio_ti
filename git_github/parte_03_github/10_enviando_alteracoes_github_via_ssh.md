## Tempo estimado de leitura

**25 minutos**

**Nível:** Intermediário

# Capítulo 10 – Enviando Alterações para o GitHub utilizando SSH

---

# Neste capítulo você aprenderá

- Como enviar alterações do repositório local para o GitHub utilizando SSH.
- O significado do comando `git push`.
- A função da opção `-u`.
- O que é um repositório remoto.
- Como verificar se o envio foi realizado com sucesso.

---

# Objetivo

Após configurar a autenticação por chave SSH e alterar a URL do repositório remoto, chegou o momento de realizar o primeiro envio de alterações utilizando esse novo método de autenticação.

Neste capítulo aprenderemos como utilizar o comando `git push`, responsável por enviar os commits do repositório local para o repositório hospedado no GitHub.

---

# O comando git push

O comando utilizado para enviar alterações é:

```bash
git push -u origin nome_da_branch
```

No projeto deste portfólio foi utilizado:

```bash
git push -u origin padronizacao_documentacao
```

Vamos entender cada parte desse comando.

---

## git

Executa o Git.

---

## push

A palavra **push** significa:

> **Empurrar**

No Git, representa a ação de enviar os commits do computador para um repositório remoto.

---

## -u

A opção **-u** significa:

> **Upstream**

Em português, pode ser entendida como:

> **Definir um repositório remoto padrão para esta branch.**

Após utilizar essa opção pela primeira vez, os próximos envios poderão ser realizados apenas com:

```bash
git push
```

E os próximos downloads de alterações poderão ser realizados apenas com:

```bash
git pull
```

Isso acontece porque o Git memoriza qual repositório remoto e qual branch estão associados à branch local.

---

## origin

O nome **origin** representa o repositório remoto principal.

É para ele que os commits serão enviados.

---

## padronizacao_documentacao

Corresponde ao nome da branch local que será enviada ao GitHub.

Cada branch representa uma linha de desenvolvimento independente dentro do projeto.

---

## git push -u origin

Juntando todas as partes:

| Termo | Tradução |
|--------|----------|
| git | Git |
| push | Enviar alterações |
| -u | Definir upstream |
| origin | Repositório remoto principal |

Podemos entender que:

> **git push -u origin = Enviar a branch para o repositório remoto e definir sua associação para os próximos envios.**

---

# Executando o comando

No projeto foi utilizado:

```bash
git push -u origin padronizacao_documentacao
```

Durante o envio, o Git exibirá informações sobre:

- quantidade de objetos enviados;
- compactação dos arquivos;
- velocidade da transferência;
- criação da branch remota;
- associação entre a branch local e a branch remota.

Uma saída semelhante à seguinte poderá ser exibida:

```text
Enumerating objects: 283, done.
Counting objects: 100% (283/283), done.
Delta compression using up to 4 threads.
Compressing objects: 100% (.../...).
Writing objects: 100% (.../...).
Total ... (delta ...), reused ...
remote:
remote: Create a pull request for 'padronizacao_documentacao' on GitHub by visiting:
remote: https://github.com/usuario/repositorio/pull/new/padronizacao_documentacao
remote:
To github.com:usuario/repositorio.git
 * [new branch]      padronizacao_documentacao -> padronizacao_documentacao
Branch 'padronizacao_documentacao' set up to track remote branch 'padronizacao_documentacao' from 'origin'.
```

A quantidade de objetos e demais informações poderá variar conforme o projeto.

---

# O que significa "Branch set up to track"?

Quando o Git exibe a mensagem:

```text
Branch 'padronizacao_documentacao' set up to track remote branch...
```

significa que a branch local passou a acompanhar automaticamente a branch remota.

A partir desse momento, comandos como:

```bash
git push
```

e

```bash
git pull
```

não precisarão mais informar `origin` e o nome da branch, pois essa associação já foi registrada.

---

# Verificando o envio

Após concluir o envio, acesse seu repositório no GitHub.

Verifique se:

- a nova branch foi criada;
- os commits estão disponíveis;
- os arquivos enviados aparecem corretamente no repositório.

Isso confirma que a comunicação entre o Git local e o GitHub ocorreu com sucesso utilizando SSH.

---

# Integração com o Projeto Linux

Neste capítulo foi apresentado o envio de alterações para um servidor remoto utilizando o protocolo SSH.

Embora o usuário interaja apenas com o comando `git push`, internamente o Git utiliza uma conexão SSH autenticada por chave criptográfica para estabelecer uma comunicação segura com o GitHub.

No **Projeto Linux**, serão estudados em detalhes os mecanismos que tornam essa comunicação possível, incluindo o funcionamento do OpenSSH, autenticação por chave pública, negociação de algoritmos criptográficos, permissões dos arquivos e boas práticas de segurança.

---

# Boas práticas

- Sempre realize um `git status` antes do `git push`.
- Escreva mensagens de commit claras antes de enviar alterações.
- Confirme se está na branch correta utilizando `git branch`.
- Utilize `git push -u` apenas no primeiro envio da branch.
- Após a configuração do upstream, utilize apenas `git push`.

---

# Resumo

Neste capítulo você aprendeu:

- como utilizar o comando `git push`;
- o significado da opção `-u`;
- a função do repositório remoto `origin`;
- como enviar uma branch para o GitHub;
- como verificar se a branch passou a acompanhar o repositório remoto.

Seu projeto agora está sincronizado entre o computador e o GitHub utilizando autenticação por chave SSH.

---

# O que foi realizado na prática

Durante este capítulo foram realizadas as seguintes atividades:

- ✔ Envio da branch para o GitHub utilizando SSH.
- ✔ Estudo do comando `git push`.
- ✔ Compreensão da opção `-u`.
- ✔ Associação entre a branch local e a branch remota.
- ✔ Validação da sincronização do repositório.

---

# Próximo capítulo

## Capítulo 11 – Alterando a Branch Padrão no GitHub

No próximo capítulo você aprenderá como alterar a branch padrão do repositório no GitHub, entendendo sua importância para o desenvolvimento do projeto e para a organização do fluxo de trabalho.
