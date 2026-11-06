LAB 04 — Controle de Estoque e Reposição

Projeto de automação desenvolvido com n8n, Google Sheets e Telegram.

"n8n" (https://img.shields.io/badge/n8n-Automation-orange)
"Google Sheets" (https://img.shields.io/badge/Google%20Sheets-Integration-green)
"Telegram" (https://img.shields.io/badge/Telegram-Notifications-blue)
"Status" (https://img.shields.io/badge/Projeto-Laboratório-informational)

Sobre o projeto

Este laboratório apresenta uma solução de automação para controle de estoque e acompanhamento de movimentações, utilizando o n8n como plataforma de integração e automação de processos.

A proposta é organizar o registro de movimentações, atualizar os saldos e sinalizar situações que exigem atenção, como a necessidade de reposição de produtos.

Objetivo

Desenvolver um fluxo automatizado capaz de:

- Receber informações de movimentação de estoque.
- Processar os dados recebidos.
- Verificar as condições do estoque.
- Atualizar os registros no Google Sheets.
- Identificar situações que exigem reposição.
- Encaminhar notificações pelo Telegram quando aplicável.

Tecnologias utilizadas

Tecnologia| Aplicação
n8n| Orquestração do workflow
Google Sheets| Registro e atualização dos dados
Telegram| Envio de notificações
Expressões n8n| Tratamento e processamento de informações

Funcionamento da automação

O fluxo foi estruturado para processar movimentações de estoque e direcionar os dados conforme as condições identificadas.

Etapas principais:

1. Recebimento dos dados da movimentação.
2. Processamento das informações.
3. Verificação das condições do estoque.
4. Direcionamento dos caminhos de execução.
5. Atualização do saldo.
6. Registro da movimentação no Google Sheets.
7. Notificação pelo Telegram no fluxo de alerta de reposição.

Regras de negócio

- O saldo do estoque deve ser atualizado conforme a movimentação registrada.
- As condições de estoque são verificadas durante a execução.
- Situações que exigem reposição seguem um caminho específico de alerta.
- As movimentações são registradas para permitir acompanhamento e consulta.

Integrações

Google Sheets: utilizado como base para armazenamento e atualização das informações de estoque.

Telegram: utilizado como canal de comunicação para notificações relacionadas à reposição.

Estrutura do projeto

LAB-04-controle-de-estoque/
├── README.md
└── LAB-04-CONTROLE-ESTOQUE-PORTFOLIO-SANITIZADO.json

Segurança

O arquivo JSON disponibilizado neste repositório foi preparado para portfólio, com identificadores e referências de credenciais substituídos por valores sanitizados.

Para executar o workflow em outro ambiente, é necessário configurar novamente as credenciais e os identificadores das integrações.

Não compartilhe credenciais, tokens ou dados pessoais em arquivos públicos.

Competências desenvolvidas

- Automação de processos com n8n.
- Integração entre diferentes serviços.
- Manipulação e atualização de dados.
- Construção de regras condicionais.
- Organização de fluxos de trabalho.
- Notificações automatizadas.
- Estruturação de projetos para portfólio.

Status do projeto

Laboratório desenvolvido e documentado. A validação funcional completa deve ser realizada no ambiente n8n com as credenciais e os recursos devidamente configurados.

---

Desenvolvido por Jaime Elias Filho

Projeto de estudos e desenvolvimento de soluções de automação.
