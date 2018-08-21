[Voltar](README.md)

# Instalação

[https://git-scm.com/downloads](https://git-scm.com/downloads)

## Sugestões Adicionais de Instalação

Windows:
 * meld: http://meldmerge.org/
 * Visual Studio Code: https://code.visualstudio.com/
 * winmerge: http://winmerge.org/downloads/

Linux:
 * meld: http://meldmerge.org/
 * Visual Studio Code: https://code.visualstudio.com/

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

----
## Listando Configurações

```
git config --global --list
```

```
$ git config --global --list
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
user.name=Jairo Gubler
user.email=jairo.gubler@gmail.com
merge.tool=meld
merge.tool=C:\ProgramData\Microsoft\Windows\Start
diff.tool=meld
diff.tool=C:\ProgramData\Microsoft\Windows\Start
diff.guitool=meld
credential.helper=manager
mergetool.meld.path=C:\Program Files (x86)\Meld\Meld.exe
```

[Voltar](README.md)