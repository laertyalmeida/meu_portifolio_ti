Manipulação de Arquivos

No Linux, usamos alguns comandos básicos para criar, copiar, mover, renomear e apagar arquivos e diretórios.

---

"touch" — Touch (Criar/Atualizar)

Cria um arquivo vazio se ele ainda não existir.

touch arquivo.txt

Se o arquivo já existir, atualiza sua data de modificação.

---

"mkdir" — Make Directory (Criar Diretório)

Cria um diretório.

mkdir documentos

"-p" — Parents (Pais)

Cria também os diretórios necessários no caminho.

mkdir -p projetos/linux/lpic

Sem "-p", os diretórios anteriores precisam existir.

---

"cp" — Copy (Copiar)

Copia arquivos ou diretórios.

cp arquivo.txt backup.txt

"-r" — Recursive (Recursivo)

Usado para copiar diretórios e todo o seu conteúdo.

cp -r documentos backup

---

"mv" — Move (Mover)

Move ou renomeia arquivos e diretórios.

Mover:

mv arquivo.txt documentos/

Renomear:

mv antigo.txt novo.txt

---

"rm" — Remove (Remover)

Remove arquivos.

rm arquivo.txt

"-r" — Recursive (Recursivo)

Remove diretórios e seu conteúdo.

rm -r documentos

"-f" — Force (Forçar)

Não pede confirmação e ignora arquivos inexistentes.

rm -f arquivo.txt

Cuidado: "rm" pode apagar arquivos definitivamente.

---

"rmdir" — Remove Directory (Remover Diretório)

Remove um diretório vazio.

rmdir documentos

Se houver arquivos dentro, o comando não remove o diretório.

---

Exemplo prático

mkdir projeto
cd projeto
touch arquivo.txt
cp arquivo.txt copia.txt
mv copia.txt backup.txt
ls
rm backup.txt

Resultado final:

projeto/
└── arquivo.txt

---

LPIC-1 — O que saber

- "touch" cria arquivos vazios.
- "mkdir" cria diretórios.
- "cp" copia.
- "mv" move ou renomeia.
- "rm" remove.
- "rmdir" remove diretórios vazios.
- "-r" significa Recursive (Recursivo).
- "-f" significa Force (Forçar).
- "-p" significa Parents (Diretórios pais).

---

Resumo

touch   → criar arquivo
mkdir   → criar diretório
cp      → copiar
mv      → mover / renomear
rm      → remover
rmdir   → remover diretório vazio

Principais opções

-p → Parents (Pais)
-r → Recursive (Recursivo)
-f → Force (Forçar)
