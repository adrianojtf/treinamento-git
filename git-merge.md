# Merge

Após criar um branch e fazer as alterações desejadas convém fazer um commit e, se for o caso, fazer um **merge** com algum outro branch.

Exemplo:
```
$ git commit --amend -am 'branch, tag, checkout'
[falando-sobre-branches aae5ad5] branch, tag, checkout
 Date: Sat Aug 18 14:10:47 2018 -0300
 8 files changed, 196 insertions(+), 9 deletions(-)
 create mode 100644 branches-commits-tags.md
 create mode 100644 imagens/git-branches.png

$ git checkout master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.

$ git branch
  falando-sobre-branches
* master

$ git merge falando-sobre-branches
Updating f1a4c21..aae5ad5
Fast-forward
 README.md                    |  16 ++++++-
 branches-commits-tags.md     | 102 +++++++++++++++++++++++++++++++++++++++++++
 conceitos.md                 |  15 ++++---
 criando-repositorio-local.md |   7 ++-
 imagens/git-branches.png     | Bin 0 -> 30668 bytes
 instalacao.md                |   6 ++-
 operacoes-locais.md          |  51 ++++++++++++++++++++++
 resumo-comandos.md           |   8 +++-
 8 files changed, 196 insertions(+), 9 deletions(-)
 create mode 100644 branches-commits-tags.md
 create mode 100644 imagens/git-branches.png
```

Neste caso bem simples, o git utilizou o método **fast-forward** para executar o merge, pois não havia nenhum commit no master posterior a criação do branch.
----

## git mergetool

Merges mais complexos podem exibir uma ferramenta de merge.

Criando um cenário mais complexo:

```
git checkout falando-sobre-branches
echo -e "\n\nAdicionando texto ao final de uma arquivo" >> README.md
git commit -am 'Teste do merge'
git checkout master
echo -e "\n\nAdicionando outro texto ao final do mesmo arquivo no branch master" >> README.md
git commit -am 'Adicionando texto ao README.md no master' 
```

Agora tentando fazer o merge:
```
$ git merge falando-sobre-branches
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

As principais ferramentas de merge aceitas pelo git são listadas assim:
```
git mergetool --tool-help
```

```
git mergetool --tool=winmerge
ou 
git mergetool --tool=meld
```

Após fazer manualmente o merge, o git finaliza o merge.
```
$ git mergetool --tool=winmerge
Merging:
README.md

Normal merge conflict for 'README.md':
  {local}: modified file
  {remote}: modified file
```