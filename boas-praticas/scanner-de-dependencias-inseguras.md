# Scanner de Dependências Inseguras

Esta boa prática foi implementada no projeto como parte da [PoC 1](../provas-de-conceito/poc-1-containerizacao-e-ci-cd/). Para mais detalhes sobre uma aplicação dessa prática em um sistema e suas especificações, visite a prova de conceito em questão.

Esta prática concentra-se na detecção automatizada de bibliotecas e pacotes vulneráveis em projetos _backend_ e _frontend_, utilizando _**pip-audit**_ para _Python_ (_backend_) e _**npm audit**_ para _JavaScript/Node.js_ (_frontend_).

### Benefícios em Arquitetura de Microsserviços

* **Detecção Precoce**: Falhas conhecidas são identificadas antes do _deploy_, evitando vulnerabilidades em ambientes de produção.
* **Governança de Dependências**: Políticas de qualidade, como o _**Python Packing Advisory Database**_ via _PyPI JSON API_ para o backend, bloqueiam _builds_ inseguras.
* **Integração Contínua (**_**CI/CD**_**):** Conecta‑se facilmente a _pipelines_ (GitHub Actions, Azure DevOps, GitLab CI etc.) para detecção automatizada de dependências inseguras.
* **Visibilidade e Relatórios**: _Logs_ detalhados para auditorias e _compliance_ são recebidos a cada execução do _scanner_, separados para cada serviço.

Para começar, acesse a documentação de ambos os _scanners_, _pip-audit_ e _npm audit_, e realize a configuração inicial de instalação, que permitirá a execução dos comandos e visualização das possíveis vulnerabilidades.
