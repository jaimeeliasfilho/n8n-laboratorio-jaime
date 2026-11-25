LAB 16 — Gestão Centralizada de Erros e Falhas em Workflows com n8n

📌 Sobre o projeto

Este laboratório demonstra a implementação de um mecanismo centralizado de tratamento de erros no n8n, permitindo capturar falhas ocorridas em workflows associados, padronizar as informações do erro e enviar notificações automáticas pelo Telegram.

A solução utiliza um workflow dedicado ao tratamento de falhas, evitando que cada automação precise implementar individualmente uma estrutura de notificação de erros.

🎯 Objetivo

Desenvolver uma estrutura reutilizável de monitoramento de falhas em automações, utilizando o Error Trigger do n8n para capturar erros, organizar informações relevantes e notificar o responsável pela operação.

🏗️ Arquitetura da solução

O workflow é composto por três nós principais:

1. Error Trigger — captura erros provenientes de workflows configurados para utilizar este workflow como mecanismo de tratamento de falhas.
2. Edit Fields (Set) — padroniza os dados recebidos, extraindo o nome do workflow, a mensagem do erro e o último nó executado.
3. Telegram — Send Message — envia uma notificação estruturada com as informações da falha.

Fluxo

Error Trigger → Padronização dos dados do erro → Notificação no Telegram

⚙️ Funcionamento

Quando um workflow associado apresenta uma falha durante sua execução:

- O Error Trigger recebe os dados da execução que apresentou erro.
- O nó de padronização extrai as informações relevantes.
- Os dados são organizados em campos específicos.
- Uma mensagem de alerta é enviada automaticamente pelo Telegram.

Informações notificadas

- Nome do workflow que apresentou a falha.
- Mensagem do erro.
- Último nó executado.

📩 Exemplo de notificação

🚨 ALERTA DE FALHA NA AUTOMAÇÃO

Workflow: TESTE - Simulação de falha para o LAB 16

Erro: Falha controlada para validar o Lab 16

Último nó executado: 02 - Provocar Erro Controlado

A notificação permite identificar rapidamente qual automação apresentou falha e qual etapa estava sendo executada, direcionando o responsável para a investigação.

🧪 Testes realizados

Para validar o funcionamento do mecanismo, foi criado um workflow auxiliar de teste contendo:

- Webhook Trigger.
- Nó Code com erro controlado.

O workflow auxiliar foi associado ao workflow central de tratamento de erros.

Após a execução do teste, foi confirmada a captura da falha e o recebimento da notificação no Telegram com:

- Nome correto do workflow.
- Mensagem de erro.
- Identificação do último nó executado.

Resultado: teste funcional de ponta a ponta concluído com sucesso.

Após a validação, os workflows foram despublicados, mantendo o ambiente de laboratório inativo.

🛠️ Tecnologias e recursos utilizados

- n8n
- Error Trigger
- Edit Fields (Set)
- Telegram
- Webhook
- Code Node (simulação de erro controlado)
- Expressões do n8n
- Tratamento centralizado de erros
- Automação de notificações

💼 Aplicação prática em ambientes empresariais

Este mecanismo pode ser aplicado em automações empresariais que executam processos como:

- Integrações entre sistemas.
- Processamento de formulários.
- Fluxos de atendimento.
- Processamento de documentos.
- Rotinas administrativas.
- Integrações com APIs.
- Processos automatizados de vendas e operações.

A centralização das notificações facilita a identificação de falhas, reduz o tempo de percepção de incidentes e contribui para a manutenção e confiabilidade dos processos automatizados.

📚 Competências desenvolvidas

- Implementação de workflows de tratamento de erros.
- Utilização do Error Trigger.
- Configuração de Error Workflow.
- Captura e organização de dados de execução.
- Manipulação de expressões no n8n.
- Integração com Telegram para notificações.
- Simulação e validação controlada de falhas.
- Estruturação de mecanismos reutilizáveis de monitoramento operacional.

⚠️ Limitações identificadas

Durante o teste, o campo referente ao link direto da execução não retornou valor. Esse recurso não foi considerado validado e foi retirado da versão final do laboratório.

A solução foi mantida focada na captura e notificação das informações essenciais para identificação da falha.

🚀 Resultado

Laboratório concluído com validação funcional de ponta a ponta, demonstrando a implementação de um mecanismo reutilizável de tratamento centralizado de erros no n8n e integração com Telegram para alertas operacionais.

---

Projeto desenvolvido para fins de aprendizado, experimentação e portfólio profissional em automação de processos e integração de sistemas.
