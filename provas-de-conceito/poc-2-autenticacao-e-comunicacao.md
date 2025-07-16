# PoC 2 - Autenticação e Comunicação

### Definição

Essa PoC consistiu na aplicação de boas práticas associadas à validação de dados de\
entrada e saída, manipulação e armazenamento de dados, autenticação e autorização no sistema.

### Boas práticas trabalhadas

* Utilização de [ORM (Object-Relational Mapping) e validação de dados](../boas-praticas/orm-e-validacao-de-dados.md) de entrada e saída;
* Utilização de práticas de [Criptografia de Dados](../boas-praticas/criptografia-de-dados.md);
* Utilização do protocolo [JWT](../boas-praticas/jwt-e-oauth2.md) para autenticação e autorização, e
* Utilização do protocolo [OAuth 2.0](../boas-praticas/jwt-e-oauth2.md) para autenticação e autorização.

### Planejamento

As vulnerabilidades do **OWASP Top Ten** implantadas nessa PoC foram as seguintes:

* _**A01 - Broken Access Control:**_ A ocorrência de uma quebra de autorização em um aplicativo de comércio eletrônico pode causar a realização indevida de pagamentos utilizando informações pessoais alheias, causando prejuízo aos usuários;
* _**A02 - Cryptographic Failure:**_ A ausência de criptografia pode tornar expostas as informações de clientes em caso de invasões, o que prejudicaria a privacidade dos mesmos;
* _**A03 - Injection:**_ As telas de _login_ ou pagamento tornariam possível realizar a operação de injeção para o banco de dados, possibilitando pessoas mal intencionadas a acessar informações pessoais de outros usuários;
* _**A04 - Insecure Design:**_ Com um _design_ falho do sistema, seria possível aproveitar-se de brechas na segurança de seus componentes;
* _**A07 - Identification and Authentication Failures:**_ Caso não sejam possíveis a autenticação e autorização de maneira correta, as falhas iriam abranger para a permissão indevida de ações de administrador para usuários comuns, causando ações possivelmente irreversíveis;
* _**A08 - Software and Data Integrity Failures:**_ A falha de integridade de dados também pode ocorrer em caso de falhas na comunicação entre microsserviços, provocando a perda de dados ou transações, e
* _**A10 - Server-Side Request Forgery:**_ Devido à complexidade de uma Arquitetura de Microsserviços, o uso de ataques _SSRF_ (_Server-Side Request Forgery_) para requisições indevidas na comunicação entre serviços é crescente.



Com as vulnerabilidades em mente, o planejamento dessa PoC seguiu com as seguintes tarefas:

*

### Desenvolvimento

Portanto, foi possível seguir para as etapas de desenvolvimento da PoC em questão:

1.

### Análise de Resultados
