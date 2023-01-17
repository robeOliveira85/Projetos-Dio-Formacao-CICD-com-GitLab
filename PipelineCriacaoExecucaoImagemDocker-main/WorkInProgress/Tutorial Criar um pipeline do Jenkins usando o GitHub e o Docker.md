[Learn](https://learn.microsoft.com/pt-br/) [Azure](https://learn.microsoft.com/pt-br/azure/) [Developer](https://learn.microsoft.com/pt-br/azure/developer/) [Jenkins](https://learn.microsoft.com/pt-br/azure/developer/jenkins/) 

[Ler em inglês](https://learn.microsoft.com/en-us/azure/developer/jenkins/pipeline-with-github-and-docker)Salvar

<details class="popover popover-right" id="article-header-page-actions-overflow" style="box-sizing: inherit; outline-color: inherit; display: inline-block; position: relative;"><summary class="justify-content-flex-start button button-clear button-sm button-primary" aria-label="Mais ações" style="box-sizing: inherit; outline-color: inherit; display: inline-flex; cursor: pointer; min-height: 2.25em; appearance: none; box-shadow: none; vertical-align: top; border: 1px solid rgba(0, 0, 0, 0); border-radius: 0.125rem; justify-content: center; align-items: center; padding-block: calc(0.375em - 1px); padding-inline: 0.75em; font-size: 0.875rem; line-height: 1.5; position: relative; user-select: none; background-color: rgba(0, 0, 0, 0); color: var(--theme-primary-base); text-align: center; font-weight: 600; text-decoration: none; list-style: none;"><span class="icon" aria-hidden="true" style="box-sizing: inherit; outline-color: inherit; justify-content: center; align-items: center; display: inline-flex; width: 1em; height: 1em; margin: 0px;"><span class="docon docon-more-vertical" style="box-sizing: inherit; outline-color: inherit; font-family: docons; font-size: inherit; speak: none; font-variant: normal; text-transform: none; text-align: center; direction: ltr; -webkit-font-smoothing: antialiased; font-style: normal; font-weight: 400; line-height: 16px; display: inline-block;"></span></span></summary><div class="popover-content padding-none" style="box-sizing: inherit; outline-color: inherit; padding: 1rem; width: 224px; border: 1px solid var(--theme-border); background-color: var(--theme-body-background); box-shadow: 0 6.4px 14.4px 0 var(--theme-box-shadow-medium),0 1.2px 3.6px 0 var(--theme-box-shadow-light); z-index: 1060; border-radius: 0.25rem; margin-block-start: 0.5rem; position: absolute; inset-inline-end: 0px;"><button class="button button-block button-clear button-sm justify-content-flex-start has-inner-focus" title="Imprimir" type="button" aria-label="Imprimir" data-bi-name="print" data-page-action-item="overflow-all" data-popover-close="" data-print-page="" data-check-hidden="true" style="box-sizing: inherit; outline-color: inherit; margin: 0px; font-family: inherit; font-size: 0.875rem; line-height: 1.5; overflow: visible; text-transform: none; appearance: button; color: currentcolor; background-color: rgba(0, 0, 0, 0); cursor: pointer; min-height: 2.25em; box-shadow: none; vertical-align: top; border: 1px solid rgba(0, 0, 0, 0); border-radius: 0.125rem; justify-content: center; align-items: center; padding-block: calc(0.375em - 1px); padding-inline: 0.75em; display: flex; position: relative; user-select: none; text-align: center; font-weight: 600; text-decoration: none; width: 222px;"><span class="icon" aria-hidden="true" style="box-sizing: inherit; outline-color: inherit; justify-content: center; align-items: center; display: inline-flex; width: 1em; height: 1em; margin-inline-end: 0.375em;"><span class="docon docon-print" style="box-sizing: inherit; outline-color: inherit; font-family: docons; font-size: inherit; speak: none; font-variant: normal; text-transform: none; text-align: center; direction: ltr; -webkit-font-smoothing: antialiased; font-style: normal; font-weight: 400; line-height: 16px; display: inline-block;"></span></span><span style="box-sizing: inherit; outline-color: inherit;"></span></button><div aria-hidden="true" class="margin-none border-top" data-page-action-item="overflow-all" style="box-sizing: inherit; outline-color: inherit; border-block-start: 1px solid var(--theme-border) !important; margin: 0px !important;"></div><a class="button button-clear button-sm has-inner-focus button-block text-decoration-none justify-content-flex-start share-twitter" data-bi-name="twitter" data-page-action-item="overflow-all" href="https://twitter.com/intent/tweet?original_referer=https%3A%2F%2Flearn.microsoft.com%2Fpt-br%2Fazure%2Fdeveloper%2Fjenkins%2Fpipeline-with-github-and-docker%3FWT.mc_id%3Dtwitter&amp;text=Tutorial%20%E2%80%93%20Criar%20um%20pipeline%20do%20Jenkins%20usando%20o%20GitHub%20e%20o%20Docker%20%7C%20Microsoft%20Learn&amp;tw_p=tweetbutton&amp;url=https%3A%2F%2Flearn.microsoft.com%2Fpt-br%2Fazure%2Fdeveloper%2Fjenkins%2Fpipeline-with-github-and-docker%3FWT.mc_id%3Dtwitter" style="box-sizing: inherit; outline-color: inherit; color: currentcolor; cursor: pointer; overflow-wrap: break-word; text-decoration: none; background-color: rgba(0, 0, 0, 0); outline-style: initial; outline-width: 0px; min-height: 2.25em; appearance: none; box-shadow: none; vertical-align: top; border: 1px solid rgba(0, 0, 0, 0); border-radius: 0.125rem; justify-content: center; align-items: center; padding-block: calc(0.375em - 1px); padding-inline: 0.75em; font-size: 0.875rem; line-height: 1.5; display: flex; position: relative; user-select: none; text-align: center; font-weight: 600; width: 222px;"><span class="icon" aria-hidden="true" style="box-sizing: inherit; outline-color: inherit; justify-content: center; align-items: center; display: inline-flex; width: 1em; height: 1em; margin-inline-end: 0.375em;"><span class="docon docon-brand-twitter" style="box-sizing: inherit; outline-color: inherit; font-family: docons; font-size: inherit; speak: none; font-variant: normal; text-transform: none; text-align: center; direction: ltr; -webkit-font-smoothing: antialiased; font-style: normal; font-weight: 400; line-height: 16px; display: inline-block;"></span></span><span style="box-sizing: inherit; outline-color: inherit;"></span></a><a class="button button-clear button-sm has-inner-focus button-block text-decoration-none justify-content-flex-start share-linkedin" data-bi-name="linkedin" data-page-action-item="overflow-all" href="https://www.linkedin.com/cws/share?url=https%3A%2F%2Flearn.microsoft.com%2Fpt-br%2Fazure%2Fdeveloper%2Fjenkins%2Fpipeline-with-github-and-docker%3FWT.mc_id%3Dlinkedin" style="box-sizing: inherit; outline-color: inherit; color: currentcolor; cursor: pointer; overflow-wrap: break-word; text-decoration: none; background-color: rgba(0, 0, 0, 0); outline-style: initial; outline-width: 0px; min-height: 2.25em; appearance: none; box-shadow: none; vertical-align: top; border: 1px solid rgba(0, 0, 0, 0); border-radius: 0.125rem; justify-content: center; align-items: center; padding-block: calc(0.375em - 1px); padding-inline: 0.75em; font-size: 0.875rem; line-height: 1.5; display: flex; position: relative; user-select: none; text-align: center; font-weight: 600; width: 222px;"><span class="icon" aria-hidden="true" style="box-sizing: inherit; outline-color: inherit; justify-content: center; align-items: center; display: inline-flex; width: 1em; height: 1em; margin-inline-end: 0.375em;"><span class="docon docon-brand-linkedin" style="box-sizing: inherit; outline-color: inherit; font-family: docons; font-size: inherit; speak: none; font-variant: normal; text-transform: none; text-align: center; direction: ltr; -webkit-font-smoothing: antialiased; font-style: normal; font-weight: 400; line-height: 16px; display: inline-block;"></span></span><span style="box-sizing: inherit; outline-color: inherit;"></span></a><a class="button button-clear button-sm button-block has-inner-focus text-decoration-none justify-content-flex-start share-facebook" data-bi-name="facebook" data-page-action-item="overflow-all" href="https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Flearn.microsoft.com%2Fpt-br%2Fazure%2Fdeveloper%2Fjenkins%2Fpipeline-with-github-and-docker%3FWT.mc_id%3Dfacebook" style="box-sizing: inherit; outline-color: inherit; color: currentcolor; cursor: pointer; overflow-wrap: break-word; text-decoration: none; background-color: rgba(0, 0, 0, 0); outline-style: initial; outline-width: 0px; min-height: 2.25em; appearance: none; box-shadow: none; vertical-align: top; border: 1px solid rgba(0, 0, 0, 0); border-radius: 0.125rem; justify-content: center; align-items: center; padding-block: calc(0.375em - 1px); padding-inline: 0.75em; font-size: 0.875rem; line-height: 1.5; display: flex; position: relative; user-select: none; text-align: center; font-weight: 600; width: 222px;"><span class="icon" aria-hidden="true" style="box-sizing: inherit; outline-color: inherit; justify-content: center; align-items: center; display: inline-flex; width: 1em; height: 1em; margin-inline-end: 0.375em;"><span class="docon docon-brand-facebook" style="box-sizing: inherit; outline-color: inherit; font-family: docons; font-size: inherit; speak: none; font-variant: normal; text-transform: none; text-align: center; direction: ltr; -webkit-font-smoothing: antialiased; font-style: normal; font-weight: 400; line-height: 16px; display: inline-block;"></span></span><span style="box-sizing: inherit; outline-color: inherit;"></span></a><a class="button button-clear button-sm button-block has-inner-focus text-decoration-none justify-content-flex-start share-email" data-bi-name="email" data-page-action-item="overflow-all" href="mailto:?subject=%5BArtigo%20compartilhado%5D%20Tutorial%20%E2%80%93%20Criar%20um%20pipeline%20do%20Jenkins%20usando%20o%20GitHub%20e%20o%20Docker%20%7C%20Microsoft%20Learn&amp;body=Tutorial%20%E2%80%93%20Criar%20um%20pipeline%20do%20Jenkins%20usando%20o%20GitHub%20e%20o%20Docker%20%7C%20Microsoft%20Learn%0A%0Ahttps%3A%2F%2Flearn.microsoft.com%2Fpt-br%2Fazure%2Fdeveloper%2Fjenkins%2Fpipeline-with-github-and-docker%3FWT.mc_id%3Demail" style="box-sizing: inherit; outline-color: inherit; color: currentcolor; cursor: pointer; overflow-wrap: break-word; text-decoration: none; background-color: rgba(0, 0, 0, 0); outline-style: initial; outline-width: 0px; min-height: 2.25em; appearance: none; box-shadow: none; vertical-align: top; border: 1px solid rgba(0, 0, 0, 0); border-radius: 0.125rem; justify-content: center; align-items: center; padding-block: calc(0.375em - 1px); padding-inline: 0.75em; font-size: 0.875rem; line-height: 1.5; display: flex; position: relative; user-select: none; text-align: center; font-weight: 600; width: 222px;"><span class="icon" aria-hidden="true" style="box-sizing: inherit; outline-color: inherit; justify-content: center; align-items: center; display: inline-flex; width: 1em; height: 1em; margin-inline-end: 0.375em;"><span class="docon docon-mail-message-fill" style="box-sizing: inherit; outline-color: inherit; font-family: docons; font-size: inherit; speak: none; font-variant: normal; text-transform: none; text-align: center; direction: ltr; -webkit-font-smoothing: antialiased; font-style: normal; font-weight: 400; line-height: 16px; display: inline-block;"></span></span><span style="box-sizing: inherit; outline-color: inherit;"></span></a></div></details>

# Tutorial: Criar um pipeline do Jenkins usando o GitHub e o Docker

- Artigo
- 22/09/2022
- 9 minutos para o fim da leitura
- 5 colaboradores

Comentários

 Importante

Muitos serviços do Azure têm plug-ins do Jenkins. Alguns desses plug-ins ficarão sem suporte a partir de 29 de fevereiro de 2024. A CLI do Azure é a maneira atualmente recomendada para integrar o Jenkins aos serviços do Azure. Para obter mais informações, confira o artigo [Plug-ins do Jenkins para Azure](https://learn.microsoft.com/pt-br/azure/developer/jenkins/plug-ins-for-azure).

Para automatizar as fases de build e teste do desenvolvimento de aplicativos, você pode usar um pipeline de CI/CD (implantação e integração contínuas). Neste tutorial, você cria um pipeline de CI/CD em uma VM do Azure, incluindo como:

- Criar uma VM Jenkins
- Instalar e configurar o Jenkins
- Criar integração de webhooks entre o GitHub e Jenkins
- Criar e disparar trabalhos de build do Jenkins por meio de confirmações do GitHub
- Criar uma imagem de Docker para o aplicativo
- Verificar se as confirmações do GitHub compilam a nova imagem do Docker e atualizam o aplicativo em execução

Este tutorial usa a CLI dentro do [Azure Cloud Shell](https://learn.microsoft.com/pt-br/azure/cloud-shell/overview), que é constantemente atualizada para a versão mais recente. Para abrir o Cloud Shell, selecione **Experimentar** na parte superior de um bloco de código qualquer.

Se você optar por instalar e usar a CLI localmente, este tutorial exigirá que você execute a CLI do Azure versão 2.0.30 ou posterior. Execute `az --version` para encontrar a versão. Se você precisa instalar ou atualizar, consulte [Instalar a CLI do Azure](https://learn.microsoft.com/pt-br/cli/azure/install-azure-cli).

## Criar instância do Jenkins

Em um tutorial anterior sobre [Como personalizar uma máquina virtual do Linux na primeira inicialização](https://learn.microsoft.com/pt-br/azure/virtual-machines/linux/tutorial-automate-vm-deployment), você aprendeu a automatizar a personalização de VM com a inicialização de nuvem. Este tutorial usa um arquivo de inicialização de nuvem para instalar o Jenkins e o Docker em uma VM. Jenkins é um conhecido servidor de automação de código aberto que se integra perfeitamente com o Azure para habilitar a integração contínua (CI) e fornecimento contínuo (CD). Para ver mais tutoriais sobre como usar o Jenkins, consulte [Jenkins no hub do Azure](https://learn.microsoft.com/pt-br/azure/jenkins/).

No shell atual, crie um arquivo chamado *cloud-init-jenkins.txt* e cole a configuração a seguir. Por exemplo, crie o arquivo no Cloud Shell e não em seu computador local. Insira `sensible-editor cloud-init-jenkins.txt` para criar o arquivo e ver uma lista de editores disponíveis. Certifique-se de que o arquivo de inicialização de nuvem inteiro seja copiado corretamente, especialmente a primeira linha:

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

Antes de criar uma máquina virtual, crie um grupo de recursos com o [az group create](https://learn.microsoft.com/pt-br/cli/azure/group). O exemplo a seguir cria um grupo de recursos chamado *myResourceGroupJenkins* na localização *eastus*:

CLI do AzureCopiarExperimente

```azurecli
az group create --name myResourceGroupJenkins --location eastus
```

Agora, crie uma VM com [az vm create](https://learn.microsoft.com/pt-br/cli/azure/vm). Utiçize o `--custom-data` parâmetro para passar no arquivo de configuração de inicialização de nuvem. Forneça o caminho completo para a configuração *cloud-init-jenkins.txt* se você salvou o arquivo fora do seu diretório de trabalho atual.

CLI do AzureCopiarExperimente

```azurecli
az vm create --resource-group myResourceGroupJenkins \
    --name myVM \
    --image UbuntuLTS \
    --admin-username azureuser \
    --generate-ssh-keys \
    --custom-data cloud-init-jenkins.txt
```

Demora alguns minutos para que a VM seja criada e configurada.

Para permitir que o tráfego da Web alcance a VM, use [az vm open-port](https://learn.microsoft.com/pt-br/cli/azure/vm) para abrir a porta *8080* para tráfego do Jenkins e a porta *1337* para o aplicativo do Node.js que é usado para executar um aplicativo de exemplo:

CLI do AzureCopiarExperimente

```azurecli
az vm open-port --resource-group myResourceGroupJenkins --name myVM --port 8080 --priority 1001
az vm open-port --resource-group myResourceGroupJenkins --name myVM --port 1337 --priority 1002
```

## Configurar o Jenkins

Para acessar a instância do Jenkins, obtenha o endereço IP público da VM:

CLI do AzureCopiarExperimente

```azurecli
az vm show --resource-group myResourceGroupJenkins --name myVM -d --query [publicIps] --o tsv
```

Para fins de segurança, você precisa inserir a senha de administrador inicial que é armazenada em um arquivo de texto na sua VM para iniciar a instalação do Jenkins. Use o endereço IP público obtido na etapa anterior para conectar-se à sua VM por SSH:

BashCopiar

```bash
ssh azureuser@<publicIps>
```

Verifique se o Jenkins está executando usando o comando `service`:

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

Exiba o `initialAdminPassword` para sua instalação do Jenkins e copie-o:

BashCopiar

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Se o arquivo ainda não está disponível, aguarde alguns minutos para a nuvem-init concluir a instalação Jenkins e o Docker.

Agora, abra um navegador da Web e vá para `http://<publicIps>:8080`. Conclua a configuração inicial do Jenkins da seguinte maneira:

- Escolha **Selecionar plug-ins para instalar**

- Procure *GitHub* na caixa de texto na parte superior. Marque a caixa *GitHub* e selecione **Instalar**

- Crie o primeiro usuário administrador. Insira um nome de usuário, por exemplo, **admin**, depois forneça sua própria senha de segurança. Por fim, digite um nome completo e o endereço de email.

- Selecione **Salvar e Concluir**

- Assim que o Jenkins estiver pronto, selecione

   

  Começar a usar o Jenkins

  - Se seu navegador da Web exibir uma página em branco quando você começar a usar o Jenkins, reinicie o serviço do Jenkins. Em sua sessão do SSH, digite `sudo service jenkins restart`, depois atualize seu navegador da Web.

- Se necessário, faça logon no Jenkins com o nome de usuário e a senha que você criou.

## Criar um webhook do GitHub

Para configurar a integração com o GitHub, abra o [aplicativo de exemplo Olá, Mundo do Node.js](https://github.com/Azure-Samples/nodejs-docs-hello-world) do repositório de exemplos do Azure. Para bifurcar o repositório para sua conta do GitHub, selecione o botão **Bifurcação** no canto superior direito.

Crie um webhook dentro da bifurcação criada:

- Selecione **Configurações** e, em seguida, **Webhooks** no lado esquerdo.
- Escolha **Adicionar webhook** e, em seguida, digite *Jenkins* na caixa de filtro.
- Para a **URL de Conteúdo**, insira `http://<publicIps>:8080/github-webhook/`. Certifique-se de incluir a barra à direita (/)
- Para **Tipo de Conteúdo**, selecione *application/x-www-form-urlencoded*.
- Para **Quais eventos você deseja que disparem esse webhook?** , selecione *Apenas o evento de envio por push.*
- Defina **Ativo** como marcado.
- Clique em **Adicionar webhook**.

![Add GitHub webhook to your forked repo](https://learn.microsoft.com/pt-br/azure/developer/jenkins/media/pipeline-with-github-and-docker/github-webhook.png)

## Criar trabalho do Jenkins

Para o Jenkins responder a um evento no GitHub, tal como confirmação de código, crie um trabalho do Jenkins. Use as URLs para sua própria bifurcação do GitHub.

No seu site do Jenkins, selecione **Criar novos trabalhos** na página inicial:

- Insira *HelloWorld* como nome do trabalho. Escolha **Projeto Freestyle** e selecione **OK**.
- Na seção **Geral**, selecione o **projeto do GitHub** e insira a URL do repositório bifurcado, como `https://github.com/cynthn/nodejs-docs-hello-world`
- Na seção **Gerenciamento de código-fonte**, selecione **Git** e insira a URL *.git* do repositório bifurcado, como, por exemplo, `https://github.com/cynthn/nodejs-docs-hello-world.git`
- Na seção **Gatilhos de Build**, selecione **Gatilho de gancho do GitHub para sondagem de GITscm**.
- Na seção **Compilar**, clique em **Adicionar etapa de compilação**. Selecione **Executar shell** e, em seguida, digite `echo "Test"` na janela de comando.
- Selecione **Salvar** na parte inferior da janela de trabalhos.

## Testar a integração do GitHub

Para testar a integração do GitHub com o Jenkins, confirme uma alteração em seu bifurcação.

De volta à interface do usuário da Web do GitHub, selecione o repositório bifurcado e, em seguida, o arquivo **index.js**. Selecione o ícone de lápis para editar esse arquivo, de modo que a linha 6 fique assim:

JavaScriptCopiar

```javascript
response.end("Hello World!");
```

Para confirmar suas alterações, selecione o botão **Confirmar alterações** na parte inferior.

No Jenkins, um novo build começa na seção **Histórico de build** do canto inferior esquerdo da sua página de trabalho. Escolha o link com o número de build e selecione **Saída do console** no lado esquerdo. Você pode exibir as etapas que o Jenkins realiza conforme seu código é extraído por pull do GitHub e a ação de build gera a mensagem `Test` no console. Cada vez que uma confirmação é feita no GitHub, o webhook alcança o Jenkins e dispara um novo build dessa maneira.

## Definir a imagem de build do Docker

Para ver o aplicativo do Node.js em execução com base em suas confirmações GitHub, compilaremos uma imagem do Docker para executar o aplicativo. A imagem é compilada de um Dockerfile que define como configurar o contêiner que executa o aplicativo.

Da conexão do SSH para a VM, altere para o diretório de workspace do Jenkins nomeado como o trabalho que você criou em uma etapa anterior. Nesse exemplo, isso foi nomeado como *HelloWorld*.

BashCopiar

```bash
cd /var/lib/jenkins/workspace/HelloWorld
```

Crie um arquivo nesse diretório de workspace com `sudo sensible-editor Dockerfile` nese cole o conteúdo a seguir. Certifique-se de que o Dockerfile inteiro foi copiado corretamente, especialmente a primeira linha:

YAMLCopiar

```yaml
FROM node:alpine

EXPOSE 1337

WORKDIR /var/www
COPY package.json /var/www/
RUN npm install
COPY index.js /var/www/
```

Este Dockerfile usa a imagem base Node.js usando o Linux Alpine, expõe a porta 1337 em que o aplicativo Olá, Mundo é executado e, em seguida, copia os arquivos do aplicativo e o inicializa.

## Criar regras de build do Jenkins

Na etapa anterior, você criou uma regra de build básica do Jenkins que gera uma mensagem para o console. Permite criar a etapa de build para usar nosso Dockerfile e executar o aplicativo.

Em sua instância do Jenkins, selecione o trabalho que você criou em uma etapa anterior. Selecione **Configurar** no lado esquerdo e role para baixo até a seção **Build**:

- Remova sua etapa de build `echo "Test"` existente. Selecione a cruz vermelha no canto superior direito da caixa da etapa de build existente.

- Escolha **Adicionar etapa de build** e, em seguida, selecione **Executar shell**

- Na caixa **Comando**, insira os comandos do Docker a seguir e então selecione **Salvar**:

  BashCopiar

  ```bash
  docker build --tag helloworld:$BUILD_NUMBER .
  docker stop helloworld && docker rm helloworld
  docker run --name helloworld -p 1337:1337 helloworld:$BUILD_NUMBER node /var/www/index.js &
  ```

As etapas de build do Docker criam uma imagem e marcam-na com o número de build do Jenkins para que você possa manter um histórico das imagens. Qualquer contêiner existente executando o aplicativo é interrompido e, em seguida, removido. Um novo contêiner é então iniciado usando a imagem e executa o aplicativo do Node.js com base nas confirmações mais recentes no GitHub.

## Testar o pipeline

Para ver o pipeline inteiro em ação, edite novamente o arquivo *index.js* no seu repositório bifurcado do GitHub e selecione **Confirmar alteração**. Um novo trabalho é iniciado no Jenkins com base no webhook para GitHub. Leva alguns segundos para criar a imagem de Docker e iniciar seu aplicativo em um novo contêiner.

Se necessário, obtenha o endereço IP público de sua VM novamente:

CLI do AzureCopiarExperimente

```azurecli
az vm show --resource-group myResourceGroupJenkins --name myVM -d --query [publicIps] --o tsv
```

Abra um navegador da Web e insira `http://<publicIps>:1337`. Seu aplicativo Node.js é exibido e reflete as confirmações mais recentes em sua bifurcação do GitHub, da seguinte maneira:

![Running Node.js app](https://learn.microsoft.com/pt-br/azure/developer/jenkins/media/pipeline-with-github-and-docker/running-nodejs-app.png)

Agora, faça outra edição para o arquivo *index.js* no GitHub e confirme a alteração. Aguarde alguns segundos para o trabalho ser concluído no Jenkins e atualize seu navegador da Web para ver a versão atualizada de seu aplicativo em execução em um novo contêiner, da seguinte maneira:

![Running Node.js app after another GitHub commit](https://learn.microsoft.com/pt-br/azure/developer/jenkins/media/pipeline-with-github-and-docker/another-running-nodejs-app.png)

## Próximas etapas

Neste tutorial, você configurou o GitHub para executar um trabalho de build do Jenkins em cada confirmação de código e, em seguida, implantar um contêiner do Docker para testar seu aplicativo. Você aprendeu a:

- Criar uma VM Jenkins
- Instalar e configurar o Jenkins
- Criar integração de webhooks entre o GitHub e Jenkins
- Criar e disparar trabalhos de build do Jenkins por meio de confirmações do GitHub
- Criar uma imagem de Docker para o aplicativo
- Verificar se as confirmações do GitHub compilam a nova imagem do Docker e atualizam o aplicativo em execução

Avance para o próximo tutorial para saber mais sobre como integrar o Jenkins ao Azure DevOps Services.

[Implantar aplicativos com o Jenkins e o Azure DevOps Services](https://learn.microsoft.com/pt-br/azure/developer/jenkins/deploy-to-linux-vm-using-azure-devops-services)

------

## Conteúdo recomendado

- [Introdução – Instalar o Jenkins em uma VM Linux do Azure](https://learn.microsoft.com/pt-br/azure/developer/jenkins/configure-on-linux-vm?source=recommendations)

  Saiba como instalar o Jenkins em uma máquina virtual do Linux no Azure e crie um aplicativo Java de exemplo.

- [Implantação na máquina virtual do Linux usando o Jenkins e o Azure DevOps Services](https://learn.microsoft.com/pt-br/azure/developer/jenkins/deploy-to-linux-vm-using-azure-devops-services?source=recommendations)

  Saiba como facilitar a CI/CD (integração e implantação contínuas) para implantar aplicativos em máquinas virtuais do Linux usando o Jenkins e o Azure DevOps Services

- [Tutorial – Usar as Instâncias de Contêiner do Azure como um agente de build Jenkins](https://learn.microsoft.com/pt-br/azure/developer/jenkins/azure-container-instances-as-jenkins-build-agent?source=recommendations)

  Saiba como configurar um servidor Jenkins para executar trabalhos de build nas Instâncias de Contêiner do Azure

- [Tutorial – Dimensionar implantações do Jenkins com a VM em execução no Azure](https://learn.microsoft.com/pt-br/azure/developer/jenkins/scale-deployments-using-vm-agents?source=recommendations)

  Saiba como adicionar mais capacidade aos seus pipelines do Jenkins usando máquinas virtuais do Azure

- [Tutorial – Implantar o Serviço de Aplicativo do Azure com o Jenkins e a CLI do Azure](https://learn.microsoft.com/pt-br/azure/developer/jenkins/deploy-to-azure-app-service-using-azure-cli?source=recommendations)

  Saiba como usar a CLI do Azure para implantar um aplicativo Web do Java no Azure na pipeline do Jenkins

- [Implantar Java WAR na VM no Azure Stack Hub - Azure Stack Hub](https://learn.microsoft.com/pt-br/azure-stack/user/azure-stack-dev-start-howto-vm-java?source=recommendations)

  Implante um Java WAR em uma máquina virtual no Azure Stack Hub.

- [Tutorial – Usar o Docker Compose para implantar o grupo de vários contêineres - Azure Container Instances](https://learn.microsoft.com/pt-br/azure/container-instances/tutorial-docker-compose?source=recommendations)

  Use o Docker Compose para compilar e executar um aplicativo de vários contêineres e, em seguida, colocar o aplicativo em Instâncias de Contêiner do Azure

- [Instalar a CLI do Azure no Linux](https://learn.microsoft.com/pt-br/cli/azure/install-azure-cli-linux?source=recommendations)

  Aprenda a instalar e executar o CLI do Azure no Linux manualmente. Você pode instalar o CLI do Azure em computadores Linux com um comando ou um processo passo a passo.

Mostrar menos