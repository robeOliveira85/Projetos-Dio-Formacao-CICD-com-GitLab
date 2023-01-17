### CRIANDO E ENVIANDO IMAGENS DOCKER AUTOMATICAMENTE

[9 de junho de 2021](https://smarti.blog.br/criando-e-enviando-imagens-docker-automaticamente/)[Paulo Cezar](https://smarti.blog.br/author/paulorpc/)[Paulo Cezar](https://smarti.blog.br/author/paulorpc/)[Automação](https://smarti.blog.br/category/automacao/), [Software](https://smarti.blog.br/category/software/)[Automatização](https://smarti.blog.br/tag/automatizacao/), [Docker](https://smarti.blog.br/tag/docker/), [Docker Hub](https://smarti.blog.br/tag/docker-hub/), [Docker Image](https://smarti.blog.br/tag/docker-image/), [Dockerfile](https://smarti.blog.br/tag/dockerfile/), [dockerfile-maven-plugin](https://smarti.blog.br/tag/dockerfile-maven-plugin/), [Java](https://smarti.blog.br/tag/java/), [Maven](https://smarti.blog.br/tag/maven/), [Software](https://smarti.blog.br/tag/software/)

[![Share on LinkedIn](https://smarti.blog.br/wp-content/plugins/simple-share-buttons-adder/buttons/somacro/linkedin.png)](http://www.linkedin.com/shareArticle?mini=true&url=https://smarti.blog.br/criando-e-enviando-imagens-docker-automaticamente/)[![Share on Facebook](https://smarti.blog.br/wp-content/plugins/simple-share-buttons-adder/buttons/somacro/facebook.png)](http://www.facebook.com/sharer.php?u=https://smarti.blog.br/criando-e-enviando-imagens-docker-automaticamente/)[![Tweet about this on Twitter](https://smarti.blog.br/wp-content/plugins/simple-share-buttons-adder/buttons/somacro/twitter.png)](http://twitter.com/share?url=https://smarti.blog.br/criando-e-enviando-imagens-docker-automaticamente/&text=Criando e Enviando Imagens Docker Automaticamente )[![Email this to someone](https://smarti.blog.br/wp-content/plugins/simple-share-buttons-adder/buttons/somacro/email.png)](mailto:?subject=Criando e Enviando Imagens Docker Automaticamente&body= https://smarti.blog.br/criando-e-enviando-imagens-docker-automaticamente/)
Compartilhe conhecimento... ![😀](https://s.w.org/images/core/emoji/13.0.1/svg/1f600.svg)

## Criação e Envio de Imagens Docker Automaticamente em Ambientes Java

Se você já leu o post "[O que é Docker e seus Comandos Básicos](https://smarti.blog.br/entenda-o-que-e-docker/)", já entendeu o que é e como funciona o **Docker** e está pronto para entender como usá-lo em conjunto com projetos **Java** / **Maven** para que possamos criar Imagens Docker automaticamente**.** Além de criar as Imagens Docker automaticamente, também abordaremos como automatizar o processo de envio da imagem ao Docker Hub através de *plugins* de integração com o maven. São estes os dois métodos apresentados: (i) utilizando Docker e Dockerfile para criar Imagens Docker e; (ii) utilizando um *plugin* para integrar o Maven com o Docker para criar e enviar a Docker Image ao Docker Hub automaticamente.

Nosso cenário é o mais simples possível para não haver distrações, mantendo o foco em entender as etapas necessárias para criar uma Imagem Docker (imutável), disponibilizar num repositório online (que pode ser público ou privado) e executar a imagem em um contêiner de forma simples, rápida e automática. A aplicação será empacotada no formato WAR tradicional e executada num servidor de aplicação Apache Tomcat. O projeto foi desenvolvido com o framework *Spring Boot,* contendo dois serviços [REST](http://smarti.blog.br/api-rest-principios-boas-praticas-para-arquiteturas-restful/). Para criar uma Imagem Docker do cenário acima de forma manual não é difícil, mas exige a execução de algumas linhas de comando, que é, no mínimo, uma perda de tempo. Segue o link do projeto no github: [dockerfile-maven-api](https://github.com/Paulorpc/dockerfile-maven-api).

### Dockerfile

O Docker possui um recurso para auxiliar a construção de imagens através de um arquivo chamado **Dockerfile**. Este arquivo armazena um conjunto de instruções e cada vez que o arquivo é processado, é construída uma imagem com base nessas informações. Todas essas instruções poderiam ser executadas através de linhas de comandos. No entanto, fazer o *build* através do Dockerfile torna mais simples e produtivo esse processo. Abaixo segue o exemplo de um *Dockerfile* e uma breve explicação.

FROM <imagem>

EXPOSE <porta>

RUN <cmd_shell>

COPY <origem> <destino>

CMD ["executable", "param1", "param2"]

Vamos entender um pouco melhor cada instrução. Para mais detalhes ou instruções adicionais, veja a [documentação](https://docs.docker.com/engine/reference/builder/).

- **FROM:** indica que a nova imagem será criada a partir de uma imagem base, a qual os comando subsequentes serão executados;
- **EXPOSE** (opcional): uma espécie de documentação para quem administra o contêiner, não a publicação da porta de fato;
- **RUN** (opcional): executará comandos sobre a imagem atual, onde a imagem resultante será usada para a próxima etapa no Dockerfile;
- **COPY:** copia arquivos ou diretórios do caminho de origem e os adiciona ao sistema de arquivos do contêiner no caminho de destino;
- **CMD:** tem como objetivo principal fornecer padrões para um contêiner em execução. A instrução pode ser escrita no formato shell ou como array json, que é o preferido para o CMD.

Para gerar o Dockerfile, basta criar um arquivo na raiz do projeto com o nome *Dockerfile* e copiar as instruções abaixo.

FROM tomcat:9.0.20-jre8-alpine

EXPOSE 8080

RUN rm -rf /usr/local/tomcat/webapps/*

COPY ./src/main/resources/tomcat/conf/* /usr/local/tomcat/conf/

COPY ./target/dockerfile-maven-api-1.0.war /usr/local/tomcat/webapps/smarti.war

CMD ["catalina.sh","run"]

Já vimos o que significa cada comando, mas vamos entender agora o que o Docker vai processar em cada linha:

- **Linha 1:** a imagem final será criada a partir de uma imagem do Tomcat que já existe. Por este motivo, em nenhum momento precisamos nos preocupar com sua implementação;
- **Linha 2:** estamos documentando que a porta 8080 é a porta de acesso à aplicação Java no contêiner;
- **Linha 3:** é executado o comando shell "remove" para remover qualquer aplicação que possa existir na pasta webapps da imagem base, por exemplo, o manager. Caso deseje manter essas aplicações, basta não incluir esta instrução;
- **Linha 4:** estamos copiando um arquivo de configuração do Tomcat que armazenamos em uma pasta do projeto para o Tomcat instalado na imagem. Na verdade, o arquivo xml disponível no projeto é o arquivo *default* de configuração do Tomcat e, inclusive, já existe na imagem base do Tomcat (indicada na linha 1). Porém, adicionamos essa instrução para deixar evidente que é possível transferir diversos dados (incluindo configurações) para a imagem durante o *build* de uma forma muito simples.
- **Linha 5:** é feito a cópia do pacote WAR da aplicação, gerado por default na pasta *target* do projeto, para a pasta webapps do Tomcat. Esse processo é justamente o que permite que nossa API Java possa ser executada quando rodarmos o contêiner da imagem. Também estamos renomeando o arquivo para que a API seja publicada com um nome de acesso fácil.
- **Linha 6:** estamos passando os parâmetros para inicialização do Tomcat sempre que o contêiner for executado.

 

### I. Docker Image usando Dockerfile e *build* manual

Considero esse processo semi-automático, pois é necessário executar manualmente a linha de comando de *build* do Docker. No entanto, não será necessário executar uma série de linhas de comandos para construção da imagem, pois essas instruções estão armazenadas no Dockerfile*, que* serão lidas e processadas durante o processo de construção (*build)* da imagem.

#### Execução

Uma vez que o Dockerfile já foi criado e configurado, agora é preciso gerar o pacote (.WAR) da aplicação. Há diversas formas de fazer este procedimento, acredito que a mais simples é executando o comando Maven abaixo através do terminal, na pasta do projeto:

$ mvn clean package

Neste momento, o pacote WAR da API Java foi criado na pasta *target* do projeto. Agora, basta executar o comando de *build* do Docker para gerar a imagem. Caso a imagem base (tomcat:9.0.20-jre8-alpine) não seja localizada no host local, o Docker fará o download automático do repositório público, o Docker Hub. Lembrando que a imagem é constituída por 

<repositório>:<tag>

.



$ docker build -t imagemTeste:v1 .

**Obs:** Atente-se que há um **ponto final** no final da linha de comando do *build*. Ele deve ser adicionado ao comando, pois indica o caminho onde encontrar os arquivos para o “contexto” do *build*.

Pronto, a imagem já foi criada e já poderá rodar o contêiner! ![🙂](https://s.w.org/images/core/emoji/13.0.1/svg/1f642.svg) . Para isso, veja a seção **"Rodando o contêiner e Testando a Aplicação"**.

### II. Docker Image automática com *Plugin* de Integração Maven/Docker

Existem algumas opções de *plugins* com a finalidade de gerar Imagens de Docker e OCI para java, como: **[jib-maven-plugin](https://github.com/GoogleContainerTools/jib/tree/master/jib-maven-plugin), [dockerfile-maven](https://github.com/spotify/dockerfile-maven), [fabric8io](http://dmp.fabric8.io/)** e outros**.** O Jib, do Google é uma opção interessante para quem dispensa o uso do Dockerfile e também de uma configuração funcional do Docker. Neste artigo optamos pelo **dockerfile-maven-plugin**, que é um *plugin* do Spotfy bastante popular e que tem como premissa o uso do Dockerfile e necessita de uma configuração funcional do Docker. Acredito que o uso do Dockerfile torna o projeto mais simples de configurar e mais flexível, possibilitando a criação das imagens utilizando o *plugin* ou não. Este *plugin* requer pelo menos Java 7 e o Maven 3.

#### Configuração do dockerfile-maven-plugin

Considerando que já temos o Dockerfile criado e configurado, para configurar o dockerfile-maven-plugin em seu projeto, basta adicionar o código abaixo no POM.xml, dentro da tag **<plugins>**. A configuração é simples, mas caso precise ir além, há mais detalhes na [página de uso do plugin](https://github.com/spotify/dockerfile-maven/blob/master/docs/usage.md). É importante estar atento nas especificações: **<goal>, <repository>,** **<tag>, <username> e <password>**. No exemplo abaixo estamos configurando o *plugin* para realizar dois objetivos: (i) a construção (*build)* da imagem e, (ii) o envio (*push*) da imagem para o Docker Hub. Claro, para isso precisa ter criado sua conta na [plataforma](https://hub.docker.com/signup). ![😉](https://s.w.org/images/core/emoji/13.0.1/svg/1f609.svg)

Os marcadores *repository* e *tag* são responsáveis por gerar o nome da imagem no formato mencionado acima  

<repository>:<tag>

 e, também, para indicar qual o repositório será disponibilizada a imagem no **Docker Hub**. Segundo a configuração abaixo, o repositório e tag são gerados com base em propriedades do próprio POM.xml do [projeto](https://github.com/Paulorpc/dockerfile-maven-api). Já os marcadores de *usuário* e *senha* para acesso ao repositório, são lidos de variáveis de ambiente do host para evitar expor dados sensíveis no código fonte, ou seja, basta você incluir as variáveis de ambiente em seu sistema operacional e já funcionará. No entanto, se quiser digitar o código e senha SOMENTE para teste, vá em frente. Também há outras formas de autenticação usando o settings.xml do maven e config.json do docker que não entraremos em detalhes.



<plugin>  <groupId>com.spotify</groupId>  <artifactId>dockerfile-maven-plugin</artifactId>  <version>${dockerfile-maven-plugin.version}</version>  <executions>    <execution>      <id>default</id>      <goals>        <goal>build</goal>        <goal>push</goal>      </goals>    </execution>  </executions>  <configuration>    <username>${env.DOCKERHUB_USERNAME}</username>    <password>${env.DOCKERHUB_PASSWORD}</password>    <repository>${dockerhub.repository}</repository>    <tag>${project.version}</tag>    <skipDockerInfo>true</skipDockerInfo>  </configuration></plugin>

Uma observação importante que vale ser mencionada é que vamos utilizar a fase **deploy** do ciclo de vida de *build* do Maven para o envio da imagem ao Docker Hub (explicado adiante), porém pode ser que seu projeto não faça deploy. Portanto, irá faltar a configuração necessária para tal e uma exceção pode ser lançada. Para evitar este problema, basta adicionar a propriedade abaixo em seu POM.xml.

<**maven.deploy.skip**>true</**maven.deploy.skip**>

#### Execução

Por incrível que pareça, o mais complexo já foi feito... a configuração. Agora, basta executar a fase de ***package*** ou ***deploy*** do Maven, conforme melhor lhe convir. Por exemplo:

- Gerar a Imagem Docker

  :

  Caso queira compilar o projeto e apenas gerar a imagem (

  goal 

  build)

  , ou seja, a imagem não será enviada para sua conta Docker Hub, então basta executar:

  

  mvn clean package;

- Gerar e publicar a Imagem Docker:

  Agora, caso deseje compilar, fazer o

   

  build

   

  da imagem e enviá-la à sua conta Docker Hub (

  goal

  push

  ), então basta executar:

  

  mvn clean deploy;

- Gerar ou publicar a Imagem Docker:

  Você ainda tem a opção de fazer o

   

  build

   

  ou

   

  push

   

  diretamente através dos comandos:

  

  mvn dockerfile:build;

  \# ou 

  mvn dockerfile:push;

Vale lembrar que estou abstraindo ao máximo as informações de execução, pois envolve detalhes do ciclo de vida de *build* do Maven que não é objeto de interesse neste artigo, mas caso queira ir um pouco além, fica como sugestão que veja a documentação do [maven](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html) e do [dockerfile-maven-plugin](https://github.com/spotify/dockerfile-maven).

Pronto, agora é só rodar o contêiner e ser feliz! ![🙂](https://s.w.org/images/core/emoji/13.0.1/svg/1f642.svg) . Veja abaixo como conferir que tudo está funcionando.

## Rodando o contêiner e Testando a Aplicação

Abaixo segue três comando, o primeiro para verificar se a imagem foi de fato gerada, o segundo para rodar o contêiner da imagem no Docker e o terceiro para confirmar que a imagem está sendo executada. O sinalizador **-p** no comando **docker run** faz o mapeamento de portas entre endereço local do seu computador e o endereço apontado no contêiner. Caso queira executar diversos contêineres da mesma aplicação, basta alterar a porta local, por exemplo: **8080**:8080; **8081**:8080, etc. Ao rodar o último comando, deverá ser listado o contêiner de nome **smarti** que acabou de ser inicializado.

$ docker image ls

$ docker run --name smarti -d -p 8080:8080 smarti/dockerfilemavenapi:1.0

$ docker ps

Pronto, simples e fácil! Está tudo rodando. Agora para verificar os serviços da API, faça as requisições como se a API estivesse rodando num servidor tomcat local normalmente.

**Obs:** Lembre-se que a porta local de acesso foi definida no comando  

docker run -p

 e o nome da aplicação foi definido na instrução **COPY** do Dockerfile.



### Acessando o URL pelo navegador (Requisição GET)

curl -X GET http://localhost:8080/smarti/

![Teste navegador da API Java rodando em Docker Container](http://smarti.blog.br/wp-content/uploads/2021/03/smarti_docker_java_api_url.png)

**Figura 1**. Teste da API Java rodando no Contêiner Docker através do navegador.

### Através de uma requisição POST

curl -X POST http://localhost:8080/smarti/hello \

--header 'Content-Type: application/json' \

--data '{"nome":""}';

![Teste POST da API Java rodando em Docker Container](http://smarti.blog.br/wp-content/uploads/2021/03/smarti_docker_java_api_postman-1024x585.png)

**Figura 2.** Teste da API Java rodando no Contêiner Docker através de uma requisição POST.

### 

[![Share on LinkedIn](https://smarti.blog.br/wp-content/plugins/simple-share-buttons-adder/buttons/somacro/linkedin.png)](http://www.linkedin.com/shareArticle?mini=true&url=https://smarti.blog.br/criando-e-enviando-imagens-docker-automaticamente/)[![Share on Facebook](https://smarti.blog.br/wp-content/plugins/simple-share-buttons-adder/buttons/somacro/facebook.png)](http://www.facebook.com/sharer.php?u=https://smarti.blog.br/criando-e-enviando-imagens-docker-automaticamente/)[![Tweet about this on Twitter](https://smarti.blog.br/wp-content/plugins/simple-share-buttons-adder/buttons/somacro/twitter.png)](http://twitter.com/share?url=https://smarti.blog.br/criando-e-enviando-imagens-docker-automaticamente/&text=Criando e Enviando Imagens Docker Automaticamente )