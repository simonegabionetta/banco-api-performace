# Testes de Performance da API do Banco com K6

[![License](https://img.shields.io/github/license/SimoneGabionetta/banco-api-performace)](https://github.com/SimoneGabionetta/banco-api-performace/blob/main/LICENSE)


Repositório com testes de performance automatizados desenvolvidos com a ferramenta [Grafana K6](https://k6.io/) e escritos em JavaScript, voltados para a API do sistema bancário.


---

## Introdução

Este projeto tem como objetivo simular diferentes cargas e cenários de uso para a API do banco, avaliando seu desempenho e identificando possíveis gargalos. Os testes são escritos com foco em modularidade, organização por contexto e reutilização de modelos de dados.

---

##  Tecnologias Utilizadas

![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![K6](https://img.shields.io/badge/K6-FF5C5C?style=for-the-badge&logo=k6&logoColor=white)
![JSON](https://img.shields.io/badge/JSON-000000?style=for-the-badge&logo=json&logoColor=white)
---

## Estrutura do Repositório

```
banco-api-performance/
├── fixtures/         # Dados de entrada para os testes (ex: usuários, payloads)
├── helpers/          # Funções utilitárias reutilizáveis para interação com a API
├── tests/            # Casos de teste organizados por módulo da API
├── utils /           # Funções utilitárias reutilizáveis
├── config/           # Arquivos de configuração de variáveis de ambiente
└── README.md         # Este documento
```

---

## Objetivo de Cada Grupo de Arquivos

- **`fixtures/`**: Dados de entrada para os testes (ex: usuários, payloads).
- **`helpers/`**: Funções utilitárias reutilizáveis para interação com a API.
- **`tests/`**: Casos de teste organizados por módulo da API
- **`utils/`**: Funções utilitárias reutilizáveis.
- **`config/`**: Arquivos de configuração de variáveis de ambiente

---

##  Instalação e Execução

### 1. Clone o Repositório

```bash
git clone https://github.com/juliodelimas/banco-api-performance.git
cd banco-api-performance
```

### 2. Configure as Variáveis de Ambiente

Altere o arquivo `config.local.json` e defina a URL base da API a ser testada:

```json
{
    "baseUrl": "http://localhost:3000"
}
```

>  Essas variáveis serão usada dinamicamente nos testes para montar as requisições.

### 3. Execute um Teste

```bash
k6 run tests/login.test.js
```

Certifique-se de passar a variável de ambiente `BASE_URL`, caso não esteja usando um `config.local.json` ou uma abordagem de carregamento automático:

```bash
k6 run tests/autenticacao/login.test.js -e BASE_URL=http://localhost:3000
```

### 4. Acompanhamento em Tempo Real + Exportação de Relatório

Você pode ativar o modo dashboard do K6 e exportar o relatório ao final do teste:

```bash
K6_WEB_DASHBOARD=true \
K6_WEB_DASHBOARD_EXPORT=html-report.html \
k6 run tests/autenticacao/login.test.js \
-e BASE_URL=http://localhost:3000
```

Após a execução, o relatório estará salvo como `html-report.html`.

Criado por [Simone Gabionetta ](https://www.linkedin.com/in/smgabionetta/)
