# Comunicação Segura com TLS

Esta boa prática foi implementada no projeto como parte da [PoC 3](../provas-de-conceito/poc-3-gerenciamento-de-containers-e-servicos.md). Para mais detalhes sobre uma aplicação dessa prática em um sistema e suas especificações, visite a prova de conceito em questão.

Esta prática concentra-se na utilização da conexão TLS para segurança de requisições entre os microsserviços.

### Benefícios em Arquitetura de Microsserviços

* **Certificado TLS**: Certificado que provém autenticação de identidade ao subdomínio de uma aplicação.&#x20;
* **Autorização e Autenticação:** Requisições ao subdomínio da aplicação passam a requerir o Certificado TLS.
* **Segurança de Requisições:** Requisições previamente em HTTP recebem uma camada de segurança com o HTTPS, realizada através do navegador a ser utilizado.

Para começar, acesse a documentação de uma possibilidade de criação de Certificado do TLS, e procure configurá-lo em seu projeto.
