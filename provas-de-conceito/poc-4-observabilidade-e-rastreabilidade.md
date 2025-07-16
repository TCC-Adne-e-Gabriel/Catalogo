# PoC 4 - Observabilidade e Rastreabilidade

### Definição

A PoC consistiu na aplicação de boas práticas associadas a Monitoramento, Observabilidade, Rastreabilidade e Detecção de Falhas.

### Boas práticas trabalhadas

* Utilização de ferramenta de [Log](../boas-praticas/logging.md) em cada serviço;
* Utilização do [Prometheus](../boas-praticas/prometheus-com-grafana.md) para coleta de métricas relevantes de Monitoramento;
* Utilização de ferramenta para análise e visualização de métricas como o [Grafana](../boas-praticas/prometheus-com-grafana.md);
* Utilização de ferramentas de [coleta e filtro de logs](../boas-praticas/prometheus-com-grafana.md), e
* Definição de [Alertas](../boas-praticas/prometheus-com-grafana.md) configurados para determinadas métricas.

### Planejamento

As vulnerabilidades do OWASP Top Ten implantadas nessa PoC foram as seguintes:

* **A01 - Broken Access Control:** Qualquer requisição que falhe em quesito de autorização\
  de uma ação deve ser monitorada de acordo, possibilitando ao administrador da\
  aplicação averiguá-la;
* **A05 - Security Misconfiguration:** A configuração de segurança também engloba a utilização das ferramentas de monitoramento para configurar alertas, _logs_;
* **A08 - Software and Data Integrity Failures:** Qualquer falha na integridade de dados\
  deve ser detectada pelo monitoramento de dados e notificada de acordo, permitindo\
  a avaliação e tratamento da mesma, e
* **A09 - Security Logging and Monitoring Failures:** De modo geral, engloba todas as\
  falhas de Segurança e Monitoramento que podem ocorrer no sistema, assim como a\
  persistência de suas informações para estudo.



Com as vulnerabilidades em mente, o planejamento dessa PoC seguiu com as seguintes tarefas:

* U

### Desenvolvimento

Portanto, foi possível seguir para as etapas de desenvolvimento da PoC em questão:

1. F

### Análise de Resultados
