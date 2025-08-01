# PoC 3 - Gerenciamento de Containers e Serviços

### Definição

Essa PoC consiste na aplicação de boas práticas de segurança na _conteinerização_ dos microsserviços, utilizando o **Kubernetes** como orquestrador e comunicação segura baseada no Protocolo de **TLS**.\
Por meio da _**API Gateway**_, implementaram-se mecanismos de roteamento de requisições, enquanto o Kubernetes proporciona o escalonamento e distribuição.

### Boas práticas trabalhadas

* Utilização de [Kubernetes](../../boas-praticas/gerenciamento-de-containers.md) para gerenciamento dos _containers_;
* Utilização do Protocolo de Comunicação Segura via [TLS](../../boas-praticas/comunicacao-segura-entre-microsservicos.md), e
* Restrição de acesso a APIs públicas com [API Gateway](../../boas-praticas/roteamento-de-trafego.md).

### Planejamento

As vulnerabilidades do **OWASP Top Ten** implantadas nessa PoC foram as seguintes:

* _**A04 - Insecure Design:**_ A primeira vulnerabilidade explorada foi o _design_ inseguro dos\
  &#xNAN;_&#x63;ontainers_ da aplicação, tornando visível em prática quais seriam as consequências\
  de uma aplicação estruturada arquiteturalmente de maneira incorreta;
* _**A05 - Security Misconfiguration:**_ Do mesmo modo, as configurações de segurança de\
  uma aplicação conteinerizada também podem trazer vulnerabilidades ao sistema,\
  causando, por exemplo, a perda dos dados pessoais dos usuários;
* _**A10 - Server-Side Request Forgery:**_ Devido à complexidade de uma Arquitetura de\
  Microsserviços, o uso de ataques _SSRF_ (_Server-Side Request Forgery_) para requisições indevidas na comunicação entre serviços é crescente, e
* _**A08 - Software and Data Integrity Failures:**_ A falha de integridade de dados também\
  pode ocorrer em caso de comunicação com os serviços.



Com as vulnerabilidades em mente, o planejamento dessa PoC seguiu com as seguintes tarefas:

* Orquestração de Containers (JAMSHIDI et al.,\
  2018\);&#x20;
* Utilização do protocolo de comunicação segura via TLS (GONZALEZ; ORTIZ,\
  2024\), e
* Restrição de acesso a APIs públicas com API Gateway.

### Desenvolvimento

Portanto, foi possível seguir para as etapas de desenvolvimento da PoC em questão:

1. [Orquestração de Containers](gerenciamento-de-container-com-kubernetes.md);
2. [Implementação de comunicação segura via TLS](implementacao-de-comunicacao-segura-via-tls.md), e&#x20;
3. [API Gateway](api-gateway-ingress.md).

### Análise de Resultados

Após a aplicação das boas práticas ao desenvolvimento da prova de conceito, foi possível realizar uma análise dos resultados obtidos, presente no seguinte tópico: [Análise de Resultados](analise-de-resultados.md).

### Referências

JAMSHIDI et al. Microservices: The journey so far and challenges ahead. IEEE Software, 2018. Acessado em: 07 jan. 2025

GONZALEZ, S.; ORTIZ, I. Overcoming challenges in microservice architetures. ResearchGate, 2024. Acessado em: 07 jan. 2025. Disponível em: \<https://www. researchgate.net/publication/386219405\_Overcoming\_Challenges\_in\_Microservice\_ Architectures>
