Visualização de Arquivos

No Linux, existem vários comandos para ler o conteúdo de arquivos sem precisar abrir um editor.

---

"cat" — Concatenate (Concatenar)

Mostra o conteúdo de um arquivo.

cat arquivo.txt

Também pode juntar o conteúdo de vários arquivos:

cat arquivo1.txt arquivo2.txt

---

"less" — Less (Menos)

Permite visualizar um arquivo página por página.

less arquivo.txt

É útil para arquivos grandes.

Dentro do "less":

Space → próxima página
b     → página anterior
q     → sair

---

"more" — More (Mais)

Também permite visualizar arquivos uma página por vez.

more arquivo.txt

É mais simples que "less".

---

"head" — Head (Início)

Mostra as primeiras linhas de um arquivo.

head arquivo.txt

Por padrão, mostra 10 linhas.

"-n" — Number (Número)

Define quantas linhas serão mostradas.

head -n 5 arquivo.txt

→ Mostra as primeiras 5 linhas.

---

"tail" — Tail (Final)

Mostra as últimas linhas de um arquivo.

tail arquivo.txt

Por padrão, mostra 10 linhas.

"-n" — Number (Número)

Define quantas linhas serão mostradas.

tail -n 5 arquivo.txt

→ Mostra as últimas 5 linhas.

---

"tail -f"

"-f" — Follow (Acompanhar)

Continua mostrando novas linhas adicionadas ao arquivo.

tail -f /var/log/syslog

Isso é muito útil para acompanhar logs em tempo real.

Para sair:

Ctrl + C

---

"wc" — Word Count (Contagem de Palavras)

Conta informações sobre um arquivo.

wc arquivo.txt

Pode mostrar:

linhas  palavras  bytes

"-l" — Lines (Linhas)

Conta apenas as linhas.

wc -l arquivo.txt

"-w" — Words (Palavras)

Conta apenas as palavras.

wc -w arquivo.txt

"-c" — Bytes (Bytes)

Conta os bytes.

wc -c arquivo.txt

---

LPIC-1 — O que saber

- "cat" mostra o conteúdo.
- "less" permite navegar pelo arquivo.
- "more" mostra o arquivo por páginas.
- "head" mostra o início.
- "tail" mostra o final.
- "tail -f" acompanha novas linhas.
- "wc" conta informações do arquivo.
- "-n" = Number (Número).
- "-f" = Follow (Acompanhar).
- "-l" = Lines (Linhas).
- "-w" = Words (Palavras).
- "-c" = Bytes (Bytes).

---

Resumo

cat       → conteúdo
less      → visualizar página por página
more      → visualizar por páginas
head      → início
tail      → final
tail -f   → acompanhar em tempo real
wc        → contar

Principais opções

-n → Number (Número)
-f → Follow (Acompanhar)
-l → Lines (Linhas)
-w → Words (Palavras)
-c → Bytes
