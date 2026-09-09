# Instalação e Gerenciamento de Pacotes

## 08 — Dependências

### Dependency — Dependência

**Dependency — Dependência** é um pacote, biblioteca ou componente que outro programa precisa para funcionar corretamente.

Exemplo:

    Programa A
        ↓
    precisa da Biblioteca B
        ↓
    Biblioteca B
        ↓
    precisa da Biblioteca C

Sem as dependências necessárias, o programa pode não funcionar.

---

## Library — Biblioteca

**Library — Biblioteca** é um conjunto de funções e recursos que podem ser utilizados por programas.

Exemplo:

    Programa
       ↓
    Biblioteca
       ↓
    Funções do sistema

No Linux, muitas bibliotecas são compartilhadas entre vários programas.

---

## Shared Library — Biblioteca Compartilhada

Uma biblioteca compartilhada normalmente possui extensão:

    .so

**SO — Shared Object — Objeto Compartilhado**

Exemplo:

    lib exemplo.so

Podemos procurar bibliotecas utilizadas por um programa com:

    ldd programa

- `ldd` — List Dynamic Dependencies — listar dependências dinâmicas

---

## Dependency Resolution — Resolução de Dependências

**Dependency Resolution — Resolução de Dependências** é o processo de localizar e instalar os pacotes necessários para que um programa funcione.

Com um gerenciador de pacotes:

    Programa
       ↓
    Gerenciador
       ↓
    Dependência A
    Dependência B
    Dependência C
       ↓
    Instalação

O **APT** e o **DNF** conseguem resolver dependências automaticamente usando seus repositórios.

---

## Debian — APT

Para instalar um programa:

    sudo apt install programa

O APT verifica as dependências necessárias e pode instalá-las automaticamente.

Consultar dependências:

    apt depends programa

- `depends` — dependências

---

## dpkg

O `dpkg` trabalha diretamente com pacotes `.deb`.

Exemplo:

    sudo dpkg -i programa.deb

Se o pacote possuir dependências ausentes, o `dpkg` pode informar que elas precisam ser instaladas.

Depois, o APT pode ajudar a corrigir as dependências:

    sudo apt install -f

- `-f` — fix-broken — corrigir pacotes quebrados/dependências

---

## RPM — Red Hat

O `rpm` também trabalha diretamente com pacotes.

Exemplo:

    sudo rpm -i programa.rpm

Se existirem dependências ausentes, o `rpm` pode informar quais são necessárias.

Para utilizar os repositórios e resolver dependências:

    sudo dnf install programa.rpm

O DNF pode localizar as dependências necessárias nos repositórios configurados.

---

## Dependency Tree — Árvore de Dependências

Podemos imaginar as dependências como uma árvore:

    programa
       ├── biblioteca A
       │      └── biblioteca C
       │
       └── biblioteca B
              └── biblioteca C

A mesma dependência pode ser utilizada por vários programas.

---

## Broken Dependencies — Dependências Quebradas

**Broken Dependencies — Dependências Quebradas** acontecem quando um pacote depende de algo que está ausente, incompatível ou em estado incorreto.

No Debian, podemos verificar problemas com:

    sudo apt install -f

Também é possível consultar:

    sudo apt check

- `check` — verificar

---

## Dependência Direta × Indireta

### Direct Dependency — Dependência Direta

O programa depende diretamente de outro pacote.

    Programa A
        ↓
    Biblioteca B

### Indirect Dependency — Dependência Indireta

O programa depende de B, e B depende de C.

    Programa A
        ↓
    Biblioteca B
        ↓
    Biblioteca C

---

## Comandos importantes

| Comando | Tradução | Função |
|---|---|---|
| `apt depends` | dependências | Mostrar dependências de um pacote |
| `apt install` | instalar | Instalar pacote e dependências |
| `apt install -f` | corrigir | Corrigir dependências/pacotes quebrados |
| `apt check` | verificar | Verificar problemas de dependências |
| `ldd` | listar dependências dinâmicas | Mostrar bibliotecas usadas por um programa |
| `dnf install` | instalar | Instalar pacote e resolver dependências |

---

## Resumo LPIC-1

- **Dependency — Dependência** = componente necessário para um programa funcionar.
- **Library — Biblioteca** = conjunto de funções utilizadas por programas.
- `.so` = **Shared Object — Objeto Compartilhado**.
- `ldd` = mostra dependências dinâmicas de um programa.
- `apt depends` = mostra dependências de um pacote.
- `apt install` = instala pacote e suas dependências.
- `apt install -f` = tenta corrigir dependências/pacotes quebrados.
- `apt check` = verifica problemas no sistema de pacotes.
- `rpm` = trabalha diretamente com pacotes `.rpm`.
- `dpkg` = trabalha diretamente com pacotes `.deb`.
- **APT e DNF** são ferramentas de alto nível que resolvem dependências usando repositórios.
- **Direct Dependency — Dependência Direta** = necessária diretamente pelo programa.
- **Indirect Dependency — Dependência Indireta** = dependência de outra dependência.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
