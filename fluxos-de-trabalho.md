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

# epa, esqueci de criar um branch, não era no master... :(

git reset --hard HEAD~1
git branch desenvolvimento

git checkout desenvolvimento
```

[Voltar](README.md)