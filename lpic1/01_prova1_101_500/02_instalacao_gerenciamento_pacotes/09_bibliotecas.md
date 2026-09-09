# Instalação e Gerenciamento de Pacotes

## 09 — Bibliotecas

### Library — Biblioteca

**Library — Biblioteca** é um conjunto de código pronto que fornece funções e recursos para outros programas.

Em vez de cada programa implementar tudo sozinho, ele pode utilizar bibliotecas existentes.

Exemplo:

    Programa
       ↓
    Biblioteca
       ↓
    Funções prontas
       ↓
    Sistema

---

## Shared Library — Biblioteca Compartilhada

**Shared Library — Biblioteca Compartilhada** é uma biblioteca que pode ser utilizada por vários programas.

No Linux, geralmente possui extensão:

    .so

**SO — Shared Object — Objeto Compartilhado**

Exemplos:

    libc.so
    libm.so

Uma biblioteca compartilhada normalmente é carregada em tempo de execução.

---

## Static Library — Biblioteca Estática

**Static Library — Biblioteca Estática** é incorporada ao programa durante a compilação.

Normalmente utiliza a extensão:

    .a

**Archive — Arquivo de Biblioteca**

Exemplo:

    libexemplo.a

Comparação:

| Tipo | Extensão | Característica |
|---|---|---|
| Shared Library | `.so` | Compartilhada em tempo de execução |
| Static Library | `.a` | Incorporada durante a compilação |

---

## Dynamic Linking — Ligação Dinâmica

**Dynamic Linking — Ligação Dinâmica** ocorre quando um programa utiliza uma biblioteca compartilhada durante sua execução.

Exemplo:

    programa
       ↓
    libc.so
       ↓
    funções da biblioteca

Isso evita que cada programa precise carregar uma cópia completa da mesma biblioteca.

---

## Dynamic Linker — Ligador Dinâmico

**Dynamic Linker — Ligador Dinâmico** é o componente responsável por localizar e carregar as bibliotecas compartilhadas necessárias para um programa.

Um componente importante é:

    ld.so

Também podemos encontrar arquivos relacionados ao carregamento dinâmico em diretórios como:

    /lib
    /usr/lib

- `/lib` — libraries — bibliotecas
- `/usr` — Unix System Resources — recursos do sistema
- `/usr/lib` — bibliotecas de programas do sistema

Em sistemas modernos, `/lib` pode ser um link simbólico para um diretório dentro de `/usr`.

---

## ldd — List Dynamic Dependencies

**ldd — List Dynamic Dependencies — Listar Dependências Dinâmicas**

Mostra as bibliotecas compartilhadas utilizadas por um programa.

Exemplo:

    ldd /bin/ls

Saída simplificada:

    libc.so.6 => /lib/.../libc.so.6

Isso mostra que o `ls` utiliza a biblioteca `libc`.

---

## ldconfig — Configuração do Linker Dinâmico

**ldconfig — Dynamic Linker Configuration — Configuração do Ligador Dinâmico**

Atualiza o cache utilizado pelo carregador de bibliotecas compartilhadas.

Executar:

    sudo ldconfig

Consultar bibliotecas conhecidas:

    ldconfig -p

- `-p` — print — exibir

---

## ld.so.conf

A configuração do carregador dinâmico pode envolver:

    /etc/ld.so.conf

- `/etc` — etcetera — configuração do sistema
- `ld.so.conf` — configuração dos caminhos das bibliotecas

Também podem existir arquivos adicionais em:

    /etc/ld.so.conf.d/

Esses arquivos permitem indicar diretórios onde existem bibliotecas compartilhadas.

---

## LD_LIBRARY_PATH

**LD_LIBRARY_PATH** é uma variável de ambiente que pode adicionar diretórios para busca de bibliotecas compartilhadas.

Exemplo:

    echo $LD_LIBRARY_PATH

Adicionar temporariamente um diretório:

    export LD_LIBRARY_PATH=/caminho/lib:$LD_LIBRARY_PATH

- `export` — exportar — tornar variável disponível para processos filhos

É uma configuração de ambiente, portanto deve ser utilizada com cuidado.

---

## Bibliotecas × Dependências

Uma biblioteca pode ser uma dependência de um programa.

Exemplo:

    programa
       ↓
    libc.so.6
       ↓
    biblioteca compartilhada

Por isso:

**Library — Biblioteca** = código reutilizável.

**Dependency — Dependência** = componente necessário para o funcionamento de outro componente.

Uma biblioteca pode ser uma dependência, mas nem toda dependência é necessariamente uma biblioteca.

---

## Localizar uma biblioteca

Podemos usar:

    ldconfig -p | grep libc

- `ldconfig -p` — mostrar bibliotecas conhecidas
- `grep` — localizar linhas que correspondem a um padrão
- `libc` — biblioteca padrão da linguagem C

Também podemos procurar arquivos:

    find /usr/lib -name "*.so*"

- `find` — localizar
- `-name` — nome
- `"*.so*"` — arquivos relacionados a bibliotecas compartilhadas

---

## Pacotes de Bibliotecas

As bibliotecas também podem ser distribuídas através de pacotes.

Exemplo:

    pacote
       ↓
    biblioteca .so
       ↓
    programa utiliza a biblioteca

No Debian:

    apt search libc

No sistema RPM:

    dnf search libc

---

## Resumo LPIC-1

- **Library — Biblioteca** = código reutilizável por programas.
- **Shared Library — Biblioteca Compartilhada** = biblioteca utilizada por vários programas.
- `.so` = **Shared Object — Objeto Compartilhado**.
- `.a` = biblioteca estática.
- **Dynamic Linking — Ligação Dinâmica** = uso de bibliotecas compartilhadas durante a execução.
- **Dynamic Linker — Ligador Dinâmico** = carrega bibliotecas necessárias.
- `ldd` = mostra bibliotecas compartilhadas usadas por um programa.
- `ldconfig` = atualiza o cache das bibliotecas.
- `ldconfig -p` = lista bibliotecas conhecidas pelo sistema.
- `/lib` e `/usr/lib` = diretórios relacionados a bibliotecas.
- `/etc/ld.so.conf` = configuração de caminhos de bibliotecas.
- `/etc/ld.so.conf.d/` = configurações adicionais.
- `LD_LIBRARY_PATH` = variável que pode adicionar caminhos de bibliotecas.
- **Biblioteca pode ser uma dependência de um programa.**

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
