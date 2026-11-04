LAB 03 — Gestão de Leads e CRM

Objetivo

Desenvolver uma automação para pequenas empresas que recebem contatos comerciais por formulário e precisam organizar seus potenciais clientes.

Problema de negócio

O registro manual de contatos pode gerar perda de informações, retrabalho e dificuldade no acompanhamento das oportunidades comerciais.

Solução desenvolvida

Um workflow no n8n que recebe os dados de potenciais clientes, padroniza as informações e registra automaticamente cada novo lead em uma planilha Google Sheets.

Arquitetura do workflow

1. Form Trigger: recebe os dados por formulário.
2. Edit Fields: organiza e padroniza os sete campos recebidos.
3. Google Sheets: adiciona automaticamente uma nova linha ao CRM.

Tecnologias utilizadas

- n8n
- Google Sheets
- Google OAuth 2.0
- JSON
- Expressões do n8n

Dados registrados

- Data de cadastro
- Nome
- E-mail
- Telefone
- Empresa
- Interesse comercial
- Origem do contato
- Observações

Testes realizados

- Envio de formulário com dados fictícios.
- Validação da saída JSON.
- Teste das expressões de mapeamento.
- Integração com Google Sheets.
- Confirmação do registro automático na planilha.

Competências desenvolvidas

- Automação de processos.
- Integração entre aplicações.
- Manipulação de dados JSON.
- Mapeamento de campos.
- Expressões no n8n.
- Integração com Google Sheets.

Segurança

O workflow público não deve conter credenciais, tokens, identificadores privados ou dados pessoais reais. Cada usuário deverá configurar sua própria autenticação Google.

Status

Protótipo funcional validado em ambiente de testes.

Autor

Jaime Elias Filho

Projeto desenvolvido como parte do portfólio de automação com n8n.
