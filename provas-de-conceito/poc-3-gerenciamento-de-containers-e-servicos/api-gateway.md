# API Gateway

Como forma de centralizar as requisições para os serviços foi utilizado o Traefik, que é um proxy reverso e Load Balancer. Ele atua como um controlador de tráfego para os serviços da aplicação. Juntamente com um recurso do Kubernetes, do tipo Ingress, o Traefik observa e interpreta os recursos Ingress e roteia o tráfego recebido para o serviço desejado, que é visível internamente pelo cluster.&#x20;

{% code lineNumbers="true" %}
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: moreofthis-ingress
  namespace: default
  annotations:
    traefik.ingress.kubernetes.io/router.entrypoints: websecure
    traefik.ingress.kubernetes.io/router.tls.certresolver: default
    traefik.ingress.kubernetes.io/router.tls: "true"
spec:
  ingressClassName: traefik
  rules:
    - host: moreofthis.morettis.me
      http:
        paths:
          - path: /api/v1/customer
            pathType: Prefix
            backend:
              service:
                name: tcc-customer
                port:
                  number: 80
          - path: /api/v1/address
            pathType: Prefix
            backend:
              service:
                name: tcc-customer
                port:
                  number: 80
          - path: /api/v1/product
            pathType: Prefix
            backend:
              service:
                name: tcc-catalog
                port:
                  number: 80
          - path: /api/v1/order
            pathType: Prefix
            backend:
              service:
                name: tcc-order
                port:
                  number: 80
          - path: /api/v1/order
            pathType: Prefix
            backend:
              service:
                name: tcc-order
                port:
                  number: 80
  tls:
    - hosts:
        - moreofthis.morettis.me
```
{% endcode %}

Para uma API Gateway, também é possível acrescentar mecanismos de Rate Limit, autenticação e autorização. Porém, no contexto do trabalho, isso não foi configurado.&#x20;

### Referências

TRAEFIK. Traefik Proxy Documentation - Traefik. 2025. Disponível em: \<https:\
//doc.traefik.io/traefik/>
