# Comandos Essenciais: Bash e Git

Este guia é a continuação do provisionamento do ambiente e foca nos comandos que você usará no dia a dia para navegar pelo sistema e controlar o versionamento do código.

---

### 1. Por que usar a Linha de Comando?

Aprender a usar o terminal é fundamental por três motivos principais: **controle**, **velocidade** e **padronização**. Ferramentas com interface gráfica são úteis, mas o terminal oferece um controle muito mais fino e direto sobre suas tarefas. Muitas operações são mais rápidas via teclado, e o mais importante: ele é uma ferramenta universal no mundo do desenvolvimento, garantindo que todos na equipe sigam um fluxo de trabalho padronizado e eficiente.

---

### 2. Comandos Básicos do Terminal (Bash)

Antes de entrarmos no Git, você precisa saber se movimentar pelo sistema de arquivos. Os comandos a seguir são a base para a navegação e manipulação de pastas e arquivos.

> **Nota sobre o CMDer:** Ao usar o CMDer no Windows, você tem acesso a muitos comandos do Linux/Bash, como os listados abaixo. No entanto, alguns comandos mais avançados podem não funcionar como esperado. Os comandos de navegação, listagem e criação de diretórios funcionarão perfeitamente.

#### `pwd` (Print Working Directory)
Mostra o caminho completo da pasta em que você está no momento. É útil para você se localizar.

```bash
ventosul@bigode:~$ pwd
/home/ventosul/projects
```

#### `ls` (List)
Lista todos os arquivos e pastas no diretório atual.

* `ls -lha`: Mostra a lista em formato detalhado (`-l`), incluindo arquivos ocultos (`-a`) e com tamanhos legíveis (`-h`).

```bash
ventosul@bigode:~/projects$ ls
controle-telemetria-2025   vs-research
```

#### `cd` (Change Directory)
Muda de um diretório para outro.

* `cd nome-da-pasta`: Entra na pasta especificada.
* `cd ..`: Sobe um nível no diretório (vai para a pasta "pai").
* `cd ~` ou `cd`: Volta para o seu diretório inicial (home).

```bash
ventosul@bigode:~/projects$ cd controle-telemetria-2025/

ventosul@bigode:~/projects/controle-telemetria-2025$ ls
LICENSE   README.md   sensor   svr_model   webpage
```

#### `mkdir` (Make Directory)
Cria um novo diretório (uma nova pasta).

```bash
ventosul@bigode:~/projects/controle-telemetria-2025$ mkdir docs

ventosul@bigode:~/projects/controle-telemetria-2025$ ls
LICENSE   README.md   docs   sensor   svr_model   webpage
```

---

Para aprofundar seus conhecimentos sobre o terminal e praticar mais comandos, este recurso interativo é excelente:
* [Linux Journey: The Shell](https://labex.io/lesson/the-shell)
