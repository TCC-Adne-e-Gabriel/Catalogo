# API Gateway

Esta boa prática foi implementada no projeto como parte da [PoC 3](../provas-de-conceito/poc-3-gerenciamento-de-containers-e-servicos.md). Para mais detalhes sobre uma aplicação dessa prática em um sistema, visite a prova de conceito em questão.

Esta prática concentra-se na utilização do API Gateway como parte do roteamento de quaisquer requisições entre os microsserviços, como único ponto de entrada.

### Benefícios em Arquitetura de Microsserviços

* **Roteamento Inteligente**: Mesmo em arquiteturas complexas, é capaz de abstrair as múltiplas rotas ou microsserviços, facilitando seu roteamento.
* **Configuração de Segurança:** Por possuir um único ponto de entrada, possibilita a aplicação de configurações de segurança em um único local.
* **Vulnerabilidade OWASP A04 - Design Inseguro:** Ao permitir um único ponto de entrada, unifica os microsserviços e melhora a robustez de suas interações.

Para começar, acesse a documentação de um API Gateway, e procure configurá-lo em seu projeto.
