# JWT e OAuth2

Esta boa prática foi implementada no projeto como parte da [PoC 2](../provas-de-conceito/poc-2-autenticacao-e-comunicacao.md). Para mais detalhes sobre uma aplicação dessa prática em um sistema, visite a prova de conceito em questão.

Esta prática concentra-se na utilização de práticas de OAuth2, com tokenização por meio dos JSON Web Tokens, para promover a Autorização e Autenticação no sistema.

### Benefícios em Arquitetura de Microsserviços

* **Assinatura de Token**: Cada JWT é criptograficamente assinado, o que significa que\
  clientes ou partes mal-intencionadas não podem modificar o conteúdo JSON.
* **Token autocontido:** Pela garantia e expiração, outros sistemas não precisam consultar o serviço de usuários para verificar permissões, o que reduz latência\
  nas requisições de serviços distribuídos.
* **Gerenciamento Seguro de Fluxos de Autorização:** OAuth é descrito como uma maneira segura de gerenciar fluxos de autorização, melhorando a segurança em microsserviços.
* **Vulnerabilidade OWASP A01 - Quebra de Controle de Acesso:** Atua diretamente na resolução da vulnerabilidade, trazendo robustez ao controle de acesso e processos de autorização e autenticação.

Para começar, acesse a documentação de ambos OAuth e JSON Web Tokens, e configure-os em seu projeto.

