# Segurança na Arquitetura de Microsserviços

Dicas de boas práticas de segurança em arquitetura de microsserviços:

* Utilização de _brokers_ na comunicação entre serviços
* Criptografia das mensagens
* Aplicação de protocolos seguros
* Criação de uma API _gateway_ com autorização e autenticação centralizados, técnicas de taxas de limitação, coleta de métricas para o monitoramento dos serviços e registro dos _logs_ das requisições
* Adicionar um _service mesh_
* Implementar o balanceamento de carga
* Descoberta de serviços
* Monitoramento de tráfego
* Tolerância a falhas
* Controle de acesso e autenticação
* Interrupção de circuitos



### Brokers na comunicação entre serviços

Considerando o aspecto de resistência a falhas em aplicações distribuídas, é comum lidar com comunicação assíncrona entre os serviços, que permite aos sistemas a troca de mensagens através de _brokers_, ao invés de aguardar uma resposta direta.

_Broker_ (AVGERIOU; ZDUN, 2005) é um padrão arquitetural, no qual faz-se uso de sistemas de filas de mensagens, bem como de publicação de eventos. Isso permite estabelecer uma comunicação mais confiável.

### Criptografia das mensagens

Como os microsserviços comunicam-se através da rede, também é de fundamental importância garantir comunicação intra-serviços segura. Para isso, é essencial que as mensagens sejam sempre criptografadas para evitar ataques do tipo _men-in-the-middle_ (MitM) e _eavesdropping_.

### Protocolos seguros

TLS (_Transport Layer Security_) (CLOUDFARE, 2025) é um protocolo de segurança amplamente adotado pelas soluções do mercado, responsável por criptografar a comunicação entre aplicações e serviços hospedados na internet.

### API _Gateway_

#### Autenticação

Ao invés de adicionar uma autenticação para cada serviço uma abordagem mais adequada seria utilizar o _gateway_ de API para lidar com a autenticação de maneira centralizada, autenticando antes de redirecionar para outros serviços.

#### Autorização

A autorização consiste em verificar se o cliente é autorizado para realizar a operação que está tentando realizar. Assim como a autenticação, a centralização da autorização em um _gateway_ de API reduz o risco do aparecimento de vulnerabilidades.

#### Taxas de limitação

Considerando as colocações de Ghosh (2023), as taxas de limitação são técnicas utilizadas para limitar a taxa com que requisições são submetidas à rede em um determinado período de tempo, servidor ou outro recurso da aplicação. A utilização desse tipo de técnica é importante para evitar uso excessivo de recursos, evitar ataques de indisponibilidade como o DoS (_Denial-of-Service_).

#### Coleção de métricas

Consiste em coletar métricas na API com o propósito de análise e monitoramento, tais como: latência das requisições; taxa de erros; _throughput_ (requisições por segundo); tempo de execução; uso de memória e processamento, e número de conexões ativas (ZHAO et al., 2018);

#### _Log_ de requisições

Consiste em registrar em _log_ as requisições realizadas para rastreabilidade;

### _Service Mesh_

Service Mesh é algo mais atual na área de Segurança de Software



