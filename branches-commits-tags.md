# Branch, Commit, Tag e Checkout

![Branches, Commits e Tags](/imagens/git-branches.png)

 * commit: é uma versão/revisão do projeto identificada por um SHA-1
 * branch: é um ramo de desenvolvimento e independente que posteriormente poderá ser fundido ao branch principal.
 * tag: utilizado para marcar commits “importantes”. Uma tag “aponta” para o SHA-1 do commit. 
   
Tags podem ser:
 * simples: aponta para um commit.
 * anotadas: aponta para um commit, com informações adicionais como data, identificador de usuário, e-mail, mensagem.


## Branches

git branch é o comando utilizado para visualizar e criar branches.

**git branch <novo-branch>** permite criar um novo branch.
```
git branch falando-sobre-branches
```

git branch mostra os branches.
```
$ git branch
  falando-sobre-branches
* master
```

**git branch -a** mostra também os branches remotos.

git branch -v / git branch -vv: mostra mensagens de commit dos branches

```
$ git branch -v
* falando-sobre-branches 60fe7c4 Adicionando informações sobre branches
  master                 f1a4c21 Primeira versão, com arquivo índice (README.md) e as primeiras operações para criar um repositório e inserir um arquivo
```

## Checkout

```
git checkout -b desenvolvimento master
git checkout master
git checkout desenvolvimento
git checkout -b bugx v1.2.3
```