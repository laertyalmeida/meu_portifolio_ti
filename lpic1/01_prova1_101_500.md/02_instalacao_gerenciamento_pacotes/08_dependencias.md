Dependências

Dependency — Dependência

Uma Dependency (Dependência) é outro pacote ou biblioteca que um programa precisa para funcionar.

Imagine que você queira instalar um programa:

Programa A
   ↓
precisa de
   ↓
Biblioteca B

Sem a Biblioteca B, o Programa A pode não funcionar.

---

Exemplo

Imagine:

Editor de texto
    ↓
Biblioteca gráfica
    ↓
Outra biblioteca

O gerenciador de pacotes identifica essas necessidades e instala o que for necessário.

---

APT e dependências

O APT resolve dependências automaticamente.

sudo apt install nome-do-pacote

O APT verifica o que o pacote precisa e pode instalar os pacotes necessários.

---

DNF e dependências

O DNF também resolve dependências automaticamente.

sudo dnf install nome-do-pacote

---

"dpkg" e dependências

O "dpkg" trabalha diretamente com o pacote ".deb", mas não resolve automaticamente todas as dependências como o APT.

Por isso, em sistemas Debian, normalmente usamos:

apt
 ↓
dpkg

O APT cuida das dependências e utiliza o "dpkg" para trabalhar com os pacotes.

---

Dependency Conflict — Conflito de Dependências

Pode acontecer de dois pacotes exigirem versões incompatíveis de uma mesma biblioteca.

Programa A → Biblioteca X versão 1
Programa B → Biblioteca X versão 2

O gerenciador de pacotes tenta encontrar uma solução.

---

LPIC-1 — O que saber

- Dependência é algo que um programa precisa para funcionar.
- Pode ser outro pacote ou uma biblioteca.
- "apt" resolve dependências automaticamente.
- "dnf" resolve dependências automaticamente.
- "dpkg" trabalha diretamente com ".deb" e não é um gerenciador completo de dependências.
- Dependências podem causar conflitos entre pacotes.

---

Resumo

Programa
   ↓
Depende de
   ↓
Pacote / Biblioteca

apt → resolve dependências
dnf → resolve dependências
dpkg → trabalha diretamente com .deb
