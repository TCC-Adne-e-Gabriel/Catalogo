---
icon: laptop-code
---

# Gerenciamento de Container com Kubernetes

O desenvolvimento da Prova de Conceito iniciou-se com a configuração do cluster utilizando do k3s. No trabalho em questão, utilizou-se de uma máquina virtual e duas físicas dos próprios autores para os testes. As especificações das máquinas utilizadas são:

* Nó principal: Máquina Virtual Debian 12, com 4GB de RAM;
* Worker 1: Máquina Windows com WSL Ubuntu 22.02, 40GB de RAM;
* Worker 2: Máquina com Manjaro, 8GB de RAM;

O k3s foi escolhido por ser uma distribuição do K9s com maior facilidade de configuração. A documentação pode ser seguida para instalação dos nós que atuam como workers e para o master: [https://docs.k3s.io/quick-start](https://docs.k3s.io/quick-start).&#x20;

A instalação do k3s no nó master pode ser realizada com o seguinte comando:&#x20;

`curl -sfL https://get.k3s.io | sh -`

{% hint style="warning" %}
Os autores encontraram problemas na comunicação entre os nós com a instalação básica, que pode ser devido à configurações das distribuições linux utilizadas, por isso, para o nó master, o seguinte comando foi utilizado:&#x20;

curl -sfL https://get.k3s.io | INSTALL\_K3S\_EXEC='--flannel-backend=wireguard-native' sh -

O parâmetro `--flannel-backend=wireguard-native` é uma **opção de configuração do Flannel**, um **plugin de rede** usado em clusters Kubernetes (como K3s ou kubeadm) para permitir comunicação entre pods em diferentes nós.
{% endhint %}

Para que os outros nós entrem no cluster é a partir do comando:&#x20;

`curl -sfL https://get.k3s.io/ | K3S_URL=https:/// K3S_TOKEN= sh -`

O token do master pode ser encontrado em `/var/lib/rancher/k3s/server/node-token`  no nó master.&#x20;

Apesar de ser o nó com menor capacidade de processamento, a máquina virtual foi escolhida para ser o nó principal, pois ficou dedicada para esse uso. Sendo assim, por ser o nó que roda mais pods, essa foi considerada uma limitação durante o trabalho.

Após inicialização com sucesso, é possível visualizar os nós da rede com o comando:

\
`kubectl get nodes`&#x20;

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

<p align="center">Fonte: Autores.</p>

Para o acesso aos serviços no cluster kubernetes, também foi necessária a criação de repositórios do Docker Hub, que funcionam como repositórios centralizados de gerenciar e armazenar imagens docker.

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

<p align="center">Fonte: Autores. Ferramenta: Docker (2025).</p>

Para buildar a imagem com o repositório criado:&#x20;

`docker build adnemoretti/tcc-customer:latest .`&#x20;

E para publicar no DockerHub:&#x20;

`docker push adnemoretti/tcc-customer:latest`&#x20;

### Banco de Dados

Para o banco de dados, foi necessário:&#x20;

* ConfigMap;
* PersitentVolume;&#x20;
* PersistentVolumeClaim; &#x20;
* Service, e&#x20;
* Deployment.&#x20;

{% hint style="info" %}
Importante pesquisar sobre o tipo StateFul do Kubernetes e se adequa ao seu contexto. No contexto do trabalho, não foi utilizado.&#x20;
{% endhint %}

O ConfigMap foi utilizado para definir variáveis de ambiente para o serviço, basicamente um mapeamento do nome da variável de ambiente com o valor dela.

{% code title="app-secrets.yml" lineNumbers="true" %}
```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: catalog-secrets
  labels:
    app: catalog-db
data:
  POSTGRES_PORT: "5432"
  POSTGRES_DB: catalog_db
  POSTGRES_USER: moretti_catalog
  POSTGRES_PASSWORD: moretti
```
{% endcode %}

O PersistentVolume é uma parte de armazenamento dentro do cluster; enquanto que o PersistentVolumeClaim é uma requisição do armazenamento por algum usuário. O Código PersistentVolume apresenta o código do volume persistente; enquanto que o Código PersistentVolumeClaim apresenta a solicitação do volume com acesso de leitura e escrita. Importante ressaltar que além do nome, o caminho em hostPath deve ser diferente para cada banco de dados de cada serviço, para que não acessem o mesmo lugar da memória.

**PersistentVolume**:&#x20;

{% code lineNumbers="true" %}
```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: catalog-volume
  labels:
    type: local
    app: catalog-db
spec:
  storageClassName: manual
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteMany
  hostPath:
    path: /data/catalogdb
```
{% endcode %}

**PersistentVolumeClaim:**&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: catalog-volume-claim
  labels:
    app: catalog-db
spec:
  storageClassName: manual
  accessModes:
    - ReadWriteMany
  resources:
    requests:
      storage: 1Gi
```
{% endcode %}

**Deployment:**

Um **Deployment** é um objeto que **gera e gerencia réplicas de pods** a partir de um template. Ele garante que sempre exista um número desejado de réplicas (cópias da aplicação) em execução.

{% code overflow="wrap" lineNumbers="true" %}
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: catalog-db
spec:
  replicas: 1
  selector:
    matchLabels:
      app: catalog-db
  template:
    metadata:
      labels:
        app: catalog-db
    spec:
      containers:
        - name: catalog-db
          image: 'postgres:14'
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 5432
          envFrom:
            - configMapRef:
                name: catalog-secrets
          volumeMounts:
            - mountPath: /var/lib/postgresql/data
              name: postgresdata
      volumes:
        - name: postgresdata
          persistentVolumeClaim:
            claimName: catalog-volume-claim code
```
{% endcode %}

**Service:**&#x20;

Um **Service** é um recurso que expõe os pods para acesso dentro ou fora do cluster. O banco ficou com type ClusterIP, então só é acessível dentro do cluster. Para acessar externamente, basta usar o tipo NodePort.&#x20;

{% code title="" lineNumbers="true" %}
```yaml
apiVersion: v1
kind: Service
metadata:
  name: catalog-db
  labels:
    app: catalog-db
spec:
  type: ClusterIP
  ports:
    - port: 5432
  selector:
    app: catalog-db
```
{% endcode %}

### Aplicações:&#x20;

O arquivo de services e de deployment foi o mesmo para todos os serviços do backend, com mudanças apenas no nome.

**Deployment**:

{% code lineNumbers="true" %}
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: tcc-catalog
  labels:
    app: tcc-catalog
spec:
  replicas: 2
  selector:
    matchLabels:
      app: tcc-catalog
  template:
    metadata:
      labels:
        app: tcc-catalog
    spec:
      initContainers:
      - name: db-migration-init
        image: adnemoretti/tcc-catalog:latest
        command: ["/bin/sh", "-c", "/app/scripts/prestart.sh"] 
        env:
        - name: POSTGRES_SERVER
          value: catalog-db
        - name: POSTGRES_PORT
          value: "5432"
        - name: POSTGRES_DB
          value: catalog_db
        - name: POSTGRES_USER
          valueFrom:
            configMapKeyRef:
              name: catalog-secrets
              key: POSTGRES_USER
        - name: POSTGRES_PASSWORD
          valueFrom:
            configMapKeyRef:
              name: catalog-secrets
              key: POSTGRES_PASSWORD

      containers:
      - name: tcc-catalog
        image: adnemoretti/tcc-catalog:latest
        ports:
        - containerPort: 8002
        env:
        - name: POSTGRES_SERVER
          value: catalog-db
        - name: POSTGRES_PORT
          value: "5432"
        - name: POSTGRES_DB
          value: catalog_db
        - name: POSTGRES_USER
          valueFrom:
            configMapKeyRef:
              name: catalog-secrets
              key: POSTGRES_USER
        - name: POSTGRES_PASSWORD
          valueFrom:
            configMapKeyRef:
              name: catalog-secrets
              key: POSTGRES_PASSWORD
        - name: SECRET_KEY
          value: <key>
        - name: ALGORITHM
          value: <algorithm>
        - name: ACCESS_TOKEN_EXPIRE_DAYS
          value: "<tempo>"
```
{% endcode %}

**Service**:&#x20;

{% code lineNumbers="true" %}
```yaml
apiVersion: v1
kind: Service
metadata:
  name: tcc-catalog
  labels:
    app: tcc-catalog
spec:
  type: ClusterIP
  ports:
  - port: 80
    targetPort: 8002
    name: tcc-catalog
  selector:
    app: tcc-catalog
```
{% endcode %}



O repositório com todos os arquivos de configuração utilizados no projeto podem ser visualizados aqui: [https://github.com/TCC-Adne-e-Gabriel/k3s-configs](https://github.com/TCC-Adne-e-Gabriel/k3s-configs).

### Referências

DOCKER. What is Docker? 2025. Disponível em: https://docs.docker.com/\
get-started/docker-overview/.

KUBERNETES. Kubernetes. 2025. Disponível em: https://kubernetes.io/pt-br/docs/\
home/

K3S. K3s - Lightweight Kubernetes. 2025. [https://k3s.io/](https://k3s.io/). Acesso em: jul. 2025.\
Citado na página 63.
