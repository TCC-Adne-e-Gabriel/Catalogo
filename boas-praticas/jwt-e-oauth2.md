# JWT e OAuth2

Esta boa prática foi implementada no projeto como parte da [PoC 2](../provas-de-conceito/poc-2-autenticacao-e-comunicacao/). Para mais detalhes sobre uma aplicação dessa prática em um sistema e suas especificações, visite a prova de conceito em questão.

Esta prática concentra-se na utilização de práticas de _**OAuth2 (**_[_**https://oauth.net/2/**_](https://oauth.net/2/)_**)**_, com _tokenização_ por meio dos _**JSON Web Tokens (**_[_**https://jwt.io/introduction**_](https://jwt.io/introduction)_**)**_, para promover a Autorização e Autenticação no sistema.

### Benefícios em Arquitetura de Microsserviços

* **Assinatura de Token**: Cada _JWT_ é criptograficamente assinado, o que significa que\
  clientes ou partes mal-intencionadas não podem modificar o conteúdo _JSON_.
* _**Token**_**&#x20;Autocontido:** Pela garantia e expiração, outros sistemas não precisam consultar o serviço de usuários para verificar permissões, o que reduz latência nas requisições de serviços distribuídos.
* **Gerenciamento Seguro de Fluxos de Autorização:** _OAuth_ é descrito como uma maneira segura de gerenciar fluxos de autorização, melhorando a segurança em microsserviços.
* **Vulnerabilidade OWASP A01 - Quebra de Controle de Acesso:** Atua diretamente na resolução da vulnerabilidade, trazendo robustez ao controle de acesso e processos de autorização e autenticação.

Para começar, acesse a documentação de ambos [_OAuth_](https://oauth.net/2/) e [_JSON_ _Web_ _Tokens_](https://jwt.io/introduction), e configure-os em seu projeto.

