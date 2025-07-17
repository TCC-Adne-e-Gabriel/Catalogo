# Implementação de comunicação segura via TLS

TLS (Transport Layer Security) é um protocolo de segurança que criptografa a\
comunicação ponta a ponta entre dois sistemas, como um navegador e um servidor\
web, garantindo a privacidade e a segurança dos dados transmitidos, normalmenmte\
com a utilização de certificado digital emitido por uma terceira parte confiável, uma\
Autoridade Certificadora (AC). Sendo assim, é uma boa prática para ser aplicada\
nos serviços da aplicação.

A autoridade certificadora utilizada para o trabalho foi o Let’s Encrypt com o protocolo ACME, que ao inserir dados personalizados do subdomínio da aplicação, que no caso é `moreofthis.morettis.me`, e o email, gera um certificado válido para utilização de TLS. Para isso, o Traefik (TRAEFIK, 2025b) também é utilizado para pegar o certificado. Sendo assim, para que o acesso ao certificado fosse possível, foi necessário modificar os arquivos de cofniguração do traefik no k3s, que se encontravam no caminho `/var/lib/rancher/k3s/server/manifests/traefik-config.yaml`, com as seguintes configurações:&#x20;

{% code title="/var/lib/rancher/k3s/server/manifests/traefik-config.yaml" lineNumbers="true" %}
```yaml
apiVersion: helm.cattle.io/v1
kind: HelmChartConfig
metadata:
    name: traefik
    namespace: kube-system
spec:
    valuesContent: |-
    additionalArguments:
    -"--certificatesresolvers.default.acme.email=<email>"
    -"--certificatesresolvers.default.acme.storage=/data/acme.json"
    -"--certificatesresolvers.default.acme.httpchallenge.entrypoint=web"
ports:
    web:
        exposedPort: 80
    websecure:
        exposedPort: 443
        tls:
          enabled: true
    
providers:
    kubernetesIngress:
        enabled: true
    kubernetesGateway:
        enabled: false
```
{% endcode %}

A configuração adiciona a forma de resolução do certificado a partir do trarfik, além de especificar que será utilizado API Ingress do kubernetes, e não Gateway API.&#x20;



### Referências

TRAEFIK. Traefik Proxy Documentation - Traefik. 2025. Disponível em: \<https:\
//doc.traefik.io/traefik/>.
