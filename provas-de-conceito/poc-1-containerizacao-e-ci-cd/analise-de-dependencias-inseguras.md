---
description: Descrição da segunda boa prática da POC1
icon: barcode-scan
---

# Análise de Dependências Inseguras

Para a análise de Dependências inseguras, seguiu-se como o SonarQube e também foi adicionado ao mesmo arquivo de workflow de build. Para isso, os autores escolheram as seguintes ferramentas:&#x20;

* npm audit, e
* pip audit.&#x20;

A escolha se deve ao fato de serem ferramentas de scanner das ferramentas utilizadas que levam em conta vulnerabilidades reportadas, com maior frequência de atualização, além de possuirem ferramentas que viabilizam a utilização em pipelines.&#x20;

&#x20;Configuração para o pip-audit:&#x20;

```yaml
name: scan
on:
  push:
    branches: [ main ]
  pull_request:
    types: [opened, synchronize, reopened]
  workflow_dispatch:

jobs:
  pip-audit:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: pypa/gh-action-pip-audit@v1.1.0
        with:
          inputs: requirements.txt
```

Já o de configuração para o Front-End:&#x20;

```yaml
name: scan
on:
  push:
    branches: [ main ]
  pull_request:
    types: [opened, synchronize, reopened]
  workflow_dispatch:

jobs:
  npm-audit:
    name: NPM Audit
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
        with:
          fetch-depth: 0
        
      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 20
          cache: 'npm'
          cache-dependency-path: frontend/package-lock.json
          
      - name: Audit npm dependencies
        run: |
          cd frontend
          npm run audit:ci || true
        shell: bash
```
