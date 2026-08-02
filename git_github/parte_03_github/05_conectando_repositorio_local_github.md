## Tempo estimado de leitura

**20 minutos**

**Nível:** Iniciante

# Capítulo 05 – Conectando um Repositório Local ao GitHub

---

# Neste capítulo você aprenderá

- O que é um repositório remoto.
- O que significa conectar um repositório local ao GitHub.
- O significado dos comandos utilizados nessa integração.
- Como verificar se a conexão foi criada corretamente.
- A importância do repositório remoto no controle de versões.

---

# Objetivo

Até este momento, todo o desenvolvimento foi realizado apenas no computador local.

Neste capítulo, será criada a conexão entre o repositório Git existente no computador e o repositório remoto criado no GitHub.

Essa conexão permitirá enviar e receber alterações entre os dois ambientes.

---

# O que é um repositório remoto?

Um **repositório remoto** é uma cópia do projeto armazenada em um servidor, permitindo que o código seja sincronizado pela internet.

Enquanto o repositório local fica armazenado no computador, o repositório remoto fica hospedado no GitHub.

Essa estrutura oferece diversas vantagens:

- Backup do projeto.
- Compartilhamento do código.
- Trabalho em equipe.
- Acesso ao projeto em diferentes computadores.
- Histórico centralizado das alterações.

---

# Obtendo o endereço do repositório

Após criar o repositório no GitHub, será exibido um endereço semelhante a um dos exemplos abaixo.

Via HTTPS:

```text
https://github.com/usuario/git_github.git
```

Via SSH:

```text
git@github.com:usuario/git_github.git
```
O **usuario** significa:

> **username** → *O nome de usuario público cadastrado no capítulo 02*

---

Neste momento apenas utilizaremos esse endereço para criar a conexão.

A autenticação via HTTPS e SSH será estudada detalhadamente nos próximos capítulos.

---

# O comando git remote

O comando utilizado para gerenciar repositórios remotos é:

```bash
git remote
```

A palavra **remote** significa:

> **Remoto**

Esse comando é responsável por listar, adicionar, remover e alterar conexões entre o repositório local e repositórios remotos.

---

# Adicionando um repositório remoto

Para criar a conexão utiliza-se o comando:

```bash
git remote add origin <URL_DO_REPOSITORIO>
```

Exemplo:

```bash
git remote add origin git@github.com:usuario/git_github.git
```

Vamos entender cada parte desse comando.

---

## git

Executa o Git.

---

## remote

Significa:

> **Remoto**

Informa que o comando trabalhará com repositórios remotos.

---

## add

A palavra **add** significa:

> **Adicionar**

Nesse caso, será adicionada uma nova conexão com um repositório remoto.

---

## origin

A palavra **origin** significa:

> **Origem**

Ela é apenas um apelido (alias) criado para identificar o repositório remoto principal.

Embora seja possível utilizar outro nome, **origin** é o padrão adotado pela maioria dos projetos.

---

## URL_DO_REPOSITORIO

É o endereço do repositório criado no GitHub.

Pode utilizar HTTPS ou SSH.

---

# Verificando a conexão

Após adicionar o repositório remoto, podemos verificar se tudo foi configurado corretamente utilizando:

```bash
git remote -v
```

A opção **-v** significa:

> **Verbose**

Em português:

> **Detalhado**

Ela faz com que o Git exiba o endereço utilizado para envio (**push**) e recebimento (**fetch**) das alterações.

Exemplo:

```text
origin  git@github.com:usuario/git_github.git (fetch)
origin  git@github.com:usuario/git_github.git (push)
```

---

# O que significa Fetch?

A palavra **Fetch** significa:

> **Buscar**

É utilizada quando o Git consulta alterações existentes no repositório remoto.

---

# O que significa Push?

A palavra **Push** significa:

> **Enviar**

É utilizada quando enviamos alterações do computador para o GitHub.

Nos próximos capítulos esse comando será utilizado na prática.

---

# Boas práticas

- Utilize sempre o endereço correto do repositório.
- Verifique a conexão utilizando `git remote -v`.
- Evite adicionar o mesmo repositório remoto mais de uma vez.
- Utilize nomes diferentes apenas quando trabalhar com múltiplos repositórios remotos.

---

# Resumo

Neste capítulo você aprendeu:

- o que é um repositório remoto;
- como conectar o Git ao GitHub;
- o significado do comando `git remote`;
- a função do apelido **origin**;
- como verificar se a conexão foi criada corretamente.

Seu projeto agora está preparado para realizar a primeira sincronização com o GitHub.

---

# O que foi realizado na prática

Durante este capítulo foram realizadas as seguintes atividades:

- ✔ Cópia da URL do repositório remoto.
- ✔ Criação da conexão entre o Git e o GitHub.
- ✔ Configuração do repositório remoto **origin**.
- ✔ Verificação da conexão utilizando `git remote -v`.

---

# Próximo capítulo

## Capítulo 06 – Autenticação via HTTPS

No próximo capítulo você aprenderá como funciona a autenticação utilizando HTTPS, compreenderá suas vantagens e limitações e entenderá por que, posteriormente, será realizada a migração para autenticação via SSH.
