# PoC 3 - Gerenciamento de Containers e Serviços

### Definição

Essa PoC consiste na aplicação de boas práticas de segurança na _conteinerização_ dos microsserviços, utilizando o **Kubernetes** como orquestrador e comunicação segura baseada no Protocolo de **TLS**.\
Por meio da _**API Gateway**_, implementaram-se mecanismos de roteamento de requisições, enquanto o Kubernetes proporciona o escalonamento e distribuição.

### Boas práticas trabalhadas

* Utilização de [Kubernetes](../../boas-praticas/kubernetes.md) para gerenciamento dos _containers_;
* Utilização do Protocolo de Comunicação Segura via [TLS](../../boas-praticas/comunicacao-segura-com-tls.md), e
* Restrição de acesso a APIs públicas com [API Gateway](../../boas-praticas/api-gateway.md).

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

* U

### Desenvolvimento

Portanto, foi possível seguir para as etapas de desenvolvimento da PoC em questão:

1. F

### Análise de Resultados
