# Configuração da identidade do Git

## Objetivo

Configurar o nome e o e-mail que serão registrados automaticamente em cada commit (registro no repositório) realizado pelo Git.

Essas informações identificam o autor das alterações realizadas no repositório.

---

## Ambiente utilizado

- Sistema operacional: Debian 13 (Trixie)
- Shell: Bash
- Terminal: XFCE Terminal
- Git: versão 2.47.3

---

## Configurando o nome do usuário

```bash
git config --global user.name "Seu Nome"
```

Exemplo:

```bash
git config --global user.name "Laerte Costa"
```

---

## Configurando o e-mail

```bash
git config --global user.email "seuemail@email.com"
```

Exemplo:

```bash
git config --global user.email "laerte@email.com"
```

---

## Verificando a configuração

Consultar apenas o nome:

```bash
git config --global user.name
```

Consultar apenas o e-mail:

```bash
git config --global user.email
```

Visualizar todas as configurações do Git:

```bash
git config --list
```

---

## Onde essas informações ficam armazenadas

Quando utilizamos a opção `--global`, as configurações são gravadas no arquivo:

```text
~/.gitconfig
```

É possível visualizar esse arquivo com:

```bash
cat ~/.gitconfig
```

---

## Resumo

- `git config` → configura opções do Git.
- `--global` → aplica a configuração para todos os repositórios do usuário.
- `user.name` → nome do autor dos commits.
- `user.email` → e-mail do autor dos commits.
- `git config --list` → mostra todas as configurações.
- `cat ~/.gitconfig` → exibe o arquivo onde as configurações são armazenadas.

---

## Próxima etapa

Na próxima etapa será criado o primeiro repositório Git e serão apresentados os comandos:

```bash
git init
git status
```

Esses comandos iniciam o controle de versão de um projeto e permitem verificar o estado dos arquivos.
