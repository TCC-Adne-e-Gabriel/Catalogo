# Análise de Segurança de Código

Esta boa prática foi implementada no projeto como parte da [PoC 1](../provas-de-conceito/poc-1-containerizacao-e-ci-cd.md). Para mais detalhes sobre uma aplicação dessa prática em um sistema, visite a prova de conceito em questão.

A abordagem recomendada baseia‑se no uso de ferramentas de análise estática de código, como o **SonarCloud**, para garantir qualidade e segurança contínuas em cada serviço de uma arquitetura de microsserviços.

### Benefícios em Arquitetura de Microsserviços

* **Visibilidade Granular por Serviço:** Cada microsserviço é analisado de forma independente, proporcionando relatórios detalhados de vulnerabilidades, bugs e dívidas técnicas por repositório;
* **Integração Contínua (CI/CD):** Conecta‑se facilmente a pipelines (GitHub Actions, Azure DevOps, GitLab CI etc.), bloqueando builds quando novos problemas de segurança ou cobertura abaixo do padrão são detectados.
* **Métricas de Qualidade e Tendências:** Monitora indicadores como duplicação de código, cobertura de testes, complexidade de código e novas vulnerabilidades ao longo do tempo, facilitando decisões baseadas em dados.
* **Detecção de Vulnerabilidades OWASP:** Oferece regras específicas para mapear e evitar vulnerabilidades do OWASP Top 10, como a  A04: **Insecure Design**. Ao aplicar essas regras, o SonarCloud identifica falhas de design antes mesmo da escrita de grande parte do código, sugerindo padrões arquiteturais seguros (por exemplo, validação de entrada centralizada, uso de contratos claros entre serviços, tratamento padronizado de erros).

Para começar, crie um projeto no SonarCloud ([https://sonarcloud.io](https://sonarcloud.io)) de cada microsserviço. Com sua configuração inicial, toda nova branch será automaticamente avaliada, idealmente impedindo regressões de segurança e qualidade antes do merge.
