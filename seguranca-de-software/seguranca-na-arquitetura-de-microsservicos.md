# Segurança na Arquitetura de Microsserviços

Considerando estudos realizados na comunidade de _software_, diversas boas práticas de segurança em arquitetura de microsserviços foram criadas e utilizadas ao longo do tempo. Dentre as várias práticas utilizadas pela comunidade, seguem algumas das principais:

* Utilização de _brokers_ na comunicação entre serviços;
* Criptografia das mensagens;
* Aplicação de protocolos seguros;
* Criação de uma _API Gateway_ com autorização e autenticação centralizados, técnicas de taxas de limitação, coleta de métricas para o monitoramento dos serviços e registro dos _logs_ das requisições;
* Adicionar um _service mesh:_
  * Implementar o balanceamento de carga;
  * Descoberta de serviços;
  * Monitoramento de tráfego;
  * Tolerância a falhas;
  * Controle de acesso e autenticação, e
  * Interrupção de circuitos.



A seguir, é possível visualizar uma breve explicação das práticas citadas acima, considerando o contexto de Segurança em Microsserviços:

### Brokers na comunicação entre serviços

Considerando o aspecto de resistência a falhas em aplicações distribuídas, é comum lidar com comunicação assíncrona entre os serviços, que permite aos sistemas a troca de mensagens através de _brokers_, ao invés de aguardar uma resposta direta.

_Broker_ (AVGERIOU; ZDUN, 2005) é um padrão arquitetural, no qual faz-se uso de sistemas de filas de mensagens, bem como de publicação de eventos. Isso permite estabelecer uma comunicação mais confiável.

### Criptografia das mensagens

Como os microsserviços comunicam-se através da rede, também é de fundamental importância garantir comunicação intra-serviços segura. Para isso, é essencial que as mensagens sejam sempre criptografadas para evitar ataques do tipo _men-in-the-middle_ (_MitM_) e _eavesdropping_.

Para contexto, no ataque _MitM_, um invasor se posiciona entre duas partes de uma conexão que acreditam estar se comunicando diretamente, possibilitando a alteração ou injeção de mensagens\
sem detecção por nenhuma das partes. Já no _eavesdropping_, também conhecido como espionagem digital, a pessoa mal-intencionada apenas escuta a comunicação sem interferir, capturando dados sensíveis.

### Protocolos seguros

TLS (_Transport Layer Security_) (CLOUDFARE, 2025) é um protocolo de segurança amplamente adotado pelas soluções do mercado, responsável por criptografar a comunicação entre aplicações e serviços hospedados na _internet_.

### API _Gateway_

#### Autenticação

Ao invés de adicionar uma autenticação para cada serviço, uma abordagem mais adequada seria utilizar o _gateway_ de _API_ para lidar com a autenticação de maneira centralizada, autenticando antes de redirecionar para outros serviços.

#### Autorização

A autorização consiste em verificar se o cliente é autorizado para realizar a operação que está tentando realizar. Assim como a autenticação, a centralização da autorização em um _gateway_ de API reduz o risco do aparecimento de vulnerabilidades.

#### Taxas de limitação

Considerando as colocações de Ghosh (2023), as taxas de limitação são técnicas utilizadas para limitar a taxa com que requisições são submetidas à rede em um determinado período de tempo, servidor ou outro recurso da aplicação. A utilização desse tipo de técnica é importante para evitar uso excessivo de recursos, evitar ataques de indisponibilidade como o DoS (_Denial-of-Service_).

#### Coleção de métricas

Consiste em coletar métricas na API com o propósito de análise e monitoramento, tais como: latência das requisições; taxa de erros; _throughput_ (requisições por segundo); tempo de execução; uso de memória e processamento, e número de conexões ativas (ZHAO et al., 2018);

#### _Log_ de requisições

Consiste em registrar em _log de_ requisições realizadas entre os serviços do software, permitindo assim melhor rastreabilidade de informações;

### _Service Mesh (Malha de Serviços)_

_Service Mesh_ é algo mais atual na área de Segurança de Software, e trata-se, essencialmente, de um conjunto de _proxies_ de rede que são implantados através da aplicação, que age como mediador nas comunicações entre serviços e aplicações externas. Coloca-se que um _proxy_ é um padrão de projeto que permite proteger um recurso ou funcionalidade do sistema quanto a acessos indevidos.

#### Balanceamento de carga

Além de sua camada de criptografia, o _Service Mesh_ fornece regras baseadas em balanceamento de carga, que consiste na permissão do roteamento de tráfego através da rede, considerando latência e estado das instâncias do _Back-End_.

#### Descoberta de serviços

Em aplicações de arquitetura distribuída, o número de instâncias do serviço podem mudar de forma dinâmica. Nesse contexto, é necessário que existam mecanismos para descoberta de serviços, que habilitam serviços a encontrar outros e realizar requisições dinâmicas.

#### Monitoramento de tráfego

Todas as comunicações entre os serviços podem ser capturadas e registradas, possibilitando a coleta de métricas de latência, erro, sucesso, volume de requisições, dentre outros.

#### Tolerância a falhas

Normalmente, em caso de uma malha de serviços encontrar uma falha em sua abstração de rede TCP/IP, faz-se uso do redirecionamento para uma instância saudável, realizando o tratamento de falhas.

#### Controle de acesso e autenticação

Com políticas de controle de acesso através de um painel de controle, é possível definir quais serviços são autorizados a acessar cada serviço, assim como seus tipos de tráfegos autorizados.

#### Interrupção de circuitos

No caso de acesso a serviços que estejam sobrecarregados e com alta latência, é possível interromper as requisições para evitar que a falha se propague.





