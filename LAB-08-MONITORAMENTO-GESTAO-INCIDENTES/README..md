LAB 08 — Central Inteligente de Monitoramento e Gestão de Incidentes

Sobre o projeto

Este laboratório apresenta uma solução de automação para monitoramento de disponibilidade de serviços e identificação de possíveis incidentes operacionais.

O workflow utiliza o n8n para executar verificações periódicas em uma API, interpretar o resultado das requisições, identificar situações de falha e encaminhar alertas pelo Telegram.

O projeto simula um cenário empresarial no qual a indisponibilidade de serviços externos pode comprometer operações e exige uma resposta rápida da equipe responsável.

Objetivo

Desenvolver um fluxo automatizado capaz de:

- Executar verificações periódicas de disponibilidade.
- Consultar uma API externa por meio de requisição HTTP.
- Identificar respostas de sucesso e situações de falha.
- Classificar o resultado da verificação.
- Padronizar informações sobre incidentes.
- Gerar mensagens de alerta.
- Encaminhar notificações pelo Telegram.

Tecnologias utilizadas

- n8n: orquestração e automação do workflow.
- HTTP Request: integração com API externa.
- GitHub API: serviço utilizado nos testes de disponibilidade.
- IF: avaliação condicional dos resultados.
- Edit Fields / Code: tratamento e organização dos dados.
- Telegram: envio automatizado de notificações.

Arquitetura do workflow

O fluxo foi estruturado em etapas:

1. Schedule Trigger: programação das verificações periódicas, configurada para execução a cada cinco minutos.
2. Consulta à API: requisição HTTP GET ao endpoint de teste.
3. Classificação do status: interpretação do retorno da requisição.
4. Verificação de disponibilidade: identificação de respostas bem-sucedidas ou situações de falha.
5. Tratamento do incidente: organização das informações relacionadas à ocorrência.
6. Padronização dos dados: preparação das informações para comunicação.
7. Construção da mensagem: geração do conteúdo do alerta.
8. Notificação: envio da mensagem pelo Telegram.

Testes realizados

Foram validados cenários de operação e falha, incluindo:

- Resposta de sucesso da API.
- Resposta HTTP de erro 503.
- Identificação de serviço com falha.
- Geração de mensagem contendo serviço, código HTTP, situação e descrição do incidente.
- Envio de alerta pelo Telegram.
- Caminho de execução sem necessidade de notificação quando não há incidente.

Exemplo de alerta

🚨 ALERTA DE INCIDENTE

Serviço: API do GitHub
Status HTTP: 503
Situação: COM FALHA
Mensagem: Serviço apresentou uma resposta HTTP de erro.

Aplicação empresarial

Uma solução com essa estrutura pode ser adaptada para monitoramento de APIs, integrações, serviços de terceiros e sistemas essenciais à operação de uma empresa.

A automação contribui para reduzir a dependência de verificações manuais e acelerar a comunicação de incidentes.

Competências desenvolvidas

- Automação de processos com n8n.
- Integração via API REST.
- Requisições HTTP.
- Tratamento e validação de respostas.
- Lógica condicional.
- Padronização de dados.
- Notificações automatizadas.
- Estruturação de workflows orientados a processos empresariais.

Observação

Projeto desenvolvido em ambiente de laboratório para fins de aprendizado e portfólio. Os testes utilizaram uma API externa e cenários simulados de falha. Não representa uma implantação de monitoramento em ambiente produtivo.

---

Autor: Jaime Elias Filho
Projeto: Laboratório 08 — Automação com n8n
