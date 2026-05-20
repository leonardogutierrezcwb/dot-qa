# Teste Técnico – Analista de Testes

## 1. Objetivo

Este documento tem como objetivo apresentar a entrega do teste técnico para a posição de **Analista de Testes**, contemplando:

- História do usuário;
- Critérios de aceite;
- Casos de teste;
- Estimativa de tempo de teste;
- Estratégia de automação com Cypress;
- Arquivos sugeridos para o projeto;
- Pipeline para execução dos testes automatizados.

---

## 2. Site escolhido

**Site:** SauceDemo  
**URL:** https://www.saucedemo.com/

O site SauceDemo foi escolhido por ser uma aplicação pública, simples e bastante utilizada em estudos e testes de QA. Ele permite validar fluxos essenciais como login, listagem de produtos, carrinho, checkout e logout.

Essa escolha permite demonstrar conhecimento em:

- Análise funcional;
- Escrita de critérios de aceite;
- Criação de casos de teste;
- Automação E2E com Cypress;
- Estruturação de pipeline CI/CD;
- Registro de evidências em caso de falha.

---

## 3. Funcionalidade escolhida

### Fluxo de compra no SauceDemo

O fluxo validado contempla:

1. Login com usuário válido;
2. Visualização da listagem de produtos;
3. Adição de produto ao carrinho;
4. Validação do carrinho;
5. Preenchimento dos dados de checkout;
6. Finalização da compra;
7. Logout do sistema.

---

## 4. História do usuário

**Como** usuário autenticado da loja SauceDemo,  
**quero** acessar a listagem de produtos, adicionar itens ao carrinho e finalizar uma compra,  
**para que** eu consiga simular uma jornada completa de compra com sucesso.

---

## 5. Critérios de aceite

### CA001 — Login com sucesso

**Dado** que o usuário esteja na página de login,  
**quando** informar usuário e senha válidos,  
**então** deverá ser redirecionado para a página de produtos.

### CA002 — Listagem de produtos

**Dado** que o usuário esteja autenticado,  
**quando** acessar a página inicial da loja,  
**então** os produtos disponíveis devem ser exibidos corretamente.

### CA003 — Adicionar produto ao carrinho

**Dado** que o usuário esteja na listagem de produtos,  
**quando** clicar em `Add to cart` em um produto,  
**então** o item deverá ser adicionado ao carrinho.

### CA004 — Validar carrinho

**Dado** que o usuário tenha adicionado um produto ao carrinho,  
**quando** acessar o carrinho,  
**então** o produto selecionado deverá ser exibido corretamente.

### CA005 — Checkout com sucesso

**Dado** que o usuário esteja no carrinho com produto adicionado,  
**quando** preencher os dados obrigatórios do checkout,  
**então** deverá avançar para a tela de resumo da compra.

### CA006 — Finalização da compra

**Dado** que o usuário esteja na tela de resumo do pedido,  
**quando** clicar em `Finish`,  
**então** o sistema deverá exibir a mensagem de compra concluída com sucesso.

### CA007 — Logout

**Dado** que o usuário esteja autenticado,  
**quando** clicar na opção de logout,  
**então** deverá retornar para a tela de login.

---

## 6. Casos de teste funcionais

| ID | Cenário | Pré-condição | Passos | Resultado Esperado | Prioridade |
|---|---|---|---|---|---|
| CT001 | Login com usuário válido | Estar na tela de login | Informar usuário `standard_user` e senha `secret_sauce` | Usuário acessa a página de produtos | Alta |
| CT002 | Login com senha inválida | Estar na tela de login | Informar usuário válido e senha inválida | Sistema exibe mensagem de erro | Alta |
| CT003 | Validar produtos na tela inicial | Usuário logado | Acessar página de produtos | Produtos são exibidos | Média |
| CT004 | Adicionar produto ao carrinho | Usuário logado | Clicar em `Add to cart` | Carrinho exibe quantidade 1 | Alta |
| CT005 | Remover produto do carrinho | Produto no carrinho | Clicar em `Remove` | Produto é removido do carrinho | Média |
| CT006 | Validar item no carrinho | Produto adicionado | Acessar carrinho | Produto selecionado aparece corretamente | Alta |
| CT007 | Checkout sem preencher campos obrigatórios | Produto no carrinho | Clicar em `Continue` sem preencher dados | Sistema exibe mensagem de erro | Alta |
| CT008 | Checkout com dados válidos | Produto no carrinho | Preencher nome, sobrenome e CEP | Sistema avança para resumo da compra | Alta |
| CT009 | Finalizar compra | Checkout preenchido | Clicar em `Finish` | Mensagem de sucesso é exibida | Alta |
| CT010 | Logout com sucesso | Usuário autenticado | Acessar menu e clicar em logout | Usuário retorna para tela de login | Média |

---

## 7. Estimativa de tempo de teste

### 7.1 Critérios considerados

Para calcular o tempo estimado, foram considerados:

- Tempo de entendimento do fluxo;
- Escrita da história do usuário;
- Escrita dos critérios de aceite;
- Escrita dos casos de teste;
- Execução manual dos testes;
- Registro de evidências;
- Análise de possíveis falhas;
- Criação dos testes automatizados;
- Configuração do projeto Cypress;
- Criação da pipeline.

### 7.2 Estimativa para documentação e teste manual

| Atividade | Quantidade | Tempo médio | Total |
|---|---:|---:|---:|
| Leitura e entendimento do fluxo | 1 | 30 min | 30 min |
| Escrita da história do usuário | 1 | 20 min | 20 min |
| Escrita dos critérios de aceite | 7 | 5 min | 35 min |
| Escrita dos casos de teste | 10 | 8 min | 80 min |
| Execução manual dos testes | 10 | 5 min | 50 min |
| Registro de evidências | 10 | 3 min | 30 min |
| Análise de bugs ou inconsistências | 1 | 30 min | 30 min |

**Total estimado para documentação e teste manual:**  
**275 minutos**, aproximadamente **4h35min**.

### 7.3 Estimativa para automação

| Atividade | Quantidade | Tempo médio | Total |
|---|---:|---:|---:|
| Configuração do projeto Cypress | 1 | 30 min | 30 min |
| Criação dos testes automatizados | 5 fluxos | 25 min | 125 min |
| Ajustes de seletores e waits | 1 | 40 min | 40 min |
| Execução local e correções | 1 | 40 min | 40 min |
| Criação da pipeline | 1 | 30 min | 30 min |

**Total estimado para automação:**  
**265 minutos**, aproximadamente **4h25min**.

### 7.4 Estimativa total

| Etapa | Tempo |
|---|---:|
| Documentação e testes manuais | 4h35min |
| Automação e pipeline | 4h25min |

**Tempo total estimado:** aproximadamente **9 horas**.

---

## 8. Fluxos escolhidos para automação

Para a automação com Cypress, foram escolhidos os fluxos mais críticos da jornada do usuário:

1. Login com sucesso;
2. Login inválido;
3. Adicionar produto ao carrinho;
4. Validar produto no carrinho;
5. Checkout com sucesso;
6. Logout.

### Justificativa da escolha

Esses fluxos foram escolhidos porque representam a jornada principal da aplicação e cobrem pontos importantes como:

- Autenticação;
- Validação de credenciais;
- Navegação entre páginas;
- Manipulação de carrinho;
- Preenchimento de formulário;
- Finalização de compra;
- Encerramento de sessão.

---

## 9. Estrutura sugerida do projeto

```text
teste-tecnico-qa/
├── cypress/
│   ├── e2e/
│   │   └── saucedemo.cy.js
│   ├── fixtures/
│   │   └── users.json
│   └── support/
│       ├── commands.js
│       └── e2e.js
├── cypress.config.js
├── package.json
└── .github/
    └── workflows/
        └── cypress.yml
```

---

## 10. Arquivo package.json

```json
{
  "name": "teste-tecnico-qa-saucedemo",
  "version": "1.0.0",
  "description": "Teste técnico para Analista de Testes utilizando Cypress",
  "scripts": {
    "cy:open": "cypress open",
    "cy:run": "cypress run"
  },
  "devDependencies": {
    "cypress": "^13.15.0"
  }
}
```

---

## 11. Arquivo cypress.config.js

```javascript
const { defineConfig } = require("cypress");

module.exports = defineConfig({
  e2e: {
    baseUrl: "https://www.saucedemo.com",
    viewportWidth: 1366,
    viewportHeight: 768,
    defaultCommandTimeout: 10000,
    video: true,
    screenshotOnRunFailure: true
  }
});
```

---

## 12. Arquivo cypress/fixtures/users.json

```json
{
  "validUser": {
    "username": "standard_user",
    "password": "secret_sauce"
  },
  "invalidUser": {
    "username": "standard_user",
    "password": "senha_invalida"
  },
  "checkoutUser": {
    "firstName": "Leonardo",
    "lastName": "Gutierrez",
    "postalCode": "80000-000"
  }
}
```

---

## 13. Arquivo cypress/support/commands.js

```javascript
Cypress.Commands.add("login", (username, password) => {
  cy.visit("/");
  cy.get('[data-test="username"]').type(username);
  cy.get('[data-test="password"]').type(password);
  cy.get('[data-test="login-button"]').click();
});
```

---

## 14. Arquivo cypress/e2e/saucedemo.cy.js

```javascript
describe("Teste Técnico QA - Fluxo SauceDemo", () => {
  beforeEach(() => {
    cy.fixture("users").as("users");
  });

  it("CT001 - Deve realizar login com sucesso", function () {
    cy.login(this.users.validUser.username, this.users.validUser.password);

    cy.url().should("include", "/inventory.html");
    cy.get(".title").should("contain", "Products");
    cy.get(".inventory_item").should("have.length.greaterThan", 0);
  });

  it("CT002 - Deve exibir erro ao realizar login com senha inválida", function () {
    cy.login(this.users.invalidUser.username, this.users.invalidUser.password);

    cy.get('[data-test="error"]')
      .should("be.visible")
      .and("contain", "Username and password do not match");
  });

  it("CT003 - Deve adicionar produto ao carrinho com sucesso", function () {
    cy.login(this.users.validUser.username, this.users.validUser.password);

    cy.get('[data-test="add-to-cart-sauce-labs-backpack"]').click();

    cy.get(".shopping_cart_badge").should("be.visible").and("contain", "1");
    cy.get('[data-test="remove-sauce-labs-backpack"]').should("be.visible");
  });

  it("CT004 - Deve validar produto no carrinho", function () {
    cy.login(this.users.validUser.username, this.users.validUser.password);

    cy.get('[data-test="add-to-cart-sauce-labs-backpack"]').click();
    cy.get(".shopping_cart_link").click();

    cy.url().should("include", "/cart.html");
    cy.get(".inventory_item_name").should("contain", "Sauce Labs Backpack");
    cy.get(".cart_quantity").should("contain", "1");
  });

  it("CT005 - Deve realizar checkout com sucesso", function () {
    cy.login(this.users.validUser.username, this.users.validUser.password);

    cy.get('[data-test="add-to-cart-sauce-labs-backpack"]').click();
    cy.get(".shopping_cart_link").click();

    cy.get('[data-test="checkout"]').click();

    cy.get('[data-test="firstName"]').type(this.users.checkoutUser.firstName);
    cy.get('[data-test="lastName"]').type(this.users.checkoutUser.lastName);
    cy.get('[data-test="postalCode"]').type(this.users.checkoutUser.postalCode);

    cy.get('[data-test="continue"]').click();

    cy.url().should("include", "/checkout-step-two.html");
    cy.get(".summary_info").should("be.visible");
    cy.get(".inventory_item_name").should("contain", "Sauce Labs Backpack");

    cy.get('[data-test="finish"]').click();

    cy.url().should("include", "/checkout-complete.html");
    cy.get(".complete-header").should("contain", "Thank you for your order!");
  });

  it("CT006 - Deve realizar logout com sucesso", function () {
    cy.login(this.users.validUser.username, this.users.validUser.password);

    cy.get("#react-burger-menu-btn").click();
    cy.get('[data-test="logout-sidebar-link"]').click();

    cy.url().should("eq", "https://www.saucedemo.com/");
    cy.get('[data-test="login-button"]').should("be.visible");
  });
});
```

---

## 15. Pipeline GitHub Actions

### Caminho do arquivo

```text
.github/workflows/cypress.yml
```

### Conteúdo do arquivo

```yaml
name: Cypress Tests

on:
  push:
    branches:
      - main
      - master
  pull_request:
    branches:
      - main
      - master

jobs:
  cypress-run:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout do repositório
        uses: actions/checkout@v4

      - name: Configurar Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 20

      - name: Instalar dependências
        run: npm install

      - name: Executar testes Cypress
        run: npm run cy:run

      - name: Publicar evidências em caso de falha
        if: failure()
        uses: actions/upload-artifact@v4
        with:
          name: cypress-evidencias
          path: |
            cypress/screenshots
            cypress/videos
```

---

## 16. Evidências esperadas

Durante a execução dos testes, as evidências poderão ser geradas automaticamente pelo Cypress.

### Evidências em caso de falha

- Screenshots em `cypress/screenshots`;
- Vídeos em `cypress/videos`;
- Logs da execução no terminal;
- Artefatos publicados na pipeline do GitHub Actions.

---

## 17. Como executar localmente

### Instalar dependências

```bash
npm install
```

### Abrir o Cypress em modo interativo

```bash
npm run cy:open
```

### Executar os testes em modo headless

```bash
npm run cy:run
```

---

## 18. Conclusão

A entrega proposta cobre a jornada principal do usuário dentro do site SauceDemo, contemplando documentação funcional, critérios de aceite, casos de teste, estimativa de tempo, automação E2E com Cypress e pipeline de execução.

A escolha do SauceDemo permite uma avaliação objetiva da capacidade de análise, organização, documentação, automação e entendimento de fluxo crítico de negócio, sem depender de cadastro real, captcha, dados sensíveis ou integrações externas instáveis.
