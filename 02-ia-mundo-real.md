# 📌 Módulo 2: Como a IA se Conecta ao Mundo Real

## 🐍 Python Aplicado a IA (Prioridade Máxima)
A linguagem padrão do ecossistema. É obrigatório dominar Python para orquestrar dados, pipelines, manipular SDKs de LLMs, gerar embeddings e construir agentes autônomos.

### Integração com APIs Generativas
Desenvolvedores de IA não criam modelos do zero; eles consomem modelos consolidados via código.
* **SDKs Oficiais:** Utilização de bibliotecas como `openai` e `anthropic`.
* **Streaming de Resposta:** Configurar a API para entregar o texto aos poucos (efeito máquina de escrever), reduzindo o tempo de percepção de espera do usuário (*Time to First Token*).
* **Engenharia de Produção básica:** Controle estrito de custos (contagem de tokens enviados/recebidos) e tratamento de erros de limites de requisições (*Rate Limiting*).

---

## 📚 RAG (Retrieval-Augmented Generation)
> 🚨 **Conceito Obrigatório:** O mercado parou de criar apenas "Wrappers de ChatGPT" (sistemas que só repassam o prompt do usuário) e passou a exigir **Sistemas de IA com memória de negócio corporativa**.

O RAG resolve o problema das alucinações e da falta de dados privados das LLMs injetando dinamicamente informações de uma base de dados no prompt antes de enviá-lo ao modelo.

### O Pipeline do RAG:
1. **Chunking:** Quebrar arquivos gigantescos (manuais, PDFs, docs) em pedaços menores e gerenciáveis.
2. **Embeddings:** Transformar esses pedaços de texto em vetores numéricos que representam seu significado semântico.
3. **Vector Search:** Armazenar os vetores e buscar as informações mais parecidas com a dúvida do usuário usando métricas como **Similaridade de Cosseno (Cosine Similarity)**.
4. **Context Injection:** Pegar os pedaços de textos mais relevantes encontrados e colá-los dentro do prompt como contexto.
5. **Reranking:** Reordenar os resultados encontrados por relevância usando modelos menores antes de enviar ao LLM, garantindo o melhor contexto possível.
6. **Hybrid Search:** Combinar a busca semântica (por significado) com a busca clássica por palavras-chave (*Keyword Search*) para resultados perfeitos.

### Ferramentas de Mercado para RAG & Orquestração:
* **LangChain]:** O framework mais famoso para encadear componentes de IA.
* **LlamaIndex:** Framework excelente e altamente focado em ingestão e indexação de dados privados para RAG.
* **Bancos de Dados Vetoriais:**
  * `Pinecone`: Banco vetorial 100% gerenciado em nuvem de baixa latência.
  * `Weaviate`: Banco open-source robusto focado em escala e busca semântica.
  * `FAISS` (Meta AI): Biblioteca open-source ultraeficiente para busca de similaridade local em larga escala.

---

## 🔌 MCP (Model Context Protocol)
O **Model Context Protocol** é um padrão aberto (lançado pela Anthropic) projetado para funcionar como uma **"porta USB-C universal"** para conectar IAs a dados e ferramentas externas sem a necessidade de criar integrações customizadas e complexas para cada sistema.

### Pilares do MCP:
* **Conector Universal:** Atua como um tradutor único agnóstico entre modelos (clientes) e fontes de dados (servidores).
* **Componentes Core:** Estruturado em **Tools** (ações que a IA pode executar), **Resources** (dados de leitura que ela pode consumir) e **Prompts** (templates de contexto predefinidos).
* **Segurança:** Centralização de autenticação e governança sobre o que a IA pode ler ou alterar nos sistemas da empresa.
* **Adoção Prática:** Suporte nativo crescendo rapidamente em IDEs modernas como *Cursor* e *VS Code*.

### Function Calling (Chamada de Funções)
Técnica onde o modelo de linguagem atua como decisor, analisando o texto do usuário e escolhendo qual função do seu código, API externa ou banco de dados ele deve disparar para resolver o problema, retornando uma estrutura de dados limpa (geralmente em JSON).

```text
Usuário: "Como está o clima em SP?" 
  ↳ LLM analisa 
    ↳ LLM responde: "Disparar função buscar_clima(cidade='Sao Paulo')"
```

## 🛠️ Stack Mínima Ideal para o Desenvolvedor
Para construir aplicações modernas de IA no mundo real, você deve dominar essa stack:
* **FastAPI:** Para construir APIs assíncronas de alta performance que servem os modelos.
* **Pydantic:** Para validação rigorosa de tipos e parsing de dados de entrada/saída.
* **Requests / HTTPX & Asyncio:** Para requisições assíncronas concorrentes de APIs de IA.
* **SDKs Oficiais:** OpenAI / Anthropic SDKs.
* **Frameworks Avançados:** LangChain, LangGraph, Agno.

### Referências
- [Learn RAG From Scratch – Python AI Tutorial from a LangChain Engineer](https://www.youtube.com/watch?v=sVcwVQRHIc8)
- [Hello Langchain]()