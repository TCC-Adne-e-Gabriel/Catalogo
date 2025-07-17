---
icon: star
---

# Análise de Resultados

Após a aplicação da boa prática de pipeline de scanner de segurança pelo SonarQube, e considerando que as aplicações estavam com vulnerabilidades previamente instaladas pelos autores, foi possível obter um resultado satisfatório. Antes mesmo do código subir na branch principal a partir de alguma criada, já foi possível identificar as falhas de segurança do sistema, levando em consideração vulnerabilidades presentes na OWASP Top Ten (OWASP, 2021) e no CWE (CWE, 2022).&#x20;

#### Serviço de Usuários

O serviço de usuários, denominado como tcc-customer, é o responsável por tratar de funcionalidades relacionadas ao usuário, à autenticação e à autorização no sistema. Com a análise do SonarQube, o serviço apresentou:&#x20;

8 problemas severos de Segurança, sendo eles:&#x20;

* 6 relacionados à SQL Injection: Change this code to not construct SQL queries directly from user-controlled data, e
* 2 relacionados senhas expostas: Revoke and change this password, as it is compromised.&#x20;

4 Hotspots de segurança para serem revisados:&#x20;

* 1 Hotspot com prioridade alta: "TOKEN" detected here, make sure this is not a hard-coded secret.
* 1 Hotspot com prioridade baixa: Make sure that hashing data is safe here, e
* 2 relacionados a senhas expostas: "password" detected here, review this potentially hard-coded credential.

#### Serviço de Produtos

5 problemas severos de Segurança, sendo eles:

* 3 relacionados à SQL Injection: Change this code to not construct SQL queries directly from user-controlled data, e
* 2 relacionados a senhas expostas: Revoke and change this password, as it is compromised.

**Serviço de Pedidos**

8 problemas severos de Segurança, sendo eles:

* 3 relacionados à SQL Injection: Change this code to not construct SQL queries directly from user-controlled data, e
* 2 relacionados a senhas expostas: Revoke and change this password, as it is compromised.

1 problema com alta prioridade de Segurança, sendo ele:

* 1 relacionado a Tratamento de exceções: Revoke and change this password, as it is compromised;

2 Hotspots de segurança para serem revisados:

* 2 relacionados a senhas expostas: "password" detected here, review this potentially hard-coded credential.



A utilização de ferramentas para análise estática do código, como o SonarQube, pode apresentar ganhos em relação à VULNERABILIDADE OWASP A05 Security Misconfiguration.&#x20;

Da mesma forma, a aplicação do pipeline de scanner de dependências inseguras, apesar de não reportar problemas nas dependências dos serviços em questão, apresentou um resultado satisfatório, pois atua como mais uma barreira de proteção para o desenvolvimento de código inseguro.&#x20;

A utilização de containers usando as ferramentas do Docker (DOCKER, 2025c) e Docker Compose (DOCKER, 2025d) representa ganhos em relação à VULNERABILIDADE OWASP A04 Insecure Design. Segundo Perry (2022), a utilização de containers proporciona um melhor isolamento para cada microsserviço, garantindo que uma vulnerabilidade encontrada em um container não se propague para outro container. Uma aplicação hospedada direto em um Sistema Operacional de um Hospedeiro é menos seguro.
