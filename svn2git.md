[Voltar](README.md)

# Migração de subversion para git

## svn export

A forma mais simples de trazer um código do subversion para o git, desconsiderando todo o histórico de alterações é utilizar o comando svn export e posteriormente criar um novo repositório.

```
svn export http://svn.xxx projetox
cd projetox 
git init
git add .
git commit -m 'Projeto adicionado ao git, sem histórico nenhum'
```

Quando uma migração simples, sem histórico, não for o caso há a opção de utilizar a ferramenta svn2git ou git-svn
----

## Ferramenta svn2git

----
## git svn

git svn permite operações bidirecionais entre o git e o svn.


[Voltar](README.md)
