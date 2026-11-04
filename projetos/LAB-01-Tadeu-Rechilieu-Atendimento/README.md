,LAB-01 — Tadeu Rechilieu

Automação de Pedidos e Atendimento com n8n

📌 Sobre o projeto

Projeto prático de automação desenvolvido com n8n, com o objetivo de organizar e padronizar o recebimento de solicitações de clientes de um pequeno negócio.

A solução utiliza um formulário para receber informações e direcionar automaticamente as solicitações de acordo com o assunto, facilitando a organização do atendimento.

🎯 Objetivo

- Reduzir tarefas manuais e repetitivas.
- Padronizar a entrada de solicitações.
- Organizar pedidos de orçamento, consultas de prazo e informações de pagamento.
- Demonstrar a aplicação de automação em processos reais de pequenos negócios.

⚙️ Arquitetura e funcionamento

O workflow segue as seguintes etapas:

1. Form Trigger: recebe os dados enviados pelo cliente por meio de um formulário.
2. Edit Fields: trata, organiza e normaliza os campos recebidos.
3. Switch: identifica o tipo de solicitação e direciona o fluxo.
4. Rotas de atendimento: organiza as solicitações em três categorias:
   - Orçamento
   - Prazo
   - Pagamento
5. Tratamento de dados: prepara as informações para as próximas etapas da automação.

🛠️ Tecnologias e recursos utilizados

- n8n — Plataforma de automação de workflows.
- Form Trigger — Captura de dados por formulário.
- Edit Fields — Tratamento e organização de informações.
- Switch — Roteamento condicional.
- JavaScript Expressions — Normalização e manipulação de dados.
- JSON — Estruturação e exportação do workflow.

💡 Competências desenvolvidas

- Construção e organização de workflows.
- Integração de etapas de automação.
- Recebimento e tratamento de dados.
- Normalização de textos e campos.
- Implementação de regras condicionais.
- Identificação e direcionamento de solicitações.
- Documentação e versionamento de projetos.

📈 Resultado

Desenvolvimento de um workflow com 15 nós e conexões estruturadas, capaz de receber solicitações, tratar os dados e direcionar cada atendimento conforme sua categoria.

O projeto demonstra, na prática, como a automação de processos pode contribuir para a organização operacional e a eficiência do atendimento em pequenos negócios.

📂 Estrutura do projeto

- "workflow-publico-final.json" — Arquivo do workflow sanitizado para consulta e importação.
- "README.md" — Documentação do projeto.

🔐 Segurança

O arquivo disponibilizado foi preparado para publicação, com remoção de credenciais e identificadores internos. As credenciais necessárias devem ser configuradas novamente pelo usuário após a importação.

---

Projeto desenvolvido como laboratório prático de aprendizagem em automação com n8n.
