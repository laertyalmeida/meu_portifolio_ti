# Comandos GNU/UNIX

## 01 — Terminal e Shell

### Terminal — Terminal

**Terminal** é o ambiente usado para interagir com o sistema por meio de comandos de texto.

Exemplo:

    usuário@linux:~$

Partes comuns:

    usuário@linux:~$
    │      │     │
    │      │     └── diretório atual
    │      └──────── nome do computador
    └─────────────── usuário

---

### Shell — Interpretador de Comandos

**Shell — Interpretador de Comandos** é o programa que recebe os comandos digitados e os interpreta para o sistema operacional.

O shell mais comum no Linux é:

**Bash — Bourne Again SHell — Shell Bourne Novamente**

Exemplo:

    echo "Olá"

O Bash interpreta o comando e executa:

    echo
      ↓
    "Olá"
      ↓
    texto exibido no terminal

---

## Terminal × Shell

Não são a mesma coisa.

**Terminal** = ambiente/interface onde você digita comandos.

**Shell** = programa que interpreta e executa esses comandos.

Exemplo:

    Terminal
       ↓
      Bash
       ↓
    Comando
       ↓
     Linux

---

## Prompt — Indicador de Comando

O **Prompt — Indicador de Comando** mostra que o shell está pronto para receber um comando.

Exemplo de usuário comum:

    laerte@linux:~$

Exemplo de usuário root:

    root@linux:~#

Geralmente:

- `$` — usuário comum
- `#` — root — superusuário

---

## Comandos básicos

### pwd — Print Working Directory — Mostrar Diretório de Trabalho

    pwd

Mostra o diretório atual.

Exemplo:

    /home/laerte

- `Print` — mostrar
- `Working Directory` — diretório de trabalho

---

### whoami — Who Am I — Quem Sou Eu

    whoami

Mostra o usuário atualmente efetivo.

Exemplo:

    laerte

---

### hostname — Host Name — Nome do Computador

    hostname

Mostra o nome do computador.

---

### date — Date — Data

    date

Mostra a data e a hora atuais.

---

### echo — Echo — Exibir

    echo "Olá Linux"

Exibe o texto informado.

---

### clear — Clear — Limpar

    clear

Limpa o conteúdo visível do terminal.

---

### exit — Exit — Sair

    exit

Encerra a sessão do shell atual.

---

## Executando comandos

Um comando normalmente possui esta estrutura:

    comando opção argumento

Exemplo:

    ls -l /home

- `ls` — List — listar
- `-l` — long — formato detalhado
- `/home` — diretório pessoal dos usuários

Outro exemplo:

    cat /etc/hostname

- `cat` — Concatenate — concatenar/exibir
- `/etc` — configuração do sistema
- `hostname` — nome do computador

---

## Command — Comando

Um comando pode ser:

- **Builtin — Comando interno**: faz parte do próprio shell.
- **External Command — Comando externo**: programa separado executado pelo shell.

Exemplo:

    type cd

O `cd` normalmente é um comando interno do Bash.

    type ls

O `ls` normalmente é um programa externo.

---

## PATH — Caminho de Busca

**PATH — Path — Caminho** é uma variável que informa ao shell onde procurar comandos executáveis.

Ver o PATH:

    echo $PATH

Exemplo:

    /usr/local/bin:/usr/bin:/bin

- `/usr` — recursos do sistema
- `/bin` — programas/comandos essenciais
- `/usr/bin` — programas executáveis do sistema
- `/usr/local/bin` — programas instalados localmente

Quando você executa:

    ls

o shell procura o programa `ls` nos diretórios definidos no `PATH`.

---

## Command History — Histórico de Comandos

O shell mantém um histórico dos comandos utilizados.

Ver histórico:

    history

Executar novamente o último comando:

    !!

Usar o comando anterior com a seta:

    ↑

O histórico facilita a repetição e correção de comandos.

---

## Teclas importantes

| Tecla | Função |
|---|---|
| `↑` | comando anterior |
| `↓` | próximo comando do histórico |
| `Tab` | autocompletar |
| `Ctrl+C` | interromper comando |
| `Ctrl+D` | finalizar entrada/encerrar shell |
| `Ctrl+L` | limpar a tela |
| `Ctrl+Z` | suspender processo |

---

## Resumo LPIC-1

- **Terminal** = ambiente/interface para digitar comandos.
- **Shell** = interpretador de comandos.
- **Bash — Bourne Again SHell** = shell muito utilizado no Linux.
- **Prompt** = indicador de que o shell está pronto.
- `$` = normalmente usuário comum.
- `#` = normalmente root.
- `pwd` = mostrar diretório atual.
- `whoami` = mostrar usuário atual.
- `hostname` = mostrar nome do computador.
- `date` = mostrar data e hora.
- `echo` = exibir texto.
- `clear` = limpar terminal.
- `exit` = sair do shell.
- `type` = identificar se um comando é interno ou externo.
- `PATH` = caminhos onde o shell procura comandos.
- `history` = mostrar histórico.
- `Tab` = autocompletar.
- `Ctrl+C` = interromper comando.
- `Ctrl+Z` = suspender processo.

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
