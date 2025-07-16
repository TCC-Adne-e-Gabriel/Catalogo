---
description: Descrição da primeira boa prática da POC 1
icon: pen-field
---

# Análise de Segurança de Código

Ferramentas de análise de segurança de software:

Para a aplicação da primeira boa prática, adotou-se a ferramenta de análise de\
código estática SonarQube. Para isso, foi necessária a criação de uma organização no\
SonarCloud para os repositórios do trabalho de conclusão de curso, além da adição\
de um workflow no GitHub para rodar o scanner do SonarCloud nas seguintes ações:

* Push na branch principal do projeto, e
* Em abertura de pull request.

O SonarQube possui um app do Github Actions, o que permite que sejam definidas regras para rodar a análise. Isso é definido no arquivo `.github/workflows/<nome-do-workflow>.yml` . As configurações estabelecidas pelos autores foram:&#x20;



```yaml
name: scan
on:
  push:
    branches: [ main ]
  pull_request:
    types: [opened, synchronize, reopened]
  workflow_dispatch:

jobs:
  sonarcloud:
    name: SonarCloud
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0 

      - name: SonarQube Scan
        uses: SonarSource/sonarqube-scan-action@v5
        env:
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
```



A env `SONAR_TOKEN`  é coletada por meio da interface do SonarCloud, do repositório em que deseja configurar. É necessária para visualização do painel na ferramenta e visualização de métricas.&#x20;



