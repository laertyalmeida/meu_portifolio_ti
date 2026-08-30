Permissões Básicas

Permission — Permissão

No Linux, cada arquivo e diretório possui permissões que controlam quem pode ler, modificar ou executar.

As três permissões básicas são:

r → Read (Ler)
w → Write (Escrever)
x → Execute (Executar)

---

"r" — Read (Ler)

Permite visualizar o conteúdo de um arquivo.

r

Para um diretório, permite consultar os nomes dos arquivos existentes.

---

"w" — Write (Escrever)

Permite modificar um arquivo.

Em um diretório, permite criar, apagar ou renomear arquivos, dependendo das outras permissões.

w

---

"x" — Execute (Executar)

Em um arquivo, permite executá-lo como programa ou script.

Em um diretório, permite entrar/acessar o diretório.

x

---

"ls -l"

Podemos visualizar as permissões com:

ls -l

Exemplo:

-rwxr-xr--

Vamos separar:

- rwx r-x r--
│ │   │   │
│ │   │   └── outros
│ │   └────── grupo
│ └────────── proprietário
└──────────── tipo

---

Owner — Proprietário

Primeiro grupo:

rwx

São as permissões do Owner (Proprietário).

---

Group — Grupo

Segundo grupo:

r-x

São as permissões do Group (Grupo).

---

Others — Outros

Terceiro grupo:

r--

São as permissões dos Others (Outros usuários).

---

Os três grupos

Sempre pense:

Owner  → proprietário
Group  → grupo
Others → outros

E para cada um:

r → ler
w → escrever
x → executar

---

Permissões numéricas

As permissões também podem ser representadas por números:

r = 4
w = 2
x = 1

Somamos os valores.

Exemplo

rwx

4 + 2 + 1 = 7

Então:

rwx = 7
r-x = 5
r-- = 4

---

Exemplo "755"

755

Significa:

7 → rwx → proprietário
5 → r-x → grupo
5 → r-x → outros

Portanto:

rwxr-xr-x

---

"chmod" — Change Mode (Alterar Permissões)

Usado para alterar permissões.

chmod 755 arquivo.sh

Resultado:

rwxr-xr-x

---

LPIC-1 — O que saber

- "r" = Read (Ler) = 4
- "w" = Write (Escrever) = 2
- "x" = Execute (Executar) = 1
- As permissões são divididas entre:
  - Owner
  - Group
  - Others
- "ls -l" mostra permissões.
- "chmod" altera permissões.
- "755" = "rwxr-xr-x".

---

Resumo

r → Read    → 4
w → Write   → 2
x → Execute → 1

Owner  → proprietário
Group  → grupo
Others → outros

755
 ↓
rwx r-x r-x
 ↓   ↓   ↓
 O   G   O

Regra para memorizar:

4 + 2 + 1
r   w   x
