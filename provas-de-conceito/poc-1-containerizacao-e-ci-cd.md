# PoC 1 - Containerização e CI/CD

### Definição

Essa PoC consistiu na aplicação de práticas de segurança utilizando conceitos de\
conteinerização para isolamento de ambiente e para elaboração de integração contínua (CI/CD)\
para os diferentes microsserviços, assim possibilitando a implantação e a análise de segurança do código.

### Boas práticas trabalhadas

* Utilização de um [container](../boas-praticas/container-docker.md) Docker para cada microsserviço;
* Utilização de ferramentas de [análise de segurança](../boas-praticas/analise-de-seguranca-de-codigo.md) de código em tempo de deploy, ou seja, aplicação de pipelines de segurança com a utilização de SonarQube, e
* Utilização de ferramentas para [análise de dependências inseguras](../boas-praticas/scanner-de-dependencias-inseguras.md) em tempo de deploy.

### Planejamento

As vulnerabilidades do OWASP Top Ten implantadas nessa PoC foram as seguintes:

* A04 - Insecure Design: Design Inseguro de containers Docker da aplicação, evidenciando as consequências de uma aplicação estruturada arquiteturalmente de maneira incorreta;
* A05 - Security Misconfiguration: Do mesmo modo, as configurações incorretas de uma aplicação em container podem trazer vulnerabilidade ao sistema, potencialmente causando, por exemplo, a perda de dados de um usuário.
* A06 - Vulnerable and Outdated Components: Componentes desatualizados ou vulneráveis ao realizar a configuração do Docker podem tornar o sistema falho.
* A08 - Software and Data Integrity Failures: Ao atualizar para uma nova versão do software, a integridade do banco de dados pode falhar, causando perdas críticas de dados pessoais, pagamentos, entre outros.



Com as vulnerabilidades em mente, o planejamento dessa PoC seguiu com as seguintes tarefas:

* Utilização de Docker e Docker-compose para os containers em todos os microsserviços;
* Utilização do SonarCloud como ferramenta de análise de segurança, e
* Utilização de Pip Audit e Npm Audit como ferramentas para análise de dependências inseguras.

### Desenvolvimento

Portanto, foi possível seguir para as etapas de desenvolvimento da PoC em questão:

1.  Ferramentas de análise de segurança de software:

    Para a aplicação da primeira boa prática, adotou-se a ferramenta de análise de\
    código estática SonarQube. Para isso, foi necessária a criação de uma organização no\
    SonarCloud para os repositórios do trabalho de conclusão de curso, além da adição\
    de um workflow no GitHub para rodar o scanner do SonarCloud nas seguintes ações:
2. a

### Análise de Resultados











