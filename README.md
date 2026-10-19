# Unit Tests com Jest e Stryker

Fork de [ugioni/unit-tests-jest](https://github.com/ugioni/unit-tests-jest), adaptado para experimentar a técnica de **testes de mutação** com [StrykerJS](https://stryker-mutator.io/).

## Objetivo

Executar os testes unitários existentes com Jest e avaliar sua capacidade de identificar pequenas modificações introduzidas automaticamente no código pelo Stryker. Um mutante **morto** foi identificado por um teste; um mutante **sobrevivente** pode apontar uma lacuna nos testes.

## Executar localmente

Requer Node.js 20+ e npm.

```bash
npm install
npm test
npm run coverage
npm run mutation
```

O `npm install` também atualiza o arquivo `package-lock.json` com as novas dependências, que deve ser incluído em um commit.

## Resultados

O Stryker gera o relatório HTML em `reports/mutation/html/index.html`. Abra-o no navegador após `npm run mutation`.

A pontuação de mutação indica a eficácia da suíte para detectar as alterações testadas. Não confunda cobertura de código com mutation score: executar linhas não garante detectar bugs.

## Estrutura

- `src/`: código original
- `test/`: testes Jest
- `stryker.config.json`: configuração dos testes de mutação
- `.github/workflows/mutation-tests.yml`: execução automatizada com GitHub Actions

### Procedimento de análise

1. Execute a suíte Jest original.
2. Rode o Stryker e observe mutantes mortos, sobreviventes e erros.
3. Inspecione no relatório os mutantes sobreviventes e identifique condições ou casos não testados.
4. Melhore os testes e execute novamente o Stryker, comparando os resultados.

Projeto baseado no repositório de ugioni.
