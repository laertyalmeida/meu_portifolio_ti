## Tempo estimado de leitura

**30 minutos**

**Nível:** Intermediário

# Capítulo 08 – Gerando e Configurando uma Chave SSH

---

# Neste capítulo você aprenderá

- O que é uma chave SSH.
- Como gerar um par de chaves criptográficas.
- O significado do comando `ssh-keygen`.
- Como adicionar a chave pública ao GitHub.
- Como testar a conexão entre o computador e o GitHub.

---

# Objetivo

Após compreender o funcionamento do protocolo SSH, o próximo passo é gerar um par de chaves criptográficas.

Essas chaves permitirão que o computador seja reconhecido pelo GitHub de forma segura, dispensando a necessidade de informar credenciais durante as operações do Git.

---

# O comando ssh-keygen

O comando utilizado para gerar chaves SSH é:

```bash
ssh-keygen
```

Vamos entender o significado desse comando.

---

## ssh

A sigla **SSH** significa:

> **Secure Shell**

Em português:

> **Shell Seguro**

É o protocolo responsável pela comunicação segura entre computadores.

---

## key

A palavra **key** significa:

> **Chave**

No contexto do SSH, representa uma chave criptográfica utilizada para autenticação.

---

## gen

A palavra **gen** é uma abreviação de:

> **Generate**

Em português:

> **Gerar**

---

## ssh-keygen

Juntando todas as partes:

| Termo | Tradução         |
|-------|------------------|
| ssh   | Secure Shell     |
| key   | Chave            |
| gen   | Generate (Gerar) |

Podemos entender que:

> **ssh-keygen = Gerador de Chaves SSH**

---

# Gerando a chave

O comando utilizado neste projeto foi:

```bash
ssh-keygen -t ed25519 -C "seu_email@exemplo.com"
```

Vamos entender cada parte.

---

## -t

A opção **-t** significa:

> **Type**

Em português:

> **Tipo**

Ela informa qual algoritmo será utilizado para gerar a chave.

---

## ed25519

O **Ed25519** é um algoritmo criptográfico moderno utilizado para gerar chaves SSH.

Atualmente é considerado um dos algoritmos mais seguros, rápidos e eficientes para autenticação.

Por esse motivo, é o algoritmo recomendado pelo GitHub para a maioria dos usuários.

---

## -C

A opção **-C** significa:

> **Comment**

Em português:

> **Comentário**

Normalmente é utilizada para adicionar um endereço de e-mail que ajudará a identificar a chave futuramente.

Esse comentário não interfere na segurança da chave.

---

# Onde as chaves são armazenadas?

Após executar o comando, o SSH cria automaticamente um diretório chamado:

```text
~/.ssh
```

Dentro dele normalmente são criados dois arquivos.

---

## id_ed25519

Esse arquivo contém a:

> **Chave Privada**

Ela deve permanecer apenas no computador.

**Nunca compartilhe esse arquivo.**

---

## id_ed25519.pub

Esse arquivo contém a:

> **Chave Pública**

Ela poderá ser compartilhada e adicionada ao GitHub.

---

# Adicionando a chave pública ao GitHub

Para visualizar a chave pública pode ser utilizado:

```bash
cat ~/.ssh/id_ed25519.pub
```

O comando `cat` exibirá o conteúdo da chave.

Copie todo o conteúdo exibido.

No GitHub acesse:

**Settings → SSH and GPG keys → New SSH key**

---

## SSH and GPG keys

Significa:

> **Chaves SSH e GPG**

É a área onde ficam cadastradas as chaves utilizadas para autenticação.

---

## New SSH key

Significa:

> **Nova chave SSH**

Clique nessa opção para adicionar a chave pública gerada anteriormente.

---

## Title

Significa:

> **Título**

Utilize um nome que identifique facilmente o computador.

Exemplo:

```text
Notebook Debian 13
```

---

## Key

Significa:

> **Chave**

Cole nesse campo todo o conteúdo do arquivo:

```text
id_ed25519.pub
```

Depois clique em:

**Add SSH key**

que significa:

> **Adicionar chave SSH**

---

# Testando a conexão

Após adicionar a chave ao GitHub, utilize o comando:

```bash
ssh -T git@github.com
```

Vamos entender esse comando.

---

## ssh

Inicia uma conexão utilizando o protocolo SSH.

---

## -T

A opção **-T** significa:

> **Disable pseudo-terminal allocation**

Em português:

> **Não criar um terminal interativo.**

Como o objetivo é apenas verificar a autenticação, não é necessário abrir um terminal remoto.

---

## git@github.com

Indica o serviço e o servidor que receberão a conexão.

---

# Resultado esperado

Se tudo estiver correto, será exibida uma mensagem semelhante a:

```text
Hi usuario! You've successfully authenticated, but GitHub does not provide shell access.
```

Tradução:

> Olá, usuário! Sua autenticação foi realizada com sucesso, porém o GitHub não fornece acesso ao Shell.

Isso significa que a autenticação foi realizada corretamente.

---

# Integração com o Projeto Linux

Neste capítulo foi apresentada a utilização do protocolo SSH para autenticação entre o Git instalado no computador e o GitHub.

Embora o foco deste projeto seja a integração entre Git e GitHub, o SSH é um protocolo muito mais amplo e amplamente utilizado na administração de sistemas Linux.

Por esse motivo, o **Projeto Linux** deste portfólio contará com um capítulo exclusivo dedicado ao SSH, abordando esse assunto de forma muito mais aprofundada.

Entre os tópicos que serão estudados nesse projeto estão:

- instalação do OpenSSH Server;
- instalação do OpenSSH Client;
- configuração do arquivo `sshd_config`;
- geração de chaves SSH utilizando algoritmos modernos, como **Ed25519**, e comparação com algoritmos legados, como **RSA**;
- autenticação por chave pública;
- autenticação por senha;
- configuração de permissões corretas dos arquivos de chave;
- alteração da porta padrão do SSH;
- desativação do acesso direto do usuário **root**;
- utilização do arquivo `authorized_keys`;
- configuração do arquivo `known_hosts`;
- boas práticas de segurança (Hardening);
- testes de conexão entre computadores Linux;
- administração remota de servidores utilizando SSH.

Também será apresentada uma abordagem mais aprofundada sobre segurança, demonstrando como fortalecer a autenticação utilizando algoritmos modernos e configurações recomendadas para reduzir riscos de acesso não autorizado.

Dessa forma, este projeto apresenta o SSH sob a perspectiva da integração entre o Git e o GitHub, enquanto o Projeto Linux abordará o protocolo SSH como um dos serviços mais importantes para administração de sistemas Linux.

---

# Boas práticas

- Nunca compartilhe sua chave privada.
- Compartilhe apenas a chave pública.
- Utilize um título que identifique cada computador.
- Faça backup seguro das suas chaves.
- Remova chaves antigas que não são mais utilizadas.

---

# Resumo

Neste capítulo você aprendeu:

- como gerar um par de chaves SSH;
- o significado do comando `ssh-keygen`;
- a função das opções `-t` e `-C`;
- a diferença entre chave pública e chave privada;
- como adicionar uma chave ao GitHub;
- como testar a autenticação.

Seu computador agora está preparado para utilizar autenticação SSH com o GitHub.

---

# O que foi realizado na prática

Durante este capítulo foram realizadas as seguintes atividades:

- ✔ Geração do par de chaves SSH.
- ✔ Estudo dos parâmetros do comando `ssh-keygen`.
- ✔ Cadastro da chave pública no GitHub.
- ✔ Teste da autenticação utilizando `ssh -T`.
- ✔ Validação da comunicação segura entre o computador e o GitHub.

---

# Próximo capítulo

## Capítulo 09 – Alterando a URL do Repositório de HTTPS para SSH

No próximo capítulo você aprenderá como alterar a URL do repositório remoto utilizando o comando `git remote set-url`, migrando definitivamente a autenticação de HTTPS para SSH.
