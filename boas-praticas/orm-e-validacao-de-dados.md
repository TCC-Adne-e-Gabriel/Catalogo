# ORM e Validação de Dados

Esta boa prática foi implementada no projeto como parte da [PoC 2](../provas-de-conceito/poc-2-autenticacao-e-comunicacao.md). Para mais detalhes sobre uma aplicação dessa prática em um sistema, visite a prova de conceito em questão.

Esta prática concentra-se na utilização do SQLAlchemy, um ORM que fornece uma camada de abstração para acesso ao banco de dados, e a utilização da biblioteca de Python Pydantic para validação de dados.

### Benefícios do SonarCloud em Microsserviços

* **Robustez e Segurança**: Evita a coleta e tentativa de utilização de dados indesejados pelo banco dados, assim como ataques cibernéticos como SQL Injection.
* **Legibilidade e manutenabilidade:** A abstração do ORM ao banco de dados promove uma estrutura de código mais segura, legível e de fácil escalabilidade e manutenção.
* **Retorno Precoce:** Ao utilizar o Pydantic, um endpoint que receba um dado fora do esperado retorna automaticamente, com o erro **"422 Unprocessable Entity"**.
* **Continuidade de dados:** Previne o envio de dados incorretos entre microsserviços, evitando conflitos e erros.

Para começar, utilize o comando Pip para instalação de ambos Pydantic e SQLAlchemy, seguindo o guia existente na documentação de ambos.
