[Voltar](README.md)

# Resumo de comandos

| Comando        | Descrição  |
| ------------- |-------------|
| git init | Cria um novo repositório git local (cria a pasta .git) |
| git config  | Define configuração do projeto |
| git config --local | Define configuração do projeto |
| git config --global | Define configuração do usuário |
| git config --system | Define configuração para o sistema |
| git config --local --list | Lista as configurações locais do projeto |
| git config --global --list | Lista as configurações do usuário |
| git config --system --list | Lista as configurações do sistema |
| git add arquivo | Adiciona um arquivo na área de stage |
| git status | Verifica o estado dos arquivos |
| git rm arquivo | Adiciona exclusão de arquivo na área de stage |
| git commit | Envia para o repositório local as alterações que definidas na área de stage. |
| git commit -m "Mensagem" | Faz o commit já passando a mensagem como argumento |
| git commit -a | Faz o commit dos arquivos alterados, mesmo que não tenham sido adicionados à area de stage|
| git commit --amend | Substitui o commit anterior adicionando novas alterações ou substituíndo a mensagem|
| git branch branch-name| Cria um novo branch|
| git branch | Lista os branches locais |
| git branch -a | Lista tanto branches locais como remotos|
| git branch -d branch | Remove um branch |
| git branch -D branch | Remove um branch que não está em nenhum merge |
| git checkout branch-name| Traz o conteúdo de determinado branch para a área de trabalho|
| git checkout -b branch-novo branch-name| Cria o branch-novo a partir de branch-name e traz o conteúdo para a área de trabalho|
| git checkout -- arquivo|Desfaz as alterações realizados num arquivo na área de trabalho e devolve o conteúdo a partir do último commit do branch|
| git stash | Armazena as alterações na área de trabalho em área temporária e retorna a área de trabalho ao estado original do último commit |
| git stash apply| Aplica as alterações que foram enviadas para a área temporária na área de trabalho |
| git log | mostra as versões do repositório |
| git log --oneline | mostra as versões do repositório (uma linha por commit)|
| git log --oneline --decorate --graph --all| Mostra as revisões indicando merges e branches de forma "gráfica"|
| git remote add repo-name url| Configura um repositório remoto para um repositório local|
| git clone url [-o local-repo-name] [dirname]|Faz um clone de um repositório remoto para a pasta dirname e vai chamar o repositório de local-repo-name (se omitido utilizado **origin**). Se a pasta destino for omitida é utilizado o nome do projeto|
| git push repo-name branch-name| Envia os commits do branch corrente no repositório local para o repositório remoto **repo-name** no branch branch-name|
| git pull repo-name> branch-name|Busca os commits do branch branch-name do repositório repo-name e aplica no repositório local e na área de trabalho (faz merge)|
| git fetch repo-name branch-name|Busca os commits do branch branch-name do repositório repo-name e aplica no repositório local (não faz merge)|
| git remote rename repo-origem repo-destino|Altera o nome do repositório remoto de repo-origem para repo-destino|
| git merge branch|Faz **merge** do branch com o branch atual na área de trabalho|
| git reset ^HEAD| Desfaz um commit|

[Voltar](README.md)
