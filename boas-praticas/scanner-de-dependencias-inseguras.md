# Scanner de dependências inseguras

Esta boa prática foi implementada no projeto como parte da [PoC 1](../provas-de-conceito/poc-1-containerizacao-e-ci-cd.md). Para mais detalhes sobre uma aplicação dessa prática em um sistema, visite a prova de conceito em questão.

Esta prática concentra-se na detecção automatizada de bibliotecas e pacotes vulneráveis em projetos backend e frontend, utilizando **pip-audit** para Python (backend) e **npm audit** para JavaScript/Node.js (frontend).

### Benefícios do SonarCloud em Microsserviços

* **Detecção Precoce**: Falhas conhecidas são identificadas antes do deploy, evitando vulnerabilidades em ambientes de produção.
* **Governança de Dependências**: políticas de qualidade, como o Python Packing Advisory Database via PyPI JSON API para o backend, bloqueiam builds inseguras.
* **Integração Contínua (CI/CD):** Conecta‑se facilmente a pipelines (GitHub Actions, Azure DevOps, GitLab CI etc.) para detecção automatizada de dependências inseguras.
* **Visibilidade e Relatórios**: logs detalhados para auditorias e compliance são recebidos a cada execução do scanner, separados para cada serviço.

Para começar, acesse a documentação de ambos os scanners, pip-audit e npm audit, e realize a configuração inicial de instalação, que permitirá a execução dos comandos e visualização das possíveis vulnerabilidades.
