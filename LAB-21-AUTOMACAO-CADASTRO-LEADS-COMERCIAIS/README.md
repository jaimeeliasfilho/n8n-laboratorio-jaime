LAB 21 — Automação de Cadastro de Leads Comerciais

Visão geral

Este laboratório demonstra uma automação de entrada e cadastro de leads comerciais usando n8n, Webhook, validação de dados e PostgreSQL.

O cenário simula uma empresa que recebe informações de potenciais clientes por meio de um formulário ou sistema externo. A requisição chega ao n8n, os dados são organizados e validados e, se estiverem corretos, são gravados no banco de dados. Ao final, a automação devolve uma resposta HTTP informando o resultado do processamento.

O projeto contempla dois caminhos:

- Cadastro aprovado: os dados são inseridos no PostgreSQL e a API retorna confirmação.
- Cadastro rejeitado: quando falta um campo obrigatório, o fluxo não tenta inserir o registro e retorna uma mensagem de validação.

Objetivo de negócio

Reduzir o trabalho manual de registro de leads, padronizar as informações recebidas e evitar que cadastros sem os campos obrigatórios sejam gravados no banco.

Arquitetura do workflow

01 - Receber Lead Comercial (Webhook POST)
                  |
                  v
02 - Padronizar Dados do Lead
                  |
                  v
03 - Validar Dados do Lead
             /         \
        Válido         Inválido
           |              |
           v              v
04 - Cadastrar       06 - Informar
     no PostgreSQL       Dados Inválidos
           |
           v
05 - Confirmar Cadastro

Nós utilizados

Nº| Nó| Responsabilidade
01| Receber Lead Comercial| Receber uma requisição HTTP POST com os dados do lead.
02| Padronizar Dados do Lead| Extrair e organizar nome, e-mail, telefone e empresa.
03| Validar Dados do Lead| Verificar se nome, e-mail e empresa estão preenchidos.
04| Cadastrar Lead no PostgreSQL| Inserir o registro na tabela "clientes".
05| Confirmar Cadastro do Lead| Retornar resposta JSON de sucesso, com HTTP 200.
06| Informar Dados Inválidos| Retornar resposta JSON de rejeição, com HTTP 400.

Dados recebidos

O Webhook recebe uma requisição "POST" com um corpo JSON semelhante a este:

{
  "nome": "Mariana Costa",
  "email": "mariana.teste@email.com",
  "telefone": "11999998888",
  "empresa": "Costa Soluções Digitais"
}

O telefone é opcional. Os campos obrigatórios verificados pelo fluxo são:

- "nome"
- "email"
- "empresa"

Banco de dados

O workflow utiliza PostgreSQL e grava os dados na tabela "clientes", no schema "public".

Estrutura utilizada:

Coluna| Finalidade
"id"| Identificador gerado automaticamente pela tabela.
"nome"| Nome do contato.
"email"| E-mail do contato, definido como único na tabela criada para o laboratório.
"telefone"| Telefone informado, quando disponível.
"empresa"| Empresa associada ao lead.
"criado_em"| Data e hora de criação, preenchidas pelo padrão definido no banco.

A credencial PostgreSQL não é incluída neste repositório. Após importar o workflow em outra instância do n8n, configure uma credencial própria e associe-a ao nó PostgreSQL.

Respostas da automação

1. Cadastro aprovado

Quando os campos obrigatórios estão preenchidos, o fluxo grava o lead no banco e retorna HTTP "200":

{
  "sucesso": true,
  "mensagem": "Lead cadastrado com sucesso!",
  "status": "recebido",
  "origem": "n8n"
}

2. Cadastro rejeitado

Quando um dos campos obrigatórios está vazio, o fluxo segue pelo caminho de rejeição e retorna HTTP "400":

{
  "sucesso": false,
  "mensagem": "Não foi possível cadastrar o lead. Verifique os campos obrigatórios.",
  "status": "rejeitado",
  "origem": "n8n"
}

Testes realizados

Os testes foram executados com o Hoppscotch, enviando requisições "POST" ao endereço de teste do Webhook no n8n.

Cenário| Resultado observado
Lead com nome, e-mail e empresa preenchidos| O fluxo percorreu os nós 01 a 05; o PostgreSQL retornou o registro inserido e a resposta HTTP confirmou sucesso.
Lead com nome vazio| O fluxo percorreu o caminho de rejeição pelo nó 06 e retornou a mensagem de dados inválidos com HTTP 400.

No teste de cadastro aprovado, o PostgreSQL retornou o registro com identificador gerado pelo banco e os campos do lead. No teste de rejeição, o caminho de inserção no banco não foi executado.

Tecnologias e conceitos demonstrados

- n8n: construção e orquestração do workflow.
- Webhook / HTTP POST: recebimento de dados de sistemas externos.
- JSON: estrutura de entrada e saída da integração.
- Edit Fields: padronização dos dados recebidos.
- IF: validação e direcionamento condicional.
- PostgreSQL: persistência dos dados.
- Hoppscotch: envio de requisições e validação das respostas HTTP.

Conceitos praticados: integração entre sistemas, tratamento de dados, validação de campos obrigatórios, persistência em banco relacional e tratamento de respostas de sucesso e rejeição.

Como importar e configurar

1. Importe o arquivo JSON do workflow no n8n.
2. Configure uma credencial PostgreSQL própria.
3. Associe a credencial ao nó 04 - Cadastrar Lead no PostgreSQL.
4. Confirme que o banco possui o schema "public" e a tabela "clientes" com as colunas descritas neste documento.
5. Utilize a URL de teste do Webhook para executar os testes.

O caminho configurado no Webhook neste workflow é:

lab21-leads-comercias

Use o caminho exatamente como está configurado no nó ou altere-o no n8n e atualize o endereço usado pelo cliente HTTP.

Segurança e limitações

- O arquivo de portfólio não contém a credencial pessoal do banco.
- O workflow exportado permanece inativo.
- O Webhook deste laboratório está configurado sem autenticação, adequado apenas ao ambiente controlado de teste. Antes de qualquer uso real, implemente autenticação, proteção contra abuso e controles de acesso.
- A validação implementada verifica preenchimento dos campos obrigatórios. Ela não comprova que o formato do e-mail é válido nem que o contato existe.
- O tratamento de duplicidade depende da restrição "UNIQUE" definida para o e-mail no banco. Um e-mail já cadastrado pode gerar erro de inserção; não foi implementado neste laboratório um fluxo específico de atualização ou tratamento desse conflito.

Resultado e aprendizado

O laboratório concluiu um fluxo de cadastro comercial com entrada via Webhook, padronização, validação condicional, gravação em PostgreSQL e respostas HTTP distintas para sucesso e rejeição.

A solução demonstra uma integração funcional de ponta a ponta e uma base que pode evoluir, em outro projeto, para integração com CRM, notificações e acompanhamento do funil comercial.

Autor: Jaime Filho
