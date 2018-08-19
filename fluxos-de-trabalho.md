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

Neste caso vamos utilizar o comando **git stash** e depois **git stash apply** para salvar e recuperar alterações em andamento no workspace.

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
git stash apply
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
## Comparando revisões

### git diff

Exibe as alterações da área de trabalho com relação ao último commit no branch atual ou com o conteúdo da área de staging (se houver).

````
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

 git diff branch_name

 git diff v0.0.1 v0.0.2

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

[Voltar](README.md)