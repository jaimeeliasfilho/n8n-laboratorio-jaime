LAB 11 — Integração de Sistemas com APIs REST

Visão geral

Este laboratório demonstra a construção de uma automação de integração entre sistemas utilizando n8n, Webhooks e APIs REST.

O workflow recebe uma solicitação de atualização cadastral por meio de um Webhook, prepara os dados recebidos, consulta um cadastro em uma API externa, envia uma atualização simulada e retorna uma resposta estruturada em JSON ao sistema solicitante.

O projeto simula um cenário comum em empresas que precisam integrar plataformas, CRMs e sistemas internos por meio de comunicação HTTP.

Objetivo do projeto

Desenvolver um fluxo capaz de:

- Receber dados cadastrais por meio de uma requisição HTTP POST.
- Preparar e organizar os dados recebidos.
- Consultar um registro em uma API externa utilizando HTTP GET.
- Enviar os novos dados para atualização utilizando HTTP PUT.
- Retornar uma confirmação estruturada ao sistema de origem.

Arquitetura do workflow

Fluxo de execução:

1. Webhook — Receber solicitação: ponto de entrada da automação, recebendo os dados enviados pelo sistema solicitante.
2. Edit Fields — Preparar dados: organiza os campos recebidos, como ID do cliente, nome, e-mail e telefone.
3. HTTP Request GET — Consultar cliente: consulta o registro correspondente na API externa.
4. HTTP Request PUT — Atualizar cliente: envia os dados cadastrais para atualização do registro consultado.
5. Respond to Webhook — Retornar resposta: devolve ao sistema solicitante uma resposta JSON com o resultado da operação.

Tecnologias e recursos utilizados

- n8n: construção e orquestração do workflow.
- Webhook: recebimento de requisições externas.
- HTTP Request: comunicação e integração com APIs REST.
- JSON: estruturação e transferência de dados.
- Métodos HTTP: POST, GET e PUT.
- Expressões do n8n: manipulação e recuperação dinâmica de dados entre nós.
- JSONPlaceholder: API pública utilizada para simulação dos testes.

Testes realizados

Foi executado um teste completo de ponta a ponta, enviando uma solicitação POST com os dados de um cliente.

O workflow realizou a consulta do registro na API, enviou a requisição PUT com os novos dados e retornou uma resposta JSON contendo:

- Indicador de sucesso da operação.
- Mensagem de confirmação.
- Identificador do cliente.
- Nome, e-mail e telefone atualizados na resposta.

Resultado: execução concluída com sucesso e resposta HTTP 200.

Observação técnica importante

A API JSONPlaceholder é um serviço público destinado a testes e aprendizado. Embora aceite requisições PUT e retorne os dados enviados, ela não persiste efetivamente as alterações.

Portanto, este laboratório demonstra o funcionamento da integração e da comunicação entre sistemas, mas não representa uma atualização permanente em um banco de dados real.

Competências desenvolvidas

- Integração entre sistemas utilizando APIs REST.
- Construção e configuração de Webhooks.
- Manipulação de requisições HTTP.
- Utilização dos métodos POST, GET e PUT.
- Tratamento e organização de dados JSON.
- Uso de expressões dinâmicas no n8n.
- Orquestração de fluxos de integração.
- Retorno estruturado de informações entre aplicações.

Aplicação no mercado de trabalho

Esse tipo de automação pode ser aplicado em cenários corporativos como:

- Atualização de cadastros entre CRM e ERP.
- Sincronização de informações entre plataformas.
- Integração de formulários com sistemas internos.
- Atualização de registros por meio de APIs.
- Comunicação automatizada entre aplicações.

Estrutura do repositório

- "lab-11-workflow-sanitizado.json" — arquivo exportado e sanitizado do workflow, pronto para análise e importação no n8n.

---

Projeto desenvolvido para fins de aprendizado e construção de portfólio profissional na área de Automação de Processos e Integração de Sistemas.
