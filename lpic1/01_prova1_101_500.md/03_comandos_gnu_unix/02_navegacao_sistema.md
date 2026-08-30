Navegação no Sistema

No Linux, usamos comandos para entrar em diretórios, descobrir onde estamos e listar seu conteúdo.

---

"pwd" — Print Working Directory (Mostrar Diretório Atual)

Mostra o caminho completo do diretório onde você está.

pwd

Exemplo:

/home/laerte

---

"ls" — List (Listar)

Mostra arquivos e diretórios.

ls

"-l" — Long (Detalhado)

Mostra informações adicionais.

ls -l

"-a" — All (Todos)

Mostra também arquivos ocultos.

ls -a

Podemos combinar as opções:

ls -la

---

"cd" — Change Directory (Mudar Diretório)

Entra em outro diretório.

cd /home

Voltar para o diretório anterior

cd ..

".." significa diretório pai, ou seja, o diretório que está um nível acima.

Ir para o diretório Home

cd ~

"~" representa o Home Directory (Diretório pessoal) do usuário.

---

Caminho absoluto e relativo

Absolute Path — Caminho Absoluto

Começa pela raiz "/".

cd /home/laerte

Relative Path — Caminho Relativo

Começa a partir do diretório atual.

cd documentos

---

Root — Raiz

A raiz do sistema de arquivos é:

/

Não confunda:

/     → Root Directory (Diretório raiz)

root  → usuário administrador

---

LPIC-1 — O que saber

- "pwd" mostra onde você está.
- "ls" lista arquivos e diretórios.
- "cd" muda de diretório.
- ".." representa o diretório pai.
- "~" representa o diretório Home do usuário.
- "/" é a raiz do sistema.
- "-l" mostra detalhes.
- "-a" mostra arquivos ocultos.
- Caminho absoluto começa com "/".

---

Resumo

pwd      → onde estou?
ls       → o que existe aqui?
cd       → para onde quero ir?

/        → raiz
..       → diretório pai
~        → Home

Principais opções

-l → Long (Detalhado)
-a → All (Todos)
