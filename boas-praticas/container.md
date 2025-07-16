# Container

Esta boa prática foi implementada no projeto como parte da [PoC 1](../provas-de-conceito/poc-1-containerizacao-e-ci-cd.md). Para mais detalhes sobre uma aplicação dessa prática em um sistema, visite a prova de conceito em questão.

A abordagem proposta combina **Docker** para criação de imagens, e **Docker Compose** para a criação e execução de um Container, garantindo qualidade e consistência ao longo de todo o ciclo de vida de cada serviço.

### Benefícios em Arquitetura de Microsserviços:

1. **Ambiente Isolado**
   * Cada serviço roda em seu próprio container, evitando conflitos de dependências.
2. **Portabilidade**
   * Imagens Docker podem ser executadas em qualquer host compatível, sem ajustes manuais.
3. **Escalabilidade**
   * Adicionar réplicas ou novos serviços torna‑se simples, bastando replicar o container desejado.
4. Vulnerabilidade OWASP A04 - Design Inseguro: Containers podem incorporar bases de segurança (scripts de inicialização, variáveis de ambiente criptografadas, etc.), permitindo reutilização de padrões seguros. Na contenção de falhas, uma falha em um container não se estende a outros, reduzindo risco de propagação.



Para começar, visualize a documentação do Docker ([https://www.docker.com/](https://www.docker.com/)) e realize sua própria Containerização.
