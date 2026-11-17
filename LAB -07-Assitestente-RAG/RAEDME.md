LAB 07 — Assistente Inteligente com RAG (n8n + Gemini + Telegram)

🚀 Visão geral

Este laboratório apresenta o desenvolvimento de um assistente comercial inteligente utilizando a arquitetura RAG (Retrieval-Augmented Generation).

A solução permite que um usuário envie perguntas pelo Telegram e receba respostas geradas por IA com base em informações recuperadas de uma base de conhecimento previamente preparada.

O projeto foi desenvolvido com n8n, Google Gemini e Telegram, integrando processamento de documentos, embeddings, armazenamento vetorial e geração de respostas contextualizadas.

🎯 Objetivo do projeto

Construir uma prova de conceito de um assistente comercial capaz de:

- Receber perguntas por meio do Telegram.
- Consultar uma base de conhecimento comercial.
- Recuperar informações relevantes por similaridade semântica.
- Utilizar IA para elaborar respostas contextualizadas.
- Evitar respostas inventadas quando a informação não estiver disponível no documento.

🧠 O que é RAG?

RAG significa Retrieval-Augmented Generation (Geração Aumentada por Recuperação).

É uma arquitetura que combina a recuperação de informações em uma base de conhecimento com a capacidade de geração de texto de um modelo de linguagem.

Neste projeto, o processo funciona da seguinte maneira:

1. Um documento comercial é preparado.
2. O conteúdo é transformado em embeddings.
3. As representações vetoriais são armazenadas em uma memória vetorial.
4. Quando o usuário envia uma pergunta, o sistema consulta essa memória.
5. Os trechos relevantes são encaminhados ao modelo de linguagem.
6. O Gemini utiliza o contexto recuperado para elaborar a resposta.
7. A resposta é enviada de volta ao usuário pelo Telegram.

⚙️ Arquitetura do workflow

O projeto possui dois fluxos complementares.

1. Preparação da base de conhecimento

Nó| Função
01 — Iniciar preparação da base| Inicia manualmente o processo
02 — Preparar documento de conhecimento| Disponibiliza o conteúdo do Manual Comercial
03 — Inserir documentos na memória vetorial| Insere o documento no armazenamento vetorial
3.1 — Gerar embeddings — Gemini| Gera as representações vetoriais
3.2 — Carregar conteúdo do documento| Carrega o conteúdo para inserção na memória

2. Consulta e geração de respostas

Nó| Função
06 — Receber pergunta pelo Telegram| Recebe a mensagem enviada pelo usuário
04 — Consultar memória vetorial| Recupera informações relevantes
05 — Cadeia de resposta inteligente| Organiza a pergunta e o contexto recuperado
5.1 — Modelo de linguagem — Gemini| Gera a resposta contextualizada
07 — Enviar resposta pelo Telegram| Devolve a resposta ao usuário

📚 Base de conhecimento utilizada

Para demonstrar o funcionamento, foi criado um Manual Comercial de uma empresa fictícia, contendo:

- Produtos: uniformes profissionais, batas, jalecos e conjuntos personalizados.
- Prazo de produção: até 30 dias corridos após a confirmação do pedido.
- Pagamento: 50% na confirmação do pedido e 50% na entrega.
- Personalização: conforme necessidade do cliente, mediante aprovação prévia do orçamento.
- Atendimento: solicitações de orçamento recebidas pela equipe comercial.

Os dados são exclusivamente demonstrativos.

🛠️ Tecnologias utilizadas

- n8n: construção e orquestração dos workflows.
- Google Gemini: geração de embeddings e processamento de linguagem natural.
- RAG: recuperação de informações para geração de respostas contextualizadas.
- Embeddings: representação vetorial do conteúdo documental.
- Vector Store em memória: armazenamento e recuperação semântica.
- Telegram: canal de comunicação com o assistente.

🔐 Estratégia de resposta

O modelo recebe instruções para utilizar exclusivamente as informações recuperadas do documento.

Quando uma informação não está disponível na base de conhecimento, o assistente deve informar que não encontrou aquela informação, evitando inventar dados.

🧪 Testes e resultados

Durante o desenvolvimento, foram configurados e testados os componentes de:

- Preparação do documento.
- Geração de embeddings.
- Inserção na memória vetorial.
- Consulta à base de conhecimento.
- Integração conversacional com o Telegram.
- Encaminhamento do contexto para a cadeia de resposta.

Também houve teste integrado anterior com recebimento de resposta pelo Telegram.

Na etapa final, o modelo Gemini apresentou instabilidade temporária, retornando erro HTTP 503 (high demand), o que impediu confirmar a estabilidade da geração final na última rodada de testes.

Status: arquitetura implementada, componentes de recuperação vetorial e comunicação testados. A estabilidade da geração final pelo Gemini permanece pendente de nova validação.

Essa limitação foi documentada para manter a transparência técnica do projeto.

📥 Como importar o workflow

1. Baixe o arquivo JSON disponibilizado neste repositório.
2. Acesse sua instância do n8n.
3. Utilize a opção de importar workflow a partir de arquivo.
4. Selecione o JSON.
5. Configure suas próprias credenciais do Google Gemini e Telegram.
6. Confira a disponibilidade do modelo Gemini selecionado.
7. Execute primeiro o fluxo de preparação da base de conhecimento.
8. Depois, envie perguntas pelo Telegram.

Atenção: as credenciais não estão incluídas no arquivo JSON. Cada usuário deverá configurar suas próprias conexões.

🔒 Segurança

O workflow disponibilizado foi sanitizado antes da publicação, com remoção de referências a credenciais, IDs de webhook e identificadores privados da instância original.

Não compartilhe tokens, chaves de API ou informações pessoais em repositórios públicos.

📁 Estrutura do repositório

LAB-07-Assistente-RAG/
│
├── README.md
│
└── LAB-07-Assistente-RAG-n8n-Gemini-Telegram-SANITIZADO.json

📈 Aprendizados

Este laboratório permitiu aprofundar conhecimentos práticos em:

- Arquitetura RAG aplicada à automação.
- Integração de documentos com IA.
- Geração e utilização de embeddings.
- Recuperação semântica de informações.
- Integração entre Vector Store e modelos de linguagem.
- Orquestração de workflows com n8n.
- Integração de assistentes inteligentes com Telegram.
- Tratamento de indisponibilidade de serviços externos.
- Documentação e preparação de workflows para versionamento no GitHub.
