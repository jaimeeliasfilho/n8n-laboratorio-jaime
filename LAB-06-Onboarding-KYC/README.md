LAB 06 — Automação de Onboarding KYC com Validação de CNPJ

«Projeto de portfólio desenvolvido com n8n, JavaScript, HTTP Request, BrasilAPI e Telegram para demonstrar automação de etapas iniciais de cadastro e análise cadastral de empresas.»

Visão geral

O laboratório simula uma etapa inicial de onboarding empresarial. Um formulário recebe os dados cadastrais, o CNPJ é normalizado e validado por código JavaScript, e a BrasilAPI é consultada para recuperar informações públicas do cadastro. A situação cadastral direciona o fluxo para uma pré-análise: empresas com situação ativa seguem para análise complementar; situações diferentes de ativa são sinalizadas como pendentes de revisão. Falhas de consulta e CNPJs inválidos possuem caminhos próprios de tratamento.

O objetivo é reduzir tarefas repetitivas de conferência e organizar informações para revisão humana — não aprovar ou reprovar automaticamente uma empresa.

Problema de negócio

Processos de onboarding e KYC podem exigir conferência de dados, validação de identificadores, consulta a fontes públicas e encaminhamento de inconsistências. Quando essas tarefas são realizadas manualmente, podem consumir tempo operacional e aumentar o risco de inconsistências.

Este protótipo demonstra como orquestrar essas etapas em um workflow visual, com regras explícitas e caminhos de exceção.

Arquitetura do workflow

Formulário de cadastro
        |
        v
Validação e normalização do CNPJ (JavaScript)
        |                         \
   CNPJ válido                 CNPJ inválido
        |                         |
        v                         v
Consulta BrasilAPI          Registrar motivo
        |                         |
   +----+----+                    v
   |         |              Retorno ao formulário
Sucesso    Falha
   |         |
   v         v
Organizar   Registrar falha
cadastro       |
   |           v
   v        Alerta Telegram
Verificar situação cadastral
   |
 +-+------------------+
 |                    |
Ativa              Diferente de ativa
 |                    |
 v                    v
Pré-análise         Pendente de revisão
 KYC                    |
 +----------+-----------+
            |
            v
     Preparar resumo
            |
            v
   Notificação Telegram

Etapas implementadas

1. Recebimento do cadastro: formulário com razão social, nome fantasia, CNPJ, e-mail, telefone, responsável, CPF, atividade principal, endereço e consentimento para tratamento dos dados.
2. Validação e normalização do CNPJ: código JavaScript remove caracteres de formatação, normaliza o identificador, verifica formato, sequências repetidas e dígitos verificadores.
3. Consulta externa: requisição HTTP à BrasilAPI para consultar dados públicos do CNPJ.
4. Organização dos dados: padronização de razão social, nome fantasia, CNPJ, situação cadastral, município, UF, porte e CNAE.
5. Regra de situação cadastral: o nó IF verifica se a situação retornada corresponde ao código "2" (ativa).
6. Pré-análise e pendência: empresas ativas recebem o status "EM_ANALISE"; situações diferentes de ativa recebem "PENDENTE_REVISAO".
7. Tratamento de exceções: CNPJ inválido retorna uma mensagem ao formulário; falha na consulta é registrada e encaminhada para alerta.
8. Resumo e notificação: os dados relevantes são organizados em uma mensagem e enviados por Telegram nos caminhos previstos.

Tecnologias e competências demonstradas

- n8n: construção e orquestração de workflows, gatilhos, nós de transformação, condições e ramificações.
- JavaScript: normalização de dados, validação de CNPJ, funções auxiliares, tratamento de erros e manipulação de itens do n8n.
- APIs REST / HTTP: integração com a BrasilAPI e tratamento de saída de erro.
- Telegram: integração para encaminhamento de notificações operacionais.
- Lógica de processos: separação de caminhos por regras, tratamento de exceções e encaminhamento para revisão humana.
- KYC / onboarding:
