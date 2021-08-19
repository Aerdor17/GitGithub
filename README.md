# GitGithub
Controle de versões com GitGithub

**ANOTAÇÕES:**

**GIT INIT**
- *git init* indica que aquela pasta é um repositóri git, assim o git começa a monitorar os arquivos que são criados e apagados naquela pasta
- *git init --bare* indica que o repositóri é puro, usado para criar um repositório como o Origin, o qual vai ser vir de servidor para guardar as alterações
	do projeto, e disponibilizar as mesmas para outros usuários git.
	
**GIT ADD**
- *git add {nome do arquivo}* adiciona o arquivo para o repositório git
- *git remote add {nome do repositório}* /caminho do repositório
- *git commit* faz o commit do arquivo, para o sistema de versionamento, pois quando um arquivo é criado dentro do repositório git
	não necessáriamente ele pertence ao projeto.
- *git commit -m "seu comentário aqui "* o -m serve para lhe permitir fazer um comentário ao commit.
- *git commit -am* é utilizado para adicionar todos os arquivos modificados
	**OBS:** Nunca deve ser commitado um código que não funciona
	
**STASH**
- git stash, caso eu tenha feito alguma alteração mas ainda não tenha feito o git add e precise, ir para outra tarefa, eu posso estar utilizando o git stash, para guardar essas alterações futuramente.
- git stash list, mostra todas as stash salvas.
- git stash apply {númeor da stash}
- git stash pop, tira da stash a ultima alteração e trás para a edição.
	
**GIT PULL**
- *git pull* nome-do-repositório trás dele para a  branch nome-da-branch


**GIT LOG**
- *git log --decorate* lista as alterações realizadas no repositório
- *git log --author="nome do autor"* mostra as alterações, feitas por tal autor.
- *git shortlog* mostra em ordem aufabética, quais foram os autores e quais os commits de cada pessoa
- *git shortlog -sn* mostra em ordem aufabética, quais foram as pessoas e quantos commits elas fizeram.
- *git log --graph* mostra em forma gráfica oque está acontecendo com os branchs e as versions
- *git log -p* mostra as alterações linha a linha do que foi modificado
- *git log --oneline* mostra de forma resumida os commits e suas alterações. 

**GIT DIFF**
- *git diff* : é utilizado para mostrar quais foram as modificações dos arquvios.
- *git diff --name-only* : mostra apenas a lista dos arquvios modificados.
- *git diff {hash inicial}..{hash final}* mostra as aterações no código entre estes commits.

**REVERT**
- *git checkout -- <nome do arquivo>*  é utilizado para voltar o arquivo para antes da alteração, antes de dar um git add.
- *git reset HEAD <nome do arquivo>*  é utilizado para tirar os arquivos da área de stage, caso você tenha feito o git add e precise desfazer, depois só fazer um git reset --<nome do arquivo>, caso queira desfazer a alteração.
- git revert {hash do commit}, vai reverter o commit.
- *git reset --soft*  : aponta o HEAD para o commit indicado sem mudar o stage area e o work dir
- *git reset --mixed* : aponta o HEAD para o commit indicado, e atualiza o stage area mas sem mudar o work dir
- *git reset --hard* : aponta o HEAD para o commit indicado, atualiza o stage area e atualiza o work dir. 
**MAIS EM** : [https://pt.stackoverflow.com/questions/325951/quais-diferen%C3%A7as-entre-soft-mixed-hard-no-git-reset]
	

**GIT BRANCH**
- git branch {nome do branch}, cria uma nova branch, apartir do branch atual.
- git branch -d {nome do branch}, remove o branch.
- git branch -D {nome do branch}, remove o branch, caso ele esteja a frente do branch atual.
- git checkout -b {nome da branch}, cria uma nova branch e navega até elas, -b é um atalho para git branch seguido de checkou que navega até o branch criado.
	
	
**CHECKOUT**
- *git checkout {nome da branch}* troca de branch
- *git checkout -b {nome da branch}*, cria uma nova branch e navega até elas
- *git checkout {hash da branch}* navega até aquela branch de forma desanexada do projeto, e qualquer commit feito é ignorado, para poder salvar os commits desta branch deve ser  criada uma nova branch

**MERGE AND REBASE**
-  git merge {nome de qual branch eu quero juntar com a branch que eu estou}.
-  git rebase, faz quase o mesmo que o marge.
-  git rebase -i {hash do commit anterior aos que eu quero trabalhar} vai abrir a tela para fazer o pick, de quais commits você pode juntar em um unico commit
-  git rebase -i HEAD~{número de commits que eu quero trabalhar} para fazer um novo commit.

**DEPOIS:** de fazer o git rebase -i, você deve trocar a palava pick dos commits que você quer juntar pela letra "S" e salvar. 

**REMOTE** 
- *git remote* lista os repositórios 
- *git remote add {nome do repositório} {nome do repositório remoto: EX: git@github.com:aerdor17/GitGithub}*, adiciona um repositório remoto.

**GIT CLONE**
- *git remote add {nome do repositório novo}* e qual *branch* vai ser clonada
- *git clone* {caminho do repositório se for local} {nome do repositório que eu quero utilizar}

**GIT TAG**
- *git tag -a {nome da tag ex: v1.0.0} -m "comentário"* cria uma versão de release do código, um piloto, um entregavel. 
	Recomendo ler este artico sobre versionamento, https://semver.org/lang/pt-BR/
- *git tag* mostra todas as tag's disponíveis.
**OBS:** tambem é possivel enviar tag's no **git push** *git push {tag}* ou *git push origin v1.0.0*
	
	
**CHERRY PICK**
- git cherry pick {hash do commit} é utilizado quando queremos pegar apenas um commit de uma derminada branch, e levar ele para outra branch, para utilizar só ir na branch que você quer levar o commit e fazer git cherry pick {hash do commit que você quer trazer}.
	
**GIT BISECT START**
- git bisect é utilizado para verificarmos, pontos do código, exemplo eu persebi que agora o código parou de funcionar e eu quero entender, onde foi a alteração que quebrou  o código para isso eu executo, *git bisect start* e informo um commit em que o código estava **bad** com *git bisect bad {hash do commit}* depois eu passo um commit em que o código está bom com *git bisect good {hash commit}, Depois ´é só fazer o git revert.
	
**GIT SHOW**
- git show {hash do commit}, é utilizado para mostrar todas as alterações do commit.
	
**GIT BLAME**
- com o git blame {nome do arquivo ex: index.html} o git vai listar todas as alterações daquele arquivo junto com quem as fez.
	
	
**TABALHANDO COM BRANCH's**
- uma convensão mais comum para se trabalhar com branch's é 
1° master (branch de produção)
2° devoloped que deriva da master (branch de desenvolvimento master),(a devoloped deve ser uma branch pura, onde apartir dela otras branch(que implementam features)derivam).
3° feature's 1,2,3,4... (que derivam da branch devoloped), todas as features fazem *merge* para devoloped junto com os hotfix.
4° caso algum bug emergencial seja encontrado, nunca deve ser corrigido direto na master,  deve sere criado uma branch de hotfix(correção de bug), e as branch's de hotfix, fazem  merge direto para master(produção), após fazer o merge é feito uma tag desta nova versão com correção.
5° após fazer o merge das features+hotfix, para branch de developed pode ser feito uma branch de release apartir da branch de developed, para testar, encontrados bugs na branch de release, devem ser os mesmos corrigidos nesta branch, release aprovada, deve ser feito o merge da mesma na master.
	

	


	

