## Tempo estimado de leitura

**30 minutos**

**Nível:** Intermediário

# Capítulo 07 – Autenticação via SSH

---

# Neste capítulo você aprenderá

- O que é SSH.
- Como funciona a autenticação por chaves criptográficas.
- As vantagens do SSH em relação ao HTTPS.
- O significado dos principais termos utilizados.
- Por que muitos desenvolvedores utilizam SSH.

---

# Objetivo

Após conhecer a autenticação via HTTPS, chegou o momento de aprender um método mais utilizado em ambientes profissionais.

O SSH permite estabelecer uma comunicação segura entre o computador e o GitHub utilizando um par de chaves criptográficas, dispensando a necessidade de informar credenciais durante as operações do Git.

---

# O que é SSH?

A sigla **SSH** significa:

> **Secure Shell**

Em português:

> **Shell Seguro**

O SSH é um protocolo utilizado para criar conexões seguras entre dois computadores através da rede.

Além do GitHub, o SSH é amplamente utilizado para:

- administrar servidores Linux;
- acessar máquinas remotamente;
- copiar arquivos entre computadores;
- executar comandos à distância;
- autenticar usuários em diversos serviços.

---

# O que é um Shell?

A palavra **Shell** significa:

> **Interpretador de comandos**

É o programa responsável por receber os comandos digitados pelo usuário e enviá-los ao sistema operacional.

No Linux, exemplos de Shell são:

- Bash
- Zsh
- Fish

O SSH permite utilizar esse interpretador de forma segura através da rede.

---

# Como funciona a autenticação SSH?

Ao contrário do HTTPS, o SSH utiliza duas chaves criptográficas.

Essas chaves trabalham em conjunto.

Elas são conhecidas como:

- Chave Pública (**Public Key**)
- Chave Privada (**Private Key**)

---

# Public Key

**Public Key** significa:

> **Chave Pública**

Essa chave pode ser compartilhada.

Ela será adicionada ao GitHub para identificar seu computador.

---

# Private Key

**Private Key** significa:

> **Chave Privada**

Essa chave permanece armazenada apenas no seu computador.

Ela nunca deve ser compartilhada.

Caso outra pessoa tenha acesso à sua chave privada, poderá se passar por você.

---

# Como ocorre a autenticação?

O processo funciona da seguinte forma:

1. O computador envia uma solicitação ao GitHub.

2. O GitHub verifica se a chave pública cadastrada corresponde à chave privada armazenada no computador.

3. Caso as chaves sejam compatíveis, o acesso é autorizado.

Todo esse processo acontece automaticamente.

---

# Vantagens do SSH

Entre as principais vantagens estão:

- Maior praticidade.
- Comunicação criptografada.
- Não exige informar credenciais durante cada operação.
- Muito utilizado em ambientes profissionais.
- Excelente opção para automações.

---

# HTTPS x SSH

| HTTPS | SSH |
|--------|-----|
| Utiliza protocolo HTTPS. | Utiliza protocolo SSH. |
| Configuração mais simples. | Requer configuração inicial. |
| Pode utilizar Token de Acesso. | Utiliza chaves criptográficas. |
| Ideal para iniciantes. | Muito utilizado em ambientes profissionais. |

Ambos são seguros.

A escolha dependerá das necessidades do projeto e da forma de autenticação desejada.

---

# Quando utilizar SSH?

O SSH é recomendado quando:

- você trabalha frequentemente com Git;
- utiliza sempre o mesmo computador;
- deseja maior praticidade;
- pretende trabalhar profissionalmente com desenvolvimento;
- realiza automações utilizando Git.

---

# Experiência prática

Neste projeto, a integração com o GitHub foi iniciada utilizando HTTPS.

Posteriormente, foi realizada a migração para SSH.

Essa mudança eliminou a necessidade de utilizar autenticação baseada em credenciais para cada operação, tornando o processo mais prático para o desenvolvimento diário.

---

# Boas práticas

- Nunca compartilhe sua chave privada.
- Faça backup seguro das suas chaves.
- Utilize senhas fortes em sua conta GitHub.
- Ative a autenticação em dois fatores (2FA).
- Revogue chaves antigas que não são mais utilizadas.

---

# Resumo

Neste capítulo você aprendeu:

- o significado da sigla SSH;
- como funciona a autenticação por chaves;
- a diferença entre chave pública e chave privada;
- as vantagens do SSH;
- quando utilizar esse método de autenticação.

Esses conceitos serão fundamentais para os próximos capítulos, nos quais serão geradas as chaves SSH e realizada a configuração completa da autenticação entre o Git e o GitHub.

---

# O que foi realizado na prática

Durante este capítulo foram realizadas as seguintes atividades:

- ✔ Estudo do protocolo SSH.
- ✔ Compreensão da autenticação por chaves.
- ✔ Comparação entre HTTPS e SSH.
- ✔ Planejamento da migração para autenticação via SSH.

---

# Próximo capítulo

## Capítulo 08 – Gerando uma Chave SSH

No próximo capítulo você aprenderá como gerar um par de chaves SSH utilizando o comando `ssh-keygen`, compreenderá o significado de cada parâmetro utilizado e preparará seu computador para autenticação segura com o GitHub.
