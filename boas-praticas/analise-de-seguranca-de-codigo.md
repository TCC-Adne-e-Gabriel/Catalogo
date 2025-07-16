# Análise de Segurança de Código

Esta boa prática foi implementada no projeto como parte da [PoC 1](../provas-de-conceito/poc-1-containerizacao-e-ci-cd/). Para mais detalhes sobre uma aplicação dessa prática em um sistema e suas especificações, visite a prova de conceito em questão.

A abordagem recomendada baseia‑se no uso de ferramentas de análise estática de código, como o **SonarCloud**, para garantir qualidade e segurança contínuas em cada serviço de uma arquitetura de microsserviços.

### Benefícios em Arquitetura de Microsserviços

* **Visibilidade Granular por Serviço:** Cada microsserviço é analisado de forma independente, proporcionando relatórios detalhados de vulnerabilidades, _bugs_ e dívidas técnicas por repositório;
* **Integração Contínua (CI/CD):** Conecta‑se facilmente a _pipelines_ (GitHub Actions, Azure DevOps, GitLab CI etc.), bloqueando _builds_ quando novos problemas de segurança ou cobertura abaixo do padrão são detectados.
* **Métricas de Qualidade e Tendências:** Monitora indicadores como duplicação de código, cobertura de testes, complexidade de código e novas vulnerabilidades ao longo do tempo, facilitando decisões baseadas em dados.
* **Detecção de Vulnerabilidades OWASP:** Oferece regras específicas para mapear e evitar vulnerabilidades do _OWASP Top Ten_, como a  A04: _**Design**_**&#x20;Inseguro**. Ao aplicar essas regras, o SonarCloud identifica falhas de _design_ antes mesmo da escrita de grande parte do código, sugerindo padrões arquiteturais seguros (por exemplo, validação de entrada centralizada, uso de contratos claros entre serviços, tratamento padronizado de erros).

Para começar, crie um projeto no SonarCloud ([https://sonarcloud.io](https://sonarcloud.io)) de cada microsserviço. Com sua configuração inicial, toda nova _branch_ será automaticamente avaliada, idealmente impedindo regressões de segurança e qualidade antes do _merge_.
