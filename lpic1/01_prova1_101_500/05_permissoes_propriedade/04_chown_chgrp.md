# 04 — chown e chgrp

## chown — Change Owner (Alterar Dono)

O comando `chown` altera o **dono** e, opcionalmente, o **grupo** de um arquivo ou diretório.

    chown usuario arquivo

Exemplo:

    chown laerte arquivo.txt

O dono passa a ser `laerte`.

---

## 1. Alterar dono e grupo

    chown usuario:grupo arquivo

Exemplo:

    chown laerte:linux arquivo.txt

Resultado:

    Dono  → laerte
    Grupo → linux

Também é possível alterar somente o grupo usando:

    chown :linux arquivo.txt

---

## 2. Opção recursiva

`-R` — recursive (recursivo)

    chown -R laerte:linux documentos/

Altera o dono e o grupo do diretório e de seu conteúdo.

⚠️ Use `-R` com cuidado.

---

# chgrp — Change Group (Alterar Grupo)

O comando `chgrp` altera **somente o grupo** de um arquivo ou diretório.

    chgrp grupo arquivo

Exemplo:

    chgrp linux arquivo.txt

O grupo passa a ser `linux`.

---

## 3. Alteração recursiva com chgrp

    chgrp -R linux documentos/

`-R` — recursive (recursivo)

Altera o grupo do diretório e de todo o seu conteúdo.

---

## 4. Verificar dono e grupo

Use:

    ls -l arquivo.txt

Exemplo:

    -rw-r--r-- 1 laerte linux 120 arquivo.txt

Nesse exemplo:

    Dono  → laerte
    Grupo → linux

---

## 5. Diferença entre os comandos

| Comando | Função |
|---|---|
| `chown` | altera o dono |
| `chown usuario:grupo` | altera dono e grupo |
| `chgrp` | altera o grupo |

### Exemplos

    chown laerte arquivo.txt
    chown laerte:linux arquivo.txt
    chgrp linux arquivo.txt

---

## 6. LPIC-1 — O que lembrar

- `chown` = Change Owner (Alterar Dono).
- `chgrp` = Change Group (Alterar Grupo).
- `chown usuario arquivo` → altera o dono.
- `chown usuario:grupo arquivo` → altera dono e grupo.
- `chgrp grupo arquivo` → altera somente o grupo.
- `-R` = recursive (recursivo).
- `ls -l` permite verificar dono e grupo.

### Resumo

    chown usuario arquivo
    chown usuario:grupo arquivo
    chgrp grupo arquivo
    chown -R usuario:grupo diretorio/
    chgrp -R grupo diretorio/

> **"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
