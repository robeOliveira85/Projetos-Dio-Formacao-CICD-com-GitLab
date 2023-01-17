[Learn](https://learn.microsoft.com/pt-pt/) [Azure](https://learn.microsoft.com/pt-pt/azure/) [Programador](https://learn.microsoft.com/pt-pt/azure/developer/) [Jenkins](https://learn.microsoft.com/pt-pt/azure/developer/jenkins/) 

[Ler em inglês](https://learn.microsoft.com/en-us/azure/developer/jenkins/pipeline-with-github-and-docker)Guardar

<details class="popover popover-right" id="article-header-page-actions-overflow" style="box-sizing: inherit; outline-color: inherit; display: inline-block; position: relative;"><summary class="justify-content-flex-start button button-clear button-sm button-primary" aria-label="Mais ações" style="box-sizing: inherit; outline-color: inherit; display: inline-flex; cursor: pointer; min-height: 2.25em; appearance: none; box-shadow: none; vertical-align: top; border: 1px solid rgba(0, 0, 0, 0); border-radius: 0.125rem; justify-content: center; align-items: center; padding-block: calc(0.375em - 1px); padding-inline: 0.75em; font-size: 0.875rem; line-height: 1.5; position: relative; user-select: none; background-color: rgba(0, 0, 0, 0); color: var(--theme-primary-base); text-align: center; font-weight: 600; text-decoration: none; list-style: none;"><span class="icon" aria-hidden="true" style="box-sizing: inherit; outline-color: inherit; justify-content: center; align-items: center; display: inline-flex; width: 1em; height: 1em; margin: 0px;"><span class="docon docon-more-vertical" style="box-sizing: inherit; outline-color: inherit; font-family: docons; font-size: inherit; speak: none; font-variant: normal; text-transform: none; text-align: center; direction: ltr; -webkit-font-smoothing: antialiased; font-style: normal; font-weight: 400; line-height: 16px; display: inline-block;"></span></span></summary><div class="popover-content padding-none" style="box-sizing: inherit; outline-color: inherit; padding: 1rem; width: 224px; border: 1px solid var(--theme-border); background-color: var(--theme-body-background); box-shadow: 0 6.4px 14.4px 0 var(--theme-box-shadow-medium),0 1.2px 3.6px 0 var(--theme-box-shadow-light); z-index: 1060; border-radius: 0.25rem; margin-block-start: 0.5rem; position: absolute; inset-inline-end: 0px;"><button class="button button-block button-clear button-sm justify-content-flex-start has-inner-focus" title="Imprimir" type="button" aria-label="Imprimir" data-bi-name="print" data-page-action-item="overflow-all" data-popover-close="" data-print-page="" data-check-hidden="true" style="box-sizing: inherit; outline-color: inherit; margin: 0px; font-family: inherit; font-size: 0.875rem; line-height: 1.5; overflow: visible; text-transform: none; appearance: button; color: currentcolor; background-color: rgba(0, 0, 0, 0); cursor: pointer; min-height: 2.25em; box-shadow: none; vertical-align: top; border: 1px solid rgba(0, 0, 0, 0); border-radius: 0.125rem; justify-content: center; align-items: center; padding-block: calc(0.375em - 1px); padding-inline: 0.75em; display: flex; position: relative; user-select: none; text-align: center; font-weight: 600; text-decoration: none; width: 222px;"><span class="icon" aria-hidden="true" style="box-sizing: inherit; outline-color: inherit; justify-content: center; align-items: center; display: inline-flex; width: 1em; height: 1em; margin-inline-end: 0.375em;"><span class="docon docon-print" style="box-sizing: inherit; outline-color: inherit; font-family: docons; font-size: inherit; speak: none; font-variant: normal; text-transform: none; text-align: center; direction: ltr; -webkit-font-smoothing: antialiased; font-style: normal; font-weight: 400; line-height: 16px; display: inline-block;"></span></span><span style="box-sizing: inherit; outline-color: inherit;"></span></button><div aria-hidden="true" class="margin-none border-top" data-page-action-item="overflow-all" style="box-sizing: inherit; outline-color: inherit; border-block-start: 1px solid var(--theme-border) !important; margin: 0px !important;"></div><a class="button button-clear button-sm has-inner-focus button-block text-decoration-none justify-content-flex-start share-twitter" data-bi-name="twitter" data-page-action-item="overflow-all" href="https://twitter.com/intent/tweet?original_referer=https%3A%2F%2Flearn.microsoft.com%2Fpt-pt%2Fazure%2Fdeveloper%2Fjenkins%2Fpipeline-with-github-and-docker%3FWT.mc_id%3Dtwitter&amp;text=Tutorial%20-%20Criar%20um%20oleoduto%20Jenkins%20usando%20GitHub%20e%20Docker%20%7C%20Microsoft%20Learn&amp;tw_p=tweetbutton&amp;url=https%3A%2F%2Flearn.microsoft.com%2Fpt-pt%2Fazure%2Fdeveloper%2Fjenkins%2Fpipeline-with-github-and-docker%3FWT.mc_id%3Dtwitter" style="box-sizing: inherit; outline-color: inherit; color: currentcolor; cursor: pointer; overflow-wrap: break-word; text-decoration: none; background-color: rgba(0, 0, 0, 0); outline-style: initial; outline-width: 0px; min-height: 2.25em; appearance: none; box-shadow: none; vertical-align: top; border: 1px solid rgba(0, 0, 0, 0); border-radius: 0.125rem; justify-content: center; align-items: center; padding-block: calc(0.375em - 1px); padding-inline: 0.75em; font-size: 0.875rem; line-height: 1.5; display: flex; position: relative; user-select: none; text-align: center; font-weight: 600; width: 222px;"><span class="icon" aria-hidden="true" style="box-sizing: inherit; outline-color: inherit; justify-content: center; align-items: center; display: inline-flex; width: 1em; height: 1em; margin-inline-end: 0.375em;"><span class="docon docon-brand-twitter" style="box-sizing: inherit; outline-color: inherit; font-family: docons; font-size: inherit; speak: none; font-variant: normal; text-transform: none; text-align: center; direction: ltr; -webkit-font-smoothing: antialiased; font-style: normal; font-weight: 400; line-height: 16px; display: inline-block;"></span></span><span style="box-sizing: inherit; outline-color: inherit;"></span></a><a class="button button-clear button-sm has-inner-focus button-block text-decoration-none justify-content-flex-start share-linkedin" data-bi-name="linkedin" data-page-action-item="overflow-all" href="https://www.linkedin.com/cws/share?url=https%3A%2F%2Flearn.microsoft.com%2Fpt-pt%2Fazure%2Fdeveloper%2Fjenkins%2Fpipeline-with-github-and-docker%3FWT.mc_id%3Dlinkedin" style="box-sizing: inherit; outline-color: inherit; color: currentcolor; cursor: pointer; overflow-wrap: break-word; text-decoration: none; background-color: rgba(0, 0, 0, 0); outline-style: initial; outline-width: 0px; min-height: 2.25em; appearance: none; box-shadow: none; vertical-align: top; border: 1px solid rgba(0, 0, 0, 0); border-radius: 0.125rem; justify-content: center; align-items: center; padding-block: calc(0.375em - 1px); padding-inline: 0.75em; font-size: 0.875rem; line-height: 1.5; display: flex; position: relative; user-select: none; text-align: center; font-weight: 600; width: 222px;"><span class="icon" aria-hidden="true" style="box-sizing: inherit; outline-color: inherit; justify-content: center; align-items: center; display: inline-flex; width: 1em; height: 1em; margin-inline-end: 0.375em;"><span class="docon docon-brand-linkedin" style="box-sizing: inherit; outline-color: inherit; font-family: docons; font-size: inherit; speak: none; font-variant: normal; text-transform: none; text-align: center; direction: ltr; -webkit-font-smoothing: antialiased; font-style: normal; font-weight: 400; line-height: 16px; display: inline-block;"></span></span><span style="box-sizing: inherit; outline-color: inherit;"></span></a><a class="button button-clear button-sm button-block has-inner-focus text-decoration-none justify-content-flex-start share-facebook" data-bi-name="facebook" data-page-action-item="overflow-all" href="https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Flearn.microsoft.com%2Fpt-pt%2Fazure%2Fdeveloper%2Fjenkins%2Fpipeline-with-github-and-docker%3FWT.mc_id%3Dfacebook" style="box-sizing: inherit; outline-color: inherit; color: currentcolor; cursor: pointer; overflow-wrap: break-word; text-decoration: none; background-color: rgba(0, 0, 0, 0); outline-style: initial; outline-width: 0px; min-height: 2.25em; appearance: none; box-shadow: none; vertical-align: top; border: 1px solid rgba(0, 0, 0, 0); border-radius: 0.125rem; justify-content: center; align-items: center; padding-block: calc(0.375em - 1px); padding-inline: 0.75em; font-size: 0.875rem; line-height: 1.5; display: flex; position: relative; user-select: none; text-align: center; font-weight: 600; width: 222px;"><span class="icon" aria-hidden="true" style="box-sizing: inherit; outline-color: inherit; justify-content: center; align-items: center; display: inline-flex; width: 1em; height: 1em; margin-inline-end: 0.375em;"><span class="docon docon-brand-facebook" style="box-sizing: inherit; outline-color: inherit; font-family: docons; font-size: inherit; speak: none; font-variant: normal; text-transform: none; text-align: center; direction: ltr; -webkit-font-smoothing: antialiased; font-style: normal; font-weight: 400; line-height: 16px; display: inline-block;"></span></span><span style="box-sizing: inherit; outline-color: inherit;"></span></a><a class="button button-clear button-sm button-block has-inner-focus text-decoration-none justify-content-flex-start share-email" data-bi-name="email" data-page-action-item="overflow-all" href="mailto:?subject=%5BShared%20Article%5D%20Tutorial%20-%20Criar%20um%20oleoduto%20Jenkins%20usando%20GitHub%20e%20Docker%20%7C%20Microsoft%20Learn&amp;body=Tutorial%20-%20Criar%20um%20oleoduto%20Jenkins%20usando%20GitHub%20e%20Docker%20%7C%20Microsoft%20Learn%0A%0Ahttps%3A%2F%2Flearn.microsoft.com%2Fpt-pt%2Fazure%2Fdeveloper%2Fjenkins%2Fpipeline-with-github-and-docker%3FWT.mc_id%3Demail" style="box-sizing: inherit; outline-color: inherit; color: currentcolor; cursor: pointer; overflow-wrap: break-word; text-decoration: none; background-color: rgba(0, 0, 0, 0); outline-style: initial; outline-width: 0px; min-height: 2.25em; appearance: none; box-shadow: none; vertical-align: top; border: 1px solid rgba(0, 0, 0, 0); border-radius: 0.125rem; justify-content: center; align-items: center; padding-block: calc(0.375em - 1px); padding-inline: 0.75em; font-size: 0.875rem; line-height: 1.5; display: flex; position: relative; user-select: none; text-align: center; font-weight: 600; width: 222px;"><span class="icon" aria-hidden="true" style="box-sizing: inherit; outline-color: inherit; justify-content: center; align-items: center; display: inline-flex; width: 1em; height: 1em; margin-inline-end: 0.375em;"><span class="docon docon-mail-message-fill" style="box-sizing: inherit; outline-color: inherit; font-family: docons; font-size: inherit; speak: none; font-variant: normal; text-transform: none; text-align: center; direction: ltr; -webkit-font-smoothing: antialiased; font-style: normal; font-weight: 400; line-height: 16px; display: inline-block;"></span></span><span style="box-sizing: inherit; outline-color: inherit;"></span></a></div></details>

# Tutorial: Criar um oleoduto Jenkins usando GitHub e Docker

- Artigo
- 22/09/2022
- 9 minutos para ler
- 5 contribuidores

Comentários

 Importante

Muitos serviços da Azure têm plug-ins jenkins. Alguns destes plug-ins estarão fora de suporte a partir de 29 de fevereiro de 2024. Azure CLI é a forma atualmente recomendada de integrar jenkins com os serviços Azure. Para mais informações, consulte o artigo [Jenkins plug-ins para Azure](https://learn.microsoft.com/pt-pt/azure/developer/jenkins/plug-ins-for-azure).

Para automatizar a fase de criação e teste do desenvolvimento de aplicações, pode utilizar um pipeline de integração e implementação (CI/CD) contínuas. Neste tutorial, vai criar um pipeline de CI/CD numa VM do Azure, incluindo como:

- Criar uma VM do Jenkins
- Instalar e configurar o Jenkins
- Criar a integração de webhooks entre o GitHub e Jenkins
- Criar e acionar tarefas de compilação do Jenkins a partir de consolidações do GitHub
- Criar uma imagem do Docker para a aplicação
- Verificar se as consolidações do GitHub criam uma nova imagem do Docker e atualizam a aplicação em execução

Este tutorial utiliza o CLI dentro do [Azure Cloud Shell](https://learn.microsoft.com/pt-pt/azure/cloud-shell/overview), que é constantemente atualizado para a versão mais recente. Para abrir o Cloud Shell, selecione **Experimente-o** a partir da parte superior de qualquer bloco de código.

Se optar por instalar e utilizar a CLI localmente, este tutorial requer que execute uma versão da CLI do Azure que seja a 2.0.30 ou posterior. Executar `az --version` para localizar a versão. Se precisar de instalar ou atualizar, veja [Install Azure CLI (Instalar o Azure CLI)](https://learn.microsoft.com/pt-pt/cli/azure/install-azure-cli).

## Criar instância do Jenkins

Num tutorial anterior sobre [Como personalizar uma máquina virtual do Linux no primeiro arranque](https://learn.microsoft.com/pt-pt/azure/virtual-machines/linux/tutorial-automate-vm-deployment), aprendeu a automatizar a personalização de VMs com inicialização da cloud. Este tutorial utiliza um ficheiro de inicialização da cloud para instalar o Jenkins e o Docker numa VM. O Jenkins é um servidor de automatização de código aberto popular, que se integra totalmente no Azure para permitir a integração contínua (CI) e a entrega contínua (CD). Para obter mais tutoriais sobre como utilizar o Jenkins, veja o [Jenkins no hub do Azure](https://learn.microsoft.com/pt-pt/azure/jenkins/).

Na sua shell atual, crie um ficheiro com o nome *cloud-init-jenkins.txt* e cole a seguinte configuração. Por exemplo, crie o ficheiro no Cloud Shell, não no seu computador local. Introduza `sensible-editor cloud-init-jenkins.txt` para criar o ficheiro e ver uma lista dos editores disponíveis. Certifique-se de que o ficheiro de inicialização da cloud é copiado corretamente, especialmente a primeira linha:

YAMLCopiar

```yaml
#cloud-config
package_upgrade: true
write_files:
  - path: /etc/systemd/system/docker.service.d/docker.conf
    content: |
      [Service]
        ExecStart=
        ExecStart=/usr/bin/dockerd
  - path: /etc/docker/daemon.json
    content: |
      {
        "hosts": ["fd://","tcp://127.0.0.1:2375"]
      }
runcmd:
  - apt install openjdk-8-jre-headless -y
  - wget -q -O - https://pkg.jenkins.io/debian/jenkins-ci.org.key | sudo apt-key add -
  - sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
  - apt-get update && apt-get install jenkins -y
  - curl -sSL https://get.docker.com/ | sh
  - usermod -aG docker azureuser
  - usermod -aG docker jenkins
  - service jenkins restart
```

Antes de poder criar uma VM, tem de criar um grupo de recursos com [az group create](https://learn.microsoft.com/pt-pt/cli/azure/group). O exemplo seguinte cria um grupo de recursos com o nome *myResourceGroupJenkins* na localização *eualeste*:

CLI do AzureCopiarExperimente

```azurecli
az group create --name myResourceGroupJenkins --location eastus
```

Agora, crie uma VM com [az vm create](https://learn.microsoft.com/pt-pt/cli/azure/vm). Utilize o parâmetro `--custom-data` para passar o ficheiro de configuração de inicialização da cloud. Forneça o caminho completo para *cloud-init-jenkins.txt*, se tiver guardado o ficheiro fora do diretório de trabalho atual.

CLI do AzureCopiarExperimente

```azurecli
az vm create --resource-group myResourceGroupJenkins \
    --name myVM \
    --image UbuntuLTS \
    --admin-username azureuser \
    --generate-ssh-keys \
    --custom-data cloud-init-jenkins.txt
```

Demora alguns minutos até que a VM seja criada e configurada.

Para permitir que o tráfego Web alcance a sua VM, utilize [az vm open-port](https://learn.microsoft.com/pt-pt/cli/azure/vm) para abrir a porta *8080* para o tráfego do Jenkins e a porta *1337* para a aplicação Node.js que é utilizada para executar uma aplicação de exemplo:

CLI do AzureCopiarExperimente

```azurecli
az vm open-port --resource-group myResourceGroupJenkins --name myVM --port 8080 --priority 1001
az vm open-port --resource-group myResourceGroupJenkins --name myVM --port 1337 --priority 1002
```

## Configurar o Jenkins

Para aceder à sua instância do Jenkins, obtenha o endereço IP público da sua VM:

CLI do AzureCopiarExperimente

```azurecli
az vm show --resource-group myResourceGroupJenkins --name myVM -d --query [publicIps] --o tsv
```

Por motivos de segurança, tem de introduzir a palavra-passe de administrador inicial que é armazenada num ficheiro de texto na VM para iniciar a instalação do Jenkins. Utilize o endereço IP público que obteve no passo anterior para encaminhar o SSH para a VM:

BashCopiar

```bash
ssh azureuser@<publicIps>
```

Verifique se o Jenkins está a executar usando o `service` comando:

BashCopiar

```bash
$ service jenkins status
● jenkins.service - LSB: Start Jenkins at boot time
   Loaded: loaded (/etc/init.d/jenkins; generated)
   Active: active (exited) since Tue 2019-02-12 16:16:11 UTC; 55s ago
     Docs: man:systemd-sysv-generator(8)
    Tasks: 0 (limit: 4103)
   CGroup: /system.slice/jenkins.service

Feb 12 16:16:10 myVM systemd[1]: Starting LSB: Start Jenkins at boot time...
...
```

Veja o `initialAdminPassword` da sua instalação do Jenkins e copie-o:

BashCopiar

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Se o ficheiro ainda não estiver disponível, aguarde alguns minutos para que a inicialização da cloud conclua a instalação do Jenkins e do Docker.

Agora, abra um browser e vá para `http://<publicIps>:8080`. Conclua a configuração inicial do Jenkins da seguinte forma:

- Escolha **Selecione plug-ins para instalar**

- Procure *GitHub* na caixa de texto na parte superior. Marque a caixa de *GitHub* e, em seguida, selecione **Instalar**

- Crie o primeiro utilizador administrador. Introduza um nome de utilizador, como **administrador** e forneça a sua palavra-passe segura. Por fim, escreva um nome completo e o endereço de e-mail.

- Selecionar **Guardar e Concluir**

- Assim que o Jenkins estiver pronto, selecione

   

  Começar a utilizar o Jenkins

  - Se o browser apresentar uma página em branco quando começar a utilizar o Jenkins, reinicie o serviço Jenkins. A partir da sua sessão SSH, escreva `sudo service jenkins restart` e, em seguida, atualize o browser.

- Se necessário, faça login no Jenkins com o nome de utilizador e senha que criou.

## Criar um webhook do GitHub

Para configurar a integração com o GitHub, abra a [aplicação de exemplo Node.js Hello World](https://github.com/Azure-Samples/nodejs-docs-hello-world) do repositório de exemplos do Azure. Para bifurcar o repositório para a sua própria conta do GitHub, selecione o botão **Fork** no canto superior direito.

Crie um webhook no interior do fork que criou:

- Selecione **Definições** e, em seguida, selecione **Webhooks** no lado esquerdo.
- Escolha **Adicionar webhook** e, em seguida, inserir *Jenkins* na caixa de filtro.
- Para o **URL de carga útil**, insira `http://<publicIps>:8080/github-webhook/`. Certifique-se de que inclui / à direita
- Para **o tipo de conteúdo**, selecione *aplicação/x-www-form-urlencoded*.
- Para **que eventos gostaria de desencadear este webhook?**, selecione *Just the push event.*
- Definir **Ative** para verificar.
- Clique **em Adicionar webhook**.

![Add GitHub webhook to your forked repo](https://learn.microsoft.com/pt-pt/azure/developer/jenkins/media/pipeline-with-github-and-docker/github-webhook.png)

## Criar tarefa do Jenkins

Para que o Jenkins responda a um evento no GitHub, como consolidar código, crie uma tarefa do Jenkins. Utilize os URLs do seu próprio fork do GitHub.

No seu site do Jenkins, selecione **Criar novas tarefas** na home page:

- Introduza *HelloWorld* no nome da tarefa. Escolha **Projeto de estilo livre** e selecione **OK**.
- Na secção **Geral**, selecione o projeto **GitHub** e introduza o URL do repositório bifurcado, como `https://github.com/cynthn/nodejs-docs-hello-world`
- Na secção **Gestão de código fonte**, selecione o projeto **Git** e introduza o URL *.git* do repositório bifurcado, como `https://github.com/cynthn/nodejs-docs-hello-world.git`
- Na secção **Criar Acionadores**, selecione **Acionador de hook do GitHub para consulta GITScm**.
- Na secção **Compilar**, escolha **Adicionar passo de compilação**. Selecione **Executar shell** e introduza `echo "Test"` na janela de comandos.
- Selecione **Guardar** na parte inferior da janela de tarefas.

## Testar integração do GitHub

Para testar a integração do GitHub no Jenkins, consolide uma alteração no seu fork.

Na IU Web do GitHub, selecione o repositório bifurcado e selecione o ficheiro **index.js**. Selecione o ícone de lápis para editar este ficheiro, de forma que a linha 6 seja:

JavaScriptCopiar

```javascript
response.end("Hello World!");
```

Para consolidar as alterações, selecione o botão **Consolidar alterações** na parte inferior.

No Jenkins, uma nova compilação é iniciada na secção **Histórico de compilações** do canto inferior esquerdo da página de tarefas. Escolha a ligação do número da compilação e selecione **Saída da consola** no lado esquerdo. Pode ver os passos que o Jenkins executa, à medida que o seu código é obtido do GitHub e a ação de compilação gera a saída da mensagem `Test` para a consola. Sempre que uma consolidação é efetuada no GitHub, o webhook acede ao Jenkins e aciona uma nova compilação desta forma.

## Definir imagem de compilação do Docker

Para ver a aplicação Node.js em execução com base nas suas consolidações do GitHub, vamos construir uma imagem do Docker para executar a aplicação. A imagem é criada a partir de um Dockerfile que define como configurar o contentor que executa a aplicação.

A partir da ligação SSH à sua VM, mude para o diretório de área de trabalho do Jenkins que tem o nome da tarefa que criou no passo anterior. Neste exemplo, foi-lhe atribuído o nome *HelloWorld*.

BashCopiar

```bash
cd /var/lib/jenkins/workspace/HelloWorld
```

Crie um ficheiro neste diretório de área de trabalho com `sudo sensible-editor Dockerfile` e cole os seguintes conteúdos. Certifique-se de que todo o Dockerfile é copiado corretamente, especialmente a primeira linha:

YAMLCopiar

```yaml
FROM node:alpine

EXPOSE 1337

WORKDIR /var/www
COPY package.json /var/www/
RUN npm install
COPY index.js /var/www/
```

Este Dockerfile utiliza a imagem base do Node.js com Alpine Linux, expõe a porta 1337 na qual a aplicação Hello World é executada e, em seguida, copia os ficheiros da aplicação e inicializa-a.

## Criar regras de compilação do Jenkins

Num passo anterior, criou uma regra de compilação básica do Jenkins que gera a saída de uma mensagem para a consola. Vamos criar o passo de compilação para utilizar o nosso Dockerfile e executar a aplicação.

Novamente na instância do Jenkins, selecione a tarefa que criou no passo anterior. Selecione **Configurar** no lado esquerdo e desloque-se para baixo até à secção **Compilar**:

- Remova o passo de compilação `echo "Test"` existente. Selecione a cruz vermelha no canto superior direito da caixa de passos de compilação existente.

- Escolha **Adicionar passo de compilação** e selecione **Executar shell**

- Na caixa **Comando**, introduza os seguintes comandos do Docker e selecione **Guardar**:

  BashCopiar

  ```bash
  docker build --tag helloworld:$BUILD_NUMBER .
  docker stop helloworld && docker rm helloworld
  docker run --name helloworld -p 1337:1337 helloworld:$BUILD_NUMBER node /var/www/index.js &
  ```

Os passos de compilação do Docker criam uma imagem e identificam-na com o número de compilação do Jenkins para que possa manter um histórico de imagens. Quaisquer contentores existentes em execução na aplicação são parados e, em seguida, removidos. Um novo contentor é então iniciado com a imagem e executa a aplicação Node.js com base nas consolidações mais recentes no GitHub.

## Testar o pipeline

Para ver todo o pipeline em ação, edite novamente o ficheiro *index.js* no seu repositório bifurcado do GitHub e selecione **Consolidar alteração**. Uma nova tarefa é iniciada no Jenkins, com base no webhook do GitHub. Demora alguns segundos para criar a imagem do Docker e iniciar a sua aplicação num novo contentor.

Se for necessário, obtenha novamente o endereço IP público da sua VM:

CLI do AzureCopiarExperimente

```azurecli
az vm show --resource-group myResourceGroupJenkins --name myVM -d --query [publicIps] --o tsv
```

Abra um browser e introduza `http://<publicIps>:1337`. A aplicação Node.js é apresentada e reflete as consolidações mais recentes no fork do GitHub da seguinte forma:

![Running Node.js app](https://learn.microsoft.com/pt-pt/azure/developer/jenkins/media/pipeline-with-github-and-docker/running-nodejs-app.png)

Agora, efetue outra edição no ficheiro *index.js* no GitHub e consolide a alteração. Aguarde alguns segundos até que a tarefa seja concluída no Jenkins e, em seguida, atualize o browser para ver a versão atualizada da sua aplicação em execução num novo contentor da seguinte forma:

![Running Node.js app after another GitHub commit](https://learn.microsoft.com/pt-pt/azure/developer/jenkins/media/pipeline-with-github-and-docker/another-running-nodejs-app.png)

## Passos seguintes

Neste tutorial, configurou o GitHub para executar uma tarefa de compilação do Jenkins em cada consolidação de código e, em seguida, implementar um contentor do Docker para testar a aplicação. Aprendeu a:

- Criar uma VM do Jenkins
- Instalar e configurar o Jenkins
- Criar a integração de webhooks entre o GitHub e Jenkins
- Criar e acionar tarefas de compilação do Jenkins a partir de consolidações do GitHub
- Criar uma imagem do Docker para a aplicação
- Verificar se as consolidações do GitHub criam uma nova imagem do Docker e atualizam a aplicação em execução

Avance para o próximo tutorial para saber mais sobre como integrar o Jenkins no Azure DevOps Services.

[Implementar aplicações com o Jenkins e o Azure DevOps Services](https://learn.microsoft.com/pt-pt/azure/developer/jenkins/deploy-to-linux-vm-using-azure-devops-services)

------

## Conteúdo recomendado

- [Introdução - Instale Jenkins num Azure Linux VM](https://learn.microsoft.com/pt-pt/azure/developer/jenkins/configure-on-linux-vm?source=recommendations)

  Aprenda a instalar o Jenkins numa máquina virtual Azure Linux e construa uma aplicação Java de amostra.

- [Implementar para máquina virtual Linux usando serviços Jenkins e Azure DevOps](https://learn.microsoft.com/pt-pt/azure/developer/jenkins/deploy-to-linux-vm-using-azure-devops-services?source=recommendations)

  Saiba como facilitar a integração e implementação contínuas (CI/CD) para implementar aplicações para máquinas virtuais Linux usando serviços Jenkins e Azure DevOps

- [Tutorial - Use Azure Container Instances como agente de construção jenkins](https://learn.microsoft.com/pt-pt/azure/developer/jenkins/azure-container-instances-as-jenkins-build-agent?source=recommendations)

  Aprenda a configurar um servidor Jenkins para executar trabalhos de construção em Azure Container Instances

- [Tutorial - Implantações de Escala Jenkins com VM em execução em Azure](https://learn.microsoft.com/pt-pt/azure/developer/jenkins/scale-deployments-using-vm-agents?source=recommendations)

  Saiba como adicionar capacidade adicional aos seus oleodutos Jenkins utilizando máquinas virtuais Azure

Mostrar mais