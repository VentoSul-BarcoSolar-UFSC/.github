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

Para aprofundar seus conhecimentos sobre o terminal e praticar mais comandos:
* [Linux Journey: The Shell](https://labex.io/lesson/the-shell)

### 3. Comandos Essenciais do Git

Agora que você já sabe navegar pelo terminal, vamos usar o Git para controlar o versionamento do nosso código. Nesta atividade, você vai clonar um repositório, criar sua própria linha de desenvolvimento (branch), fazer alterações e enviá-las de volta para o GitHub.

#### 3.1. Preparando o Terreno

Primeiro, vamos organizar nossa área de trabalho.

**0. Abra o CMDer**
> **Nota:** Lembre-se de nunca abrir o CMDer como administrador para operações de desenvolvimento, pois isso pode causar problemas de permissão.

Navegue até a pasta do seu usuário, crie um diretório para seus projetos e acesse-o. Substitua `SeuUsuario` pelo nome do seu usuário no Windows.

```bash
ventosul@bigode:~$ cd /c/Users/SeuUsuario/
ventosul@bigode:/c/Users/SeuUsuario$ mkdir projects
ventosul@bigode:/c/Users/SeuUsuario$ cd projects/
ventosul@bigode:/c/Users/SeuUsuario/projects$
```

#### 3.2. Clonando o Repositório

**1. `git clone`**
O comando `git clone` faz uma cópia exata de um repositório do GitHub para a sua máquina local. Como você já configurou sua chave SSH no passo anterior, o GitHub não pedirá sua senha.

```bash
ventosul@bigode:~/projects$ git clone git@github.com:VentoSul-BarcoSolar-UFSC/calouros-software.git
Cloning into 'calouros-software'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
```
**2. Entre no repositório**
Uma vez clonado, o projeto estará em uma nova pasta. Use `cd` para entrar nela.

```bash
ventosul@bigode:~/projects$ cd calouros-software/
ventosul@bigode:~/projects/calouros-software$
```

#### 3.3. Atividade Prática

Agora, siga os passos abaixo para fazer sua primeira contribuição.

**- Cheque o status e a branch atual**
Use `git status` para ver o estado atual do repositório e `git branch` para ver em qual branch você está. A branch com `*` é a sua branch atual.

```bash
ventosul@bigode:~/projects/calouros-software$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

ventosul@bigode:~/projects/calouros-software$ git branch
* main
```

**- Crie e acesse sua própria branch**
Use `git switch -c` para criar uma nova branch e já mudar para ela. Use o padrão `SeuNome_ANO`.

```bash
ventosul@bigode:~/projects/calouros-software$ git switch -c Alan_Turing_1939
Switched to a new branch 'Alan_Turing_1939'
```

**- Verifique se você está na sua branch**
Use `git branch` novamente para confirmar.

```bash
ventosul@bigode:~/projects/calouros-software$ git branch
  main
* Alan_Turing_1939
```

**- Crie uma pasta e um arquivo**
Agora, vamos criar uma pasta com seu nome e um arquivo `.txt` dentro dela. O comando `echo "Texto" > caminho/arquivo.txt` cria um arquivo com o texto especificado.

```bash
ventosul@bigode:~/projects/calouros-software$ mkdir Alan_Turing
ventosul@bigode:~/projects/calouros-software$ echo "South Wind Moustache" > Alan_Turing/meu_arquivo.txt
```

**- Cheque o status novamente**
Note que o Git detectou a nova pasta como "Untracked files" (arquivos não rastreados).

```bash
ventosul@bigode:~/projects/calouros-software$ git status
On branch Alan_Turing_1939
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Alan_Turing/

nothing added to commit but untracked files present (use "git add" to track)
```

**- Adicione os arquivos para o próximo commit (`git add`)**
O comando `git add` prepara os arquivos para serem salvos no histórico.
* `git add .` adiciona todas as alterações no diretório atual.
* `git add caminho/para/o/arquivo.txt` adiciona um arquivo específico.

Vamos usar o `git add .`

```bash
ventosul@bigode:~/projects/calouros-software$ git add .
```

**- Salve as alterações no histórico (`git commit`)**
O `git commit` cria um "ponto de salvamento" permanente no histórico. A mensagem (`-m`) é crucial para explicar o que foi feito.

```bash
ventosul@bigode:~/projects/calouros-software$ git commit -m "feat: Adiciona pasta e arquivo de Alan Turing"
```
> Para aprender a escrever mensagens de commit claras e úteis, leia este guia: [Escrevendo um bom commit](https://cbea.ms/git-commit/)

**- Envie suas alterações para o GitHub (`git push`)**
O `git push` envia seus commits locais para o repositório remoto. Na primeira vez que você envia uma branch nova, use `-u origin nome_da_branch` para ligar sua branch local à remota.

```bash
ventosul@bigode:~/projects/calouros-software$ git push -u origin Alan_Turing_1939
```

**- Peça o `git status` final**
O status agora deve mostrar que sua branch está limpa e sincronizada com a `origin` (o repositório no GitHub).

```bash
ventosul@bigode:~/projects/calouros-software$ git status
On branch Alan_Turing_1939
Your branch is up to date with 'origin/Alan_Turing_1939'.

nothing to commit, working tree clean
```

**- Volte para a branch `main`**
Use `git switch` para trocar de branch.

```bash
ventosul@bigode:~/projects/calouros-software$ git switch main
```

**- Delete sua branch local**
Já que seu trabalho está salvo no GitHub, você pode apagar a branch local com `git branch -d`.

```bash
ventosul@bigode:~/projects/calouros-software$ git branch -d Alan_Turing_1939
```

**- Traga a branch remota de volta**
Para praticar, vamos supor que você precise trabalhar naquela branch novamente. Use `git fetch` para atualizar a lista de branches do repositório remoto e depois `git switch` para recriar a branch localmente, já conectada à remota.

```bash
ventosul@bigode:~/projects/calouros-software$ git fetch
ventosul@bigode:~/projects/calouros-software$ git switch Alan_Turing_1939
```

---

### Conclusão

Parabéns, você completou o fluxo básico de trabalho com Git! Estes são apenas os comandos iniciais; o Git é uma ferramenta extremamente poderosa com muitos recursos para explorar.

Para referência futura e para aprender mais comandos, consulte este guia:
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
