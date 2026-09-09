# 01 — Arquitetura do Sistema

## 07 — Módulos do Kernel

### Kernel Module — Módulo do Kernel

**Kernel — Núcleo** é a parte central do Linux responsável por controlar os recursos do sistema e permitir a comunicação entre software e hardware.

**Kernel Module — Módulo do Kernel** é um componente que pode ser carregado no kernel quando necessário, sem precisar recompilar ou reiniciar o sistema.

Os módulos são muito utilizados para fornecer suporte a:

- Dispositivos de hardware
- Sistemas de arquivos
- Drivers
- Recursos específicos do kernel

---

### Driver — Controlador

**Driver — Controlador** é um software que permite ao sistema operacional trabalhar com determinado hardware.

Muitos drivers Linux são implementados como módulos do kernel.

Exemplos:

- Placa de rede
- Placa de vídeo
- Dispositivo USB
- Controladora de armazenamento

---

### Diretório dos módulos

Os módulos instalados ficam normalmente em:

    /lib/modules/$(uname -r)

**`/lib` — libraries — bibliotecas**

**`/modules` — módulos**

**`uname -r` — kernel release — versão/liberação do kernel**

O diretório é específico para cada versão do kernel.

Exemplo:

    /lib/modules/6.x.x/

---

### lsmod — List Modules — Listar Módulos

    lsmod

Mostra os módulos atualmente carregados no kernel.

Exemplo de informações:

- Module — módulo
- Size — tamanho
- Used by — utilizado por

---

### modprobe — Module Probe — Localizar/Carregar Módulo

    sudo modprobe nome_do_modulo

Carrega um módulo no kernel e também pode carregar automaticamente suas dependências.

Para remover:

    sudo modprobe -r nome_do_modulo

`-r` — **remove — remover**

---

### insmod — Insert Module — Inserir Módulo

    sudo insmod modulo.ko

Carrega diretamente um módulo no kernel.

O arquivo normalmente possui a extensão:

    .ko

**`.ko` — Kernel Object — Objeto do Kernel**

---

### rmmod — Remove Module — Remover Módulo

    sudo rmmod nome_do_modulo

Remove um módulo carregado.

O módulo não pode estar em uso.

---

### modinfo — Module Information — Informações do Módulo

    modinfo nome_do_modulo

Mostra informações sobre um módulo.

Pode exibir:

- Descrição
- Autor
- Licença
- Versão
- Aliases
- Parâmetros
- Dependências

---

### Verificar módulos carregados

    lsmod

Também é possível consultar:

    cat /proc/modules

**`/proc` — Process Information — Informações de Processos**

**`/proc/modules` — módulos carregados**

---

### Dependências

Um módulo pode depender de outros módulos.

O `modprobe` consegue resolver e carregar essas dependências automaticamente.

    sudo modprobe nome_do_modulo

Por isso, normalmente é preferível utilizar `modprobe` em vez de `insmod` para carregar módulos.

---

### Configuração de módulos

Configurações relacionadas aos módulos podem ser encontradas em:

    /etc/modprobe.d/

**`/etc` — etcetera/configuração do sistema**

**`modprobe.d` — configurações do modprobe**

Esses arquivos podem definir opções, aliases e regras relacionadas aos módulos.

---

## Resumo LPIC-1

- **Kernel — Núcleo** → parte central do sistema Linux.
- **Kernel Module — Módulo do Kernel** → componente carregável pelo kernel.
- **Driver — Controlador** → permite ao sistema operacional utilizar determinado hardware.
- `/lib` → **libraries — bibliotecas**.
- `/lib/modules/` → módulos instalados para as versões do kernel.
- `lsmod` → **List Modules — Listar Módulos** carregados.
- `modprobe` → **Module Probe — Localizar/Carregar Módulo**.
- `modprobe -r` → **remove — remover** módulo.
- `insmod` → **Insert Module — Inserir Módulo**.
- `rmmod` → **Remove Module — Remover Módulo**.
- `modinfo` → **Module Information — Informações do Módulo**.
- `.ko` → **Kernel Object — Objeto do Kernel**.
- `/proc/modules` → lista de módulos carregados.
- `/etc/modprobe.d/` → configurações relacionadas aos módulos.
- `sudo` → **Superuser Do — Executar como superusuário**.
- `uname -r` → **kernel release — versão/liberação do kernel**.

---

**"Conhecimento só tem valor quando é compartilhado" - Laerte Costa**
