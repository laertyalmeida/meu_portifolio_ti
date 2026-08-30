Revisão — Comandos GNU e Unix

Esta página reúne os pontos principais estudados neste livro.

---

1. Redirecionamento

>    → substituir saída
>>   → adicionar saída
<    → entrada
|    → Pipe (Canal)

Canais padrão:

0 → stdin  → entrada
1 → stdout → saída
2 → stderr → erro

---

2. Processamento de Texto

grep → procurar texto
sort → ordenar
uniq → remover repetições
cut  → extrair campos
tr   → transformar caracteres
sed  → modificar texto
awk  → trabalhar com campos

---

3. Compactação

gzip  → .gz
bzip2 → .bz2
xz    → .xz
zip   → .zip

"tar":

tar → agrupar arquivos

Exemplo:

tar -czf backup.tar.gz arquivos/

---

4. Ajuda

man       → manual
--help    → ajuda rápida
info      → documentação
apropos   → procurar assunto
whatis    → descrição curta

---

5. Histórico

history  → histórico
!!       → último comando
!n       → comando número n
Ctrl + R → procurar no histórico

---

6. Variáveis

HOME  → diretório pessoal
USER  → usuário
SHELL → shell
PATH  → caminhos dos programas

export NOME="Linux"

→ exporta uma variável.

unset NOME

→ remove uma variável.

---

7. Processos

ps    → processos
top   → processos em tempo real
kill  → enviar sinal
jobs  → tarefas
fg    → primeiro plano
bg    → segundo plano

---

8. Sinais

Os principais:

1  → SIGHUP  → Desconectar
2  → SIGINT  → Interromper
3  → SIGQUIT → Sair
9  → SIGKILL → Encerrar à força
15 → SIGTERM → Pedir encerramento
18 → SIGCONT → Continuar
19 → SIGSTOP → Parar

Regra importante:

SIGTERM → término normal
SIGKILL → término forçado

---

9. Prioridade

nice   → iniciar com prioridade diferente
renice → alterar prioridade

Valores:

-20 → maior prioridade
  0 → padrão
+19 → menor prioridade

---

10. Permissões

r → Read    → 4
w → Write   → 2
x → Execute → 1

Grupos:

u → User (Usuário)
g → Group (Grupo)
o → Others (Outros)
a → All (Todos)

"chmod":

chmod 755 arquivo

Resultado:

rwxr-xr-x

---

11. Proprietário e Grupo

chown → alterar proprietário
chgrp → alterar grupo
id    → informações do usuário
groups → grupos do usuário

Exemplo:

chown usuario:grupo arquivo

---

12. Links

ln     → Hard Link (Link Físico)
ln -s  → Symbolic Link (Link Simbólico)

Diferença:

Hard Link
→ mesmo inode

Symbolic Link
→ aponta para um caminho

---

13. Localização

find    → procurar diretamente
locate  → procurar na base de dados
updatedb → atualizar a base

Exemplo:

find /home -name "*.txt"

---

14. Arquivos Temporários

/tmp
→ temporários

/var/tmp
→ temporários mais persistentes

mktemp
→ criar arquivo temporário

umask
→ definir permissões retiradas na criação

---

🧠 O que você precisa dominar

Para a LPIC-1 Exam 101, não basta reconhecer os nomes. Você deve conseguir olhar um comando e entender o que ele fará.

Principalmente:

grep
find
tar
chmod
chown
ln
ps
kill
nice
renice

E entender:

Redirecionamento
Pipes
Permissões
Processos
Sinais
Expressões Regulares
Variáveis

---

Checklist

☐ Sei usar > e >>
☐ Sei usar |
☐ Sei procurar texto com grep
☐ Sei usar find
☐ Sei criar/extrair tar
☐ Entendo gzip, bzip2 e xz
☐ Sei consultar man
☐ Entendo PATH
☐ Entendo processos e PID
☐ Conheço os principais sinais
☐ Entendo nice e renice
☐ Sei interpretar 755
☐ Sei usar chmod
☐ Entendo chown e chgrp
☐ Sei diferenciar Hard Link e Symbolic Link
☐ Entendo /tmp e /var/tmp

Se esses pontos estiverem claros, podemos avançar para os exercícios e depois para o próximo livro. 
