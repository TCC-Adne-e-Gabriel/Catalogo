---
icon: star
---

# Análise de Resultados

### Prometheus

A coleta de métricas com o Prometheus possibilitou acompanhar em tempo real o consumo de recursos como CPU e memória de cada um dos nós, além de medir a taxa de requisições e a latência dos serviços. Esse tipo de alerta, além do próprio monitoramento, contribuem diretamente para a disponibilidade do sistema, permitindo respostas proativas antes que ocorram falhas ou degradações perceptíveis para o usuário, além de monitoramento de atividades que possam ser consideradas suspeitas, como atividade anormal no banco de dados, alta carga nas requisições dos serviços, tentativas de avesso ao sistema, entre outros.

### Grafana

A visualização das métricas foi realizada com o Grafana, por meio de dashboards personalizados. Um dos principais dashboards desenvolvidos nesta etapa foi o painel de auditoria, que filtra _logs_ classificados como _AUDIT_, os quais registram ações sensíveis dentro do sistema, como alterações em dados críticos, autenticações e mudanças de permissões. A centralização e visualização desses eventos tornam possível rastrear comportamentos suspeitos, facilitando a detecção de incidentes de segurança e contribuindo para a transparência e rastreabilidade das operações.

### Logs

Além disso, a centralização dos logs possibilitou a correlação de eventos entre diferentes serviços, o que é essencial em arquiteturas distribuídas. Essa abordagem reduz o tempo de investigação e resolução de problemas, melhora a eficiência operacional e fortalece a segurança, ao permitir uma visão holística do sistema em funcionamento.

### Conclusão

Com a implementação da PoC 4, foi possível ter maior observabilidade nos sistemas, que passaram a ser monitorados em relação aos recursos dos nós do _cluster_ em que rodam. Dessa forma, é possível visualizar o estado das máquinas de maneira mais clara e tomar as medidas necessárias para evitar indisponibilidades no sistema.

Foi possível, também, demonstrar a importância da aplicação de boas práticas de observabilidade em arquiteturas baseadas em microsserviços. Por meio da integração entre Prometheus, Grafana e o concentrador de _logs_ adotado, foi possível monitorar aspectos cruciais do sistema, como desempenho, disponibilidade e comportamento interno dos serviços.

