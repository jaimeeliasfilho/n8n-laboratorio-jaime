LAB 05 — Agente de IA para Triagem de Atendimento

1. Sobre o projeto

Este projeto consiste no desenvolvimento de um agente de Inteligência Artificial utilizando n8n e Google Gemini para automatizar a triagem inicial de solicitações de atendimento.

O sistema recebe mensagens pelo chat, identifica a intenção do cliente, classifica a solicitação em uma das sete categorias disponíveis e retorna uma resposta automática correspondente.

2. Objetivo

Demonstrar como a combinação de automação de processos e Inteligência Artificial pode otimizar o atendimento ao cliente, reduzir tarefas repetitivas e organizar solicitações por tipo de demanda.

3. Tecnologias utilizadas

- n8n: criação e execução dos workflows de automação.
- Google Gemini: modelo de IA utilizado na classificação das mensagens.
- Chat Trigger: recebimento das mensagens dos usuários.
- Edit Fields: preparação dos dados e construção das respostas automáticas.
- Google Gemini API: integração com o modelo de linguagem.

4. Arquitetura do workflow

O fluxo é composto pelas seguintes etapas:

1. Recebimento da mensagem pelo Chat Trigger.
2. Preparação e registro dos dados recebidos.
3. Classificação da intenção utilizando IA.
4. Encaminhamento para uma das sete ramificações.
5. Preparação da resposta correspondente.
6. Retorno automático da mensagem ao chat.

5. Categorias de classificação

O agente identifica sete tipos de solicitações:

Categoria| Finalidade
ORÇAMENTO| Consultas de preços e valores
PEDIDO| Consultas e solicitações relacionadas a pedidos
PRAZO| Informações sobre produção e entrega
PAGAMENTO| Dúvidas sobre condições de pagamento
RECLAMAÇÃO| Identificação de insatisfação e problemas
ATENDIMENTO HUMANO| Solicitação de atendimento por uma pessoa
OUTROS| Assuntos não identificados nas demais categorias

6. Respostas automatizadas

Cada categoria possui uma ramificação independente com uma resposta específica.

As mensagens foram elaboradas para orientar o cliente sem inventar preços, prazos, condições comerciais ou informações sobre pedidos.

7. Testes realizados

Foram realizados testes individuais com mensagens simuladas para validar as sete categorias e suas respectivas respostas.

Resultado: 7 de 7 categorias classificadas corretamente e 7 de 7 respostas automáticas funcionando nos testes realizados.

8. Boas práticas

- Separação das ramificações por categoria.
- Padronização dos nomes dos nós.
- Preservação dos dados recebidos durante o workflow.
- Respostas sem informações comerciais não confirmadas.
- Organização do workflow para facilitar manutenção e evolução.
- Exportação do workflow em formato JSON.

9. Possibilidades de evolução

- Integração com WhatsApp.
- Integração com Telegram.
- Registro das solicitações em Google Sheets.
- Encaminhamento efetivo para atendentes humanos.
- Histórico de atendimento.
- Painel de indicadores e acompanhamento das solicitações.

10. Status do projeto

Concluído: estrutura inicial, classificação com IA e sete respostas automáticas validadas em ambiente de testes.

Próximas etapas: documentação, publicação no GitHub e evolução das integrações.

---

Projeto desenvolvido por Jaime Elias Filho.

Área de estudo: Automação de Processos, Inteligência Artificial e n8n.
