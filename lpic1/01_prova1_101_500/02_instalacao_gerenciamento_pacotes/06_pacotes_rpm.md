Pacotes RPM

RPM — RPM Package Manager (Gerenciador de Pacotes RPM)

RPM é o formato e também uma ferramenta usada por várias distribuições Linux.

O formato dos pacotes normalmente é:

.rpm

Distribuições que utilizam RPM incluem:

- Fedora
- RHEL
- Rocky Linux
- AlmaLinux
- openSUSE

---

"rpm"

O comando "rpm" trabalha diretamente com arquivos ".rpm".

Instalar

sudo rpm -i pacote.rpm

"-i" — Install (Instalar)

Instala o pacote.

---

Atualizar

sudo rpm -U pacote.rpm

"-U" — Upgrade (Atualizar)

Atualiza o pacote. Se ele ainda não estiver instalado, também pode instalá-lo.

---

Remover

sudo rpm -e nome-do-pacote

"-e" — Erase (Apagar)

Remove o pacote.

---

Verificar pacotes instalados

rpm -qa

"-q" — Query (Consultar)

Consulta informações sobre pacotes.

"-a" — All (Todos)

Consulta todos os pacotes instalados.

---

"dnf"

O DNF — Dandified YUM é um gerenciador de pacotes usado principalmente em distribuições modernas baseadas em RPM.

Ele consegue buscar pacotes nos repositórios e resolver dependências.

Instalar

sudo dnf install nome-do-pacote

Remover

sudo dnf remove nome-do-pacote

Atualizar

sudo dnf upgrade

Procurar pacote

dnf search palavra

---

RPM x DNF

.rpm
 ↓
rpm → trabalha diretamente com pacotes

Repositórios
 ↓
dnf → busca pacotes + resolve dependências

---

YUM

YUM — Yellowdog Updater, Modified é um antigo gerenciador de pacotes usado em sistemas baseados em RPM.

Em sistemas modernos, o DNF substituiu o YUM em muitas distribuições.

Você ainda pode encontrar "yum" em conteúdos e sistemas mais antigos.

---

LPIC-1 — O que saber

- Pacotes RPM usam o formato ".rpm".
- "rpm" trabalha diretamente com pacotes RPM.
- "dnf" trabalha com repositórios e dependências.
- "yum" é o gerenciador tradicional que antecedeu o DNF.
- "rpm -i" instala.
- "rpm -U" atualiza.
- "rpm -e" remove.
- "rpm -qa" lista os pacotes instalados.

---

Resumo

.deb → Debian / Ubuntu
.rpm → Fedora / RHEL

dpkg → pacote .deb
apt   → repositórios .deb

rpm → pacote .rpm
dnf → repositórios .rpm

Principais flags do "rpm"

-i → Install (Instalar)
-U → Upgrade (Atualizar)
-e → Erase (Apagar)
-q → Query (Consultar)
-a → All (Todos)
