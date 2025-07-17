---
icon: magnifying-glass
---

# Logging

Para o desenvolvimento da Prova de Conceito focada no monitoramento dos serviços e dos nós, o primeiro passo foi a criação de um módulo de log em todos os serviços, atuando no lado do servidor. A biblioteca utilizada para o gerenciamento dos logs em Python foi a Logging (LOGGING, 2025), que permite criar uma instância específica para o projeto e aplicar configurações personalizadas.

Uma das primeiras decisões ao implementar o logging da aplicação consiste em definir quais tipos de logs serão capturados e quais informações relevantes deverão constar nesses registros. Isso porque os logs devem conter todos os dados necessários para auditar o sistema e facilitar a identificação de eventuais problemas.

\
Para os projetos desse trabalho foi decidido utilizar os seguintes tipos de logs:

* **INFO**: Log informativo de algo que aconteceu no sistema, por exemplo, chamadas para a API dos serviços. O FastAPI instalado já estava com essa configuração;
* **AUDIT**: Log que tem como objetivo auditar as ações realizadas por um usuário no sistema;
* **WARNING**: Log que indica situações inesperadas ou que podem levar a problemas futuros, mas que não impedem o funcionamento normal da aplicação;
* **ERROR**: Log referente a falhas que afetam diretamente uma funcionalidade da aplicação, necessitando de atenção para correção, e
* **CRITICAL**: Log para erros graves que comprometem a continuidade do sistema, exigindo intervenção imediata

Todos os logs do sistema foram pensados para conter as seguintes informações:

* Tipo de Log;
* IP do cliente que está requisitando o serviço;
* Dia e Horário que o Log foi criado;
* ID do usuário que está logado, e
* Ação que foi feita ou detalhes da exceção lançada;

Para auxiliar no suporte ao sistema, foi adicionado um código gerado aleatoriamente em mensagens de erro não tratadas. Assim, seria possível localizar os detalhes da exceção ao buscar pelo código em um possível centralizador de logs.

<figure><img src="../../.gitbook/assets/image (3).png" alt="" width="563"><figcaption></figcaption></figure>

<p align="center">Fonte: Autores. Ferramenta: Postman (2025).</p>

Para viabilizar a inclusão de logs no sistema, foi utilizada uma biblioteca do Python que permite armazenar variáveis no contexto da thread. No caso dos sistemas analisados, as variáveis definidas foram o IP do cliente que está realizando a requisição e o ID do usuário autenticado.

{% code title="app/context.py" lineNumbers="true" %}
```python
from contextvars import ContextVar

user_context: ContextVar[str | None] = ContextVar("user_context", default="anonymous")
client_ip_context: ContextVar[str | None] = ContextVar("client_ip_context", default="anonymous")
```
{% endcode %}

Para capturar o IP do cliente e adicioná-lo ao contexto, foi criado um arquivo de middleware, _que é um comp&#x6F;_&#x6E;ente inserido na cadeia de requisições HTTP e capaz de executar ações durante o processamento dessas requisições. Foi desenvolvido um middleware personalizado para inserir o IP do cliente no contexto, obtendo-o a partir do cabeçalho X-Forwarded-For.  Caso esse cabeçalho não estivesse presente — situação comum quando o cliente não utiliza proxy — o IP foi extraído diretamente do host da requisição (Request).

{% code title="app/middlewares.py" lineNumbers="true" %}
```python
from app.context import client_ip_context
from fastapi import Request
from starlette.middleware.base import BaseHTTPMiddleware

class ClientIPMiddleware(BaseHTTPMiddleware):
    async def dispatch(self, request: Request, call_next):
        x_forwarded_for = request.headers.get("X-Forwarded-For")
        client_ip = x_forwarded_for.split(",")[0].strip() if x_forwarded_for else request.client.host
        client_ip_context.set(client_ip)
        return await call_next(request)
```
{% endcode %}



Em seguida, o arquivo de configuração de _logging_ define as classes personalizadas criadas para o projeto. A classe MaxLevelFilter foi implementada para filtrar _logs_ com nível abaixo de _WARNING_, sendo utilizada posteriormente para decidir quais _logs_ seriam direcionados para o _stdout_ ou para o _stderr._

Adicionalmente, a classe ContextLoggerAdapter é responsável por processar todas as chamadas de logs, inserindo automaticamente as variáveis de contexto como itens adicionais nas mensagens, garantindo que informações relevantes estejam presentes nos registros, o IP do Cliente e o ID do usuário.

Segue o arquivo completo de configuração de log da aplicação:&#x20;

{% code title="app/customer_logging.py" lineNumbers="true" %}
```python
import logging
import sys
import logging
from app.context import user_context, client_ip_context

AUDIT_LEVEL_NUM = 25
logging.addLevelName(AUDIT_LEVEL_NUM, "AUDIT")

class MaxLevelFilter(logging.Filter):
    def __init__(self, max_level):
        self.max_level = max_level

    def filter(self, record):
        return record.levelno < self.max_level

class ContextLoggerAdapter(logging.LoggerAdapter):      
    def audit(self, msg, *args, **kwargs):
        msg, kwargs = self.process(msg, kwargs)
        if self.isEnabledFor(AUDIT_LEVEL_NUM):
            self._log(AUDIT_LEVEL_NUM, msg, args, **kwargs)
            
    def process(self, msg, kwargs):
        user_id = user_context.get()
        client_ip = client_ip_context.get()
        extra = kwargs.get("extra", {})
        extra["user_id"] = user_id
        extra["client_ip"] = client_ip
        kwargs["extra"] = extra
        return msg, kwargs
    

formatter = logging.Formatter(
    fmt="%(levelname)s: %(asctime)s - USUARIO %(user_id)s from %(client_ip)s - %(message)s"
)

stdout_handler = logging.StreamHandler(sys.stdout)
stdout_handler.setFormatter(formatter)
stdout_handler.addFilter(MaxLevelFilter(logging.WARNING))
stdout_handler.setLevel(logging.INFO)

stderr_handler = logging.StreamHandler(sys.stderr)
stderr_handler.setFormatter(formatter)
stderr_handler.setLevel(logging.WARNING)


logger = logging.getLogger("app")
logger.handlers = [stdout_handler, stderr_handler]
logger.setLevel(logging.INFO)
logger.propagate = False 

logger = ContextLoggerAdapter(logger, {})

```
{% endcode %}

Para criação de um log, basta adicionar uma linha de código semelhante a: logger.audit(), com a mensagem desejada. O "audit" representa o nível do log a ser disparado.

### Referências

LOGGING. Logging Facility — Python Documentation. 2025. \<https://docs.python.\
org/3/library/logging.html>.
