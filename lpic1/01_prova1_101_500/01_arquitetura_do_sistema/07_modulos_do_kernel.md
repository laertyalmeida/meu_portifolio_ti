Módulos do Kernel

Kernel — Núcleo

O Kernel (Núcleo) é a parte principal do Linux.

Ele faz a comunicação entre o software e o hardware.

Programa
   ↓
Kernel
   ↓
Hardware

---

Module — Módulo

Um Module (Módulo) é um código que pode ser carregado no kernel quando necessário.

Módulos são muito usados para adicionar suporte a hardware e recursos do sistema.

Exemplos:

- Placa de rede
- USB
- Sistema de arquivos
- Dispositivos de armazenamento

---

Onde ficam os módulos?

Normalmente ficam em:

/lib/modules/

Cada versão do kernel possui seu próprio diretório.

---

"lsmod" — List Modules (Listar Módulos)

Mostra os módulos atualmente carregados.

lsmod

---

"modprobe" — Module Probe (Carregar/Remover Módulo)

Usado para carregar ou remover módulos do kernel.

Carregar

sudo modprobe nome_do_modulo

Remover

sudo modprobe -r nome_do_modulo

"-r" — Remove (Remover)

Remove o módulo do kernel.

---

"rmmod" — Remove Module (Remover Módulo)

Remove um módulo carregado.

sudo rmmod nome_do_modulo

---

"modinfo" — Module Information (Informações do Módulo)

Mostra informações sobre um módulo.

modinfo nome_do_modulo

Pode mostrar:

- Descrição
- Autor
- Versão
- Dependências
- Arquivo do módulo

---

LPIC-1 — O que saber

- Kernel é o núcleo do sistema Linux.
- Módulos adicionam recursos ao kernel.
- Módulos podem ser carregados e removidos sem reiniciar o computador.
- "/lib/modules/" contém os módulos do kernel.
- "lsmod" mostra módulos carregados.
- "modprobe" carrega ou remove módulos.
- "rmmod" remove módulos.
- "modinfo" mostra informações sobre um módulo.
- "-r" significa Remove (Remover).

---

Resumo

Kernel
  ↓
Módulos
  ↓
Suporte a hardware e recursos

lsmod    → módulos carregados
modprobe → carregar/remover
rmmod    → remover
modinfo  → informações
