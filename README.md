Proposta de entrega para o Teste Técnico
Funcionalidade escolhida

Fluxo de compra no site SauceDemo

O fluxo validado será:

Login com usuário válido.
Visualização da listagem de produtos.
Adição de produto ao carrinho.
Validação do carrinho.
Preenchimento dos dados de checkout.
Finalização da compra.
Logout do sistema.
História do Usuário

Como usuário autenticado da loja SauceDemo,
quero acessar a listagem de produtos, adicionar itens ao carrinho e finalizar uma compra,
para que eu consiga simular uma jornada completa de compra com sucesso.

Critérios de Aceite
CA001 — Login com sucesso

Dado que o usuário esteja na página de login,
quando informar usuário e senha válidos,
então deverá ser redirecionado para a página de produtos.

CA002 — Listagem de produtos

Dado que o usuário esteja autenticado,
quando acessar a página inicial da loja,
então os produtos disponíveis devem ser exibidos corretamente.

CA003 — Adicionar produto ao carrinho

Dado que o usuário esteja na listagem de produtos,
quando clicar em “Add to cart” em um produto,
então o item deverá ser adicionado ao carrinho.

CA004 — Validar carrinho

Dado que o usuário tenha adicionado um produto ao carrinho,
quando acessar o carrinho,
então o produto selecionado deverá ser exibido corretamente.

CA005 — Checkout com sucesso

Dado que o usuário esteja no carrinho com produto adicionado,
quando preencher os dados obrigatórios do checkout,
então deverá avançar para a tela de resumo da compra.

CA006 — Finalização da compra

Dado que o usuário esteja na tela de resumo do pedido,
quando clicar em “Finish”,
então o sistema deverá exibir a mensagem de compra concluída com sucesso.

CA007 — Logout

Dado que o usuário esteja autenticado,
quando clicar na opção de logout,
então deverá retornar para a tela de login.

Casos de Teste
ID	Cenário	Pré-condição	Passos	Resultado Esperado	Prioridade
CT001	Login com usuário válido	Estar na tela de login	Informar usuário standard_user e senha secret_sauce	Usuário acessa a página de produtos	Alta
CT002	Login com senha inválida	Estar na tela de login	Informar usuário válido e senha inválida	Sistema exibe mensagem de erro	Alta
CT003	Validar produtos na tela inicial	Usuário logado	Acessar página de produtos	Produtos são exibidos	Média
CT004	Adicionar produto ao carrinho	Usuário logado	Clicar em “Add to cart”	Carrinho exibe quantidade 1	Alta
CT005	Remover produto do carrinho	Produto no carrinho	Clicar em “Remove”	Produto é removido do carrinho	Média
CT006	Validar item no carrinho	Produto adicionado	Acessar carrinho	Produto selecionado aparece corretamente	Alta
CT007	Checkout sem preencher campos obrigatórios	Produto no carrinho	Clicar em “Continue” sem preencher dados	Sistema exibe mensagem de erro	Alta
CT008	Checkout com dados válidos	Produto no carrinho	Preencher nome, sobrenome e CEP	Sistema avança para resumo da compra	Alta
CT009	Finalizar compra	Checkout preenchido	Clicar em “Finish”	Mensagem de sucesso é exibida	Alta
CT010	Logout com sucesso	Usuário autenticado	Acessar menu e clicar em logout	Usuário retorna para tela de login	Média
Estimativa de Tempo de Teste
Cálculo utilizado

Para estimar o tempo, considerei:

Tempo médio de execução manual por cenário.
Tempo para registrar evidências.
Tempo para análise de possíveis falhas.
Tempo para automação dos principais fluxos.
Tempo para execução e ajuste dos testes automatizados.
Estimativa manual
Atividade	Quantidade	Tempo médio	Total
Leitura e entendimento do fluxo	1	30 min	30 min
Escrita da história do usuário	1	20 min	20 min
Escrita dos critérios de aceite	7	5 min	35 min
Escrita dos casos de teste	10	8 min	80 min
Execução manual dos testes	10	5 min	50 min
Registro de evidências	10	3 min	30 min
Análise de bugs ou inconsistências	1	30 min	30 min

Total estimado para documentação e teste manual:
275 minutos, aproximadamente 4h35min.

Estimativa de automação
Atividade	Quantidade	Tempo médio	Total
Configuração do projeto Cypress	1	30 min	30 min
Criação dos testes automatizados	5 fluxos	25 min	125 min
Ajustes de seletores e waits	1	40 min	40 min
Execução local e correções	1	40 min	40 min
Criação da pipeline	1	30 min	30 min

Total estimado para automação:
265 minutos, aproximadamente 4h25min.

Estimativa total

Tempo total estimado: aproximadamente 9 horas.

Escolha dos fluxos automatizados

Eu automatizaria os fluxos mais críticos da jornada do usuário:

Login com sucesso.
Login inválido.
Adicionar produto ao carrinho.
Checkout com sucesso.
Logout.

Esses fluxos foram escolhidos porque representam a jornada principal da aplicação e cobrem pontos importantes como autenticação, navegação, regra de negócio, validação de carrinho e finalização de compra.
