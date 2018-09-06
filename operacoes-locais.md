[Voltar](README.md)

# Operações Locais

![Operações Locais](/imagens/git-areas.png)

Conforme a imagem acima, o git possui 3 áreas onde os arquivos são armazenados:
 * repositório local: na pasta .git ficam armazenadas as informações sobre os arquivos que compõe o projeto e as revisões existentes destes arquivos. Para transferir arquivos para o repositório local é necessário utilizar a operação **git commit** que gera um SHA-1 dos arquivos e cria um **commit**.
 * área de staging: é uma área provisória para indicar quais arquivos e/ou pastas entrarão no próximo commit. Arquivos são enviados para a área de staging através dos comandos **git add** e **git rm**.
 * área de trabalho: é o conteúdo onde o usuário/programador visualiza e altera os arquivos de determinada revisão. Através do comando **git checkout** é possível alternar rapidamente os arquivos do workspace entre várias revisões do repositório. 
 
Exemplo da adição de um arquivo na área de staging e posterior geração de uma versão. 
É importante observar que todas estas operações são locais.

```
echo "# TESTE" >> README.md
git status
git add README.md
git commit -m 'adicionando arquivo'
```
----

## git add

Adiciona um arquivo novo ou alterado na área de staging, para posterior envio para o repositório local.

----

## git status

Analisa o estado da área de trabalho, indicando arquivos que foram alterados e/ou adicionados e/ou removidos.

```
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   README.md
        modified:   conceitos.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        branches-commits-tags.md
        imagens/git-branches.png

no changes added to commit (use "git add" and/or "git commit -a")
```
----

## git commit

Cria um **commit** com as alterações da área de trabalho que foram previamente definidas na área de staging.

----

## git commit -a

Cria um **commit** com as alterações enviadas para a área de staging incluindo também qualquer arquivo que já esteja sob o controle do repositório e que tenha sido alterado desde o último commit.

----

## git commit --amend

Altera o último commit complementando com novos arquivos ou uma nova mensagem.

## git commit -m 'mensagem'

Faz o commit passando mensagem do commit

```
$ git commit -m 'Pequenas correções'
[master 3e8830f] Pequenas correções
 4 files changed, 46 insertions(+), 8 deletions(-)
```

[Voltar](README.md)