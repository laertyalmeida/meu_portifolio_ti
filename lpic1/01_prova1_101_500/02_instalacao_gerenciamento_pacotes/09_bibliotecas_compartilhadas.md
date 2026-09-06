Bibliotecas Compartilhadas

Library — Biblioteca

Uma Library (Biblioteca) é um conjunto de código pronto que pode ser usado por programas.

Em vez de cada programa criar tudo sozinho, ele pode usar uma biblioteca existente.

Programa
   ↓
Biblioteca
   ↓
Função necessária

---

Shared Library — Biblioteca Compartilhada

Uma Shared Library (Biblioteca Compartilhada) pode ser usada por vários programas.

No Linux, arquivos desse tipo normalmente terminam com:

.so

".so" — Shared Object (Objeto Compartilhado)

Exemplo:

libc.so.6

A biblioteca pode ficar carregada na memória e ser utilizada por vários programas.

---

Por que usar bibliotecas compartilhadas?

Elas evitam que cada programa precise carregar sua própria cópia do mesmo código.

Isso pode:

- Economizar espaço.
- Facilitar atualizações.
- Permitir que vários programas usem o mesmo código.

---

Como saber quais bibliotecas um programa usa?

"ldd" — List Dynamic Dependencies (Listar Dependências Dinâmicas)

Mostra as bibliotecas compartilhadas necessárias para um programa.

Exemplo:

ldd /bin/ls

O resultado mostra bibliotecas utilizadas pelo "ls".

---

"ldconfig" — Dynamic Linker Configuration (Configuração do Linker Dinâmico)

Ajuda o Linux a encontrar bibliotecas compartilhadas.

sudo ldconfig

Ele atualiza o cache de bibliotecas compartilhadas.

---

"/etc/ld.so.conf"

Arquivo usado para configurar caminhos onde o sistema deve procurar bibliotecas.

Também podem existir arquivos adicionais em:

/etc/ld.so.conf.d/

---

"LD_LIBRARY_PATH"

É uma variável de ambiente que pode indicar diretórios adicionais onde o sistema deve procurar bibliotecas.

Exemplo:

echo $LD_LIBRARY_PATH

---

LPIC-1 — O que saber

- Library = biblioteca de código usada por programas.
- Shared Library = biblioteca compartilhada entre programas.
- Arquivos compartilhados normalmente terminam em ".so".
- "ldd" mostra as bibliotecas usadas por um programa.
- "ldconfig" atualiza o cache de bibliotecas.
- "/etc/ld.so.conf" configura caminhos de bibliotecas.
- "/etc/ld.so.conf.d/" contém configurações adicionais.
- "LD_LIBRARY_PATH" pode adicionar caminhos para busca de bibliotecas.

---

Resumo

Programa
   ↓
Shared Library
   ↓
.so

ldd       → mostra bibliotecas
ldconfig  → atualiza o cache
LD_LIBRARY_PATH → caminhos adicionais

Termos importantes:

Library       → Biblioteca
Shared Library → Biblioteca Compartilhada
Shared Object → Objeto Compartilhado
