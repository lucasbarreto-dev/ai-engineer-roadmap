# 📌 Módulo 1: Como os Modelos Funcionam

## 🧠 Machine Learning (ML)
O objetivo principal é entender as regras básicas para saber **quando um modelo funciona ou falha**.

### Tipos de Aprendizado
* **Supervised (Supervisionado):** O modelo aprende a partir de dados rotulados (entrada e saída correta conhecidas).
* **Unsupervised (Não Supervisionado):** O modelo encontra padrões ocultos em dados sem rótulos (agrupamentos).
* **Reinforcement Learning (Por Reforço):** O modelo aprende por tentativa e erro através de um sistema de recompensa e punição.

### Modelos Básicos & Conceitos
* **Regressão Linear / Logística:** Modelos estatísticos para previsão de valores numéricos ou classificações binárias.
* **Árvores de Decisão:** Estruturas em formato de fluxograma para tomada de decisão baseada em regras.
* **Overfitting vs. Underfitting:**
  * *Overfitting:* O modelo decorou os dados de treino e falha miseravelmente com dados novos.
  * *Underfitting:* O modelo é simples demais e não conseguiu aprender nem as regras básicas do treino.

### Métricas de Sucesso
* **Accuracy (Acurácia):** Proporção geral de acertos.
* **Precision (Precisão):** De todos os classificados como positivos, quantos eram realmente positivos? (Evita falsos positivos).
* **Recall (Revocação):** De todos os positivos reais, quantos o modelo conseguiu encontrar? (Evita falsos negativos).
* **F1-Score:** Média harmônica entre Precisão e Recall, ideal para dados desbalanceados.

---

## 🕸️ Deep Learning (Redes Neurais)
O foco aqui é puramente conceitual: entender a evolução até o surgimento das LLMs.

* **O que é uma rede neural:** Algoritmos inspirados na estrutura de neurônios biológicos, organizados em camadas para processar dados complexos.
* **Forward Pass:** O fluxo dos dados de entrada passando pelas camadas até gerar uma previsão de saída.
* **Backpropagation:** O processo matemático de "voltar" corrigindo os erros da rede, ajustando os pesos dos neurônios para melhorar a próxima previsão.

### Arquiteturas Fundamentais
* **CNN (Convolutional Neural Networks):** Especialistas em processamento de **imagens** e visão computacional.
* **RNN (Recurrent Neural Networks):** Criadas para processar dados em **sequência** (como séries temporais ou textos antigos).
* **Transformers:** A arquitetura revolucionária baseada em mecanismos de atenção que permitiu o nascimento das LLMs modernas por processar contextos de texto massivos de forma paralela.

### 📚 Leitura Recomendada de Fundamentos: Álgebra Linear para Deep Learning
Para entender a matemática por trás de tensores e transformações de matrizes sem se perder em fórmulas teóricas puras, utilize este guia visual e prático baseado no clássico *The Deep Learning Book (MIT Press)*:

* 🌐 [Hadrien Jean - Deep Learning Book Series (Notebooks & Artigos)](https://github.com/hadrienj/deepLearningBook-Notes/tree/master)

O conteúdo aborda os pilares de álgebra linear aplicados com Python/Numpy através de códigos experimentais e representações gráficas:

1. **Escalares, Vetores, Matrizes e Tensores:** Introdução prática a broadcasting e manipulação de arrays multidimensionais.
2. **Multiplicação de Matrizes:** O funcionamento matemático do Produto Escalar (*Dot Product*), base das operações em camadas de redes neurais.
3. **Sistemas e Inversão:** Matrizes Identidade e Inversas aplicadas na resolução de sistemas lineares.
4. **Dependência Linear e Espaço Gerado (*Span*):** Análise de sistemas sobredeterminados e combinações lineares.
5. **Normas ($L^0, L^1, L^2$):** Funções de cálculo de magnitude vetorial, cruciais para avaliar funções de perda (*loss functions*) em modelos.
6. **Matrizes Especiais:** Estruturas diagonais, simétricas e ortogonais.
7. **Decomposições Avançadas:** Mapeamento de autovetores/autovalores (*Eigendecomposition*) e Decomposição em Valores Singulares (*SVD*), fundamentais para entender reduções de dimensionalidade (como PCA) e transformações de espaço geométrico em IA.
---

## 🔤 Grandes Modelos de Linguagem (LLMs)

### O que é um LLM?
**Large Language Model** (Grande Modelo de Linguagem) é um tipo de IA generativa treinada com volumes gigantescos de dados para compreender, processar e gerar texto em linguagem humana de forma contextual.

### Conceitos Críticos de Funcionamento

#### 1. Tokenização
Processo de dividir um texto em unidades menores chamadas **Tokens** (podem ser palavras inteiras, sílabas ou caracteres). Os modelos não leem letras; eles processam esses tokens matematicamente através de IDs numéricos.

#### 2. Context Window (Janela de Contexto)
É a "memória de curto prazo" do modelo. Define o limite máximo de tokens (texto, imagens, arquivos) que a IA consegue processar de uma só vez em uma única interação. Se estourar o limite, ela esquece o início da conversa.

#### 3. Parâmetros de Geração (Criatividade)
* **Temperatura (Temperature):** Controla a aleatoriedade. 
  * *Próxima a 0:* Respostas idênticas, determinísticas, conservadoras e técnicas.
  * *Acima de 1:* Respostas criativas, variadas, mas com alto risco de alucinação (inventar fatos).
* **Top-K:** Restringe a escolha do modelo apenas para as `K` próximas palavras mais prováveis.
* **Top-P (Nucleus Sampling):** Restringe a escolha acumulando a probabilidade das palavras até atingir a porcentagem `P` (ex: top 90% das palavras mais prováveis).

---

## 🎯 Prompt Engineering (Engenharia de Prompt)
A arte e técnica de estruturar instruções para obter saídas de alta qualidade dos modelos.

### Pilares de um Bom Prompt:
1. **Clareza e Especificidade:** Instruções diretas e sem ambiguidades.
2. **Contexto:** Explicar o cenário (Quem, o que, por que).
3. **Persona:** Definir um papel ou tom de voz para a IA (ex: *"Aja como um sênior dev especialista em segurança"*).
4. **Formato de Saída:** Exigir formatos específicos (tabelas, JSON, markdown, listas).

### Mecanismos Internos dos Transformers
> 🔥 *Se você dominar isso aqui, estará acima de 90% dos devs do mercado.*
* **Mecanismo de Atenção (Attention Mechanism):** Capacidade do modelo de focar em partes específicas da frase para entender o sentido de uma palavra (ex: entender que "banco" se refere a dinheiro ou a assento dependendo do resto da frase).
* **Self-Attention:** O modelo calcula a relação que cada palavra em uma frase tem com todas as outras palavras da mesma frase.
* **Embeddings + Positional Encoding:** Os embeddings dão o significado semântico da palavra, e o *positional encoding* diz ao modelo onde aquela palavra está localizada na ordem da frase (já que os Transformers processam tudo ao mesmo tempo).

### Referências
- [Python, IA/ML e Machine Learning](https://app.betrybe.com/learn/course/0995cbf2-7fd1-4155-927d-958efe79524d/module/ac04eb08-6c0a-4609-b2e7-13449ea1c881/section/baa5ba25-2ed9-4f57-bdec-f151cefd9891/lesson/499cca74-a194-492f-9bd5-ce859ffbdda5)
- [Python, IA/ML e Machine Learning | Gravação](https://app.betrybe.com/learn/course/0995cbf2-7fd1-4155-927d-958efe79524d/module/c555c69e-6a46-46a6-94e7-052bae0aa33c/section/cddc92b2-e192-4186-afae-f2a970513abb/lesson/80ddf7a3-40de-436e-b597-df6acf849c36)
- [How AI Turns Words Into Vectors: Embeddings - Blackboard AI](https://www.youtube.com/watch?v=lPTcTh5sRug)
