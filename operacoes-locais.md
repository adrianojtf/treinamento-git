# Operações Locais

![Operações Locais](/imagens/git-areas.png)

Conforme a imagem acima, o git possui 3 áreas onde os arquivos são armazenados:
 * repositório local: na pasta .git ficam armazenados todas as informações sobre os arquivos que compõe o projeto e todas as revisões existentes destes arquivos. Para transferir arquivos para o repositório é necessário utilizar a operação **git commit** que gera um SHA-1 dos arquivos e cria um **commit**.
 * área de staging: é uma área provisória para indicar quais arquivos e/ou pastas entrarão no próximo commit. Arquivos são enviados para a área de staging através dos comandos **git add** e **git rm**.
 * área de trabalho: é o conteúdo onde o usuário/programador visualiza e altera os arquivos de determinada revisão. Através do comando **git checkout** é possível alternar rapidamente os arquivos do workspace entre várias revisões do repositório. 
 
Exemplo da adição de um arquivo na área de staging e posterior geração de uma versão. 
É importante observar que todas estas operações são locais no repositório.

```
echo "# TESTE" >> README.md
git status
git add README.md
git commit -m 'adicionando arquivo'
```

