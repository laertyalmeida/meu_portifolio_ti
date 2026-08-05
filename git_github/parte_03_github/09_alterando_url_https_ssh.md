## Tempo estimado de leitura

**20 minutos**

**Nível:** Intermediário

# Capítulo 09 – Alterando a URL do Repositório de HTTPS para SSH

---

# Neste capítulo você aprenderá

- Como verificar a URL remota de um repositório.
- O significado do comando `git remote`.
- Como alterar a URL de HTTPS para SSH.
- Como verificar se a alteração foi realizada corretamente.
- Como preparar o repositório para utilizar autenticação por chave SSH.

---

# Objetivo

Após gerar e configurar uma chave SSH no GitHub, o próximo passo é informar ao Git que o repositório remoto deverá utilizar esse novo método de autenticação.

Neste capítulo aprenderemos como alterar a URL do repositório remoto, substituindo o endereço HTTPS pelo endereço SSH.

A partir dessa alteração, as operações de envio e recebimento de alterações poderão utilizar a autenticação por chave SSH.

---

# Verificando a URL atual

O comando utilizado para visualizar os repositórios remotos é:

```bash
git remote -v
```

Vamos entender cada parte desse comando.

---

## git

Executa o Git.

---

## remote

A palavra **remote** significa:

> **Remoto**

Representa os repositórios hospedados em serviços como GitHub, GitLab ou Bitbucket.

O comando `git remote` é responsável por gerenciar esses repositórios.

---

## -v

A opção **-v** significa:

> **Verbose**

Em português:

> **Detalhado**

Ela informa ao Git que exiba os endereços completos dos repositórios remotos.

---

## git remote -v

Juntando todas as partes:

| Termo | Tradução |
|-------|----------|
| git | Git |
| remote | Remoto |
| -v | Verbose (Detalhado) |

Podemos entender que:

> **git remote -v = Exibir detalhadamente os repositórios remotos configurados**

---

# Resultado esperado

Ao executar o comando, uma saída semelhante à seguinte será exibida:

```text
origin  https://github.com/usuario/repositorio.git (fetch)
origin  https://github.com/usuario/repositorio.git (push)
```

Observe que o endereço remoto utiliza o protocolo **HTTPS**.

---

# Alterando a URL do repositório

O comando utilizado é:

```bash
git remote set-url origin git@github.com:usuario/repositorio.git
```

Vamos entender cada parte.

---

## set-url

A expressão **set-url** significa:

> **Definir URL**

Sua função é alterar o endereço configurado para um repositório remoto.

---

## origin

O nome **origin** representa o repositório remoto principal.

Por padrão, esse nome é criado automaticamente quando clonamos um repositório utilizando o Git.

Nada impede que existam outros repositórios remotos com nomes diferentes, porém **origin** é o mais utilizado.

---

## git@github.com

Essa parte informa que a comunicação será realizada utilizando o protocolo SSH com o servidor do GitHub.

---

## usuario/repositorio.git

Corresponde ao caminho do repositório dentro da conta do GitHub.

No projeto deste portfólio foi utilizado:

```text
git@github.com:laertecosta/meu_portifolio_ti.git
```

---

## git remote set-url

Juntando todas as partes:

| Termo | Tradução |
|-------|----------|
| git | Git |
| remote | Repositório remoto |
| set-url | Definir URL |
| origin | Repositório remoto principal |

Podemos entender que:

> **git remote set-url = Alterar o endereço de um repositório remoto**

---

# Executando a alteração

No projeto foi utilizado o comando:

```bash
git remote set-url origin git@github.com:laertecosta/meu_portifolio_ti.git
```

Caso a alteração seja realizada corretamente, o Git não exibirá nenhuma mensagem.

Isso é um comportamento esperado.

---

# Confirmando a alteração

Após modificar a URL, execute novamente:

```bash
git remote -v
```

O resultado esperado será semelhante a:

```text
origin  git@github.com:laertecosta/meu_portifolio_ti.git (fetch)
origin  git@github.com:laertecosta/meu_portifolio_ti.git (push)
```

Agora o repositório está utilizando autenticação via SSH.

---

# O que mudou?

Antes da alteração:

```text
https://github.com/usuario/repositorio.git
```

Depois da alteração:

```text
git@github.com:usuario/repositorio.git
```

A principal diferença é que o Git deixará de utilizar HTTPS para utilizar SSH durante a comunicação com o GitHub.

---

# Integração com o Projeto Linux

Neste capítulo foi apresentada a alteração da URL do repositório remoto para utilizar o protocolo SSH.

Embora essa configuração seja simples, ela depende de conceitos importantes sobre comunicação segura entre computadores.

No **Projeto Linux**, o protocolo SSH será estudado em profundidade, incluindo autenticação por chaves, configuração do serviço OpenSSH, gerenciamento de permissões, hardening e boas práticas de segurança.

Assim, este projeto aborda apenas a utilização prática do SSH para integração entre Git e GitHub, enquanto o Projeto Linux explorará o funcionamento interno desse protocolo.

---

# Boas práticas

- Sempre confirme a URL utilizando `git remote -v`.
- Utilize SSH apenas após cadastrar sua chave pública no GitHub.
- Mantenha o nome `origin`, salvo quando houver necessidade de múltiplos repositórios remotos.
- Nunca altere manualmente os arquivos internos do Git para modificar a URL; utilize sempre o comando `git remote set-url`.

---

# Resumo

Neste capítulo você aprendeu:

- como visualizar a URL do repositório remoto;
- o significado do comando `git remote`;
- a função da opção `-v`;
- como alterar a URL de HTTPS para SSH;
- como confirmar se a alteração foi realizada corretamente.

Seu repositório agora está configurado para utilizar autenticação SSH nas operações com o GitHub.

---

# O que foi realizado na prática

Durante este capítulo foram realizadas as seguintes atividades:

- ✔ Verificação da URL remota utilizando `git remote -v`.
- ✔ Estudo do comando `git remote`.
- ✔ Alteração da URL do repositório para SSH.
- ✔ Validação da nova configuração.
- ✔ Preparação do repositório para utilização da chave SSH.

---

# Próximo capítulo

## Capítulo 10 – Enviando Alterações para o GitHub utilizando SSH

No próximo capítulo você aprenderá como realizar o primeiro `git push` utilizando autenticação por chave SSH, compreendendo o significado do comando `git push -u origin`, além de validar a comunicação entre o repositório local e o GitHub.
