[Voltar](README.md)

# git submodule

Submódulos no git tem uma função semelhante ao **svn externals**, mas com características próprias.


# Adicionando um submódulo a um projeto

```
git submodule add $repository $sub_dir
````

```
git submodule add -b build-64bits git@gitlab.digitro.com.br:crazylifeteam/media-streaming-server.git media-streaming-server
```

# Baixar as dependências após um git clone

````
git submodule init
git submodule update
```

Submódulos e suas alterações não são transportadas em trocas de contexto, cada branch controla individualmente seus submódulos. https://git-scm.com/book/pt-br/v1/Ferramentas-do-Git-Subm%C3%B3dulos	

[Voltar](README.md)