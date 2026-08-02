**Tempo estimado:** 20 minutos

**Nível:** Iniciante

# Capítulo 10 — Fluxo de Trabalho com Branches

---

# Pré-requisitos

Antes de iniciar este capítulo é recomendado compreender todos os capítulos anteriores desta parte.

---

# Neste capítulo você aprenderá

* Como organizar o desenvolvimento utilizando Branches.
* Um fluxo de trabalho utilizado em projetos reais.
* A sequência lógica das operações com Branches.
* Boas práticas para manter o repositório organizado.

---

# Fluxo de trabalho com Branches

Uma Branch acompanha todo o ciclo de desenvolvimento de uma funcionalidade.

Na prática, o fluxo normalmente segue esta sequência:

```text
Criar Branch
      │
      ▼
Desenvolver
      │
      ▼
Realizar commits
      │
      ▼
Comparar alterações
      │
      ▼
Mesclar (Merge)
      │
      ▼
Excluir a Branch
```

Esse processo permite desenvolver novas funcionalidades sem alterar diretamente a Branch principal.

---

# Exemplo prático

Imagine que você precisa implementar uma tela de login.

### 1. Criar uma Branch

```bash
git switch -c feature/login
```

---

### 2. Desenvolver a funcionalidade

Edite os arquivos necessários.

---

### 3. Registrar as alterações

```bash
git add .
git commit -m "Adiciona tela de login"
```

---

### 4. Retornar para a Branch principal

```bash
git switch main
```

---

### 5. Integrar a funcionalidade

```bash
git merge feature/login
```

---

### 6. Remover a Branch

```bash
git branch -d feature/login
```

---

# Representação visual

Antes do Merge:

```text
main

A ─── B ─── C
             \
feature/login D ─── E
```

Após o Merge:

```text
main

A ─── B ─── C ─── D ─── E

feature/login
```

Após excluir a Branch:

```text
main

A ─── B ─── C ─── D ─── E
```

A funcionalidade permanece no histórico da `main`, mesmo após a remoção da Branch.

---

# Boas práticas

* Crie uma Branch para cada funcionalidade ou correção.
* Utilize nomes claros e padronizados.
* Faça commits pequenos e descritivos.
* Realize o merge somente após concluir e testar a funcionalidade.
* Exclua Branches que não serão mais utilizadas.

---

# O que aconteceu internamente?

Durante todo esse fluxo, o Git apenas movimenta referências para os commits.

Os commits permanecem armazenados no histórico do repositório.

A criação, a troca, a mesclagem e a exclusão de Branches não duplicam arquivos; elas apenas organizam diferentes linhas de desenvolvimento por meio de referências.

Esse é um dos motivos pelos quais o Git é rápido e eficiente, mesmo em projetos grandes.

---

# Resumo

Nesta parte você aprendeu como utilizar Branches para organizar o desenvolvimento de um projeto. Também conheceu o fluxo completo de trabalho: criar uma Branch, desenvolver uma funcionalidade, registrar commits, comparar alterações, realizar o merge e remover a Branch quando ela não for mais necessária.

Com esses conhecimentos, você já domina o fluxo básico de trabalho com Branches utilizado pela maioria das equipes de desenvolvimento.

---

# Próxima parte

## Parte 3 — GitHub

Na próxima parte você aprenderá a trabalhar com repositórios remotos utilizando o GitHub.

Entre os assuntos abordados estarão:

* O que é o GitHub.
* Criando uma conta.
* Criando repositórios remotos.
* `git remote`.
* `git push`.
* `git pull`.
* `git fetch`.
* `git clone`.
* Fluxo básico de colaboração.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

