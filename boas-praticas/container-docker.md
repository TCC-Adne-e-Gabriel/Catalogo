# Container Docker

Esta boa prática foi implementada no projeto como parte da [PoC 1](../provas-de-conceito/poc-1-containerizacao-e-ci-cd.md). Para mais detalhes sobre uma aplicação dessa prática em um sistema e suas especificações, visite a prova de conceito em questão.

A abordagem proposta combina **Docker** para criação de imagens, e **Docker Compose** para a criação e execução de um Container, garantindo qualidade e consistência ao longo de todo o ciclo de vida de cada serviço.

### Benefícios em Arquitetura de Microsserviços:

1. **Ambiente Isolado:** Cada serviço roda em seu próprio _container_, evitando conflitos de dependências e propagação de erros.
2. **Portabilidade:** Imagens _Docker_ podem ser executadas em qualquer _host_ compatível, sem necessitar de ajustes manuais a cada máquina diferente.
3. **Escalabilidade:** Adicionar réplicas ou novos serviços torna‑se simples, bastando replicar o _container_ desejado.
4. **Vulnerabilidade OWASP A04 -&#x20;**_**Design**_**&#x20;Inseguro:** _Containers_ podem incorporar bases de segurança (scripts de inicialização, variáveis de ambiente criptografadas, etc.), permitindo reutilização de padrões seguros. Na contenção de falhas, uma falha em um _container_ não se estende a outros, reduzindo risco de propagação.



Para começar, visualize a documentação do Docker ([https://www.docker.com/](https://www.docker.com/)) e realize sua própria Containerização.
