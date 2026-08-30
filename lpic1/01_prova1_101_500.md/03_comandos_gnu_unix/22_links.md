Links

Link — Ligação

No Linux, um Link (Link/Ligação) permite criar uma referência para um arquivo.

Existem dois tipos principais:

Hard Link  → Link Físico
Symbolic Link → Link Simbólico

---

Hard Link — Link Físico

Um Hard Link (Link Físico) aponta para os mesmos dados do arquivo original.

Criamos com:

ln arquivo.txt copia.txt

Agora:

arquivo.txt
     ↕
mesmos dados
     ↕
copia.txt

Os dois nomes apontam para o mesmo conteúdo.

Se alterar um, o outro também verá a alteração.

---

Inode — Inode (Índice do Arquivo)

Cada arquivo possui um inode, que guarda informações sobre o arquivo.

Podemos visualizar o inode com:

ls -i arquivo.txt

Exemplo:

123456 arquivo.txt

O número:

123456

é o inode.

Um Hard Link possui o mesmo inode do arquivo original.

---

Symbolic Link — Link Simbólico

Um Symbolic Link (Link Simbólico) funciona como um atalho.

Criamos com:

ln -s arquivo.txt atalho.txt

"-s" — Symbolic (Simbólico)

Agora:

atalho.txt
     ↓
arquivo.txt

O link aponta para o caminho do arquivo original.

---

Ver um link

Use:

ls -l

Um link simbólico aparece parecido com:

atalho.txt -> arquivo.txt

A seta:

->

mostra para onde o link aponta.

---

Diferença importante

Hard Link

arquivo.txt ──┐
               ├── mesmos dados
copia.txt ─────┘

Os dois nomes apontam para o mesmo inode.

Symbolic Link

atalho.txt
     ↓
arquivo.txt
     ↓
dados

O link aponta para o caminho do arquivo.

---

Link simbólico quebrado

Se o arquivo original for removido:

rm arquivo.txt

o link simbólico pode ficar quebrado:

atalho.txt -> arquivo.txt
                         ✗

O arquivo apontado não existe mais.

---

"ln" — Link (Criar Link)

Comando usado para criar links.

Link físico

ln original.txt copia.txt

Link simbólico

ln -s original.txt atalho.txt

---

LPIC-1 — O que saber

- "ln" cria links.
- Hard Link aponta para o mesmo inode.
- Symbolic Link aponta para um caminho.
- "-s" = Symbolic (Simbólico).
- "ls -i" mostra o inode.
- "ls -l" ajuda a identificar links simbólicos.
- Um link simbólico pode ficar quebrado quando o arquivo original desaparece.

---

Resumo

Hard Link
↓
mesmo inode

Symbolic Link
↓
aponta para um caminho

ln arquivo.txt copia.txt

→ Hard Link.

ln -s arquivo.txt atalho.txt

→ Symbolic Link.

Para memorizar

ln     → Hard Link
ln -s  → Symbolic Link
