LAB 22 — Agente de IA para Atendimento Comercial, Registro de Leads e Notificações Automáticas

Tecnologias: n8n | OpenRouter | Agente de IA | Google Sheets | Gmail | Chat Trigger

1. Visão geral

Este projeto demonstra a construção de um agente de Inteligência Artificial para automatizar etapas de um processo de atendimento comercial.

Desenvolvido no n8n, o agente recebe mensagens de potenciais clientes, interpreta suas necessidades, conduz a conversa para coletar informações relevantes e utiliza ferramentas integradas para registrar oportunidades comerciais e notificar a equipe responsável.

A solução automatiza três etapas importantes do processo comercial:

- Atendimento inteligente: conversa com o potencial cliente e solicita informações complementares quando necessário.
- Registro de oportunidades: os dados coletados são armazenados automaticamente no Google Sheets.
- Notificação e retorno: a equipe comercial recebe um e-mail pelo Gmail e o cliente recebe uma mensagem de confirmação no próprio chat.

Importante: o e-mail é uma notificação interna para a equipe comercial, não uma mensagem enviada ao cliente. O cliente recebe seu retorno diretamente pela conversa com o agente.

2. Objetivo do projeto

Desenvolver um agente capaz de:

- Receber mensagens de potenciais clientes por meio de uma interface de chat.
- Interpretar solicitações e identificar oportunidades comerciais.
- Conduzir o atendimento de maneira contextualizada.
- Identificar informações ausentes e solicitar os dados necessários.
- Registrar os dados coletados em uma planilha do Google Sheets.
- Enviar uma notificação automática por e-mail à equipe comercial.
- Retornar ao cliente uma confirmação sobre o recebimento das informações e a notificação da equipe.
- Respeitar a sequência de execução e informar corretamente situações de sucesso ou falha.

3. Cenário de negócio

Imagine uma empresa que recebe solicitações de orçamento e informações sobre seus serviços por meio de um canal de atendimento.

Sem automação, um profissional precisa interpretar cada solicitação, coletar os dados do interessado, cadastrar manualmente a oportunidade, avisar a equipe responsável e dar um retorno ao potencial cliente.

Com esta solução, o agente de IA assume parte desse processo.

Ele conversa com o potencial cliente, identifica sua necessidade, coleta as informações necessárias, registra o lead em uma planilha, encaminha uma notificação interna à equipe comercial e retorna ao cliente com uma confirmação no próprio chat.

Dessa forma, a equipe recebe as oportunidades organizadas e o potencial cliente não fica sem resposta após concluir o primeiro contato.

4. Arquitetura da solução

O workflow possui cinco nós principais:

Nó| Função
01 - Receber mensagem do cliente| Inicia o atendimento por meio do Chat Trigger.
02 - Agente de Atendimento Comercial| Interpreta mensagens, conduz a conversa e decide quando utilizar as ferramentas.
OpenAI Chat Model| Conecta o agente ao modelo de linguagem por meio da API compatível do OpenRouter.
03 - Registro de Lead| Adiciona os dados do potencial cliente ao Google Sheets.
04 - Envio de e-mail para Equipe Comercial| Envia uma notificação interna pelo Gmail após o registro bem-sucedido.

Fluxo de funcionamento

1. O potencial cliente envia uma mensagem pelo chat.
2. O agente de IA interpreta a solicitação e identifica a necessidade comercial.
3. Caso faltem informações, solicita os dados complementares ao cliente e mantém a conversa.
4. Quando possui informações suficientes, aciona a ferramenta Google Sheets.
5. Os dados do potencial cliente são registrados na planilha comercial.
6. Após a confirmação do registro, o agente aciona a ferramenta Gmail.
7. A equipe comercial recebe um e-mail com os dados e um resumo da nova oportunidade.
8. O agente retorna ao cliente pelo chat, informando que os dados foram recebidos, registrados e que a equipe comercial foi notificada.

Regra de negócio fundamental: primeiro o lead é registrado no Google Sheets; somente depois da confirmação dessa operação é enviada a notificação por e-mail à equipe comercial. O agente também deve comunicar ao cliente o resultado das operações, sem confirmar ações que tenham falhado.

5. Integrações utilizadas

n8n

Plataforma responsável por orquestrar o workflow, conectar os serviços e executar as operações.

OpenRouter

Utilizado como provedor de acesso ao modelo de linguagem, com o modelo "openrouter/free" e endpoint compatível com a API da OpenAI.

Google Sheets — Registro de leads

Utilizado como base de organização das oportunidades comerciais.

Cada novo lead é acrescentado em uma nova linha, preservando os registros anteriores.

A planilha possui os seguintes campos:

- ID_LEAD
- DATA_RECEBIMENTO
- NOME_CLIENTE
- EMPRESA
- E-MAIL
- TELEFONE
- SEGMENTO
- NECESSIDADE
- PRAZO
- STATUS
- OBSERVACOES

Gmail — Notificação interna da equipe comercial

O Gmail é utilizado para encaminhar um e-mail interno ao endereço configurado da equipe comercial.

A notificação apresenta as informações disponíveis sobre o novo lead, incluindo:

- Nome do potencial cliente.
- Empresa, quando informada.
- E-mail de contato.
- Telefone ou WhatsApp, quando informado.
- Segmento de atuação.
- Necessidade apresentada.
- Prazo informado.
- Resumo da oportunidade comercial.

O destinatário dessa mensagem é a equipe comercial da empresa, e não o potencial cliente.

O objetivo é alertar os responsáveis para que possam acompanhar a oportunidade e dar continuidade ao relacionamento comercial.

Chat Trigger — Retorno ao cliente

O atendimento é realizado por meio do chat integrado ao n8n.

O agente utiliza a própria conversa para:

- Solicitar informações que estejam faltando.
- Esclarecer dúvidas durante o primeiro contato.
- Informar quando os dados foram registrados.
- Confirmar que a equipe comercial foi notificada, após a execução bem-sucedida do Gmail.

Assim, o processo não termina apenas com o registro interno: o cliente também recebe um retorno sobre o andamento da solicitação.

6. Regras e cuidados implementados

O agente foi orientado para:

- Não inventar informações sobre clientes.
- Solicitar dados que estejam faltando.
- Não registrar oportunidades sem informações suficientes.
- Não confirmar um cadastro antes da execução bem-sucedida da ferramenta.
- Não enviar notificações quando o registro na planilha falhar.
- Diferenciar falhas no registro de falhas no envio do e-mail.
- Utilizar somente informações fornecidas pelo cliente.
- Informar corretamente o resultado das operações realizadas.
- Não afirmar que a equipe foi notificada se o Gmail não confirmar o envio.

Tratamento de falhas

- Se faltarem informações, o agente continua a conversa e solicita os dados necessários.
- Se o registro no Google Sheets falhar, o agente não deve enviar o e-mail nem confirmar o cadastro.
- Se o registro for concluído, mas o Gmail falhar, o agente deve informar que o lead foi registrado, porém não foi possível notificar a equipe.
- A confirmação ao cliente deve refletir o resultado real das operações.

7. Validação prática

O workflow original foi submetido a testes de interação e a uma validação de ponta a ponta.

Cenário 1 — Informações insuficientes

No início do desenvolvimento, foi testada uma situação em que o potencial cliente ainda não havia fornecido informações suficientes para o registro.

O agente identificou a ausência de dados necessários e solicitou informações complementares, mantendo o atendimento em andamento.

Resultado: o agente demonstrou capacidade de conduzir a coleta de informações sem tentar registrar prematuramente uma oportunidade incompleta.

Cenário 2 — Registro e notificação completos

Uma potencial cliente demonstrou interesse em uma solução de automação para atendimento comercial e solicitações de orçamento.

O agente:

1. Interpretou a necessidade apresentada.
2. Coletou os dados comerciais.
3. Registrou o lead no Google Sheets.
4. Enviou uma notificação interna pelo Gmail.
5. Retornou ao cliente pelo chat, informando que o registro havia sido realizado e que a equipe comercial havia sido notificada.

Resultado: o registro na planilha, o envio do e-mail à equipe comercial e o retorno ao cliente foram concluídos com sucesso no teste realizado.

8. Segurança e privacidade

Para disponibilização pública no GitHub, o arquivo JSON foi preparado com sanitização de informações sensíveis.

Foram removidos ou substituídos:

- Endereços de e-mail pessoais.
- Identificadores reais de planilhas.
- IDs de credenciais e instância.
- Referências privadas de autenticação e infraestrutura.
- Outros dados que poderiam expor contas ou ambientes utilizados nos testes.

As credenciais devem ser configuradas novamente no ambiente de destino.

Importante: o endereço "equipe-comercial@example.com" é apenas um destinatário demonstrativo. Deve ser substituído pelo endereço real da equipe comercial antes da utilização operacional.

9. Configuração para reprodução

Após importar o JSON no n8n:

1. Configure a credencial do modelo de linguagem utilizando OpenRouter e o endpoint compatível.
2. Conecte uma conta Google Sheets com acesso à planilha.
3. Confira os nomes e a ordem das 11 colunas da aba "Leads".
4. Conecte uma conta Gmail válida.
5. Configure o endereço de e-mail da equipe comercial como destinatário.
6. Revise visualmente os nós, expressões e conexões no editor.

A versão disponibilizada é destinada à demonstração e ao estudo. A ativação operacional exige configuração e validação no ambiente de destino.

10. Competências demonstradas

- Construção de agentes de IA no n8n.
- Engenharia de prompts e definição de instruções de sistema.
- Integração de modelos de linguagem via API.
- Utilização de ferramentas por agentes de IA (Tool Calling).
- Integração com Google Sheets e Gmail.
- Automação de processos comerciais.
- Atendimento conversacional com IA.
- Coleta e organização automatizada de leads.
- Notificações internas de novas oportunidades.
- Retorno automatizado ao cliente.
- Definição de regras de negócio e sequência de execução.
- Configuração de credenciais OAuth2.
- Sanitização de workflows e boas práticas de segurança.

11. Conclusão

Este laboratório representa a evolução de uma automação convencional para uma solução baseada em agente de IA capaz de interpretar solicitações, decidir quando utilizar ferramentas e executar tarefas integradas.

A solução conecta o primeiro contato do potencial cliente ao processo interno da empresa: coleta informações, registra oportunidades, notifica a equipe comercial e retorna ao cliente com uma confirmação.

O resultado é um fluxo que reduz atividades manuais, organiza informações comerciais, agiliza a comunicação interna e proporciona uma experiência de atendimento mais completa desde o primeiro contato.

Projeto desenvolvido para fins de demonstração técnica e composição de portfólio profissional.

Autor: Jaime Filho
