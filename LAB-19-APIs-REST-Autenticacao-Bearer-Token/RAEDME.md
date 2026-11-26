LAB 19 — APIs REST Avançadas e Autenticação Bearer Token

Objetivo do projeto

Desenvolver um workflow no n8n para demonstrar a integração com uma API REST protegida por autenticação, utilizando o método POST para obtenção de um token de acesso e o método GET para consultar um endpoint autenticado.

O laboratório demonstra como automatizar a autenticação e reutilizar dinamicamente credenciais temporárias para acessar recursos protegidos de uma API.

Cenário de aplicação

Em ambientes corporativos, diferentes sistemas precisam compartilhar informações, como dados de clientes, pedidos e registros comerciais.

Muitas APIs exigem autenticação antes de permitir o acesso aos seus recursos.

O conhecimento desenvolvido neste laboratório pode ser aplicado em integrações entre sistemas ERP, CRM e plataformas corporativas, nas quais o n8n atua como intermediador da comunicação.

Importante: o cenário empresarial é uma possibilidade de aplicação do conhecimento. O workflow implementado neste laboratório utiliza uma API de demonstração e não realiza integração com ERP ou CRM.

Tecnologias utilizadas

- n8n — plataforma de automação de workflows.
- HTTP Request — comunicação com APIs REST.
- API REST — interface de comunicação entre sistemas.
- JSON — estrutura de envio e recebimento de dados.
- Autenticação Bearer Token — mecanismo de autorização para acesso a endpoints protegidos.
- Expressões dinâmicas do n8n — reutilização automática do token recebido.

Arquitetura do workflow

O fluxo possui três nós:

1. Manual Trigger: inicia a execução manualmente.
2. 01 - Autenticar na API: realiza uma requisição POST para o endpoint de autenticação da DummyJSON e recebe o token de acesso.
3. 02 - Consultar Dados Autenticados: realiza uma requisição GET para um endpoint protegido, utilizando o token recebido na etapa anterior.

Fluxo de execução

"Manual Trigger → Autenticar na API (POST) → Consultar Dados Autenticados (GET)"

Endpoints utilizados

Autenticação

- Método: POST
- URL: "https://dummyjson.com/auth/login"
- Finalidade: enviar as credenciais de demonstração e receber os tokens de autenticação.

Consulta autenticada

- Método: GET
- URL: "https://dummyjson.com/auth/me"
- Finalidade: consultar os dados do usuário autenticado.

Implementação técnica

Na primeira requisição, o n8n envia as credenciais em formato JSON.

Após a autenticação bem-sucedida, a API retorna um token de acesso ("accessToken").

Na segunda requisição, o token é recuperado dinamicamente por meio da expressão:

{{ 'Bearer ' + $json.accessToken }}

O valor é enviado no cabeçalho HTTP:

"Authorization: Bearer <token>"

Dessa forma, a autorização é transmitida automaticamente para o endpoint protegido, sem necessidade de copiar o token manualmente.

Testes realizados

Foram realizados três testes:

Teste| Resultado
Autenticação com credenciais válidas| Sucesso
Consulta ao endpoint protegido com token válido| Sucesso
Consulta com token inválido| Acesso recusado pela API

Os testes comprovaram o funcionamento da autenticação, da reutilização dinâmica do token e da validação de acesso ao endpoint protegido.

Aprendizados desenvolvidos

- Fundamentos de APIs REST.
- Diferenças entre requisições HTTP POST e GET.
- Envio de informações em formato JSON.
- Configuração de cabeçalhos HTTP.
- Autenticação e autorização com Bearer Token.
- Utilização de expressões dinâmicas no n8n.
- Comunicação entre sistemas por meio de APIs.
- Validação de respostas e tratamento de falhas de autenticação.

Aplicações profissionais

O conhecimento desenvolvido pode ser utilizado em projetos de:

- Integração entre sistemas ERP e CRM.
- Consulta automatizada de pedidos e cadastros.
- Sincronização de informações entre plataformas.
- Integração com APIs corporativas protegidas.
- Automação de processos comerciais e administrativos.

Segurança e boas práticas

- Não compartilhar tokens de acesso ou refresh tokens.
- Não armazenar credenciais reais diretamente no workflow.
- Utilizar mecanismos seguros de armazenamento de credenciais.
- Evitar exposição de dados pessoais ou informações sensíveis nos registros e materiais do portfólio.
- Aplicar o princípio da minimização de dados.
- Utilizar credenciais de demonstração apenas em ambientes de teste.

O arquivo JSON disponibilizado no portfólio foi sanitizado. A senha de demonstração foi substituída por um marcador que deve ser preenchido antes de uma nova execução.

Observações e limitações

Este laboratório utiliza a DummyJSON, uma API de demonstração para fins educacionais.

A implementação comprova o processo básico de autenticação e consulta protegida, mas não contempla renovação automática de tokens, integração com sistemas corporativos reais ou gerenciamento avançado de erros.

Esses recursos podem ser desenvolvidos em projetos posteriores.

Resultado final

Workflow funcional desenvolvido no n8n, com autenticação via API REST, obtenção dinâmica de token Bearer e consulta bem-sucedida a um endpoint protegido.

Status: testes funcionais concluídos.

Projeto: Trilha 2 — Laboratórios de Automação com n8n.

Identificação: LAB 19.
