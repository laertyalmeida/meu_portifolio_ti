# Capítulo 8 — Arquitetura de computador: software — Tópicos para revisão

## 1. Infraestrutura

* **Hardware:** parte física.
* **Software:** programas que controlam o hardware.
* Hierarquia: **Aplicativos → Utilitários → SO → Hardware**.
* **SO:** gerencia recursos e fornece abstrações.
* Exemplos: Windows, Linux, FreeBSD, OS X.
* **Shell:** interface por comandos.
* **GUI:** interface gráfica.
* **Modo usuário:** acesso limitado.
* **Modo núcleo:** acesso privilegiado ao hardware.

### Objetivos do SO

* Ocultar detalhes do hardware.
* Fornecer interface ao usuário.
* Gerenciar CPU, memória e armazenamento.
* Controlar E/S.

### Multiplexação

* **Tempo:** revezamento do recurso.
* **Espaço:** divisão do recurso.

---

## 2. Tipos de sistemas operacionais

### Grande porte

* Grande capacidade de E/S.
* **Batch:** tarefas sem interação.
* **Transações:** muitas operações pequenas.
* **Timesharing:** vários usuários simultâneos.

### Servidores

* Atendem vários usuários pela rede.
* Serviços: arquivos, impressão e web.
* Exemplos: Linux, FreeBSD, Solaris, Windows Server.

### Multiprocessadores

* Várias CPUs/processadores.
* Maior capacidade computacional.
* Suporte a comunicação e consistência de dados.

### Portáteis

* Smartphones e tablets.
* Exemplos: Android e iOS.
* GPS, câmera, sensores e apps.

### Embarcados

* Equipamentos específicos.
* Software geralmente instalado de fábrica.
* Exemplos: TV, carro, micro-ondas.
* Exemplos de SO: Embedded Linux, QNX, VxWorks.

### Tempo real

* Execução depende do tempo.
* **Crítico:** atraso pode causar danos.
* **Não crítico:** pequenos atrasos aceitáveis.
* Ex.: indústria, robótica e automóveis.

---

## 3. Processos

* **Processo = programa em execução.**
* Possui espaço de endereçamento e recursos necessários à execução.

### Criação

* Inicialização do sistema.
* Chamada de sistema.
* Solicitação do usuário.
* Tarefa em lote.

### Estados

* **Em execução:** usando CPU.
* **Pronto:** aguardando CPU.
* **Bloqueado:** aguardando evento.

### Gerenciamento

* **Tabela de processos:** informações dos processos.
* **Processo filho:** criado por outro processo.
* **Árvore de processos:** relação pai/filho.
* **Escalonador:** escolhe o próximo processo a executar.

---

## 4. Threads

* **Thread:** linha de execução dentro de um processo.
* Mais leves que processos.
* Criação e destruição mais rápidas.
* Threads compartilham o espaço de memória do processo.
* Processos possuem espaços independentes.
* **Multithreading:** várias threads no mesmo processo.
* Melhora concorrência e capacidade de resposta.

---

## 5. Aplicativos e utilitários

### Aplicativos

* Voltados diretamente ao usuário.
* Exemplos:

  * Editor de texto.
  * Planilha.
  * Navegador.
  * Player.

### Utilitários

* Auxiliam o sistema e o usuário.
* Exemplos:

  * Antivírus.
  * Compactadores.
  * Backup.
  * Desfragmentação.
  * Sincronização.

### Diferença principal

* **SO:** gerencia os recursos fundamentais.
* **Aplicativo:** realiza tarefas para o usuário.
* **Utilitário:** auxilia na manutenção e administração.

📌 **Observação:** Este arquivo é um resumo autoral elaborado para fins de estudo. O conteúdo foi reorganizado e escrito em linguagem simples para facilitar a compreensão e a revisão. Não substitui o material oficial da disciplina.

