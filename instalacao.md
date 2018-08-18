# Instalação

[https://git-scm.com/downloads](https://git-scm.com/downloads)

# Configurações

## Configurações do projeto

Arquivo: .git/config

```
git config --local
```

## Configurações do usuário

Arquivo: ~/.gitconfig ou ~/.config/git/config

```
git config --global
```

### Configurações Globais do Sistema

Arquivo: /etc/gitconfig 

```
git config --system
```

Exemplos:

```
git config --global user.name “Fulano de Tal”
git config --global user.email “fulano.de.tal@dominio.com”
git config --global core.editor “vim”
git config --global merge.tool vimdiff
git config --global merge.tool meld
```