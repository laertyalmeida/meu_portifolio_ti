Links — Links

O que são Links?

No Linux, um Link (Link/Ligação) é uma forma de criar outro nome ou caminho para acessar um arquivo.

Existem dois tipos importantes:

Hard Link      → Link Físico
Symbolic Link  → Link Simbólico

---

Hard Link — Link Físico

Um Hard Link aponta para o mesmo inode do arquivo original.

Criamos com:

ln arquivo.txt copia.txt

Agora:

arquivo.txt ──┐
              ├── mesmo inode
copia.txt ────┘

Os dois nomes acessam os mesmos dados.

---

Inode — Inode

O inode guarda informações sobre o arquivo.

Podemos visualizar com:

ls -i arquivo.txt

"-i" — Inode (Inode)

Exemplo:

123456 arquivo.txt

Se fizermos:

ln arquivo.txt copia.txt

e depois:

ls -i arquivo.txt copia.txt

os dois terão o mesmo número de inode.

---

Symbolic Link — Link Simbólico

O Symbolic Link funciona como um atalho.

Criamos com:

ln -s arquivo.txt atalho.txt

"-s" — Symbolic (Simbólico)

Funcionamento:

atalho.txt
     ↓
arquivo.txt
     ↓
dados

---

Ver um Symbolic Link

Use:

ls -l

Podemos encontrar algo como:

atalho.txt -> arquivo.txt

A seta mostra para onde o link aponta.

---

Link Simbólico Quebrado

Se o arquivo original for removido:

rm arquivo.txt

o link continua existindo, mas não consegue mais acessar o arquivo.

atalho.txt
     ↓
arquivo.txt
     ✗

Isso é chamado de Broken Link (Link Quebrado).

---

Hard Link × Symbolic Link

| Hard Link| Symbolic Link
Comando| "ln"| "ln -s"
Aponta para| Mesmo inode| Caminho
Precisa do arquivo original?| Não necessariamente| Sim
Pode apontar para diretório?| Normalmente não| Sim
Pode atravessar sistemas de arquivos?| Não| Sim

---

Exemplo prático

Criar um Hard Link:

ln original.txt copia.txt

Criar um Symbolic Link:

ln -s original.txt atalho.txt

Ver os links:

ls -li

"-l" — Long Listing (Lista Detalhada)

"-i" — Inode (Mostrar Inode)

---

🧠 Para a LPIC-1

Memorize:

Hard Link
↓
mesmo inode

Symbolic Link
↓
aponta para um caminho

Comandos:

ln arquivo copia

→ Hard Link.

ln -s arquivo atalho

→ Symbolic Link.

---

Flags

-s → Symbolic → Simbólico
-i → Inode → Mostrar inode
-l → Long Listing → Lista detalhada

Regra simples

ln
↓
Link Físico

ln -s
↓
Link Simbólico
