LAB 15 — Agente Inteligente de Busca e Análise de Vagas com IA

Objetivo

Desenvolver uma automação com n8n capaz de coletar oportunidades profissionais, padronizar informações, analisar a compatibilidade com um perfil profissional utilizando Inteligência Artificial, classificar vagas e enviar notificações pelo Telegram.

Tecnologias utilizadas

- n8n
- APIs REST
- OpenRouter
- Modelos de Inteligência Artificial
- Telegram Bot API
- HTTP Request
- Merge
- Split Out
- Edit Fields
- Switch
- Structured Output Parser

Arquitetura

O workflow foi desenvolvido com duas fontes de vagas:

- Joonow
- Jobicy

Os dados são coletados, separados e padronizados, reunidos em um fluxo único e encaminhados para análise de compatibilidade com IA.

A avaliação considera competências, experiências, requisitos da vaga, lacunas profissionais e aderência ao perfil.

As oportunidades são classificadas em três níveis:

- Alta compatibilidade: 75 a 100 pontos
- Média compatibilidade: 50 a 74 pontos
- Baixa compatibilidade: 0 a 49 pontos

Vagas classificadas como alta ou média compatibilidade são encaminhadas para notificação via Telegram.

Funcionalidades

- Consulta automatizada de oportunidades.
- Integração de múltiplas fontes.
- Padronização de dados.
- Análise de compatibilidade profissional com IA.
- Identificação de pontos fortes e lacunas.
- Classificação de oportunidades.
- Notificação com informações da vaga, análise e links.
- Gatilho para execução manual.
- Configuração de agendamento diário.

Aprendizados técnicos

- Integração com APIs REST utilizando HTTP Request.
- Manipulação e padronização de dados em workflows.
- Organização de fluxos com múltiplas fontes.
- Utilização de Merge no modo Append.
- Integração de modelos de IA no n8n.
- Estruturação de respostas com Structured Output Parser.
- Implementação de regras de classificação.
- Integração com Telegram.
- Controle de consumo e limitações de modelos de IA.
- Configuração de gatilhos manuais e agendados.

Validação

Foram realizados testes que comprovaram:

- Coleta de dados das fontes.
- Padronização e unificação de registros.
- Avaliação de compatibilidade com IA em execução de teste.
- Classificação de vagas.
- Envio de notificações completas ao Telegram.

A integração das fontes e o processamento em lote foram testados separadamente. O processamento conjunto de um lote maior apresentou limitação relacionada à capacidade do modelo utilizado.

Limitação técnica identificada

Durante testes com múltiplas vagas, o modelo gratuito utilizado no OpenRouter retornou resposta vazia ao Structured Output Parser.

A mensagem de erro indicou possível limitação de tokens de saída ou capacidade de geração da resposta estruturada.

O comportamento demonstra que o processamento em lote depende da capacidade, disponibilidade e limites do modelo utilizado.

O fluxo foi mantido com base nas funcionalidades comprovadas, sem consumo adicional de créditos para otimizações.

Agendamento

O workflow possui um Schedule Trigger configurado para execução diária às 9h, com intervalo de um dia.

A execução automática depende da publicação/ativação do workflow e da disponibilidade das integrações e do modelo de IA.

Fonte Jobicy

As vagas obtidas pela Jobicy devem manter a identificação da fonte e os links originais.

Fonte: https://jobicy.com/

Segurança

O arquivo disponibilizado para portfólio deve ser sanitizado, sem credenciais, tokens, IDs privados de chat ou dados pessoais.

Status do projeto

Laboratório concluído para fins de aprendizado e portfólio.

Workflow validado em testes controlados. Não publicado/ativado em produção.

Projeto desenvolvido como prática de automação de processos, integração de APIs e Inteligência Artificial utilizando n8n.
