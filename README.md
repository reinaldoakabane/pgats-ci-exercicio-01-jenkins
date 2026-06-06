[![Code coverage badge](https://img.shields.io/badge/coverage-100%25-brightgreen)](https://stryker-mutator.io/robo-coasters-example/reports/coverage/lcov-report/index.html)
[![Mutation testing badge](https://img.shields.io/endpoint?style=flat&url=https%3A%2F%2Fbadge-api.stryker-mutator.io%2Fgithub.com%2Fstryker-mutator%2Frobo-coasters-example%2Fmaster)](https://dashboard.stryker-mutator.io/reports/github.com/stryker-mutator/robo-coasters-example/master)

# Pipeline CI/CD com Jenkins e Docker 🚀

Para realizar o exercício 01 foi criada uma pipeline utilizando Jenkins com execução em container Docker, automatizando a instalação das dependências e a execução dos testes E2E com Playwright.

## Objetivo

Criar uma pipeline capaz de:

* Obter o código do repositório.
* Instalar as dependências do projeto.
* Instalar os navegadores e dependências do Playwright.
* Executar os testes E2E automatizados.

## Como funciona

A pipeline é executada dentro de um container Docker utilizando a imagem oficial Node.js 24.

### Ambiente Docker

```groovy
agent {
    docker {
        image 'node:24'
        args '-u root'
    }
}
```

A execução como usuário root foi necessária para permitir a instalação das dependências exigidas pelo Playwright.

### Checkout do Código

O Jenkins realiza o clone do repositório através do comando:

```groovy
checkout scm
```

### Instalação das Dependências

As dependências do projeto são instaladas utilizando Yarn:

```groovy
sh 'yarn'
```

### Instalação do Playwright

Os navegadores e dependências do sistema operacional são instalados através do comando:

```groovy
sh 'npx playwright install --with-deps'
```

### Execução dos Testes

Os testes E2E são executados utilizando:

```groovy
sh 'yarn run e2e'
```

## Dificuldades

A maior dificuldade encontrada durante o exercício foi a configuração do ambiente Docker e a adaptação dos comandos utilizados no GitHub Actions para o Jenkins. Após realizar pesquisas e consultar a documentação das ferramentas, foi possível compreender as diferenças entre os ambientes e ajustar os comandos necessários para que a pipeline funcionasse corretamente.

## Resultado

Ao executar a pipeline, o Jenkins cria um container Node.js, instala as dependências do projeto, configura o Playwright e executa automaticamente os testes E2E, demonstrando o funcionamento de uma pipeline básica de CI utilizando Jenkins e Docker.


<img width="1895" height="583" alt="image" src="https://github.com/user-attachments/assets/9a372477-86b8-439f-b851-095ec36238f5" />


---

💜⚡️
# pgats-ci
