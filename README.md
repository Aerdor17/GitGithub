# GitGithub
Controle de versões com GitGithub

**Anotações:**

- **GIT INIT**
*git init* indica que aquela pasta é um repositóri git, assim o git começa a monitorar os arquivos que são criados e apagados naquela pasta
*git init --bare* indica que o repositóri é puro, usado para criar um repositório como o Origin, o qual vai ser vir de servidor para guardar as alterações
	do projeto, e disponibilizar as mesmas para outros usuários git.
	
**GIT ADD**
*git add {nome do arquivo}* adiciona o arquivo para o repositório git
*git add remote {nome do repositório}* /caminho do repositório
*git commit* faz o commit do arquivo, para o sistema de versionamento, pois quando um arquivo é criado dentro do repositório git
	não necessáriamente ele pertence ao projeto.
*git commit -m "seu comentário aqui "* o -m serve para lhe permitir fazer um comentário ao commit.
*git commit -am* é utilizado para adicionar todos os arquivos modificados
	**OBS:** Nunca deve ser commitado um código que não funciona
	
**GIT PULL**
*git pull* nome-do-repositório trás dele para a  branch nome-da-branch


**GIT LOG**
*git log --decorate* lista as alterações realizadas no repositório
*git log --author="nome do autor"* mostra as alterações, feitas por tal autor.
*git shortlog* mostra em ordem aufabética, quais foram os autores e quais os commits de cada pessoa
*git shortlog -sn* mostra em ordem aufabética, quais foram as pessoas e quantos commits elas fizeram.
*git log --graph* mostra em forma gráfica oque está acontecendo com os branchs e as versions
*git log -p* mostra as alterações linha a linha do que foi modificado
*git log --oneline* mostra de forma resumida os commits e suas alterações. 

**GIT DIFF**
*git diff* : é utilizado para mostrar quais foram as modificações dos arquvios.
*git diff --name-only* : mostra apenas a lista dos arquvios modificados.
*git diff {hash inicial}..{hash final}* mostra as aterações no código entre estes commits.

**REVERT**
*git checkout {nome do arquivo}* : é utilizado para voltar o arquivo para antes da alteração.
*git reset HEAD {nome do arquivo}* : é utilizado para tirar os arquivos da área de stage, para o ponterio atual, exemplo: editei um aquivo e fiz o git add,
	se eu dar um git diff, ele não vai listar nada pois o arquivo já está "pronto" para ser commitado, neste caso é possivel utilizar o git reset HEAD, para tirar o arquivo da área de stage.
*git reset --soft*  : aponta o HEAD para o commit indicado sem mudar o stage area e o work dir
*git reset --mixed* : aponta o HEAD para o commit indicado, e atualiza o stage area mas sem mudar o work dir
*git reset --hard* : aponta o HEAD para o commit indicado, atualiza o stage area e atualiza o work dir. 
**MAIS EM** : [https://pt.stackoverflow.com/questions/325951/quais-diferen%C3%A7as-entre-soft-mixed-hard-no-git-reset]

**CHECKOUT**
*git checkout {nome da branch}* troca de branch
*git checkout -b {nome da branch}*, cria uma nova branch e navega até elas
*git checkout {hash da branch}* navega até aquela branch de forma desanexada do projeto, e qualquer commit feito é ignorado, para poder salvar os commits desta branch deve ser  criada uma nova branch

**MERGE**
*git merge {nome de qual branch eu quero juntar com a branch que eu estou}*.
git rebase, faz quase o mesmo que o marge

**REMOTE** 
*git remote* lista os repositórios 
*git remote add {nome do repositório} {nome do repositório remoto: EX: git@github.com:aerdor17/GitGithub}*, adiciona um repositório remoto.

**GIT CLONE**
*git remote add {nome do repositório novo}* e qual *branch* vai ser clonada
*git clone* {caminho do repositório se for local} {nome do repositório que eu quero utilizar}

**GIT TAG**
*git tag -a {nome da tag ex: v1.0.0} -m "comentário"* cria uma versão de release do código, um piloto, um entregavel. 
	Recomendo ler este artico sobre versionamento, https://semver.org/lang/pt-BR/
*git tag* mostra todas as tag's disponíveis.
**OBS:** tambem é possivel enviar tag's no **git push** *git push {tag}* ou *git push origin v1.0.0*

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
