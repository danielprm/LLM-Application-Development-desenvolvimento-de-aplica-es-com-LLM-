# 📒 Caderno de Estudo LLM — Utilização de LLM no Dia a Dia (NotebookLM)

Este repositório foi criado como parte de um estudo prático sobre **como utilizar LLMs (Large Language Models) no dia a dia**, principalmente em cenários corporativos, usando o NotebookLM como ferramenta de apoio para aprendizagem ativa.

A ideia aqui não foi apenas “perguntar para IA”, mas organizar um material de estudo com fontes reais, testar prompts e registrar o que funcionou e o que não funcionou, simulando situações próximas do mundo real.

---

## 🎯 Contexto e Objetivos

Ao tentar estudar Inteligência Artificial de forma mais profunda, percebi que muitos conteúdos disponíveis são extremamente amplos e acabam não ajudando quando você quer aprender algo aplicado ao trabalho.

Durante esse processo, conheci o **NotebookLM**, que funcionou muito bem como um “bloco de notas inteligente”: eu consigo subir documentos e fazer perguntas específicas com base apenas no conteúdo fornecido, evitando respostas genéricas e fora do contexto.

### Objetivos deste estudo
- Entender como LLMs podem ser aplicados no ambiente corporativo de forma segura
- Aprender conceitos importantes como RAG, embeddings e bancos vetoriais
- Explorar agentes e automação usando frameworks como LangChain
- Testar estratégias de prompts e documentar aprendizados e dificuldades
- Consolidar o aprendizado em um material reutilizável (resumo, glossário e prompts)

---

## 🧩 Tema Escolhido

**Tema:** Utilização de LLM no dia a dia  
**Motivação:** Aplicar IA em sistemas reais com busca em documentos, consultas a banco de dados e automação inteligente.

---

## 📚 Curadoria de Fontes

As fontes abaixo foram selecionadas e inseridas no NotebookLM para estudo:

1. **Melhores Bancos de Dados Vetoriais em 2026**  
   https://encore.dev/articles/best-vector-databases

2. **Criar um agente SQL (LangChain Docs)**  
   https://docs.langchain.com/oss/python/langchain/sql-agent

3. **Experimentando estratégias de chunking via LangChain (Zilliz Blog)**  
   https://zilliz.com/blog/experimenting-with-different-chunking-strategies-via-langchain

---

## 📌 NotebookLM utilizado

Material consolidado e utilizado durante o estudo:

https://notebooklm.google.com/notebook/20463594-915c-48dc-a459-ba9d49e75258

---

# 🧠 Engenharia de Prompts e "Cicatrizes"

Durante o estudo, eu utilizei o NotebookLM como suporte para tirar dúvidas técnicas específicas com base nas fontes carregadas. A ideia foi simular perguntas que normalmente surgem quando alguém quer aplicar LLMs no ambiente corporativo.

Abaixo estão alguns prompts que testei e o que aprendi com cada um.

---

## 🔎 Prompt 1 — Criar uma LLM voltada para os dados da empresa

### Pergunta
> Como fazer a criação de uma LLM com apenas o contexto e voltada para os dados da minha empresa?

### Resumo da resposta
A resposta indicou que a abordagem mais recomendada é utilizar **RAG (Retrieval-Augmented Generation)**, ao invés de treinar ou fazer fine-tuning de um modelo.

Foi descrito um fluxo bem claro:

- higienizar e carregar documentos (PDF, TXT, SQL)
- fragmentar os textos (chunking)
- gerar embeddings
- armazenar em banco vetorial (Chroma, Pinecone, pgvector)
- recuperar chunks relevantes (retrieval)
- injetar o contexto no prompt e gerar resposta

### Aprendizado principal
📌 Para empresas, RAG funciona como um modelo “livro aberto”, reduzindo alucinações e evitando retrabalho com treinamento.

### Cicatriz (dificuldade real)
Mesmo entendendo o fluxo, ficou claro que a parte mais crítica é definir chunking corretamente e garantir segurança (PII e controle de acesso).

---

## 🤖 Prompt 2 — Como usar IA para criar chatbots

### Pergunta
> Como utilizar a IA para criar chatbots?

### Resumo da resposta
A resposta reforçou que chatbots modernos geralmente usam **LLM + framework de orquestração**, com destaque para LangChain e LangGraph.

O caminho mais comum também envolve RAG:

- carregar documentos internos
- transformar em embeddings
- armazenar em banco vetorial
- recuperar trechos relevantes
- gerar resposta fundamentada no contexto

Além disso, foram citados recursos importantes:

- memória de curto prazo (para manter contexto)
- agentes e ferramentas (consultas SQL, APIs, etc.)
- prompt engineering para controlar estilo e comportamento

### Aprendizado principal
📌 Chatbot corporativo não é só “perguntar para IA”, e sim criar um pipeline que combina documentos + memória + regras.

### Cicatriz (dificuldade real)
Percebi que, sem memória, o chatbot perde credibilidade rápido, porque ele “esquece” o usuário a cada pergunta.

---

## 🧠 Prompt 3 — Como manter o histórico da conversa

### Pergunta
> Como garantir que o chatbot mantenha o histórico da conversa?

### Resumo da resposta
A resposta explicou que LLMs são **stateless**, ou seja, não guardam memória por padrão.

As estratégias apresentadas foram:

- reenviar histórico no prompt
- usar memórias prontas do LangChain (buffer, summary, vector memory)
- usar checkpointers do LangGraph para salvar estado
- persistir em banco (SQLite/Postgres)
- separar conversas usando `thread_id`

Também foi destacada a importância do controle de tokens, pois histórico grande aumenta custo e latência.

### Aprendizado principal
📌 A “memória” do chatbot é uma camada construída pelo desenvolvedor, não algo automático do modelo.

### Cicatriz (dificuldade real)
O desafio real é equilibrar contexto suficiente sem explodir o custo de tokens. A partir disso, técnicas como sumarização e recuperação semântica do histórico passam a ser necessárias.

---

## 📌 Perguntas extras levantadas durante o estudo

Durante o processo, surgiram novas dúvidas que são passos naturais para aprofundamento:

- Como o Fine-Tuning pode complementar uma arquitetura RAG?
- Quais ferramentas de orquestração existem além do LangChain?
- Como garantir segurança e privacidade de dados sensíveis (PII)?
- Como funciona o loop ReAct de um agente usando ferramentas?
- Quais vantagens práticas do RAG em comparação ao Fine-Tuning?

---

# ✅ Miniguia de Estudo (Entrega Final)

## 📌 Resumo Estruturado do Assunto

### 1) O que é um LLM
LLM (Large Language Model) é um modelo de IA treinado para compreender e gerar texto. Ele pode ser usado para automação, suporte técnico, geração de relatórios, análise de documentos e interação com sistemas internos.

---

### 2) RAG (Retrieval-Augmented Generation)
RAG é uma técnica usada para conectar um LLM a dados externos (documentos internos, PDFs, manuais, bases corporativas), permitindo que ele responda com base em fontes reais.

📌 **Vantagem:** reduz alucinação e melhora precisão.  
📌 **Ideal para empresas:** porque os dados mudam o tempo todo.

Fluxo comum:
- carregar documentos
- fragmentar (chunking)
- gerar embeddings
- salvar em banco vetorial
- buscar trechos relevantes (retrieval)
- enviar contexto + pergunta ao LLM
- gerar resposta

---

### 3) Chunking (fragmentação)
Como LLMs têm limite de contexto, documentos precisam ser divididos em blocos menores.

- chunks pequenos → mais precisão, menos contexto
- chunks grandes → mais contexto, mais custo e risco de ruído

Uma boa prática é usar **overlap**, para não perder informação em cortes.

---

### 4) Embeddings e busca semântica
Embeddings são vetores numéricos que representam o significado do texto.  
Eles permitem comparar “semelhança de sentido” entre perguntas e documentos, e não apenas palavras iguais.

---

### 5) Bancos Vetoriais
Vector Databases armazenam embeddings e fazem busca por similaridade.  
São muito usados em RAG.

Exemplos comuns:
- Chroma
- Pinecone
- pgvector
- Weaviate

---

### 6) Agentes e SQL Agents
Agentes são fluxos onde o LLM pode usar ferramentas externas.  
Um exemplo é o **SQL Agent**, que converte perguntas em linguagem natural em consultas SQL e retorna resultados automaticamente.

Isso abre espaço para automação de relatórios e análises internas.

---

### 7) Segurança no uso de LLM em empresas
Para aplicações reais, é essencial:
- controle de acesso por usuário
- proteção contra vazamento de dados
- anonimização/redação de PII
- limitar respostas ao contexto recuperado
- rastreabilidade e logs

---

# 📘 Glossário (Conceitos Aprendidos)

| Termo | Definição |
|------|----------|
| LLM | Modelo de linguagem treinado para entender e gerar texto |
| RAG | Técnica que combina recuperação de documentos + geração com LLM |
| Fine-tuning | Ajuste de um modelo com novos dados (mudando pesos internos) |
| Prompt | Instrução enviada ao modelo |
| Prompt Engineering | Processo de criar e otimizar prompts para obter melhores respostas |
| Chunking | Divisão de documentos em partes menores |
| Overlap | Sobreposição entre chunks para não perder contexto |
| Embedding | Representação vetorial de texto para busca semântica |
| Vector Database | Banco otimizado para armazenar embeddings e buscar por similaridade |
| Retrieval | Busca dos trechos mais relevantes no banco vetorial |
| Hallucination | Quando o modelo inventa informações não presentes na fonte |
| SQL Agent | Agente que transforma perguntas em consultas SQL automaticamente |
| PII | Dados sensíveis pessoais (CPF, telefone, e-mail etc.) |

---

# 🧠 Prompts Reutilizáveis (para Revisão)

### 1) Prompt para resumo rápido
> Resuma o conteúdo sobre **[tema]** em até 10 linhas e liste os principais pontos.

### 2) Prompt para aprender com exemplos reais
> Explique **[tema]** de forma simples e me dê 3 exemplos reais de uso em empresas.

### 3) Prompt para criar arquitetura RAG
> Me descreva uma arquitetura completa de RAG para uma empresa, incluindo ingestão, chunking, embeddings, banco vetorial e segurança.

### 4) Prompt para troubleshooting
> Estou tentando implementar **[tema]** e estou enfrentando o problema **[X]**. Quais são as causas mais comuns e como resolver?

### 5) Prompt para chunking ideal
> Qual estratégia de chunking você recomenda para documentos do tipo **[manual, contrato, relatório]** e por quê?

### 6) Prompt para evitar alucinações
> Responda apenas com base no contexto fornecido. Se não houver informação suficiente, responda: "não encontrado no material".

### 7) Prompt para criar um SQL Agent
> Me mostre como criar um SQL Agent com LangChain que responda perguntas em linguagem natural usando um banco SQL.

### 8) Prompt para checklist de produção
> Me dê um checklist do que é necessário para colocar um sistema RAG em produção (segurança, logs, custo e performance).

---
