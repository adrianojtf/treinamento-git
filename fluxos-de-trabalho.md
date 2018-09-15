[Voltar](README.md)

# Fluxos de Trabalho

## Implementar nova funcionalidade

```
git checkout -b nova_funcionalidade master
vi …
...
git add …
git commit -m 'nova funcionalidade implementada'
git checkout master
git merge nova_funcionalidade
git branch -d nova_funcionalidade
```
----

## Durante a implementação de nova funcionalidade surge um bug para corrigir

Neste caso vamos utilizar o comando **git stash** e depois **git stash pop** para salvar e recuperar alterações em andamento no workspace.

```
git checkout -b nova_funcionalidade master
vi ...
# surge um bug pra corrigir urgente numa release qualquer
# vou precisar salvar o que estou fazendo
git stash
git checkout -b branch_v1.0.1 v1.0.0
vi x
git commit -am "correção do bug 1234”
# gerar uma tag nova...
git tag v1.0.1
# fazer o merge da correção no master
git checkout master
git merge branch_v1.0.1
git checkout nova_funcionalidade
git stash pop
```

Se desejável aplicar o patch neste branch também:
```
git merge tags/v1.0.1
```
----

## Trabalhando com dois repositórios remotos

Existem situações nas quais estamos utilizando algum projeto open source e agregando alguns arquivos de configuração ou para criação do pacote de instalação. Nestes casos é interessante trabalhar com referência a dois repositórios.

Exemplo:
```
git clone git@gitlab.com/fulano-de-tal/janus-gateway.git -o gitlab
cd janus-gateway
git remote add github https://github.com/meetecho/janus-gateway.git
git fetch github --tags
git tag
git checkout -b nova_versao tag_local_antiga
git merge tag_remota_nova
...
```
----

## Desfazendo um commit num branch e levando para outro

```
git checkout master
vi teste.c
git commit -am 'teste.c'
```
No git log vemos isso:
```
$ git log --oneline
0f39e65 (HEAD -> master) teste.c
af3a583 Adicionando fluxos-de-trabalho e atencao
a88e334 (gitlab/master) Correção em links e adicionando informações sobre repositórios remotos
...
```

Mas como essa alteração era pra ser num branch de desenvolvimento, vamos desfazer:

```
$ git reset HEAD^
$ git log --oneline
af3a583 (HEAD -> master) Adicionando fluxos-de-trabalho e atencao
a88e334 (gitlab/master) Correção em links e adicionando informações sobre repositórios remotos
...
```

Indo para um branch:
```
git checkout -b desenvolvimento
git add teste.c
git commit -am 'teste.c no branch desenvolvimento'
```

----

## Transferindo vários commits para um novo branch

Após trabalhar num desenvolvimento fazendo 3 commits você decide que deveria criar um branch para colocar o trabalho separado do master. O seu log está assim:
```
$ git log --oneline
a347e18 (HEAD -> master) teste 3
451127b teste 2
6f5fef6 Teste
9513e39 (gitlab/master, github/master) Adicionando submódulos, migração de svn para git, e melhorando resumo de comandos.
```

Vamos utilizar os comandos abaixo para criar o novo branch:
```
$ git branch teste
$ git reset --hard HEAD~3
$ git checkout teste
```

```
$ git log --oneline
a347e18 (HEAD -> teste) teste 3
451127b teste 2
6f5fef6 Teste
9513e39 (gitlab/master, github/master, master) Adicionando submódulos, migração de svn para git, e melhorando resumo de comandos.
```
----
## Comparando revisões

### git diff

Exibe as alterações da área de trabalho com relação ao último commit no branch atual ou com o conteúdo da área de staging (se houver).

```
$ git diff
diff --git a/fluxos-de-trabalho.md b/fluxos-de-trabalho.md
index 51c6dd9..e100952 100644
--- a/fluxos-de-trabalho.md
+++ b/fluxos-de-trabalho.md
@@ -97,8 +97,11 @@ git commit -am 'teste.c no branch desenvolvimento'
 ----
 ## Comparando revisões

-git diff
+### git diff

+Exibe as alterações da área de trabalho com relação ao último commit no branch atual ou com o conteúdo da área de staging (se houve).
+
+###
```

### git diff branch_name

### git diff v0.0.1 v0.0.2

----

### git difftool 

```
$ git config --global  diff.guitool meld
$ git config --global mergetool.meld.path "C:\Program Files (x86)\Meld\Meld.exe"
$ git difftool --dir-diff --tool="meld" v0.0.1..master
```

----

## Copiar alterações específicas de alguns commits de um branch e aplicando em outro

```
git checkout branch-x
git cherry-pick <commit(s)>
```
----

## Alterar a mensagem do último e/ou adicionar arquivos

Alterar a mensagem do último commit:

```
git commit --amend -m 'nova mensagem'
```

Adicionar arquivos ao último commit:
```
git add arquivo-novo
git commit --amend -m 'novos arquivos'
```



----

## Realizar um merge agrupando todos os commits de um branch de desenvolvimento de funcionalidade

Durante o desenvolvimento de uma nova funcionalidade vamos criar um branch específico para uma funcionalidade.

Dependendo da complexidade da funcionalidade poderemos ter dezenas de commits neste branch e muitos deles talvez com mensagens não muito elaboradas.

O git permite que se faça um agrupamento destes commits em um único durante a operação de merge.

Vamos considerar que o branch funcionalidade-x contém a nova funcionalidade e develop é o branch que receberá o merge.

```
git checkout develop
git merge --squash funcionalidade-x
```

Diferente de um merge comum, aqui será necessário adicionar os arquivos à area de staging e fazer o commit.
Na operação de commit, o git exibirá todas as mensagens dos commits intermediários realizados, permitindo que você selecione e edite o que deseja que já para o commit agrupador.

```
git add ...
git commit
```


[Voltar](README.md)