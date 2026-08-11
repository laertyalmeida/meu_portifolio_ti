# Git e GitHub — Guia de Estudos

## Capítulo 09 — Ignorando Arquivos com `.gitignore`

**Tempo estimado de leitura:** 12 minutos
**Nível:** Iniciante

---

## Neste capítulo você aprenderá

* O que é o arquivo `.gitignore`.
* Por que alguns arquivos não devem ser versionados.
* Como criar um `.gitignore`.
* Como ignorar arquivos e diretórios.
* Como ignorar arquivos dentro de subdiretórios.
* Como verificar se uma regra do `.gitignore` está funcionando.
* O que fazer quando um arquivo já está sendo rastreado pelo Git.

---

# Informações do capítulo

| Campo                   | Informação                          |
| ----------------------- | ----------------------------------- |
| **Capítulo**            | 09                                  |
| **Título**              | Ignorando Arquivos com `.gitignore` |
| **Autor**               | Laerte Costa                        |
| **Sistema Operacional** | Debian GNU/Linux                    |
| **Terminal**            | Bash                                |
| **Última atualização**  | Agosto de 2026                      |

---

# Objetivo deste capítulo

Neste capítulo, você vai aprender a utilizar o arquivo `.gitignore` para informar ao Git quais arquivos e diretórios não devem fazer parte do controle de versão.

Isso é útil para evitar que arquivos temporários, logs, arquivos de configuração local e outros conteúdos desnecessários sejam adicionados ao repositório.

---

# Pré-requisitos

É recomendado ter concluído os capítulos anteriores, principalmente os capítulos sobre:

* `git status`;
* `git add`;
* `git commit`;
* Área de Trabalho;
* Área de Preparação.

---

# 1. O que é o `.gitignore`?

Nem todos os arquivos existentes em um projeto precisam ser controlados pelo Git.

Alguns arquivos são criados automaticamente pelo sistema ou pelos programas utilizados durante o desenvolvimento.

Exemplos:

```text
arquivos temporários
logs
cache
arquivos compilados
configurações locais
arquivos gerados automaticamente
```

Esses arquivos podem não fazer parte do projeto e, em muitos casos, não devem ser enviados para o repositório.

Para informar ao Git quais arquivos devem ser ignorados, utilizamos o arquivo:

```text
.gitignore
```

---

# 2. Por que utilizar o `.gitignore`?

Imagine que um programa gere automaticamente arquivos de log:

```text
app.log
erro.log
debug.log
```

Esses arquivos podem mudar constantemente e não precisam fazer parte do histórico do projeto.

Se fossem adicionados ao Git, poderiam gerar muitos *commits* desnecessários.

O `.gitignore` permite informar ao Git:

> "Esses arquivos não precisam ser considerados pelo controle de versão."

---

# 3. Criando o `.gitignore`

Primeiro, crie o arquivo `.gitignore` na raiz do projeto.

### Comando

```bash
touch .gitignore
```

O comando `touch` cria um arquivo vazio caso ele ainda não exista.

> **Resumo**
>
> `touch .gitignore` → cria o arquivo `.gitignore`.

---

# 4. Onde colocar o `.gitignore`?

Na maioria dos projetos, o `.gitignore` principal fica na **raiz do repositório**.

Por exemplo:

```text
meu_projeto/
├── .git/
├── .gitignore
├── README.md
├── docs/
├── src/
└── imagens/
```

A pasta `.git` identifica o diretório que contém o repositório.

Um `.gitignore` localizado na raiz pode definir regras que afetam arquivos e diretórios existentes em diferentes partes do projeto.

Também é possível utilizar arquivos `.gitignore` dentro de subdiretórios quando um projeto possui necessidades específicas.

Para projetos pequenos, normalmente um único `.gitignore` na raiz já é suficiente.

---

# 5. Criando regras

Abra o `.gitignore` no editor de sua preferência.

Por exemplo:

```text
*.log
*.tmp
cache/
```

Cada linha representa uma regra.

### `*.log`

```text
*.log
```

Ignora arquivos que terminam com `.log`.

Exemplos:

```text
app.log
erro.log
sistema.log
```

---

### `*.tmp`

```text
*.tmp
```

Ignora arquivos que terminam com `.tmp`.

Exemplos:

```text
arquivo.tmp
teste.tmp
backup.tmp
```

---

### `cache/`

```text
cache/
```

Ignora o diretório `cache` e seu conteúdo.

---

# 6. Ignorando arquivos em um subdiretório

Também podemos criar regras para caminhos específicos.

Imagine esta estrutura:

```text
meu_projeto/
├── parte1/
│   ├── teste.txt
│   └── exemplo.py
├── parte2/
│   └── teste.txt
└── .gitignore
```

Se quisermos ignorar apenas:

```text
parte1/teste.txt
```

podemos colocar no `.gitignore`:

```text
parte1/teste.txt
```

Nesse caso, o arquivo:

```text
parte2/teste.txt
```

não será ignorado por essa regra.

---

# 7. Ignorando uma extensão em um diretório específico

Também podemos utilizar:

```text
parte1/*.txt
```

Essa regra ignora arquivos `.txt` diretamente dentro de `parte1`.

Por exemplo:

```text
parte1/teste.txt
parte1/anotacoes.txt
parte1/exemplo.txt
```

serão ignorados.

Mas um arquivo como:

```text
parte2/teste.txt
```

não será afetado por essa regra.

---

# 8. Ignorando um diretório específico

Para ignorar um diretório dentro de uma determinada pasta:

```text
parte1/cache/
```

Nesse caso, a regra afeta o diretório `cache` localizado dentro de `parte1`.

Exemplo:

```text
meu_projeto/
├── parte1/
│   └── cache/
├── parte2/
│   └── cache/
└── .gitignore
```

A regra:

```text
parte1/cache/
```

ignora apenas:

```text
parte1/cache/
```

O diretório:

```text
parte2/cache/
```

continua sendo tratado normalmente pelo Git.

---

# 9. Testando o `.gitignore`

Vamos testar se uma regra está funcionando.

Suponha que seu `.gitignore` contenha:

```text
*.log
```

Agora crie um arquivo:

```text
teste.log
```

Você pode criá-lo com:

```bash
touch teste.log
```

Depois execute:

```bash
git status
```

O arquivo `teste.log` não deverá aparecer como um novo arquivo (*untracked*).

Isso significa que a regra do `.gitignore` está funcionando.

---

# 10. Descobrindo qual regra está ignorando um arquivo

Quando um arquivo é ignorado e você não sabe o motivo, o Git possui um comando muito útil:

```bash
git check-ignore -v teste.log
```

Esse comando verifica se o arquivo está sendo ignorado e mostra qual regra foi responsável por isso.

---

# 11. Entendendo `git check-ignore -v`

Vamos dividir o comando:

```text
git check-ignore -v teste.log
│   │           │
│   │           └── arquivo que será verificado
│   └────────────── verifica regras de arquivos ignorados
└────────────────── comando do Git
```

### `check-ignore`

Significa verificar se um arquivo está sendo ignorado.

### `-v`

Significa *verbose*, ou seja, **detalhado**.

A opção mostra informações adicionais sobre a regra encontrada.

---

# 12. Exemplo de saída

Imagine que o `.gitignore` contenha:

```text
*.log
```

Ao executar:

```bash
git check-ignore -v teste.log
```

podemos obter:

```text
.gitignore:1:*.log    teste.log
```

Podemos interpretar assim:

```text
.gitignore → arquivo que contém a regra
1          → número da linha
*.log      → regra aplicada
teste.log  → arquivo afetado
```

Esse comando é muito útil para descobrir por que determinado arquivo está sendo ignorado.

---

# 13. Como o `.gitignore` funciona?

Quando o Git encontra um arquivo que ainda não está sendo rastreado e esse arquivo corresponde a uma regra do `.gitignore`, ele normalmente não o apresenta como um arquivo novo no `git status`.

Por exemplo:

```text
*.log
```

Faz com que:

```text
app.log
erro.log
teste.log
```

sejam ignorados.

Assim, comandos como:

```bash
git status
```

e:

```bash
git add .
```

não tratarão esses arquivos como arquivos novos para serem adicionados normalmente.

---

# 14. Atenção: arquivos já rastreados

Existe um detalhe muito importante:

> O `.gitignore` não faz um arquivo já rastreado pelo Git deixar de ser rastreado.

Imagine que você tenha:

```text
config.txt
```

e já tenha feito:

```bash
git add config.txt
```

e depois:

```bash
git commit -m "Adiciona configuração"
```

Agora o Git já conhece e controla esse arquivo.

Se você adicionar:

```text
config.txt
```

ao `.gitignore`, isso **não fará o Git parar de rastreá-lo**.

---

# 15. Removendo um arquivo do controle do Git

Para deixar de rastrear o arquivo, mas mantê-lo no computador, utilize:

```bash
git rm --cached config.txt
```

O `--cached` é importante porque remove o arquivo do **índice do Git**, mas não apaga o arquivo do diretório de trabalho.

Depois disso, se o arquivo estiver listado no `.gitignore`, o Git passará a ignorá-lo.

---

# 16. Entendendo o `git rm --cached`

Podemos dividir o comando:

```text
git rm --cached config.txt
│   │       │
│   │       └── arquivo que será removido do controle
│   └────────── remove
└────────────── comando do Git
```

### `rm`

Vem de *remove*, ou seja, remover.

### `--cached`

Indica que o arquivo deve ser removido do índice do Git, mas continuar no diretório de trabalho.

Assim:

```text
Git
 ↓
para de controlar o arquivo

Computador
 ↓
arquivo continua existindo
```

---

# 17. Exemplo completo

Imagine que você não quer mais versionar:

```text
config.txt
```

Primeiro, adicione ao `.gitignore`:

```text
config.txt
```

Depois, se o arquivo já estiver sendo rastreado:

```bash
git rm --cached config.txt
```

Verifique:

```bash
git status
```

Depois crie um *commit* registrando essa mudança:

```bash
git commit -m "Ignora arquivo de configuração"
```

O arquivo continuará no computador, mas deixará de ser controlado pelo Git.

---

# 18. Exemplos comuns de regras

Um `.gitignore` pode conter várias regras.

Por exemplo:

```text
*.log
*.tmp
cache/
*.bak
.env
```

Nesse exemplo:

| Regra    | O que ignora              |
| -------- | ------------------------- |
| `*.log`  | Arquivos `.log`           |
| `*.tmp`  | Arquivos `.tmp`           |
| `cache/` | Diretórios `cache`        |
| `*.bak`  | Arquivos de backup `.bak` |
| `.env`   | Arquivo `.env`            |

A regra ideal depende das necessidades de cada projeto.

---

# 19. Boas práticas

Ao criar um `.gitignore`:

* Coloque o arquivo na raiz do projeto quando ele tiver regras gerais.
* Ignore arquivos temporários e gerados automaticamente quando eles não fizerem parte do projeto.
* Evite colocar no repositório arquivos com configurações locais que não deveriam ser compartilhadas.
* Revise as regras do `.gitignore` antes de criar o primeiro *commit*.
* Utilize `git check-ignore -v` quando não entender por que um arquivo está sendo ignorado.
* Lembre-se de que o `.gitignore` não remove automaticamente arquivos que já estão sendo rastreados.

---

# Comandos vistos neste capítulo

| Comando                       | Função                                                          |
| ----------------------------- | --------------------------------------------------------------- |
| `touch .gitignore`            | Cria o arquivo `.gitignore`.                                    |
| `git status`                  | Mostra o estado do repositório.                                 |
| `git check-ignore -v arquivo` | Mostra qual regra está ignorando um arquivo.                    |
| `git rm --cached arquivo`     | Remove o arquivo do controle do Git sem apagá-lo do computador. |

---

# Resumo

O `.gitignore` é um arquivo utilizado para informar ao Git quais arquivos e diretórios devem ser ignorados.

Ele é muito útil para evitar que arquivos desnecessários façam parte do repositório.

Um exemplo simples:

```text
*.log
*.tmp
cache/
```

Também aprendemos que:

```bash
git check-ignore -v arquivo
```

ajuda a descobrir qual regra está ignorando determinado arquivo.

E, quando um arquivo já está sendo rastreado pelo Git, podemos utilizar:

```bash
git rm --cached arquivo
```

para removê-lo do controle de versão sem apagar o arquivo do computador.

---

# O que você aprendeu

Ao concluir este capítulo, você consegue:

* ✅ Entender o que é o `.gitignore`.
* ✅ Criar um arquivo `.gitignore`.
* ✅ Ignorar arquivos por extensão.
* ✅ Ignorar diretórios.
* ✅ Criar regras para subdiretórios.
* ✅ Testar se uma regra está funcionando.
* ✅ Descobrir qual regra está ignorando um arquivo.
* ✅ Entender a função do `git check-ignore -v`.
* ✅ Remover um arquivo do controle do Git usando `git rm --cached`.
* ✅ Entender por que o `.gitignore` não afeta automaticamente arquivos já rastreados.

---

# Próximo capítulo

## Capítulo 10 — Renomeando e Removendo Arquivos

No próximo capítulo, você aprenderá a trabalhar com arquivos que precisam ser renomeados ou removidos do projeto.

Serão apresentados os comandos:

```bash
git mv
git rm
```

Esses comandos permitem informar ao Git sobre essas alterações e ajudam a manter o histórico do projeto organizado.

---

# 📚 Fonte de estudo

Este resumo foi elaborado a partir dos estudos e da prática do autor sobre **Git e GitHub**, utilizando os conteúdos da disciplina e materiais de estudo como referência.

**Observação:** este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo original das disciplinas e materiais utilizados como referência não deve ser reproduzido ou disponibilizado integralmente neste repositório.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

