# Criação de uma imagem do Docker a partir do zero

**Creating Docker Image From Scratch**

A principal vantagem do Docker sobre qualquer outra tecnologia de conteinerização é que o Docker é voltado para desenvolvedores e seus aplicativos de upstack. Embora as tecnologias de contentorização adequadas, como [LXC](https://linuxcontainers.org/) , [Zonas](https://wiki.smartos.org/display/DOC/Zones) e [Prisões](https://wiki.freebsd.org/Jails) são direcionados de uma perspectiva de operações ou, para simplificar, essas plataformas são um substituto para as máquinas virtuais em execução na nuvem. Onde as, Docker é um substituto para pacotes e binários executáveis.



Em termos gerais, o Docker está se tornando cada vez mais como um gerenciador de pacotes universal que funciona em todas as plataformas Linux possíveis. Ele pega contêineres e os usa para resolver um problema completamente diferente que os desenvolvedores enfrentam. O problema é que os desenvolvedores usam seu sistema operacional de desktop (como Windows, macOS ou Linux com uma tonelada de pacotes relacionados a desktop) para escrever aplicativos. O aplicativo que eles escrevem geralmente é executado em um sistema operacional completamente diferente em um servidor em algum lugar com alguma distribuição Linux completamente diferente daquela do laptop do desenvolvedor.

------





------



<iframe src="https://www.youtube.com/embed/yhyc3-Namto?modestbranding=1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" style="box-sizing: border-box; position: absolute; top: 0px; left: 0px; width: 588.5px; height: 370px;"></iframe>



Com o Docker, a ideia é que seu aplicativo venha empacotado como uma imagem do Docker. É função do Docker pegar essa imagem e executá-la como um aplicativo em contêiner para você. Estar em contêiner significa que o aplicativo e suas dependências serão executados em um ambiente isolado que pode ser completamente diferente do laptop do desenvolvedor e até mesmo do servidor de produção. Contanto que ambos suportem Docker, ambos podem executar o mesmo aplicativo exatamente da mesma maneira.


[![img](https://optad360.mgr.consensu.org/icons/branding-ads.svg)](https://en.optad360.com/?utm_source=branding&utm_medium=display&utm_campaign=pt.softoban.com)

## **Anatomia de uma imagem Docker**

Conforme mencionado anteriormente, um aplicativo Docker será executado em um ambiente acordado. Agora, a questão é como criamos esse ambiente? A maioria das imagens de aplicativo importaria uma imagem base do Docker e construiria seu aplicativo sobre ela.


[![img](https://optad360.mgr.consensu.org/icons/branding-ads.svg)](https://en.optad360.com/?utm_source=branding&utm_medium=display&utm_campaign=pt.softoban.com)

Os aplicativos são feitos de camadas de software. Uma imagem de contêiner wordpress é construída usando uma imagem de contêiner httpd que, por sua vez, é construída sobre uma imagem do Ubuntu. A imagem sobre a qual uma imagem mais recente é construída é conhecida como IMAGEM PRINCIPAL na terminologia do Docker. No Dockerfile (veremos o que significa Dockerfile, um pouco mais tarde), esta imagem pai é mencionada na parte superior do arquivo, conforme mostrado abaixo:

------





------

DO Ubuntu: 18.04
\## Resto do Dockerfile

Este Dockerfile, quando executado, converte seu aplicativo em uma imagem Docker (uma espécie de binário) que você pode enviar para um registro de onde pode ser puxado para criar novos contêineres em outro lugar. No entanto, todos eles terão o Ubuntu: 18.04 como imagem base e serão executados como se fosse um sistema Ubuntu em que estão sendo executados.

Você deve ter notado isso ao tentar puxar uma nova imagem do docker.


ad

![Criação de imagem Docker a partir do zero](https://softoban.com/img/docker/71/creating-docker-image-from-scratch.png)

Isso mostra quantas camadas são extraídas antes que o aplicativo real (que pode ter apenas alguns megabytes de tamanho) seja trazido.

Por este motivo, gostaríamos de criar o que é conhecido como imagem de base. Que não é construído em cima de mais nada. A palavra-chave scratch é usada para indicar que essa camada não foi construída sobre nenhuma outra. Igual a:

Do princípio
\## Resto do Dcokerfile

Primeiro criaremos um aplicativo simples de hello-world e, em seguida, descobriremos como será o resto do Dockerfile. O sistema host é Ubuntu: 18.04 LTS e estamos usando o Docker versão 17.12.1-ce para o experimento.

### **Criação de um binário estático**

Os contêineres do Docker são um conjunto de processos executados isolados do restante do sistema operacional. A única coisa com a qual esse processo está em contato é o kernel. O kernel é responsável por agendar esses processos na CPU, fazer o gerenciamento de memória e algumas outras tarefas básicas de manutenção de reserva.

Mas a maioria dos aplicativos de alto nível depende de muitas bibliotecas do sistema (como *glibc, musl, klibc, etc* ) e muitas dependências de tempo de execução como Python ou Node.js ou Java Runtime. O binário do aplicativo não tem todas as bibliotecas disponíveis dentro dele, mas quando começa a execução, ele chama essas bibliotecas do sistema operacional host.

Como estamos tentando criar uma imagem do zero, não receberíamos essas sutilezas. Portanto, nosso aplicativo precisa ser um arquivo estático ou um executável autônomo.

Vamos começar criando uma pasta chamada MyDockerImage e criando um arquivo hello.cc dentro dela.

$mkdirMyDockerImage
$CDMyDockerImage
$tocarola.cc

Abra hello.cc usando seu editor de texto favorito e adicione as seguintes linhas dentro dele.

\#incluir
usando namespace std;
inta Principal(){
custo<< 'Olá! Esta mensagem vem de um contêiner n';
Retorna 0;

}

Este é um programa C ++ simples que imprime Hello! Esta mensagem …

Por razões discutidas anteriormente, vamos compilar isso usando o sinalizador estático. O compilador usado é *g ++ (Ubuntu 7.3.0-16ubuntu3) 7.3.0.*

Para compilar o programa, execute no mesmo diretório o seguinte comando:

$ g++ -oi olá-estáticoOlá.DC

Isso cria um arquivo binário executável hello no mesmo diretório. Esse é o nosso arquivo estático. Teste se ele está funcionando conforme o esperado, mencionando o nome do arquivo no terminal.

$./Olá

![img](https://softoban.com/img/docker/71/creating-docker-image-from-scratch-2.png)

Agora estamos prontos para colocar este programa simples em contêineres.

### **Dockerfile**

O Dockerfile consiste em um conjunto de regras que pega seus arquivos de aplicativo (como binários, arquivos de origem, etc) junto com vários parâmetros de configuração, como layout do sistema de arquivos, portas expostas, etc, e os transforma em um arquivo de imagem Docker. Você pode então compartilhar o arquivo de imagem com qualquer pessoa que queira executar esse aplicativo.

Não vamos explorar todas as opções disponíveis para o Dockerfile, em vez disso, vamos escrever um Dockerfile muito minimalista. No mesmo diretório, onde reside o seu executável hello, crie um arquivo vazio chamado *Dockerfile.*

$tocarDockerfile

Abra-o com seu editor de texto favorito e escreva as seguintes linhas nele:

Do princípio
ADICIONE olá/
CMD['/Olá']

*coçar, arranhão* não é uma imagem principal. Em vez disso, indica ao Docker que a imagem não foi construída sobre nenhuma outra imagem. Ele é construído do zero. O comando ADD pegaria o binário estático denominado `hello` do diretório atual e o adicionaria ao diretório raiz do arquivo de imagem. Quando finalmente executarmos um contêiner baseado nesta imagem, o executável hello será visto dentro do próprio diretório raiz em `/hello.`

Por último, a linha CMD tem uma string */Olá* esta string será executada como um comando shell sempre que um contêiner for criado a partir dessa imagem, portanto, o arquivo binário que adicionamos ao nosso contêiner e imprimirá a mensagem que escrevemos em nosso aplicativo.

Vamos construir a imagem invocando o *construção docker* comando que iria percorrer o conteúdo do Dockerfile e gerar a imagem. Execute o seguinte comando no mesmo diretório que o Dockerfile e o binário executável.

$construção docker--marcaçãoOlá .

o *-Tag olá* flag define o nome da imagem para *Olá* e o ponto ( *. )* no final diz *construção docker* para procurar no diretório atual o Dockerfile e conteúdos relacionados.

### **Executar o contêiner do Docker**

Para verificar se a imagem que acabamos de criar aparece na lista de imagens, execute:

$imagens docker

![img](https://softoban.com/img/docker/71/creating-docker-image-from-scratch-3.png)

Observe como a imagem de olá é pequena quando comparada a outras imagens. Em qualquer caso, ele está pronto para ser executado como um contêiner,

$docker corre olá

![img](https://softoban.com/img/docker/71/creating-docker-image-from-scratch-4.png)

É isso! Você criou seu primeiro contêiner minimalista do zero.

### **Outras opções**

Embora criar imagens do zero seja sempre uma opção, as pessoas geralmente tendem a criar imagens de outras distros leves do Linux. Por exemplo, imagens como alpine e busybox são ambientes realmente leves com bibliotecas menores como musl em vez de glibc.

Usá-los como sua imagem principal usando *FROM alpine: mais recente* resultaria em imagens menores também. Uma vez que as imagens de base têm apenas 2 a 5 MB de tamanho. Informe-nos se houver algum tópico relacionado ao Docker que você queira que abordemos a seguir. Você pode nos contatar no [Twitter](https://twitter.com/linuxhint) , [Faceb](https://www.facebook.com/LinuxHint-1321325764663109)