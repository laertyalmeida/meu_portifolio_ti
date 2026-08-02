**Tempo estimado:** 15 minutos

**Nível:** Iniciante

# Capítulo 01 — O que é o GitHub?

---

# Pré-requisitos

Antes de iniciar este capítulo é recomendado compreender os conceitos estudados nas Partes 1 e 2, especialmente repositórios, commits e Branches.

---

# Neste capítulo você aprenderá

* O que é o GitHub.
* A diferença entre Git e GitHub.
* O conceito de repositório remoto.
* Como Git e GitHub trabalham juntos.

---

# O que é o GitHub?

O **GitHub** é uma plataforma que hospeda repositórios Git na internet.

Enquanto o **Git** é o sistema de controle de versão instalado no computador, o **GitHub** oferece um local para armazenar, compartilhar e colaborar em projetos utilizando o Git.

Isso permite que desenvolvedores trabalhem no mesmo projeto, mesmo estando em locais diferentes.

---

# Git x GitHub

Embora os nomes sejam parecidos, eles possuem funções diferentes.

| Git                                     | GitHub                                        |
| --------------------------------------- | --------------------------------------------- |
| Sistema de controle de versão.          | Plataforma de hospedagem de repositórios Git. |
| Funciona localmente no computador.      | Funciona na internet.                         |
| Gerencia commits, Branches e histórico. | Armazena e compartilha repositórios.          |
| Pode ser utilizado sem internet.        | Requer conexão para sincronização.            |

Em outras palavras:

* **Git** controla o histórico do projeto.
* **GitHub** armazena esse histórico em um servidor remoto.

---

# Representação visual

```text
                 GitHub
          (Repositório Remoto)
                  ▲
                  │
        Internet  │
                  │
                  ▼
      Computador do Desenvolvedor
         (Repositório Local)
                Git
```

O Git realiza o controle de versão localmente.

O GitHub recebe uma cópia desse repositório para armazenamento e compartilhamento.

---

# Glossário

| Termo             | Tradução           | Significado                                  |
| ----------------- | ------------------ | -------------------------------------------- |
| GitHub            | —                  | Plataforma de hospedagem de repositórios Git |
| Remote Repository | Repositório Remoto | Repositório armazenado em um servidor        |
| Local Repository  | Repositório Local  | Repositório armazenado no computador         |
| Repository        | Repositório        | Projeto controlado pelo Git                  |

---

# Como Git e GitHub trabalham juntos?

Durante o desenvolvimento, você realiza todas as alterações utilizando o Git no seu computador.

Quando desejar compartilhar essas alterações ou criar um backup remoto, utiliza comandos do Git para enviar os commits ao GitHub.

O fluxo básico é:

```text
Criar arquivos
       │
       ▼
Editar arquivos
       │
       ▼
git add
       │
       ▼
git commit
       │
       ▼
Git (Repositório Local)
       │
       ▼
GitHub (Repositório Remoto)
```

Nos próximos capítulos você aprenderá como realizar essa sincronização.

---

# O que aconteceu internamente?

Quando um projeto é enviado ao GitHub, o histórico criado localmente permanece intacto.

O Git apenas copia os commits para o repositório remoto.

Isso significa que o GitHub não substitui o Git: ele apenas armazena uma cópia do repositório e permite que outros desenvolvedores acessem esse histórico.

---

# Resumo

Neste capítulo você aprendeu que Git e GitHub são tecnologias diferentes, mas complementares. O Git é responsável pelo controle de versão local, enquanto o GitHub hospeda repositórios remotos para armazenamento, compartilhamento e colaboração.

Com esse conceito em mente, você está preparado para começar a trabalhar com repositórios remotos.

---

# Próximo capítulo

## Capítulo 02 — Criando uma Conta no GitHub

No próximo capítulo você aprenderá como criar uma conta no GitHub, configurar seu perfil e dar os primeiros passos na plataforma que será utilizada durante todo o restante deste curso.

---

> **"Conhecimento só tem valor quando é compartilhado."**
>
> **— Laerte Costa**

