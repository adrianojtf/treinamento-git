# Repositórios Remotos

![fluxo-trabalho-repositorios](imagens/basic-remote-workflow.png)

## git clone

Faz um **clone** de um repositório remoto para uma pasta local.
O clone contém uma cópia completa do projeto, com todas as alterações, commits e logs.

```
git clone https://github.com/nginx/nginx.git
```

Etapas envolvidas (implícitas ao git clone):
 * criação da pasta nginx (mkdir nginx; cd nginx)
 * criação da estrutura da pasta nginx/.git (git init)
 * adição do repositório remoto (git remote add origin …)
 * download do conteúdo do repositório para a pasta nginx/.git (git fetch)
 * cópia dos arquivos para o área de trabalho (git checkout master)


## git fetch

A operação **git fetch** atualiza o repositório local com novos commits ocorridos no repositório remoto.

git fetch não atualiza a área de trabalho e nem faz merge.

## git pull

**git pull** atualiza o repositório local com novos commits do repositório remoto e faz o merge com o branch atual. É uma sequência de git fetch e git merge.

## git push <remote> <branch>

Envia um branch local para um repositório remoto.


## git remote add <remote-name> <url>

Adiciona a url de configuração de um repositório remoto.

```
git remote add gitlab git@gitlab.com:jairo.gubler/treinamento-git.git
```
git push gitlab master
```

