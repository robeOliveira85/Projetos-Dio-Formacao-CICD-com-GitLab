# O que é e como usar o GitLab Ci?

PUBLICADO POR [ENGINEERING DO BRASIL](https://blog.engdb.com.br/author/marcio_buhrer/) EM AGOSTO 23, 2021 | ATUALIZADO EM AGOSTO 23, 2021

7 minutos para ler

De aplicativos simples a softwares sofisticados, o mercado de TI precisa lidar com uma demanda cada vez maior, o que requer entregas ágeis e de alta qualidade. Para isso, se faz necessário reduzir os intervalos entre testes, versões e publicações. É aí que entra em cena o GitLab Ci, que permite [integração contínua](https://blog.engdb.com.br/integracao-via-api/) e acelera o desenvolvimento de novos projetos.

Com o surgimento do [Development Operations (DevOps)](https://blog.engdb.com.br/devops/), que propõe a integração das equipes de desenvolvimento, o GitLab Ci é um poderoso aliado para trazer mais praticidade ao trabalho de TI, já que ele derruba as barreiras existentes entre desenvolvedores e testadores, bem como aproxima os analistas de negócio e infraestrutura.

Neste post, mostramos como essa ferramenta que se tornou essencial no ambiente de TI e ajuda a criar uma cultura de cooperação. Continue lendo para ficar por dentro do assunto!

## O que é o GitLab Ci?

Antes de falarmos do GitLab Ci, precisamos apresentar o seu precursor: o GitLab, que consiste em um gerenciador de repositórios de [software](https://blog.engdb.com.br/cloud-solution/), cujo funcionamento se baseia em git — sistema de versões distribuído usado para desenvolver softwares —, além de contar com o suporte de gerenciamento de tarefas, Wiki e CI/CD.

Apesar de ser semelhante a outras plataformas, o GitLab se diferencia por possibilitar que os desenvolvedores armazenem o código dentro dos seus próprios servidores, em vez de deslocá-los para servidores terceirizados. Trata-se de um programa livre, que pode ser utilizado por qualquer profissional de TI, e é disponibilizado pela Licença MIT.

O GitLab Ci caracteriza-se como um ambiente de Integração Contínua, que pertence ao GitLab, e oferece suporte para continuous integration (integração contínua), continuous deployment (implantação contínua) e continuous delivery (entrega contínua).

Por meio dessa ferramenta, os desenvolvedores podem trabalhar de forma conjunta na criação de projetos privados ou abertos. Dentro da plataforma, todo projeto que tem um código-fonte é classificado como repositório (lugar que arquiva alterações). Cada código-fonte é armazenado separadamente, adicionando organização e praticidade para o time.

## Como usar o GitLab Ci?

Para usufruir dos benefícios proporcionados pelo GitLab Ci, basta ter um projeto pronto e configurado para rodar em headless. Vamos para a parte prática? Acompanhe o passo a passo para adotar a ferramenta na sua empresa sem erros.

### Crie uma conta no GitLab e um repositório

Primeiramente, o usuário deve criar uma conta para acessar o GitLab e, logo em seguida, criar um repositório. Depois, é preciso clonar o repositório e adicionar o projeto que vai ser trabalhado dentro do repositório aberto anteriormente.

### Configure o gitlab-ci.yml

Feitos os passos anteriores, você tem um projeto que já pode ser disponibilizado no GitLab. Mas para prosseguir, há que se configurar o arquivo gitlab-ci.yml, aplicado pelo GitLab Runner com o intuito de promover o controle do projeto conforme o seu andamento.

Vá até a pasta raiz do projeto, clique para abrir e, a partir daí, crie o arquivo gitlab-ci.yml. Esse arquivo é de suma importância para definir quais ações devem ser realizadas, a ordem que terão que respeitar e demais condições a serem seguidas.

### Adicione comandos no gitlab-ci.yml

Após concluir a criação do arquivo, é o momento de adicionar os comandos que garantem o seu funcionamento adequado. São os seguintes:

- **image:** o GitLab Ci trabalha em parceria com a ferramenta Docker. Sendo assim, o comando possibilita a especificação de uma imagem personalizada da Docker, além de uma lista com os serviços que poderão ser usados;
- **stages:** é responsável por determinar os estágios que podem ser executados ao longo do projeto. Ele é definido globalmente;
- **runscript:** consiste no script que pode ser nomeado como o usuário quiser;
- **script:** entendido como um script de shell rodado pelo Runner, é a palavra-chave obrigatória para o projeto;
- **artifacts:** tem a finalidade de especificar a lista de arquivos e diretórios a serem anexados ao job depois do seu sucesso;
- **paths:** detalha o caminho que vai ser trilhado pelo arquivo.

Agora que você adicionou todos os comandos necessários, é só dar commit e push no repositório. Por último, acesse o repositório para checar se a Ci está funcionando. Se a resposta for positiva, o sistema estará pronto para rodar [testes automatizados](https://blog.engdb.com.br/testes-automatizados/).

## Como configurar pipelines de integração contínua?

Quando a equipe de TI trabalha com a integração contínua, ela ganha facilidade e [agilidade](https://blog.engdb.com.br/metodologias-ageis/) para testar uma feature em um ambiente que se parece com o de produção e efetuar o deploy (implantação) somente depois da aprovação de todos os testes, ampliando a velocidade e a qualidade da entrega do software.

Com a aplicação de testes regressivos, pode-se criar produtos mais eficientes, sabendo que possíveis novas falhas e bugs não serão adicionados à versão principal do programa. A jornada pela qual o software passa no decorrer da integração contínua é conhecida como pipeline — processo que precisa ser realizado em um lugar específico.

Nesse contexto, é essencial ter à sua disposição um Runner, que é a máquina para rodar a Ci. Ela pode estar alocada no seu computador, em um servidor ou na nuvem. A configuração do pipeline de integração contínua pode ser feita de diferentes maneiras, sempre levando em conta as ferramentas exigidas pelo projeto. Caso utilize o Docker, independentemente do local em que o Runner será rodado, é necessário instalá-lo.

A seguir, explicamos como fazer essa configuração.

### Faça a codificação do pipeline

Tudo começa com a definição da imagem da build, que pode ser java 1.8, por exemplo. Dessa forma, a codificação ficaria “image:java:8”.

### Estabeleça os stages

Os stages são as etapas do pipeline. Em um exemplo simples, eles podem ser: test e build. Tenha em mente que é preciso dar três espaços na codificação para estruturar a hierarquia de comandos. Portanto, a configuração seria:

stages:

 – test

 – build

Além disso, deve-se acrescentar um passo que precede os stages, por meio do comando “before_script:”, que fica:

before_script:

 – chmod +x mvnw

Esse passo prepara as permissões do arquivo mvnw, que funciona como um shell script do maven, para dar sequência ao build do projeto em execução. Quem começa o projeto utilizando starter do spring tem esses arquivos automaticamente.

### Defina os comandos

O primeiro dos comandos a ser definido é o de test. Coloque o nome do comando como test, depois determine o estágio de execução como teste e edite o script para “mvnw test”, para assegurar o comando do maven e a efetuação dos testes.

O próximo stage tem que ser nomeado como “build”. Já no script é preciso inserir “./mvnw package”, o que permite gerar o jar via maven. Para fechar, defina os artifacts, ou seja, os artefatos que serão produzidos pela build e deverão ser armazenados. Basicamente, essa feature do GitLab cumpre o papel de armazenar, no seu repositório, todas as versões trabalhadas no pipeline.

Terminados todos os passos, é hora de testar seu pipeline. Para tanto, é só subir o commit para o GitLab — ação que dispara a build do projeto de maneira automática. Se você quiser conferir as builds em execução, visite a home do repositório, localizada no menu lateral, depois selecione “CI/CD” e “Pipelines”.

Como você viu, o GitLab Ci facilita a rotina de operações da sua equipe de TI. Afinal, a ferramenta possibilita o trabalho conjunto dos desenvolvedores e melhora a [gestão de projetos](https://blog.engdb.com.br/gestao-de-projetos-de-ti/), eliminando gargalos que reduzem a eficiência do software, o que resulta em entregas mais ágeis e com alto nível de satisfação.

Este post te ajudou? Então, [vem seguir o nosso LinkedIn](https://www.linkedin.com/company/engineeringbr/) para acompanhar as novidades mais quentes do mundo da tecnologia!