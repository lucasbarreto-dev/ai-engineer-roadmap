📌 Módulo 4: Ambiente de Produção, DevOps e Governança

## ⚙️ DevOps + IA (LLMOps)
Colocar um script local para funcionar é fácil; o verdadeiro desafio corporativo é manter sistemas de IA estáveis, escaláveis e sob controle financeiro em ambiente produtivo.

### Infraestrutura & Nuvem
* **Deploy de APIs:** Criação de contêineres robustos com **Docker** expondo endpoints (Python/Node).
* **Nuvem:** Hospedagem nativa e escalável utilizando serviços gerenciados das gigantes **AWS** e **Google Cloud**.

### Observabilidade (Essencial para Enterprise)
> 💡 *O mercado corporativo já percebeu que "fazer o agente funcionar na sua máquina" é muito diferente de "ter qualidade consistente na produção".*

* **Monitoramento de Prompts & Tracing:** Rastrear a árvore de execução do agente para entender exatamente em qual etapa ele errou ou alucinou.
* **Tracking de Custo:** Monitorar o consumo financeiro por usuário/requisição para evitar surpresas com faturas de APIs de LLM.
* **Ferramentas de Avaliação (Evals):**
  * `Promptfoo`: CLI para testar e avaliar prompts contra regressões de qualidade.
  * `LangSmith`: Plataforma robusta do ecossistema LangChain para debugar, testar e monitorar aplicações de IA.

---

## 🔒 Segurança em Sistemas de IA
Aplicações conectadas a LLMs abrem novas superfícies de ataques cibernéticos que precisam ser blindadas:

* **Prompt Injection (Injeção de Prompt):** Quando um usuário mal-intencionado envia um texto que consegue burlar as diretrizes do sistema (System Prompt), fazendo a IA vazar dados ou executar comandos destrutivos.
* **Data Leakage (Vazamento de Dados):** Enviar dados confidenciais ou segredos comerciais da empresa para APIs públicas que usam as requisições para retreinar modelos (infringindo LGPD/GDPR).
* **Controle de Acesso:** Garantir que o agente ou o RAG só resgate informações que aquele usuário específico tem permissão legal de visualizar no sistema de arquivos.

---

## 📈 Governança & Engenharia Avançada

### Práticas de Governança:
* **Versionamento de Prompts:** Tratar prompts como código fonte, controlando alterações via Git para evitar que uma mudança sutil estrague o comportamento do sistema.
* **Avaliação de Outputs (Evals):** Criação de datasets de teste automáticos para rodar toda vez que o sistema for atualizado, garantindo que a taxa de acerto não caia.
* **Reprodutibilidade:** Mitigar o comportamento estocástico (aleatório) das IAs fixando parâmetros para manter as respostas o mais padronizadas possível.

### Fine-Tuning em Escala
> 🛑 **Atenção:** Raramente deve ser o seu ponto de partida. Ajustar os pesos internos de um modelo é caro, complexo e exige dados altamente limpos.
* **Alternativas recomendadas antes de pensar em Fine-Tuning:** Dominar primeiro **Prompt Engineering** avançado e implementar uma arquitetura de **RAG** eficiente. O Fine-Tuning só entra em jogo quando você precisa mudar a *forma/tom* de resposta do modelo ou ensiná-lo um jargão/linguagem técnica extremamente restrito que o RAG sozinho não resolve.