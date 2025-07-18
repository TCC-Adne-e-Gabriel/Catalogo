# API Gateway

Esta boa prática foi implementada no projeto como parte da [PoC 3](../provas-de-conceito/poc-3-gerenciamento-de-containers-e-servicos/). Para mais detalhes sobre uma aplicação dessa prática em um sistema e suas especificações, visite a prova de conceito em questão.

Esta prática concentra-se na utilização do _API Gateway_ como parte do roteamento de quaisquer requisições entre os microsserviços, como único ponto de entrada.

### Benefícios em Arquitetura de Microsserviços

* **Roteamento Inteligente**: Mesmo em arquiteturas complexas, é capaz de abstrair as múltiplas rotas ou microsserviços, facilitando o roteamento entre elas.
* **Configuração de Segurança:** Por possuir um único ponto de entrada, possibilita a aplicação de configurações de segurança em um único local, diminuindo a complexidade de operações e melhorando a escalabilidade.
* Integração com Kubernetes: É possível, ao integrar uma _API Gateway_ ao Kubernetes com ferramentas como o _**API Ingress**_, trabalhar diretamente com _clusters_ em sua configuração.
* **Vulnerabilidade OWASP A04 - Design Inseguro:** Ao permitir um único ponto de entrada, unifica os microsserviços e melhora a robustez de suas interações.

Para começar, acesse a documentação de um _API Gateway_ como o [Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/), e procure configurá-lo em seu projeto.
