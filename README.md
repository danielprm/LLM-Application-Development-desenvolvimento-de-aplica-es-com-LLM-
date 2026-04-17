# LLM Study Notebook — Utilização de LLM no dia a dia.
Este repositório foi criado como parte de um estudo prático sobre utilização de LLM no dia a dia, usando técnicas de LLM Application Development com foco em aprendizado guiado por IA.

Objetivos do estudo
Compreender os principais conceitos de da IA e dados na empresa
Explorar o uso de IA como ferramenta de estudo e revisão
Testar estratégias de prompt engineering e documentar melhorias
Consolidar o aprendizado em um material reutilizável (resumo, glossário e prompts)

Tema: Utilização de LLM no dia a dia.
Motivação: Aplicar IA em sistemas reais com busca em documentos e automação inteligente

As fontes abaixo foram selecionadas e inseridas no NotebookLM para estudo:

Best Vector Databases in 2026 — https://encore.dev/articles/best-vector-databases

Build a SQL agent - Docs by LangChain — https://docs.langchain.com/oss/python/langchain/sql-agent

Experiment with 5 Chunking Strategies via LangChain for LLM - Zilliz blog — https://zilliz.com/blog/experimenting-with-different-chunking-strategies-via-langchain


Prompt Engineering e "Cicatrizes" (Experimentos)
Nesta seção estão documentadas as perguntas estratégicas, prompts testados e o aprendizado obtido durante as interações com IA.

Prompt: como fazer a criação de uma llm com apenas o contexto e voltada para os dados da minha empresa?

Resposta: Para criar uma solução de Inteligência Artificial voltada para os dados da sua empresa utilizando apenas o contexto e sem a necessidade de treinar um modelo do zero, a abordagem recomendada é a Geração Aumentada por Recuperação (RAG - Retrieval-Augmented Generation)
. Diferente do Fine-Tuning, que altera os pesos internos do modelo, o RAG funciona como um sistema de "livro aberto", onde o modelo consulta documentos específicos para responder a cada pergunta
.
Abaixo estão as etapas principais para implementar essa arquitetura:
1. Higienização e Carregamento de Dados
O primeiro passo é organizar os dados proprietários da empresa, removendo informações obsoletas ou duplicadas
. Esses dados, que podem estar em formatos como PDF, arquivos de texto ou bancos de dados SQL, precisam ser carregados para o sistema por meio de ferramentas como os Document Loaders do framework LangChain
.
2. Fragmentação (Chunking)
Como os modelos de linguagem possuem um limite de processamento de texto (janela de contexto), você deve dividir os documentos em pedaços menores chamados chunks
.
Chunks pequenos garantem precisão, mas podem perder contexto importante
.
Chunks grandes capturam mais contexto, mas podem incluir informações irrelevantes e aumentar o custo de processamento
.
Recomenda-se usar uma sobreposição (overlap) entre os pedaços para garantir que a continuidade da informação não seja perdida no corte
.
3. Vetorização e Embeddings
Os fragmentos de texto são convertidos em representações numéricas chamadas embeddings
. Esse processo utiliza uma rede neural para capturar o significado semântico das palavras
. A mesma inteligência artificial usada para vetorizar os documentos da empresa deve ser usada para vetorizar a pergunta do usuário, permitindo a comparação direta entre elas
.
4. Armazenamento em Banco de Dados Vetorial
Os embeddings são armazenados em um vector database (banco de dados vetorial), como Chroma, Pinecone ou pgvector
. Esses bancos são otimizados para realizar a busca semântica, encontrando rapidamente os trechos de informação que são matematicamente mais próximos da pergunta feita pelo usuário
.
5. Recuperação e Geração de Resposta
Quando um usuário faz uma pergunta, o fluxo segue estas etapas:
Recuperação (Retrieval): O sistema busca no banco vetorial os trechos (chunks) mais relevantes para aquela dúvida específica
.
Injeção de Contexto: Os trechos encontrados são anexados ao prompt (instrução) enviado à LLM
.
Geração: O modelo de linguagem (como GPT-4 ou Llama) gera uma resposta fundamentada estritamente no contexto fornecido, o que reduz drasticamente o risco de alucinações
.
Ferramentas e Segurança
O LangChain é a ferramenta de orquestração mais utilizada para integrar todas essas etapas em Python
. Para garantir a segurança empresarial, é fundamental aplicar redação automatizada de dados sensíveis (PII) e controles de acesso baseados em contexto, garantindo que o modelo não exponha informações confidenciais a usuários não autorizados
.
Essa arquitetura permite que sua empresa tenha uma IA que se mantém atualizada em tempo real conforme novos documentos são adicionados ao banco, sem os custos e a rigidez de um retreinamento completo

Criei recentemente esse repositório com esse tema em especifico, pois ao tentar estudar mais a fundo a IA acabei encontrando dificuldades e utilizando o notebooklm descobri que ele funciona muito bem como um bloco de notas que vai poder retirar minhas duvidas de forma especifica visando apenas os dados compartilhados, então pode ser que esse documentos ajude alguém.

Material consolidado disponível em: https://notebooklm.google.com/notebook/20463594-915c-48dc-a459-ba9d49e75258
