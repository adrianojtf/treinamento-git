[Voltar](README.md)

# Branch, Commit, Tag e Checkout

![Branches, Commits e Tags](/imagens/git-branches.png)

 * commit: é uma versão/revisão do projeto identificada por um SHA-1
 * branch: é um ramo de desenvolvimento e independente que posteriormente poderá ser fundido ao branch principal.
 * tag: utilizado para marcar commits “importantes”. Uma tag “aponta” para o SHA-1 do commit. 
   
Tags podem ser:
 * simples: aponta para um commit.
 * anotadas: aponta para um commit, com informações adicionais como data, identificador de usuário, e-mail, mensagem.

----

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
----

## Checkout

O comando **git checkout** é utilizado para alterar o conteúdo da área de trabalho com arquivos e pastas de diferentes revisões do repositório. 

### git checkout <branch>

Traz para a área de trabalho o conteúdo de determinado branch criado previamente.
```
git checkout falando-sobre-git
```

```
git checkout master
```

### git checkout -b <novo-branch> <branch-base>

É possível criar um novo branch diretamente a partir de outro branch, tag ou commit:

Exemplos:
```
git checkout -b desenvolvimento master
git checkout -b correcao_bugx v1.2.3
```

----

## Tag

Uma tag é um identificador ou apontador para um commit. 

Existem diversas restrições com relação ao identificador de uma tag:
 * pode incluir barra **/** para agrupamento hierárquico (diretório), mas nenhum componente separado por barras pode começar com um ponto. ou terminar com a sequência .lock.
 * não pode conter dois pontos consecutivos ".." em qualquer lugar.
 * não pode ter caracteres de controle ASCII (ou seja, bytes cujos valores sejam menores que \ 040, ou \ 177 DEL), espaço, til ~, circunflexo ^ ou dois-pontos: em qualquer lugar.
 * não pode ter ponto de interrogação, asterisco * ou colchete [ em qualquer lugar.
 * não pode iniciar ou terminar com uma barra / ou conter várias barras consecutivas
 * não pode terminar com um ponto ".".
 * não pode conter uma sequência @ {.
 * não pode ser o único caractere @.
 * não pode conter um \.

[Mais informações sobre identificadores de tags](https://git-scm.com/docs/git-check-ref-format.html)

```
git tag v0.0.1
```

```
git tag -a -m 'Tag anotada da versão 0.0.2' v0.0.2
```

```
git tag
v0.0.1
v0.0.2
```

[Voltar](README.md)