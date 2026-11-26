LAB 20 — Webhooks e Automação Orientada a Eventos

1. Objetivo do laboratório

Desenvolver uma automação no n8n capaz de receber pedidos de uma loja virtual por meio de Webhook, validar os dados recebidos e retornar respostas HTTP diferentes conforme o resultado da validação.

O laboratório demonstra na prática a comunicação entre sistemas por meio de requisições HTTP, recebimento de dados JSON, validação de informações e tratamento de respostas.

2. Cenário de negócio

Uma loja virtual precisa receber pedidos enviados pelo seu site e verificar se as informações essenciais estão preenchidas antes de encaminhar uma confirmação.

A automação recebe o pedido, verifica os campos obrigatórios e responde ao sistema de origem:

- Pedido válido: confirmação de recebimento com HTTP 200.
- Pedido inválido: rejeição da solicitação com HTTP 400.

3. Tecnologias utilizadas

- n8n — construção e execução do workflow.
- Webhook — recebimento de requisições HTTP POST.
- Hoppscotch — simulação de requisições externas.
- JSON — estrutura de transmissão dos dados.
- HTTP — comunicação e códigos de resposta.

4. Arquitetura do workflow

O fluxo contém quatro nós:

01 — Receber Pedido (Webhook)

Recebe a requisição HTTP POST enviada pelo sistema externo.

Caminho configurado: "lab20-pedidos"

Os dados do pedido são recebidos no corpo da requisição ("body"), em formato JSON.

02 — Validar Dados do Pedido (IF)

Verifica três condições, combinadas com AND:

- "pedido_id": deve estar preenchido.
- "produto": deve estar preenchido.
- "valor_total": deve ser um número maior que zero.

O nó direciona a execução para uma das duas saídas:

- True: todas as condições foram atendidas.
- False: pelo menos uma condição não foi atendida.

03 — Confirmar Pedido Recebido (Respond to Webhook)

Executado quando o pedido passa pela validação.

Retorna uma resposta JSON com HTTP 200:

- "sucesso": true
- "mensagem": Pedido recebido com sucesso!
- "status": recebido
- "origem": n8n

04 — Informar Pedido Inválido (Respond to Webhook)

Executado quando o pedido não atende às condições.

Retorna uma resposta JSON com HTTP 400:

- "sucesso": false
- "mensagem": Pedido rejeitado: dados obrigatórios ausentes ou inválidos.
- "status": rejeitado
- "origem": n8n

5. Representação do fluxo

01 - Receber Pedido
        |
        v
02 - Validar Dados do Pedido
        |
        |--- TRUE ---> 03 - Confirmar Pedido Recebido
        |
        |--- FALSE --> 04 - Informar Pedido Inválido

6. Testes realizados

Os testes foram executados utilizando o Hoppscotch como cliente HTTP externo.

Teste 1 — Pedido válido

Dados enviados:

- Pedido: PED-2026-001
- Produto: Notebook
- Quantidade: 1
- Valor total: 3500,00

Resultado:

- Webhook recebeu os dados.
- IF direcionou a execução pela saída True.
- Hoppscotch recebeu HTTP 200 OK.
- Mensagem de confirmação retornada corretamente.

Status: aprovado.

Teste 2 — Pedido inválido

Dados enviados:

- Pedido: PED-2026-001
- Produto: campo vazio.
- Quantidade: 1
- Valor total: 3500,00

Resultado:

- Webhook recebeu os dados.
- IF direcionou a execução pela saída False.
- Hoppscotch recebeu HTTP 400 Bad Request.
- Mensagem de rejeição retornada corretamente.

Status: aprovado.

Teste adicional — Regra de valor positivo

Após a revisão técnica, a condição de valor foi ajustada de "is not empty" para "is greater than 0".

Um novo pedido válido, com valor total de 3500, foi enviado.

Resultado:

- Saída True.
- HTTP 200 OK.

Status: aprovado.

7. Conhecimentos desenvolvidos

- Criação e configuração de Webhooks.
- Recebimento de requisições HTTP POST.
- Interpretação de estruturas JSON.
- Acesso a campos por expressões n8n.
- Validação de dados com o nó IF.
- Tratamento de diferentes caminhos de execução.
- Configuração de respostas HTTP.
- Utilização dos códigos 200 OK e 400 Bad Request.
- Testes de integração utilizando Hoppscotch.

8. Aplicação empresarial

A solução pode ser utilizada como primeira etapa de um processo de recebimento de pedidos em uma loja virtual.

Uma evolução possível seria adicionar:

- Registro automático dos pedidos no Google Sheets ou PostgreSQL.
- Integração com CRM.
- Notificação da equipe comercial.
- Envio de confirmação ao cliente por e-mail ou WhatsApp.
- Consulta de estoque e disponibilidade.
- Integração com plataformas de pagamento.

Essas funcionalidades representam possibilidades futuras e não fazem parte do workflow implementado neste laboratório.

9. Segurança e limitações

- O laboratório utiliza dados fictícios.
- O Hoppscotch foi utilizado para simular o sistema externo.
- A autenticação do Webhook não foi configurada neste exercício.
- O fluxo foi desenvolvido e testado em modo de execução, sem publicação ou ativação em produção.
- A confirmação HTTP 200 indica recebimento e validação dos dados, não aprovação de pagamento ou confirmação definitiva da venda.
- Em um ambiente real, devem ser considerados autenticação, proteção de dados, prevenção de pedidos duplicados e tratamento de falhas.

10. Resultado final

Laboratório concluído com sucesso, demonstrando uma integração orientada a eventos capaz de receber pedidos externos, validar informações e retornar respostas HTTP específicas para cenários de sucesso e rejeição.

Status: funcionalidade validada em testes.

Trilha 2 — LAB 20 de 38.

Autor: Jaime Filho
