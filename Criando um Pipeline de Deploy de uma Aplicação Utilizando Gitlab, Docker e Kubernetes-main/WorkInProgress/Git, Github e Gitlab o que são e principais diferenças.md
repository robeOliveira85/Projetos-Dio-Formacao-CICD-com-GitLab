# Git, Github e Gitlab: o que são e principais diferenças

- [Desenvolvimento](https://www.zup.com.br/categorias/desenvolvimento)
- • 3 out 2019
- 

<iframe width="100%" height="83" scrolling="no" src="https://go.vooozer.com/embed/08520a74" frameborder="0" allowfullscreen="" style="box-sizing: border-box; max-width: 100%; width: 664px; margin: 0px; line-height: 1; border: none; height: 83px !important;"></iframe>

#### Neste artigo você vai ver:

- [O que é Git?](https://www.zup.com.br/blog/git-github-e-gitlab#texto-blog)
  - [Principal funcionalidade](https://www.zup.com.br/blog/git-github-e-gitlab#texto-blog)
- [Github e Gitlab, o que são?](https://www.zup.com.br/blog/git-github-e-gitlab#texto-blog)
  - [Funcionalidades](https://www.zup.com.br/blog/git-github-e-gitlab#texto-blog)
- [‍Conclusão](https://www.zup.com.br/blog/git-github-e-gitlab#texto-blog)
  - [Referências ](https://www.zup.com.br/blog/git-github-e-gitlab#texto-blog)

Pode parecer complicado para quem está entrando no mundo de desenvolvimento assimilar as várias ferramentas e tecnologias que existem, mas é fundamental que você saiba o que é **Git** e, principalmente, saber que não é a mesma coisa que **GitHub** ou **GitLab**.


Neste artigo vamos te contar tudo o que você precisa saber sobre **Git, Github e Gitlab**. Vamos lá?

## O que é Git?

Git é considerado o arroz com feijão de projetos de desenvolvimento. Não importa qual seja sua especialidade, você vai precisar dele e é importante que saiba utilizá-lo do jeito certo.

Pela [documentação oficial](https://git-scm.com/), **Git é um sistema de controle de versão distribuído de código aberto e gratuito, projetado para lidar com tudo, de projetos pequenos a grandes**. O que isso significa? Significa que com o Git é possível manter um histórico das alterações dos seus arquivos, sabendo quem, por que e quando um arquivo foi editado.

### Principal funcionalidade

A principal funcionalidade do Git, que o faz ser amplamente utilizado em projetos de desenvolvimento de software, é **a possibilidade de fazer o controle de versões de modo colaborativo,** ou seja, é possível que o mesmo arquivo seja modificado ao mesmo tempo por duas pessoas da área de desenvolvimento, e que ambas as alterações sejam salvas sem que nenhum código seja sobrescrito.

Para permitir o modo colaborativo, o Git utiliza o conceito de ramificação ou *branch*, onde cada *branch* é uma linha do tempo que possui marcos ou *commits*, e nesse *branch* os arquivos podem ser alterados livremente sem impactar outras ramificações.

Sendo assim, é possível trabalhar em ramos separadamente, desenvolvendo novas funcionalidades ou fazendo correções de *bugs*, e então quando decidirem juntar os dois ramos, o Git utiliza o conceito de mesclagem ou merge para isso.

A imagem abaixo ilustra quatro ramos sendo atualizados paralelamente ao longo do tempo através de *commits*, e então o *branch feature* sendo mesclado no *branch develop* através do processo de *merge*.

![Exemplo de ramos sendo usados de forma paralela no Git. O conteúdo foi detalhado no parágrafo anterior.](https://www.zup.com.br/wp-content/uploads/2022/03/5d9644cf2ae9dfab105b16a3_git-github-e-gitlab.png)

Mas, o que tudo isso tem a ver com GitHub ou GitLab? Antes de explicar como o Git se relaciona com esses outros dois termos, vamos às explicações de GitHub e GitLab.

## Github e Gitlab, o que são?

**GitHub e GitLab são plataformas de hospedagem de código-fonte. Elas permitem que profissionais de desenvolvimento contribuam em projetos privados ou abertos** (mais conhecidos como projetos [open source](https://www.zup.com.br/blog/open-source-no-brasil)).

Nessas plataformas, cada projeto contendo um código-fonte é considerado um repositório. Por exemplo, se você participa de projeto em que é desenvolvido o site de um *e-commerce*, e o código do [*front-end*](https://www.zup.com.br/blog/desenvolvimento-front-end) é desenvolvido separadamente do código [*back-end*](https://www.zup.com.br/blog/back-end-na-zup), cada um desses códigos-fontes serão hospedados como repositórios separados.

As duas plataformas oferecem vários recursos similares para hospedagem de código-fonte, sendo alguns como *pull request*, revisão de código, edição *inline*, *fork* e clone de repositórios, além de integrações com ferramentas de terceiros.



### Funcionalidades

Uma das principais funcionalidades que difere uma plataforma da outra é o foco que o GitLab vem dando à integração com ferramentas de [DevOps](https://www.zup.com.br/blog/tudo-sobre-devops). O GitLab proporciona, nativamente, ferramentas de integração e entrega contínua ou CI/CD, além de métricas para acompanhamento de qualidade de código, performance e teste de usabilidade.

E como tudo isso se relaciona com o Git? Ambas fazem o controle de versão dos projetos hospedados utilizando o Git. Desse modo, quando você utiliza o Git no seu projeto, você pode acompanhar o versionamento do seu repositório em uma dessas plataformas.

No geral, as duas plataformas são muito boas para hospedagem de código, cabe a você decidir qual delas faz mais sentido utilizar no seu projeto, uma vez que as duas utilizam Git como controle de versão.

Quer levar o seu controle de versões para o próximo nível? Então conheça o que é [Git Workflow](https://www.zup.com.br/blog/git-workflow) e três tipos que ele possui: Git Flow, GitLab Flow e GitHub Flow. 

## ‍Conclusão

Ainda ficou com alguma dúvida sobre as características e como utilizar Git, GitHub ou GitLab? Conte pra gente nos comentários.

Se esse artigo foi útil pra você, aproveite para compartilhar com alguém que precisa muito entender sobre o assunto.

[![img](https://www.zup.com.br/wp-content/uploads/2022/06/News-_-Banner-03-1024x128.png)](https://insights.zup.com.br/newsletter?utm_source=insights&utm_medium=referral&utm_campaign=banner&utm_term=git)

### Referências 

- [Documentação oficial Git](https://git-scm.com/)
- [GitHub](https://github.com/)
- [Sobre o GitHub](https://docs.github.com/en/get-started/quickstart/hello-world)
- [GitLab](https://about.gitlab.com/)
- [Sobre o GitLab](https://about.gitlab.com/what-is-gitlab/)