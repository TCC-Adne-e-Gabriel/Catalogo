# Arquitetura de Software

### Arquitetura de Software

Análises sobre a Arquitetura de Software têm recebido bastante atenção nas últimas décadas, pois é notável, com a prática, que ter uma arquitetura adequada em um _software_ é um fator crítico para seu sucesso (GARLAN, 2000).&#x20;

A Arquitetura de Software é uma parte relevante do processo de _design_ de um _software_, e pode ser definida como a organização das estruturas do sistema, envolvendo os elementos do _software_ e os relacionamentos entre esses diferentes componentes (BASS et al., 2003)

Importante enfatizar que não existe estilo arquitetural que se adeque a **todos** os projetos e aplicações, mas é importante que a decisão do estilo arquitetural leve em conta o contexto que o projeto está inserido, com suas especificações. A escolha da arquitetura do serviço pode impactar significativamente na adição de funcionalidades e manutenção do sistema.&#x20;

No decorrer do catálogo, dois estilos arquiteturais serão os mais abordados: O de Microsserviços e o Monolítico, porém, existem outros diversos estilos arquiteturais.&#x20;

### Arquitetura Monolítica

A Arquitetura Monolítica, de acordo com Fowler (2014), é um modelo tradicional\
de desenvolvimento de software em que um sistema é construído em apenas uma unidade.\
As aplicações monolíticas normalmente são compostas por um dispositivo de acesso por parte do usuário, a aplicação em si, e o banco de dados.

Vantagens de utilização da Arquitetura Monolítica:&#x20;

* Gestão e Monitoramento centralizados;&#x20;
* _Deploy_ único;
* Testes mais simples, pois não existe a necessidade de testes de integração com outros serviços para uma funcionalidade, e
* Menor latência de comunicação.

Porém, a depender da forma em que é construída, as arquiteturas monolíticas podem apresentar as seguintes desvantagens, segundo Richardson (2021):&#x20;

* Dificuldade de escalabilidade à medida em que os sistemas vão se tornando maiores e mais complexos;
* Dificuldade de manter uma boa estrutura modular, pois mesmo com ferramentas\
  e tecnologias que facilitem a modularização de sistemas, à medida que o código fonte aumenta de escopo, torna-se mais difícil mantê-lo com uma boa estrutura e modularização;
* À medida que a aplicação cresce em tamanho, o tempo de execução das _pipelines_ de _deploy_ e de qualidade de código aumenta também, e
* Diante da necessidade de escalar serviços que são abrigados em arquitetura monolítica, essa escalabilidade só pode ser conferida replicando o sistema monolítico como um todo, aumentando significativamente o custo de infraestrutura.

### Arquitetura de Microsserviços

Segundo Flower (2014), o estilo arquitetural de microsserviços propõe uma abordagem para desenvolver uma aplicação como um conjunto de pequenos serviços, cada um rodando um processo específico e se comunicando com os outros serviços através de sistemas de mensagerias. Dentre os princípios de microsserviços definidos por Martin Flower, estão:&#x20;

* **Independência:** Cada serviço construído como uma unidade independente;&#x20;
* **Organização por negócio:** Os serviços são organizados em módulos de negócios e exigem implementação de _software_ para a interface de usuário (_Front-End_), o banco de dados, e a aplicação do lado do servidor (_Back-End_);
* **Design para falhas:** As aplicações devem ser desenhadas de forma que consigam tolerar falhas em sistemas, e
* **Gerenciamento de dados descentralizado:** Cada serviço deve possuir o seu próprio banco de dados.

A Figura a seguir mostra um comparativo entre os dois estilos arquiteturais:&#x20;

<figure><img src=".gitbook/assets/martinflower.png" alt=""><figcaption></figcaption></figure>

&#x20;                                                           Fonte: Flower (2014)

Porém, a utilização de sistemas distribuídos também é caracterizada pela aparição de novos desafios.



### Referências

GARLAN, D.; SHAW, M. Introduction to software architecture. In: . \[S.l.]: Springer\
Nature, 2009

BASS, L.; CLEMENTS, P.; KAZMAN, R. Software Architecture in Practice. \[S.l.]:\
Addison-Wesley Professional, 2003. Google-Books-ID: mdiIu8Kk1WMC. ISBN\
978-0-321-15495-8.

FOWLER, M. Microservices. 2014. Disponível em: \<https://martinfowler.com/articles/\
microservices.html>.

RICHARDSON, C. When to use the microservice architecture: part 5 - the monolithic architecture and rapid, frequent, reliable and sustainable software delivery. 2021. Disponível em: \<https://microservices.io/post/microservices/2021/02/14/ why-microservices-part-5-monolith.html>



