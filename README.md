# Portfólio de QA · Testes Manuais de API em ServeRest

**Autor:** Luiz Vinicius Cunha Maciel
**Projeto:** Portfólio pessoal de QA
**Aplicação sob teste:** [serverest.dev](https://serverest.dev) - API REST pública que simula o back-end de uma loja virtual
**Ciclo de referência:** Ciclo 1 · 31/07/2026

---

## Sobre este projeto

Este repositório reúne o ciclo completo de um processo de testes manuais de API aplicado à ServeRest, uma API REST gratuita e open source criada para servir como ambiente de estudo e prática de testes de software. O objetivo foi simular todas as etapas de um ciclo de testes de API: planejamento, design de casos, execução via Postman, registro de defeitos e encerramento com recomendação para o produto.

Foram planejados e executados **32 casos de teste** cobrindo **17 funcionalidades/endpoints** em escopo (login, usuários, produtos e carrinhos), resultando na abertura de **1 defeito de severidade Alta**.

---

## Como navegar pelos documentos

Os documentos foram escritos na ordem em que normalmente são produzidos em um ciclo de testes real:

| # | Documento | O que contém |
|---|-----------|---------------|
| 1 | **Plano_de_Teste.pdf** | Escopo, tipos de teste, estratégia, técnicas de design de caso, critérios de entrada/saída, ambiente e ferramentas. Ponto de partida do ciclo. |
| 2 | **Casos_de_Teste.pdf** | 32 casos de teste detalhados (CT-01 a CT-32), com pré-condições, dados de teste, passos, resultado esperado, prioridade e tipo de teste, cobrindo os recursos `/login`, `/usuarios`, `/produtos` e `/carrinhos`. |
| 3 | **Matriz_Execucao.xlsx** | Planilha de execução do Ciclo 1: status de cada caso (Passou/Falhou), data, executor, evidências e observações. |
| 4 | **Testes_postman_collection.json** | Coleção Postman com as requisições organizadas por recurso (Login, Cadastro de Usuários, Produtos, Carrinhos e Segurança), criada para execução dos testes. |
| 5 | **Relatorio_de_Bugs.pdf** | O defeito encontrado na execução (BUG-01), com severidade, prioridade, passos para reproduzir, resultado esperado x obtido e evidências. |
| 6 | **Test_Summary_Report.pdf** | Report do Ciclo 1: matriz de rastreabilidade, métricas, verificação dos critérios de saída, riscos residuais e recomendação final. |

---

## Resultados do Ciclo 1

| Métrica | Valor |
|---|---|
| Casos planejados / executados | 32 / 32 (100%) |
| Casos aprovados | 31 (96,9%) |
| Casos reprovados | 1 (3,1%) |
| Casos bloqueados | 0 |
| Casos de prioridade Alta executados | 18/18 (100%) |
| Defeitos abertos | 1 (Alta) |
| Cobertura de funcionalidades em escopo | 17/17 (100%) |

**Recomendação final do ciclo:** corrigir prioritariamente o BUG-01 (GET /usuarios retorna a listagem completa de usuários, incluindo o campo "password", sem exigir autenticação de administrador) antes de qualquer evolução da API que dependa da confidencialidade dos dados de usuário. As demais 31 funcionalidades testadas foram aprovadas e não apresentam impedimentos. Após a correção, recomenda-se um Ciclo 2 de regressão focado no caso CT-31.

---

## Técnicas e abordagem aplicadas

- Testes funcionais, de contrato/schema, negativos, de regras de negócio, exploratórios e smoke test
- Particionamento de equivalência (ex.: e-mails válidos vs. inválidos) e análise de valor limite (ex.: estoque, tamanho de campos)
- Tabela de decisão para regras de negócio (ex.: usuário administrador vs. não administrador)
- Caso de uso ponta a ponta: cadastro de usuário → login → cadastro de produto → adicionar ao carrinho → concluir compra
- Rastreabilidade entre funcionalidade em escopo → caso de teste → execução → defeito
- Encerramento de ciclo com verificação formal dos critérios de saída definidos no Plano de Testes

---

## Ferramentas utilizadas

Postman para requisições HTTP · Word e Excel para gestão de casos de teste e defeitos · Swagger da própria ServeRest como base de documentação

---

## Próximos passos

- Correção e regressão do BUG-01 (CT-31), confirmando o retorno de 401 em GET /usuarios sem autenticação
- Avaliação de automação dos fluxos críticos de API (login, cadastro, carrinho) como evolução do portfólio
