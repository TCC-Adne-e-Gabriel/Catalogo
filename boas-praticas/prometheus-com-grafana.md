# Prometheus com Grafana

Esta boa prática foi implementada no projeto como parte da [PoC 4](../provas-de-conceito/poc-4-observabilidade-e-rastreabilidade.md). Para mais detalhes sobre uma aplicação dessa prática em um sistema e suas especificações, visite a prova de conceito em questão.

Esta prática concentra-se na utilização do **Prometheus (**[**https://prometheus.io/**](https://prometheus.io/)**)** para coleta de métricas dos microsserviços, enquanto as métricas coletadas são visualizadas por meio da criação de painéis de bordo do **Grafana (**[**https://grafana.com/**](https://grafana.com/)**)**.

### Benefícios em Arquitetura de Microsserviços

* **Gerenciamento em Tempo Real**: Visualização constante de estado do sistema na coleta automática de métricas do Prometheus, provendo velocidade de informações e tratamento imediato de indisponibilidades ou erros.
* **Personalização de Dados:** O Grafana permite a criação e alteração de _dashboards_ (painéis de bordo) com diversas personalizações e tipos diferentes de gráficos, dados e históricos.
* **Centralização de Logs:** Possibilita a correlação de eventos entre diferentes serviços, reduzindo o tempo de investigação e resolução de problemas, melhorando a eficiência operacional e fortalecendo a segurança.
* **Integração com Kubernetes:** É possível, também, utilizar a ferramenta _kube-prometheus-stack_ para integrar a coleta de métricas do Prometheus e a visualização do Grafana com um _cluster_ Kubernetes.
* **Definição de Alertas:** O grafana possui uma interface amigável em que é possível definir alertas específicos para a entidade que deseja observar, que podem ser configurados para serem enviados por algumas integrações de sistemas conhecidas, incluindo _emails_.

Para começar, acesse a documentação de ambos [Prometheus](https://prometheus.io/docs/introduction/overview/) e [Grafana](https://grafana.com/docs/grafana/latest/), e configure-os em seu projeto.
