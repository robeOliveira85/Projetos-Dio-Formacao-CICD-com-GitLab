[
Talles Destefani de Souza Valiatti](https://medium.com/@talles.dsv?source=post_page-----cc1d150b7f74--------------------------------)

Apr 20, 2022

·

7 min read













# Fazendo o build de imagens Docker com o Azure Pipelines

![img](https://miro.medium.com/max/700/1*YnwCsE1Biq5vXbye8a5BUA.png)

Fala galera, tudo certo?

Hoje vamos estudar o processo *build* de imagens [Docker](https://docs.docker.com/) com a ajuda do Azure Pipelines. Além disso, iremos ver como enviamos essas imagens ao [Azure Container Registry](https://docs.microsoft.com/en-us/azure/container-registry/) de uma forma segura e simples.

A ideia desse post é simples. Iremos criar ou executar os seguintes itens

- [Azure Container Registry](https://docs.microsoft.com/en-us/azure/container-registry/)
- M[inimal API do .NET](https://docs.microsoft.com/en-us/aspnet/core/tutorials/min-web-api?view=aspnetcore-6.0&tabs=visual-studio)
- [*Dockerfile*](https://docs.docker.com/engine/reference/builder/)
- [Azure Repos](https://docs.microsoft.com/en-us/azure/devops/repos/git/create-new-repo?view=azure-devops)
- [Azure Pipelines](https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started/what-is-azure-pipelines?view=azure-devops)
- Executar o Pipeline para fazer o *build* da imagem Docker (através do [*Dockerfile*](https://docs.docker.com/engine/reference/builder/)) e envio dessa imagem ao Azure Container Registry

Para isso discutiremos os seguintes itens:

- Preparação do ambiente
- Azure Container Registry
- Criação do App
- [*Dockerfile*](https://docs.docker.com/engine/reference/builder/)
- Testes locais
- Service connection
- Criação do Pipeline
- Execução do pipeline
- Limpeza dos recursos
- Conclusão

Vamos lá!

# Preparação do ambiente

Nesse post, vamos precisar que você possua os seguintes itens:

- O .[NET](https://dotnet.microsoft.com/download/dotnet/6.0): Durante a escrita desse post, o .NET 6 é a versão estável, então vamos usá-la.
- [Visual Studio Code](https://code.visualstudio.com/Download)
- [Docker](https://docs.docker.com/get-docker/). A instalação será diferente de acordo com o sistema operacional usado na sua máquina
- [CLI do Azure](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli)
- [Uma *subscription* ativa do Azure](https://tallesvaliatti.com/um-overview-sobre-azure-ad-tenants-e-subscriptions-95ab7f725c17)
- [Um projeto no Azure DevOps](https://docs.microsoft.com/en-us/azure/devops/organizations/projects/create-project?view=azure-devops&tabs=preview-page)

# Azure Container Registry

O [Azure Container Registry](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-intro) é um serviço [PaaS](https://azure.microsoft.com/en-us/overview/what-is-paas/) oferecido pela Microsoft para armazenamento de imagens privadas do Docker . Esse serviço é totalmente integrado com o [*Azure role-based acess control*](https://docs.microsoft.com/en-us/azure/role-based-access-control/overview), portanto, podemos garantir que apenas serviços autorizados possam acessar as imagens Docker criadas para nossos projetos ou para nossa empresa.

Antes de continuar a leitura desse post, recomendo fortemente que você entenda minimamente os conceitos fundamentais do Docker. Leia a [documentação](https://docs.docker.com/)!

Antes de criar o nosso Azure Container Registry, devemos criar um grupo de recursos. Vamos chamá-lo de *“rg-my-app-eastus2”* e como o nome sugere, vamos usar a localização “*eastus2".*

```
# Create a resource group to store container registryaz group create --name rg-my-app-eastus2 --location eastus2
```

![img](https://miro.medium.com/max/700/1*uSwFd18aQW6OBRdxUOvsLA.png)

Com o grupo de recursos pronto, podemos criar o nosso Azure Container Registry com o seguinte comando:

```
az acr create --resource-group rg-my-app-eastus2 \
--name myappcontainerregistryeastus2 \
--sku Basic
```

Observe que utilizamos os seguintes parâmetros:

- *--resource-group*: É o nome do grupo de recursos criado anteriormente
- --*name*: Nome do Azure Container Registry. Utilizei o nome *“myappcontainerregistryeastus2”.* Existe uma limitação quanto ao nome desse recurso.
- --*sku*: [Camada de serviço do Azure Container Registry](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-skus). Utilizei a camada *basic*

Sobre o detalhe do nome do recurso, temos uma regra na documentação oficial:

> The registry name must be unique within Azure, and contain 5–50 alphanumeric characters

Após o comando ter sido executado com sucesso, podemos verificar que o Azure Container Registry foi criado, como mostrado na imagem a seguir:

![img](https://miro.medium.com/max/700/1*3KuEUI6jx81e7FL5TuvGoA.png)

# Criação do App

É hora de criarmos o App. Como o objetivo desse post não é criar um App complexo, e sim estudar conceitos como automatização do processo de *build* de imagens docker, vamos utilizar o próprio App *default* do [minimal API do .NET](https://docs.microsoft.com/en-us/aspnet/core/tutorials/min-web-api?view=aspnetcore-6.0&tabs=visual-studio).

Vamos criar um diretório raiz para nosso projeto.

```
mkdir ContainerRegistryAutomateBuild
```

É hora de inicializar esse App. Ele será colocado dentro de um novo diretório chamado “*App”,* por isso usaremos o parâmetro *“-n App”.*

```
dotnet new webapi -minimal -n App
```

Deverá ser feito apenas uma modificação no código fonte: Habilitar a UI do swagger em ambiente produtivo. Para isso, vamos comentar o seguinte *if*:

![img](https://miro.medium.com/max/325/1*NjMmXkFEsEuHKcq4Spg3Gw.png)

# Dockerfile

Vamos criar o arquivo [*Dockerfile*](https://docs.microsoft.com/en-us/dotnet/core/docker/build-container?tabs=windows#create-the-dockerfile) dentro do diretório *App* do nosso projeto.

![img](https://miro.medium.com/max/700/1*zqmNuoLLVDZPaQetGYuYvQ.png)

<iframe src="https://tallesvaliatti.com/media/53abbb491ad0b7658d526aa39948bb69" allowfullscreen="" frameborder="0" height="369" width="680" title="Dockerfile" class="fo n iq dh bf" scrolling="auto" style="box-sizing: inherit; top: 0px; width: 680px; height: 369px; position: absolute; left: 0px;"></iframe>

Esse *Dockerfile* possui todas as instruções necessárias para a criação da nossa imagem Docker. Recomendo que você leia esse [artigo](https://docs.microsoft.com/en-us/dotnet/core/docker/build-container?tabs=windows#create-the-dockerfile) para aprofundar seus conhecimentos em .NET + Docker!

# Testes locais

Antes de criarmos e executarmos o pipeline, vamos fazer alguns testes locais para garantir que tudo está correto. Iremos executar o comando [Docker build](https://docs.docker.com/engine/reference/commandline/build/) para criar a imagem *“my-app”* a partir do *Dockerfile* criado anteriormente

```
docker build -t my-app -f Dockerfile .
```

Com a imagem criada, já podemos criar um [*container*](https://docs.docker.com/engine/reference/commandline/container/) a partir da imagem *“my-app”.* Vamos utilizar o comando [Docker run](https://docs.docker.com/engine/reference/run/) para essa finalidade:

```
docker run -d -p 80:80 my-app
```

Podemos ver que o container foi criado corretamente.

![img](https://miro.medium.com/max/700/1*bRqb2ONNuG2PKpgV5jcu9Q.png)

E que o App está respondendo.

![img](https://miro.medium.com/max/477/1*XONsciRuWeeuHQPpyJKV7g.png)

# Service connection

Para que o nosso pipeline tenha acesso ao nosso ambiente do Azure (para leitura, edição e criação de recursos), precisaremos criar um item chamado *Service connection.* Recomendo a leitura da [documentação oficial](https://docs.microsoft.com/en-us/azure/devops/pipelines/library/service-endpoints?view=azure-devops&tabs=yaml).

Uma dica para estudo: No fundo, a criação do *Service connection* irá criar um item dentro do Azure chamado [*Service Principal*](https://docs.microsoft.com/en-us/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)*.* Vale o estudo!

Vamos ao menu lateral no canto inferior esquerdo do Azure DevOps e clicar em *“Service connections”.*

![img](https://miro.medium.com/max/298/1*u2bLVkFug2BqIhUnf26M8g.png)

Iremos criar um conexão do tipo *“Docker Registry”.*

![img](https://miro.medium.com/max/518/1*bxUoaJ5DFeSgCcuSABjbKw.png)

Para essa nova conexão, será necessário fornecer os dados do nosso Azure Container Registry criado anteriormente.

![img](https://miro.medium.com/max/527/1*egkweo-DVQtqwjxAIYGjhg.png)

Guarde o valor do nome da conexão, no caso *“my-acr-service-connection”*. Iremos utilizá-la dentro do nosso *pipeline*

# Criação do Pipeline

Vamos voltar ao diretório raiz do nosso projeto. Para criar os comandos do *pipeline,* iremos criar um arquivo chamado *“azure-pipeline.yaml”.*

![img](https://miro.medium.com/max/700/1*WOwiMFfGryfnc1Uq6vGhLA.png)

E temos o seguinte conteúdo do arquivo:

<iframe src="https://tallesvaliatti.com/media/c6b029639c3f8e8953aa612fd2a32d19" allowfullscreen="" frameborder="0" height="677" width="680" title="azure-pipeline.yaml" class="fo n iq dh bf" scrolling="auto" style="box-sizing: inherit; top: 0px; width: 680px; height: 677px; position: absolute; left: 0px;"></iframe>

Basicamente criamos apenas um [*stage*](https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started/key-pipelines-concepts?view=azure-devops#stage)*,* com apenas um [*job*](https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started/key-pipelines-concepts?view=azure-devops#step) e que executa a [*task*](https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started/key-pipelines-concepts?view=azure-devops#task) [*buildAndpush*](https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/build/docker?view=azure-devops#task-inputs)! Eu já escrevi um [post](https://tallesvaliatti.com/deploy-de-arquivos-bicep-com-o-azure-pipelines-61943950a0af) explicando melhor alguns dos conceitos do Azure Pipelines. Boa leitura!

Outros detalhes:

- Utilizamos o valor do *Service connection* criado anteriormente, dentro do parâmetro *containerRegistry* da *task* [*buildAndpush*](https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/build/docker?view=azure-devops#task-inputs)
- A imagem terá o nome de *myapp*
- A imagem terá o versionamento feito com base no valor do *BuildId* da execução do *pipeline.* Isso será feito através do parâmetro *tags*

Recomendo que você leia a documentação oficial do [Azure Pipelines](https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started/what-is-azure-pipelines?view=azure-devops).

Com tudo pronto, devemos criar um [novo Azure Rep](https://docs.microsoft.com/en-us/azure/devops/repos/git/create-new-repo?view=azure-devops)os para levar nosso código fonte ao Azure DevOps. Vamos criar um repositório do tipo git, chamado *“My-App”.*

![img](https://miro.medium.com/max/700/1*8-Wuko_4-vuIp5hdXAt9Eg.png)

![img](https://miro.medium.com/max/500/1*Dh1NLyv5sO1HAUdoiD7sew.png)

Dentro da pasta raiz no nosso projeto, vamos criar um repositório local, adicionar um novo [*remote*](https://git-scm.com/docs/git-remote) e subir nosso código

```
git initdotnet new gitignore
 
git add .git commit -m "First"git remote add origin https://tallesdsv@dev.azure.com/tallesdsv/Blog/_git/My-Appgit push --set-upstream origin master
```

Tudo relacionado ao Azure Repos está concluído. É hora de criarmos um novo *pipeline*.

Ele terá como código fonte o repositório *“My-App”.*

![img](https://miro.medium.com/max/700/1*u5rOGDUnPzRaEfCs3nQ8uQ.png)

![img](https://miro.medium.com/max/700/1*aphg-WC_AiFiQYBp4RAzQQ.png)

Esse *pipeline* terá o arquivo *“Azure-pipelie.yaml”* como base para sua construção.

![img](https://miro.medium.com/max/700/1*IX5B2eqzVjM9LtyxnM29Iw.png)

![img](https://miro.medium.com/max/500/1*L-mCAnzRV_KEuGbt2raGHw.png)

# Execução do pipeline

Vamos executar o *pipeline*!

![img](https://miro.medium.com/max/594/1*-Dj5ZmNHE5HK3cb92tgznQ.png)

Podemos ir ao nosso ambiente do Azure, dentro do grupo de recursos criado, dentro no Azure Container Registry, e ver que a imagem Docker *myapp está* presente e versionada com base no *buildId* da execução do *pipeline.*

![img](https://miro.medium.com/max/700/1*lyOnzc2HJElZK9cnziV_8A.png)

# Limpeza dos recursos

Vamos deletar todos os recursos criados nesse post.

```
az group delete --name rg-my-app-eastus2
```

# Conclusão

Docker é amplamente utilizado em projetos ao redor do mundo. Essa ferramenta traz um série de benefícios as nossas soluções, como: Economia de recursos, facilidade de gerenciamento, ambiente similares, padronização e replicação, etc …

Com certeza iremos estudar mais dessa ferramenta aqui no Blog. Você pode baixar o projeto por esse [link](https://github.com/TallesValiatti/ContainerRegistryAutomateBuild).

Até a próxima, abraços!

Me siga no [LinkedIn](https://www.linkedin.com/in/talles-destefani-de-souza-valiatti-685558174/)!

[Docker](https://medium.com/tag/docker?source=post_page-----cc1d150b7f74---------------docker-----------------)

[Dockerfiles](https://medium.com/tag/dockerfiles?source=post_page-----cc1d150b7f74---------------dockerfiles-----------------)

[Azure Container Registry](https://medium.com/tag/azure-container-registry?source=post_page-----cc1d150b7f74---------------azure_container_registry-----------------)

[Azure Pipelines](https://medium.com/tag/azure-pipelines?source=post_page-----cc1d150b7f74---------------azure_pipelines-----------------)













## [More from tallesvaliatti.com](https://tallesvaliatti.com/?source=post_page-----cc1d150b7f74--------------------------------)

[Follow](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fsubscribe%2Fcollection%2Ftallesvaliatti%2Fcc1d150b7f74&operation=register&redirect=https%3A%2F%2Ftallesvaliatti.com%2Ffazendo-o-build-de-imagens-docker-com-o-azure-pipelines-cc1d150b7f74&collection=tallesvaliatti.com&collectionId=1cfd3aca7f97&source=post_page-----cc1d150b7f74---------------------follow_footer-----------)

Atuo como Tech Lead de uma equipe com foco em .NET, Azure, DevOps e SQL. Sou formado em Engenharia Elétrica, entusiasta por novas tecnologias e tenho 5 anos de experiência em projetos escaláveis com qualidade, segurança e performance. Estou sempre pronto para novos desafios!

[![Talles Destefani de Souza Valiatti](https://miro.medium.com/fit/c/24/24/1*n9a19vHcuMqfSkigq1RKkw.png)](https://medium.com/@talles.dsv?source=post_page-----cc1d150b7f74----0----------------------------)[Talles Destefani de Souza Valiatti](https://medium.com/@talles.dsv?source=post_page-----cc1d150b7f74----0----------------------------)[·Apr 14, 2022](https://tallesvaliatti.com/utilizando-os-segredos-do-azure-key-vault-1142fc1b6e8d?source=post_page-----cc1d150b7f74----0----------------------------)[Utilizando os segredos do Azure Key VaultVamos estudar sobre como podemos utilizar segredos em nossas soluções de nuvem, de uma forma fácil e bastante segura Fala galera, tudo certo? Hoje vamos estudar como podemos guardar os segredos das nossas aplicações em um Azure Key Vault, e acessá-las através de um managed identity. Nesse post discutiremos os…](https://tallesvaliatti.com/utilizando-os-segredos-do-azure-key-vault-1142fc1b6e8d?source=post_page-----cc1d150b7f74----0----------------------------)[Azure Key Vault](https://medium.com/tag/azure-key-vault?source=post_page-----cc1d150b7f74---------------azure_key_vault-----------------)[7 min read](https://tallesvaliatti.com/utilizando-os-segredos-do-azure-key-vault-1142fc1b6e8d?source=post_page-----cc1d150b7f74----0----------------------------)[![Utilizando os segredos do Azure Key Vault](https://miro.medium.com/fit/c/112/112/1*RKKW_Kdq3nYmxL66yXpdGw.png)](https://tallesvaliatti.com/utilizando-os-segredos-do-azure-key-vault-1142fc1b6e8d?source=post_page-----cc1d150b7f74----0----------------------------)Share your ideas with millions of readers.[Write on Medium](https://medium.com/new-story?source=post_page_footer_cta_write-------------------------------------)[![Talles Destefani de Souza Valiatti](https://miro.medium.com/fit/c/24/24/1*n9a19vHcuMqfSkigq1RKkw.png)](https://medium.com/@talles.dsv?source=post_page-----cc1d150b7f74----1----------------------------)[Talles Destefani de Souza Valiatti](https://medium.com/@talles.dsv?source=post_page-----cc1d150b7f74----1----------------------------)[·Mar 31, 2022](https://tallesvaliatti.com/design-pattern-adapter-9eb5adec466d?source=post_page-----cc1d150b7f74----1----------------------------)[Design Pattern: AdapterVamos ver como podemos criar invólucros para classes e serviços legados, deixando-os compatíveis com padrões arquiteturais mais modernos No dia a dia do desenvolvedor, é comum termos que trabalhar com classes ou serviços legados, que muitas vezes são incompatíveis com a arquitetura atual do nosso projeto. …](https://tallesvaliatti.com/design-pattern-adapter-9eb5adec466d?source=post_page-----cc1d150b7f74----1----------------------------)[Design Patterns](https://medium.com/tag/design-patterns?source=post_page-----cc1d150b7f74---------------design_patterns-----------------)[3 min read](https://tallesvaliatti.com/design-pattern-adapter-9eb5adec466d?source=post_page-----cc1d150b7f74----1----------------------------)[![Design Pattern: Adapter](https://miro.medium.com/fit/c/112/112/1*pKJhXBVSfGl_jlsyulgsEQ.png)](https://tallesvaliatti.com/design-pattern-adapter-9eb5adec466d?source=post_page-----cc1d150b7f74----1----------------------------)[![Talles Destefani de Souza Valiatti](https://miro.medium.com/fit/c/24/24/1*n9a19vHcuMqfSkigq1RKkw.png)](https://medium.com/@talles.dsv?source=post_page-----cc1d150b7f74----2----------------------------)[Talles Destefani de Souza Valiatti](https://medium.com/@talles.dsv?source=post_page-----cc1d150b7f74----2----------------------------)[·Mar 25, 2022](https://tallesvaliatti.com/deploy-de-arquivos-bicep-com-o-azure-pipelines-61943950a0af?source=post_page-----cc1d150b7f74----2----------------------------)[Deploy de arquivos bicep com o Azure PipelinesVamos estudar como podemos fazer o deploy de arquivos bicep de uma forma automática, eficiente e segura Fala galera, tudo certo? Nesse blog, recorrentemente utilizamos o bicep para fazer o deploy das infraestruturas utilizadas nos posts. A infraestrutura com código, além de ser uma forma simples e amigável para nós…](https://tallesvaliatti.com/deploy-de-arquivos-bicep-com-o-azure-pipelines-61943950a0af?source=post_page-----cc1d150b7f74----2----------------------------)[Bicep](https://medium.com/tag/bicep?source=post_page-----cc1d150b7f74---------------bicep-----------------)[9 min read](https://tallesvaliatti.com/deploy-de-arquivos-bicep-com-o-azure-pipelines-61943950a0af?source=post_page-----cc1d150b7f74----2----------------------------)[![Deploy de arquivos bicep com o Azure Pipelines](https://miro.medium.com/fit/c/112/112/1*roz9L4k-9km5teWImUA09g.png)](https://tallesvaliatti.com/deploy-de-arquivos-bicep-com-o-azure-pipelines-61943950a0af?source=post_page-----cc1d150b7f74----2----------------------------)[![Talles Destefani de Souza Valiatti](https://miro.medium.com/fit/c/24/24/1*n9a19vHcuMqfSkigq1RKkw.png)](https://medium.com/@talles.dsv?source=post_page-----cc1d150b7f74----3----------------------------)[Talles Destefani de Souza Valiatti](https://medium.com/@talles.dsv?source=post_page-----cc1d150b7f74----3----------------------------)[·Mar 17, 2022](https://tallesvaliatti.com/criando-data-transfer-objects-com-o-automapper-981f4c11b6b0?source=post_page-----cc1d150b7f74----3----------------------------)[Criando Data Transfer Objects com o AutoMapperIremos estudar como podemos mudar o formato dos dados retornados da nossa Web Api com o AutoMapper Fala galera, tudo certo? Hoje estudaremos o conceito de DTO (Data Transfer Object) e como podemos implementá-lo com o uso do AutoMapper. Nesse post vamos discutir os seguintes itens: Preparação do ambiente Criação…](https://tallesvaliatti.com/criando-data-transfer-objects-com-o-automapper-981f4c11b6b0?source=post_page-----cc1d150b7f74----3----------------------------)[Dto](https://medium.com/tag/dto?source=post_page-----cc1d150b7f74---------------dto-----------------)[4 min read](https://tallesvaliatti.com/criando-data-transfer-objects-com-o-automapper-981f4c11b6b0?source=post_page-----cc1d150b7f74----3----------------------------)[![Criando Data Transfer Objects com o AutoMapper](https://miro.medium.com/fit/c/112/112/1*TxKOROr11RHJ7HNz5WjbhQ.png)](https://tallesvaliatti.com/criando-data-transfer-objects-com-o-automapper-981f4c11b6b0?source=post_page-----cc1d150b7f74----3----------------------------)[![Talles Destefani de Souza Valiatti](https://miro.medium.com/fit/c/24/24/1*n9a19vHcuMqfSkigq1RKkw.png)](https://medium.com/@talles.dsv?source=post_page-----cc1d150b7f74----4----------------------------)[Talles Destefani de Souza Valiatti](https://medium.com/@talles.dsv?source=post_page-----cc1d150b7f74----4----------------------------)[·Mar 9, 2022](https://tallesvaliatti.com/upload-de-arquivos-para-o-azure-blob-storage-6c6491fecdaf?source=post_page-----cc1d150b7f74----4----------------------------)[Upload de arquivos para o Azure Blob StorageVamos fazer o upload de arquivos para o Azure Blob Storage através de uma aplicação .NET Fala galera, tudo certo? Hoje vamos estudar o Azure Blob Storage e ver como podemos fazer o upload de arquivos através de uma aplicação .NET. Nesse post discutiremos os seguintes itens: Preparação do ambiente …](https://tallesvaliatti.com/upload-de-arquivos-para-o-azure-blob-storage-6c6491fecdaf?source=post_page-----cc1d150b7f74----4----------------------------)[Blob Storage](https://medium.com/tag/blob-storage?source=post_page-----cc1d150b7f74---------------blob_storage-----------------)[7 min read](https://tallesvaliatti.com/upload-de-arquivos-para-o-azure-blob-storage-6c6491fecdaf?source=post_page-----cc1d150b7f74----4----------------------------)[![Upload de arquivos para o Azure Blob Storage](https://miro.medium.com/fit/c/112/112/1*w20268-c5VOhr_FFkH2z9A.png)](https://tallesvaliatti.com/upload-de-arquivos-para-o-azure-blob-storage-6c6491fecdaf?source=post_page-----cc1d150b7f74----4----------------------------)

[Read more from tallesvaliatti.com](https://tallesvaliatti.com/?source=post_page-----cc1d150b7f74--------------------------------)