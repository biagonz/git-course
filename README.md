# Git Course
Instruction to facility the life with git and practice writing english. My first experience with markdown language.

# Install
To install `git` in your computer access: [Git](https://git-scm.com/)

# How to configure git
O git guarda suas informações em três lugares. 
No `git config` do sistema com um todo, do usuário ou do projeto.
Para acessar o config do usuário vamos utilizar o `git config --global`

## Configurar o nome
    git config --global user.name "Your Name"

## Configurar o e-mail
    git config --global user.email "youremail@email.com"

## Configurar o editor principal
    git config --global core.editor code
Caso o editor não seja alterado o padrão é utilizar o Vim. No exemplo o editor principal foi alterado para o [Visual Studio Code](https://code.visualstudio.com/).

## Abrir o git.config

    git config --global --edit
## Para listar todas as configurações
    git config --list

# Inicializar um repositório
Para inicializar um repositório é necessário utilizar o comando `git init`. Ele é responsável por inicializar o repositório e ficar monitorando 
tudo o que é modificado dentro do repositório.

# Usando o editor do terminal 
- Para abrir um arquivo: 

    > vim nome_do_arquivo.txt

- Com o arquivo aberto no vim: Inserir a letra I para habilitar o modo --INSERT--
- Utilizar a tecla ESC para sair do modo de inserção
- A tecla `:` quer dizer algum comando será iniciado
    - wq: escrever, salvar e sair
    - q: para sair do modo edição

# Ciclo de vida dos status dos arquivos - File Status Lifecycle

## Untracked
Untracked ou não marcado é um arquivo que ainda não está sendo monitorado pelo git. O git ainda não reconhece versões desse arquivo dentro das versões do repositório.

## Unmodified 
Um arquivo é considerado unmodified depois de ser adicionado ao monitoramento do repositório. 

## Modified
É considerado modified quando está em unmodified e é modificiado

## Staged
É a área onde será criada a versão. Diz para o git "No momento em que a versão for fechada, leve esses arquivos". Assim que você fizer o commit, que é criar essa versão (esse hash), todos esses arquivos que foram adicionados voltam a ser unmodified. Nesse estado o git entende que naquele arquivo anda foi modificado desde a última versão criada.


# Comandos

## Git Status
O comando `git status` serve para reportar como está o repositório no momento atual (localmente). Ele diz em qual branch você está e se tem algo para commitar.

## Git Add
O comando `git add` é utilizado para adicionar os arquivos ao staged. Se um arquivo que está no staged é modificado é necessário adicioná-lo novamente utilizando `git add`.

## Git Commit 
O comando `git commit -m "Add message"` é utilizado para criar uma versão de todos os arquivos que foram adicionados no staged. O commit é o momento onde você avisa o git: "Olha, pegue todos esses arquivos que estão no staged e crie uma versão deles (snapshot)".

O comando abaixo serve para adicionar um arquivo que já existe e commitra a mensagem ao mesmo tempo.

     git commit -am "Add message"

## Git Log
O comando `git log` permite ver uma lista com a hash, o autor, a data e a mensagem dos commits. Para sair da listagem dos commits basta apertar a letra 'q'. Também é possível passar algumas opções, como:

### Decorate
Ele mostra de foi de uma branch para outra, se foi um merge, que tags foram geradas. REVER AS INFORMAÇÕES

### Author
Filtra todos os commits pelo nome do autor 

    git log --author="Name"

### Shortlog
Mostra em ordem alfabética, quais foram os autores, quantos e quais commits fizeram. Com o -sn é possível ver a quantidade de commits com o nome do autor.

    git shortlog
    git shortlog -sn


### Graph
Ele mostra em forma gráfica no terminal o que está acontencendo com os branchs e as versões.

    git log --graph

## Git Show
Ao capturar a hash utilizando o `git log` é possível ver o conteúdo modificado naquele commit utilizando o comando 

    git show *insira a hash aqui*

## Git Diff
O diff permite ver as mudanças antes de serem enviadas. Ele mostra o que foi adicionado e/ou removido dos arquivos alterados.

    git diff

### Name Only
Retorna somente o nome dos arquvos alterados.

    git diff --name-only

## Git Reset
Uma possibilidade do git é resetar os erros, remover o que foi feito por último.
Volta para no pointeiro anterior

    git reset HEAD

### Git Reset --soft

    git reset --soft *insira a hash aqui*

Esse comando volta para a hash passada e mantem os arquivos em staged. É necessário ser sempre um commit anterior ao que será apagado, pois tudo a frente dessa hash não existirá mais.

### Git Reset --mixed

    git reset --mixed *insira a hash aqui*

Esse comando volta para a hash passada e mantem os arquivos em modified. É necessário ser sempre um commit anterior ao que será apagado, pois tudo a frente dessa hash não existirá mais.

### Git Reset --hard

    git reset --hard *insira a hash aqui*

Esse comando volta para a hash passada e descarta qualquer alteração. É necessário ser sempre um commit anterior ao que será apagado, pois tudo a frente dessa hash não existirá mais. Não é recomendado utilizar quando o commit já estiver no repositório remoto.

## Git Checkout
Ao digitar esse comando antes do commit é possível excluir todas as modificações realizadas no arquivo.

    git checkout file_name.js

O checkout tambpém pode ser utilizado para sair de uma branch para outra.

    git checkout -b branch-name


# Git Delete
Apaga a branch

    git branch --delete main

    or

    git branch --delete --force main

    or 

    git branch -D main

# Criar um novo repositório
https://github.com/new

# Criando e adicionando uma chave SSH

O SSH é um protocolo que serve autenticar um usuário remoto a um servidor. Ele é baseado em chaves, onde existe uma chave publica e uma privada, onde a chave privada consegue abrir a chave pública. A chave pública fica dentro do git e a chave privada na máquina e é possível realizar a conexão.

> [Tutorial do GitHub](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)


# Ligando repositório local a um remoto

## Criar um novo repositório

    echo "# repo name" >> README.md
    git init
    git add README.md
    git commit -m "first commit"
    git remote add origin git@github.com:user/repo-name.git
    git push -u origin master

## Usar um repositório existente

    git remote add origin git@github.com:user/repo-name.git
    git push -u origin master

