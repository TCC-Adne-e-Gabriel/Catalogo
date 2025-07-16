# Monitoramento de Software

### Observabilidade

Como os serviços podem falhar a qualquer momento, é muito importante detectar as falhas o mais rápido possível, para que o serviço possa ser reestabelecido apropriadamente. Por isso, a arquitetura de microsserviços demanda um esforço de monitoramento em tempo real mais intensivo e mais desafiador.

Nesse contexto, **observabilidade** é uma medida que se pode inferir sobre o estado interno de um sistema, baseado principalmente em dados de saída externos. Seus 3 (três) principais pilares são os termos _**logs**_, _**metrics**_ e _**traces**_. Desse modo:

* O _**log**_ pode ser qualquer evento registrado em um serviço;
* A agregação de _logs_ pode produzir uma **métrica** (_metric_), que é uma quantidade mensurável de alguma característica do sistema, e
* Os _**traces**_ são baseados em logs, mas têm o objetivo de rastrear uma requisição\
  do ponto de entrada até o ponto de saída, para entendimento de latência e identificação de gargalos.



### Métricas de Monitoramento

Métricas de monitoramento são representações de dados medidos em um intervalo de tempo, que normalmente vêm da utilização e do comportamento de um sistema. Essas métricas podem ser utilizadas para fazer predições de comportamentos futuros do sistema, ou detectar anomalias. Dentre essas métricas, algumas conhecidas e utilizadas pela comunidade de software são:

* **Latência e tempo de resposta:** São, respectivamente, o tempo que uma requisição toma para ir do\
  cliente para o serviço e voltar, e o tempo de processar o _request_ e gerar uma resposta. Com a coleta dessas métricas, é possível identificar gargalos e problemas de desempenho;
* **Taxa de erros e métricas de erro:** Envolve a quantidade de erros e exceções encontradas em requisições e operações, auxiliando a identificar _bugs_, problemas de configuração, e falhas em serviços internos;
* **Volume de requisições e&#x20;**_**Throughput**_**:** Número de requisições que o microsserviço pode lidar com em um determinado período de tempo, auxiliando na checagem de escalabilidade e desempenho;
* **Métricas de uso de recursos:** Métricas que monitoram a quantidade de CPU, espaço\
  de disco e rede do microsserviço estão sendo utilizadas, e
* _**Service Level Indicators**_**&#x20;(SLIs):** SLIs são métricas arbitrariamente escolhidas, que definem o comportamento desejado para o serviço para aspectos críticos da qualidade do serviço, como latência, taxa de erros, disponibilidade ou taxa de sucesso das requisições.
* _**Service Level Objectives**_**&#x20;(SLOs):** SLOs são metas e limites definidos para os SLIs. Com a utilização dessas métricas, é possível definir expectativas claras quanto ao desempenho dos microsserviços. Sendo assim, quando as métricas divergem dos SLOs, podem ser emitidos alertas e notificações.

