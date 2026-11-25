LAB 18 — Planejamento Inteligente de Estoque e Reposição de Produtos

📌 Sobre o projeto

Automação desenvolvida no n8n para analisar dados de estoque e vendas, identificar produtos com risco de falta e recomendar quantidades de reposição.

O projeto utiliza dados do Google Sheets, regras de negócio implementadas em JavaScript e notificações via Telegram, permitindo que o responsável pelo estoque receba um relatório consolidado para apoiar decisões de compra.

O objetivo é demonstrar como a automação de processos pode auxiliar pequenas empresas na gestão de estoque, reduzir análises manuais e melhorar a tomada de decisão.

---

🎯 Objetivos

- Automatizar a análise de estoque e vendas.
- Calcular o consumo médio diário dos produtos.
- Identificar produtos que atingiram o ponto de reposição.
- Estimar quantidades recomendadas para reposição.
- Consolidar os resultados em um relatório.
- Enviar notificações automáticas ao responsável.
- Preservar a aprovação humana antes de qualquer compra.

---

🏢 Cenário de negócio

Uma loja de equipamentos de informática precisa acompanhar seus produtos para evitar falta de mercadorias e compras desnecessárias.

A análise manual de planilhas pode consumir tempo, dificultar a identificação de produtos críticos e atrasar decisões de reposição.

A solução proposta automatiza essa análise e envia um resumo diário com os produtos que precisam de atenção.

Fluxo operacional proposto

1. Os dados de produtos e vendas são atualizados no Google Sheets.
2. O n8n executa a rotina programada diariamente às 8h.
3. Os dados são consultados e unificados.
4. As regras de negócio são aplicadas.
5. Um relatório é gerado automaticamente.
6. O responsável recebe a notificação pelo Telegram.
7. A decisão de compra permanece sob responsabilidade humana.

---

🛠️ Tecnologias utilizadas

- n8n — Orquestração e automação de workflows.
- Google Sheets — Fonte de dados de produtos e vendas.
- JavaScript — Implementação das regras de negócio e cálculos.
- Telegram — Canal de notificação e entrega do relatório.
- Google Colab / Python — Desenvolvimento e validação inicial dos cálculos.
- Schedule Trigger — Agendamento de execução diária.

---

⚙️ Arquitetura do workflow

Nós utilizados

Nó| Função
00 — Iniciar Execução Manual| Permite executar testes manualmente
00 — Agendamento Diário — 08h| Configuração de execução diária
01 — Ler Produtos| Consulta os dados de cadastro e estoque
02 — Ler Vendas| Consulta o histórico de vendas
03 — Unificar Dados| Combina as duas fontes de dados
04 — Calcular Estoque e Reposição| Aplica regras de negócio e cálculos
05 — Preparar Relatório| Consolida os resultados em uma mensagem
06 — Enviar Relatório ao Responsável| Envia o relatório pelo Telegram

Representação simplificada

Manual Trigger ─────┐
                    ├── Ler Produtos ────┐
Schedule Trigger ───┤                    │
                    ├── Ler Vendas ──────┤
                    │                    ▼
                    │               Merge
                    │                 │
                    │                 ▼
                    │         Calcular Estoque
                    │                 │
                    │                 ▼
                    │       Preparar Relatório
                    │                 │
                    │                 ▼
                    └────────────── Telegram

Os gatilhos manual e agendado iniciam as duas consultas de dados, permitindo testes manuais e uma futura rotina operacional automatizada.

---

📊 Regras de negócio

O workflow utiliza cálculos determinísticos implementados em JavaScript.

1. Consumo médio diário

O consumo diário é estimado a partir da quantidade vendida no período histórico de 30 dias.

Fórmula:

Consumo médio diário =
Quantidade vendida nos últimos 30 dias ÷ 30

2. Ponto de reposição

O ponto de reposição considera o prazo de entrega do fornecedor e o estoque de segurança.

Fórmula:

Ponto de reposição =
Consumo diário × (Prazo de reposição + Dias de segurança)

3. Identificação da necessidade de reposição

Quando o estoque atual é igual ou inferior ao ponto de reposição, o produto é classificado como necessitando de reposição.

Se estoque atual <= ponto de reposição:
    Reposição recomendada
Caso contrário:
    Estoque normal

4. Quantidade recomendada

O modelo utiliza uma cobertura de estoque estimada de 30 dias.

Estoque desejado =
Consumo diário × 30 dias

Quantidade recomendada =
Estoque desejado − Estoque atual

O resultado é arredondado para cima e não pode ser negativo.

A quantidade recomendada é calculada somente quando o produto necessita de reposição.

---

🧪 Dados utilizados no teste

Base fictícia de uma loja de informática, contendo:

- 5 produtos cadastrados.
- 15 registros de vendas.
- Histórico considerado de 30 dias.
- Prazo de reposição variável por produto.
- Estoque de segurança de 3 dias.

Resultados obtidos

Produto| Estoque atual| Consumo diário| Ponto de reposição| Reposição| Quantidade sugerida
Teclado USB| 12| 1,00| 8,00| Não| 0
Mouse sem fio| 8| 1,50| 15,00| Sim| 37
Monitor 24 polegadas| 20| 0,40| 5,20| Não| 0
Headset USB| 5| 1,00| 7,00| Sim| 25
Webcam HD| 18| 0,30| 2,70| Não| 0

Resumo da execução

- Produtos analisados: 5
- Produtos com estoque normal: 3
- Produtos com reposição recomendada: 2
- Quantidade total recomendada: 62 unidades

---

📱 Exemplo de notificação enviada

📦 RELATÓRIO DE ESTOQUE

Produtos analisados: 5
Estoque normal: 3
Precisam de reposição: 2

⚠️ REPOSIÇÃO RECOMENDADA

• Mouse sem fio
  Estoque atual: 8
  Quantidade sugerida: 37 unidades

• Headset USB
  Estoque atual: 5
  Quantidade sugerida: 25 unidades

Total recomendado: 62 unidades

Atenção: recomendação sujeita à aprovação humana.
Nenhuma compra foi realizada.

---

✅ Validação do laboratório

O workflow foi executado manualmente e validado de ponta a ponta.

Testes realizados

- [x] Leitura dos produtos no Google Sheets.
- [x] Leitura das vendas no Google Sheets.
- [x] Unificação dos dados no Merge.
- [x] Cálculos implementados em JavaScript.
- [x] Identificação dos produtos que precisam de reposição.
- [x] Cálculo das quantidades recomendadas.
- [x] Consolidação do relatório.
- [x] Envio efetivo da mensagem pelo Telegram.
- [x] Conferência dos resultados com os cálculos previamente validados no Google Colab.
- [x] Configuração do Schedule Trigger para execução diária às 8h.
- [x] Configuração do fuso horário "America/Sao_Paulo".
- [x] Conexões dos dois gatilhos às duas fontes de dados.

Resultado: execução manual ponta a ponta aprovada.

O agendamento foi configurado, mas não ativado. A execução automática em produção não foi testada.

---

🔐 Segurança

O workflow disponibilizado neste repositório possui sanitização prévia de informações sensíveis.

As credenciais reais dos serviços devem ser configuradas individualmente no ambiente n8n de quem importar o projeto.

Não utilizar credenciais pessoais, tokens ou identificadores privados em repositórios públicos.

---

⚠️ Limitações do protótipo

- A base de dados utiliza informações fictícias.
- O histórico de vendas considera um período fixo de 30 dias.
- O cálculo não realiza filtragem dinâmica de datas.
- A atualização dos dados depende da alimentação das planilhas.
- A integração com ERP ou sistema de vendas não foi implementada.
- O workflow não executa pedidos de compra.
- O agendamento está configurado, mas não ativado.
- A aprovação de reposição é realizada externamente pelo responsável.

---

🚀 Possibilidades de evolução comercial

Este protótipo pode ser adaptado para pequenas empresas que necessitam de maior controle de estoque.

Possíveis evoluções:

- Integração direta com ERP, PDV ou sistema de vendas via API.
- Atualização automática dos dados de estoque.
- Histórico dinâmico de vendas por período.
- Diferentes regras de reposição por categoria de produto.
- Inclusão de fornecedores e preços de compra.
- Estimativa financeira do custo de reposição.
- Alertas de produtos críticos.
- Dashboard gerencial.
- Aprovação de pedidos por WhatsApp, Telegram ou painel.
- Registro histórico das recomendações e aprovações.

A solução pode ser adaptada de acordo com a realidade operacional e as regras de cada empresa.

---

💡 Aprendizados desenvolvidos

Durante este laboratório, foram praticados:- Construção de workflows com múltiplas entradas.
- Integração de diferentes fontes de dados.
- Uso do Merge para consolidação.
- Manipulação de dados com JavaScript.
- Aplicação de regras de negócio.
- Cálculos de indicadores operacionais.
- Tratamento e consolidação de resultados.
- Integração com Telegram.
- Configuração de agendamento.
- Validação ponta a ponta.
- Estruturação de uma automação orientada a problemas empresariais.

---

👨‍💻 Autor

Jaime Filho

Projeto desenvolvido como parte de estudos práticos em automação de processos, n8n, integrações e soluções com inteligência aplicada a negócios.

Foco profissional: Automação de Processos | n8n | Integrações | JavaScript | Automação com IA | Soluções Digitais

---

«Projeto / protótipo de solução empresarial. Os dados são fictícios e qualquer implantação comercial deverá passar por validação das regras de negócio, segurança, integrações e condições operacionais do cliente.»
