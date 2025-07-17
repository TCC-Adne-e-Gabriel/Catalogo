# Logging

Esta boa prática foi implementada no projeto como parte da [PoC 4](../provas-de-conceito/poc-4-observabilidade-e-rastreabilidade/). Para mais detalhes sobre uma aplicação dessa prática em um sistema e suas especificações, visite a prova de conceito em questão.

Esta prática concentra-se na utilização de _logs_ personalizados para os microsserviços, produzindo informações personalizadas acerca dos eventos dos sistema.

### Benefícios em Arquitetura de Microsserviços

* **Configuração Personalizada:** É possível criar atribuições personalizadas para os tipos e contextos de logs em cada sistema.
* **Suporte Informativo ao Sistema:** Ao inserir um código gerado aleatóriamente em mensagens de erro não tratadas, permite localizá-las, dentre os microsserviços, ao buscar pelo código em um centralizador de _logs_.
* **Compartilhamento de Instância:** É possível utilizar uma instância de _logger_ principal para o projeto, englobando os microsserviços e facilitando a visualização.
* **Vulnerabilidade OWASP A09 - Falhas de Registro e Monitoramento de Segurança:** Possibilita a visualização de registros e erros por meio de _logs_, assim como falhas de segurança.

Para começar, acesse a documentação de sistemas de _log_ como o [**Logging**](https://docs.python.org/3/library/logging.html) do **Python**, e configure-os em seu projeto.
