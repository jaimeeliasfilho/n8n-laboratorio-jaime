LAB 10 — Automação de Solicitações Comerciais com n8n

1. Visão geral

Este projeto consiste no desenvolvimento de um workflow de automação comercial utilizando n8n, com recebimento de solicitações via Webhook, validação de dados, verificação de estoque, regras de aprovação comercial, integração HTTP simulada com CRM e retorno automatizado ao solicitante.

O objetivo é demonstrar como automatizar etapas de um processo comercial, reduzir verificações manuais e tratar diferentes situações de negócio de forma estruturada.

2. Objetivos do projeto

- Receber solicitações comerciais por meio de um Webhook.
- Preparar e validar os dados recebidos.
- Verificar a disponibilidade de estoque.
- Identificar solicitações que necessitam de aprovação comercial.
- Simular o registro da solicitação em um CRM.
- Gerar um protocolo de atendimento.
- Retornar mensagens específicas para cada cenário.
- Tratar exceções sem interromper indevidamente o fluxo.

3. Arquitetura do workflow

Fluxo principal

1. Webhook — recebimento da solicitação.
2. 02 - Preparar Dados da Solicitação Comercial.
3. 03 - Validar Quantidade Solicitada.
4. 04 - Validar Produto Solicitado.
5. 05 - Consultar Disponibilidade.
6. 06 - Verificar Estoque Disponível.
7. 07 - Preparar Pedido para Aprovação.
8. 08 - Verificar Necessidade de Aprovação Comercial.
9. 09 - Registrar Solicitação de Aprovação Comercial.
10. 10 - Integrar Solicitação ao CRM.
11. 11 - Preparar Retorno ao Cliente.
12. 12 - Responder ao Solicitante.

Tratamento de exceções

- 03.1 - Preparar Retorno de Quantidade Inválida.
- 04.1 - Preparar Retorno de Produto Não Informado.
- 06.1 - Preparar Retorno de Estoque Insuficiente.
- 08.1 - Preparar Retorno sem Aprovação.

As três primeiras exceções retornam diretamente ao solicitante. A situação sem necessidade de aprovação segue para o processamento compartilhado de registro e retorno.

4. Regras de negócio

Validação de quantidade

A solicitação deve apresentar quantidade maior que zero.

Validação de produto

O produto precisa estar informado para que a solicitação prossiga.

Verificação de estoque

A quantidade solicitada deve ser compatível com a disponibilidade simulada.

Aprovação comercial

- Até 10 unidades: aprovação automática.
- Acima de 10 unidades: encaminhamento para aprovação comercial.

Registro e protocolo

As solicitações aprovadas automaticamente ou encaminhadas para aprovação passam pela etapa de integração HTTP simulada com o CRM.

5. Tecnologias e recursos utilizados

- n8n: construção e orquestração do workflow.
- Webhook: recebimento de solicitações via HTTP.
- Edit Fields: preparação, organização e transformação dos dados.
- IF: validação de condições e direcionamento do fluxo.
- HTTP Request: integração com serviço externo.
- JSON: estruturação e transferência de dados.
- JSONPlaceholder: API pública utilizada para simular o registro no CRM.

6. Cenários de teste e validação

Foram executados cinco testes funcionais:

Cenário| Entrada| Resultado
Aprovação automática| 10 unidades| Solicitação aprovada automaticamente
Aprovação comercial| 20 unidades| Encaminhamento à equipe comercial
Quantidade inválida| 0 unidades| Retorno de quantidade inválida
Produto não informado| Campo ausente| Retorno solicitando identificação do produto
Estoque insuficiente| 40 unidades, estoque 35| Retorno de indisponibilidade

Resultado: os cinco cenários foram executados e apresentaram os retornos esperados.

7. Aprendizados técnicos

Durante o desenvolvimento, foram trabalhados conceitos importantes:

- Construção de workflows com múltiplas condições.
- Organização de caminhos alternativos e convergência de ramificações.
- Utilização de expressões n8n para recuperar dados de outros nós.
- Uso de operadores de fallback para tratar campos ausentes.
- Integração HTTP com envio de dados em JSON.
- Preparação de respostas dinâmicas conforme o status da solicitação.
- Tratamento de exceções e validação por cenários.

8. Limitações da demonstração

Este projeto possui finalidade educacional e demonstrativa.

- A disponibilidade de estoque é simulada.
- O JSONPlaceholder representa uma API de teste, não um CRM real.
- O protocolo retornado é um identificador simulado.
- Não há conexão com um sistema comercial ou estoque de produção.

9. Resultado final

O LAB 10 demonstra a construção de uma automação comercial estruturada, com validações, regras de negócio, integração HTTP, tratamento de exceções e respostas personalizadas.

O projeto faz parte de uma sequência prática de estudos em automação de processos e integrações utilizando n8n.

10. Autor

Projeto desenvolvido por Jaime, como parte de sua jornada prática de aprendizado e desenvolvimento de soluções de automação de processos utilizando n8n.
