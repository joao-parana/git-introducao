# git-introducao

## Introdução ao Uso do GIT

### Sua Identidade
A primeira coisa que você deve fazer após instalar o Git é definir o seu nome de usuário e 
endereço de e-mail. Isso é muito importante porque todos os commits no Git utilizam essas 
informações que são anexadas nos commits que você realiza. Veja exemplo com meu nome e e-mail abaixo:

    git config --global user.name "João Antonio Ferreira (Paraná)"
    git config --global user.email joao.parana@gmail.com
    
Você só precisará fazer isso uma vez (opção --global), pois o Git sempre usará essa informação para 
qualquer comando git que você use no sistema.  

### Verificando Suas Configurações
Caso você queira verificar suas configurações, você pode utilizar o comando git config --list para listar todas as configurações que o Git encontrar num dado momento:

    git config --list
    
### Obtendo Ajuda
Caso você precise de ajuda usando o Git, exitem três formas de se obter ajuda das páginas de manual (manpage) para quaisquer comandos do Git. A forma mais simples é digitar :

    git help <verbo>  
    
Exemplo

    git help status
    
## Obtendo um Repositório Git
Você pode obter um projeto Git utilizando duas formas diferentes. 
1. A primeira faz uso de um projeto ou diretório existente e o importa para o Git. 
2. A segunda clona um repositório Git existente a partir de outro servidor, por exemplo, [github.com](http://github.com).

Segue abaixo uma descrição das duas opções: 

## Opção 1

### Inicializando um Repositório em um Diretório Existente
Caso você esteja iniciando o monitoramento de um projeto existente com Git, você precisa ir para o diretório do projeto e digitar

    git init
    
Isso cria um novo subdiretório chamado .git que contem todos os arquivos necessários de seu repositório — um esqueleto de repositório Git. Neste ponto, nada em seu projeto é monitorado. (Veja o Capítulo 9 para maiores informações sobre quais arquivos estão contidos no diretório .git que foi criado.)

Caso você queira começar a controlar o versionamento dos arquivos existentes (diferente de um diretório vazio), você provavelmente deve começar a monitorar esses arquivos e fazer um commit inicial. Você pode realizar isso com poucos comandos git add que especificam quais arquivos você quer monitorar, seguido de um commit:

    touch README.md
    vi README.md

    git add *.html
    git add README.md
    git commit -m 'versão Inicial do meu projeto'
    
Suponha que você tenha criado um Repositório no GitHub para seu projeto. Suponha que o repositório se chame `git-introducao` 

Neste caso o comando abaixo irá enviar as alterações objeto do commit para o repositório remoto.

    git remote add origin https://github.com/joao-parana/git-introducao.git
    git push -u origin master

Bem, nós iremos repassar esses comandos mais a frente. Neste ponto, você tem um repositório Git com um README.md e arquivos HTML monitorados em um commit inicial. Além disso os arquivos "comitados" estão armazenados seguramente em servidor remoto.

## Opcão 2

### Clonando um Repositório Existente
Caso você queira copiar um repositório Git já existente — por exemplo, um projeto que você queira contribuir — o comando necessário é git clone. Caso você esteja familiarizado com outros sistemas VCS, tais como Subversion, você perceberá que o comando é clone e não checkout. Essa é uma diferença importante — Git recebe uma cópia de quase todos os dados que o servidor possui. Cada versão de cada arquivo no histórico do projeto é obtida quando você roda git clone. De fato, se o disco do servidor ficar corrompido, é possível utilizar um dos clones em qualquer cliente para reaver o servidor no estado em que estava quando foi clonado (você pode perder algumas características do servidor, mas todos os dados versionados estarão lá — veja o Capítulo 4 para maiores detalhes).

Você clona um repositório com git clone [url]. Por exemplo, caso você queria clonar a biblioteca Git do Ruby chamada Grit, você pode fazê-lo da seguinte forma:

    git clone https://github.com/joao-parana/git-introducao.git
Isso cria um diretório chamado grit, inicializa um diretório .gitdentro deste, obtém todos os dados do repositório e verifica a cópia atual da última versão. Se você entrar no novo diretório grit, você verá todos os arquivos do projeto nele, pronto para serem editados ou utilizados. Caso você queira clonar o repositório em um diretório diferente de grit, é possível especificar esse diretório utilizando a opção abaixo:

    git clone https://github.com/joao-parana/git-introducao.git meuEstudoGit
    
Este comando faz exatamente a mesma coisa que o anterior, mas o diretório alvo será chamado `meuEstudoGit`.

O Git possui diversos protocolos de transferência que você pode utilizar. O exemplo anterior utiliza o protocolo https://, mas você também pode usar git(s):// ou user@server:/path.git, que utiliza o protocolo de transferência SSH. 

### Gravando Alterações no Repositório
Você tem um repositório Git e um checkout ou cópia funcional dos arquivos para esse projeto. Você precisa fazer algumas mudanças e fazer o commit das partes destas mudanças em seu repositório cada vez que o projeto atinge um estado estavel no qual você queira gravar. Por exemplo, após implementar alguma funcionalidade nova e testa-la com sucesso.

Lembre-se que cada arquivo em seu diretório de trabalho pode estar em um de dois estados: 

* monitorado 
* não monitorado 

Arquivos monitorados são arquivos que estavam no último snapshot (fotografia); podendo estar inalterados, modificados ou selecionados. 

Arquivos não monitorados são todo o restante — qualquer arquivo em seu diretório de trabalho que não estava no último snapshot e também não estão em sua área de seleção. 

Quando um repositório é inicialmente clonado, todos os seus arquivos estarão monitorados e inalterados porque você simplesmente os obteve e ainda não os editou.

Conforme você edita esses arquivos, o Git passa a vê-los como modificados, porque você os alterou desde seu último commit.

Você seleciona esses arquivos modificados e então faz o commit de todas as alterações selecionadas. Este ciclo se repete indefinidamente. Este ciclo é apresentado na abaixo.

![Ciclo de Vida](18333fig0201-tn.png)


