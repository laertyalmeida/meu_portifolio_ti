## Tempo estimado de leitura

**20 minutos**

**Nível:** Iniciante

# Capítulo 06 – Autenticação via HTTPS

---

# Neste capítulo você aprenderá

- O que é HTTPS.
- Como funciona a autenticação via HTTPS.
- Quais são suas vantagens e limitações.
- Quando utilizar esse método de autenticação.
- Como verificar a URL HTTPS de um repositório.

---

# Objetivo

Para que o Git possa enviar e receber alterações de um repositório remoto, é necessário utilizar um método de autenticação.

O primeiro método estudado será o HTTPS, que é amplamente utilizado por sua simplicidade e facilidade de configuração.

---

# O que é HTTPS?

A sigla **HTTPS** significa:

> **HyperText Transfer Protocol Secure**

Em português:

> **Protocolo Seguro de Transferência de Hipertexto**

O HTTPS é um protocolo utilizado para transmitir informações de forma criptografada pela internet.

Ele é utilizado diariamente em diversos serviços, como:

- bancos;
- lojas virtuais;
- redes sociais;
- serviços de e-mail;
- GitHub.

Quando um endereço começa com:

```text
https://
```

isso indica que a comunicação entre o computador e o servidor é realizada utilizando uma conexão segura.

---

# Como o Git utiliza o HTTPS?

Ao conectar um repositório utilizando HTTPS, o Git envia e recebe informações através desse protocolo.

Um endereço HTTPS normalmente possui o seguinte formato:

```text
https://github.com/usuario/repositorio.git
```

Nesse exemplo:

- **https://** → protocolo utilizado para comunicação.
- **github.com** → servidor onde o projeto está hospedado.
- **usuario** → nome do proprietário da conta (username).
- **repositorio.git** → nome do repositório.

---

# Como visualizar a URL HTTPS?

Na página principal do **repositório** no GitHub:

1. Clique no botão **Code**.

A palavra **Code** significa:

> **Código**

2. Será exibida uma janela contendo diferentes formas de acesso ao repositório.

3. Selecione a opção **HTTPS**.

4. Copie a URL apresentada.

---

# Quando utilizar HTTPS?

O HTTPS costuma ser recomendado quando:

- você está aprendendo Git e GitHub;
- utiliza computadores compartilhados;
- não deseja configurar chaves SSH;
- precisa de uma configuração rápida.

É um método simples e bastante utilizado por iniciantes.

---

# Limitações do HTTPS

Embora seja simples de configurar, o HTTPS possui algumas limitações.

Dependendo da configuração utilizada, poderá ser necessário realizar autenticação sempre que forem enviados dados ao GitHub.

Atualmente, o GitHub não permite mais autenticação utilizando apenas senha da conta.

Em seu lugar, podem ser utilizados recursos como:

- Personal Access Token (PAT);
- Gerenciadores de credenciais;
- Outros mecanismos de autenticação suportados.

Esses recursos tornam o acesso mais seguro do que o uso de senhas tradicionais.

---

# HTTPS x Segurança

É importante entender que o HTTPS continua sendo um protocolo seguro.

A principal diferença está na forma como o usuário comprova sua identidade para acessar o GitHub.

Por esse motivo, muitos desenvolvedores preferem utilizar autenticação via SSH, assunto que será estudado nos próximos capítulos.

---

# Boas práticas

- Utilize sempre URLs iniciadas por `https://`.
- Nunca compartilhe seus tokens de acesso.
- Evite armazenar credenciais em computadores públicos.
- Mantenha sua conta protegida com autenticação em dois fatores (2FA).

---

# Resumo

Neste capítulo você aprendeu:

- o significado da sigla HTTPS;
- como funciona a autenticação utilizando esse protocolo;
- como localizar a URL HTTPS de um repositório;
- quando utilizar esse método;
- quais são suas vantagens e limitações.

O HTTPS é uma excelente opção para iniciar os estudos e compreender como ocorre a comunicação entre o Git e o GitHub.

---

# O que foi realizado na prática

Durante este capítulo foram realizadas as seguintes atividades:

- ✔ Identificação da URL HTTPS do repositório.
- ✔ Estudo da estrutura da URL.
- ✔ Compreensão do funcionamento da autenticação via HTTPS.
- ✔ Comparação inicial entre HTTPS e SSH.

---

# Próximo capítulo

## Capítulo 07 – Autenticação via SSH

No próximo capítulo você aprenderá por que muitos desenvolvedores utilizam SSH, conhecerá suas vantagens em relação ao HTTPS e iniciará o processo de migração da autenticação para esse novo método.
