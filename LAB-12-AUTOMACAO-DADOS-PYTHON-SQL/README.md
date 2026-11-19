LAB 12 — Automação de Dados com Python e SQL

Objetivo do projeto

Desenvolver uma solução prática de tratamento, organização, consulta e análise de dados empresariais utilizando Python, Pandas e SQLite.

O laboratório simula uma rotina de uma empresa que precisa identificar inconsistências em cadastros de clientes, relacionar informações comerciais e gerar relatórios para apoiar a tomada de decisão.

Tecnologias utilizadas

- Python
- Pandas
- SQLite
- SQL
- Google Colab
- Excel

Etapas desenvolvidas

1. Preparação e diagnóstico dos dados

- Criação de uma base fictícia de clientes.
- Identificação de registros duplicados.
- Verificação de campos vazios.
- Diagnóstico da qualidade dos dados.

2. Tratamento e validação

- Criação de uma cópia da base original.
- Remoção de registros com e-mail duplicado, conforme a regra definida no exercício.
- Identificação de cadastros com informações pendentes.
- Classificação dos registros por situação cadastral.

3. Armazenamento em banco de dados

- Criação de um banco SQLite.
- Armazenamento dos dados tratados na tabela "clientes".
- Criação da tabela "pedidos".

4. Consultas e análise com SQL

Aplicação dos seguintes recursos:

- "SELECT" para consulta de registros.
- "WHERE" para filtragem.
- "COUNT" para contagem.
- "GROUP BY" para agrupamento.
- "INNER JOIN" para relacionamento entre tabelas.
- "SUM" para cálculo de valores.
- "AVG" para cálculo de médias.
- "ORDER BY" para ordenação dos resultados.

5. Geração de relatório

Integração entre SQL e Pandas para consolidar os dados comerciais e exportar os resultados para Excel.

Arquivo gerado: "relatorio_vendas_lab12.xlsx".

Resultados obtidos

- 6 registros originais de clientes analisados.
- 5 registros mantidos após o tratamento.
- 1 cadastro com e-mail pendente.
- 1 cadastro com telefone pendente.
- 5 pedidos simulados relacionados aos clientes.
- R$ 1.800,00 em faturamento simulado.
- R$ 360,00 de ticket médio.

Aplicação empresarial

Uma solução semelhante pode ser utilizada para:

- Identificar inconsistências em bases cadastrais.
- Preparar dados para integração entre sistemas.
- Consolidar informações de clientes e pedidos.
- Gerar relatórios operacionais e comerciais.
- Apoiar indicadores de acompanhamento da operação.

Aprendizados

O projeto permitiu praticar o tratamento de dados com Python, consultas SQL, relacionamento entre tabelas e geração de relatórios Excel.

Também reforçou a importância da validação dos dados e da aplicação de regras de negócio antes de utilizar informações em processos automatizados.

Observação técnica

Os dados utilizados são fictícios e foram criados exclusivamente para fins de aprendizagem. A remoção de duplicidades por e-mail é uma regra simplificada deste exercício; em ambientes reais, a identificação de duplicidade deve considerar os critérios de negócio e os identificadores oficiais dos registros.

O banco SQLite e o relatório foram utilizados em ambiente de execução do Google Colab.

---

Projeto integrante do portfólio prático de Automação de Processos, Integração de Sistemas e Inteligência Artificial.
