# Kubernetes

Esta boa prática foi implementada no projeto como parte da [PoC 3](../provas-de-conceito/poc-3-gerenciamento-de-containers-e-servicos.md). Para mais detalhes sobre uma aplicação dessa prática em um sistema, visite a prova de conceito em questão.

Esta prática concentra-se na utilização do Kubernetes para gerenciamento e hospedagem de containers dos microsserviços de uma aplicação.

### Benefícios em Arquitetura de Microsserviços

* **Sistema distribuído**: A aplicação pode ser distribuída em uma ou mais réplicas, que rodam em diferentes máquinas e dividem seu processamento.
* **Prevenção de falhas:** O modo distribuído de hospedagem dos microsserviços permite a contínua atividade do servidor, mesmo que uma das máquinas falhe.
* **Gerenciamento de redes e volumes:** Melhor escalabilidade e visualização de redes, volumes de serviços, melhorando a robustez e escalabilidade do sistema.
* **Portabilidade:** Devido à disponibilidade de múltiplas máquinas, é possível transmitir o processamento do servidor para qualquer alteração de máquinas.

Para começar, acesse a documentação do Kubernetes, e configure-o em seu projeto.
