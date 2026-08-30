Arquivos Temporários e Diretórios

"/tmp" — Temporary (Temporário)

O diretório "/tmp" é usado para armazenar arquivos temporários.

Exemplo:

ls /tmp

Programas podem criar arquivos temporários nesse diretório durante sua execução.

---

"/var/tmp" — Variable Temporary (Temporário Persistente)

Também guarda arquivos temporários, mas existe uma diferença importante:

/tmp
→ temporário
→ pode ser limpo durante a inicialização

/var/tmp
→ temporário
→ normalmente permanece após reinicialização

Para a prova, memorize essa diferença.

---

"mktemp" — Make Temporary (Criar Temporário)

Cria um arquivo temporário com um nome único.

mktemp

Exemplo de resultado:

/tmp/tmp.X7k92a

Também podemos criar um diretório temporário:

mktemp -d

"-d" — Directory (Diretório)

Cria um diretório temporário.

---

"tempfile" — Temporary File (Arquivo Temporário)

Em sistemas antigos, o comando "tempfile" pode aparecer, mas o mais importante atualmente é conhecer:

mktemp

---

"umask" — User File-Creation Mask (Máscara de Criação)

O "umask" define quais permissões serão retiradas dos novos arquivos e diretórios.

Veja o valor atual:

umask

Exemplo:

0022

Isso influencia as permissões padrão de novos arquivos e diretórios.

---

"mkdir" — Make Directory (Criar Diretório)

Cria um diretório.

mkdir projeto

"-p" — Parents (Diretórios Pais)

Cria também os diretórios necessários.

mkdir -p projeto/linux/comandos

Sem "-p", os diretórios pais precisam existir.

---

"rmdir" — Remove Directory (Remover Diretório)

Remove um diretório vazio.

rmdir projeto

Se houver arquivos dentro, o comando não remove o diretório.

---

"rm -r" — Remove Recursive (Remover Recursivamente)

Remove um diretório e seu conteúdo.

rm -r projeto

"-r" — Recursive (Recursivo)

Entra nos subdiretórios e remove o conteúdo.

⚠️ Cuidado com esse comando.

---

LPIC-1 — O que saber

- "/tmp" → arquivos temporários.
- "/var/tmp" → temporários que normalmente permanecem após reinicialização.
- "mktemp" → cria arquivo temporário único.
- "mktemp -d" → cria diretório temporário.
- "umask" → controla permissões retiradas dos novos arquivos.
- "mkdir" → cria diretório.
- "mkdir -p" → cria diretórios pais.
- "rmdir" → remove diretório vazio.
- "rm -r" → remove recursivamente.

Flags

-d → Directory (Diretório)
-p → Parents (Diretórios Pais)
-r → Recursive (Recursivo)

---

Resumo

/tmp
↓
temporário

/var/tmp
↓
temporário mais persistente

mktemp
↓
criar temporário

umask
↓
permissões padrão

mkdir
↓
criar diretório

rmdir
↓
remover diretório vazio
