# 📌 Módulo 3: Autonomia e Agentes Inteligentes

## 🤖 Agentes Autônomos
Diferente de um simples chatbot que apenas responde perguntas sequenciais, um agente possui autonomia para decidir seus próprios passos para resolver problemas complexos de ponta a ponta.

### O Loop Core do Agente:
O comportamento de um agente roda em um ciclo contínuo baseado no padrão **ReAct** (Reasoning and Acting):

```text
🔄 PENSAMENTO (O que preciso fazer?) 
    ↳ AÇÃO (Qual ferramenta devo usar?) 
      ↳ OBSERVAÇÃO (O que a ferramenta retornou?) 
        ↳ REPETE ATÉ CHEGAR À SOLUÇÃO
```

- Tool Usage (Uso de Ferramentas): Capacidade de usar calculadoras, navegadores web, interpretadores de código ou APIs externas para coletar dados reais.

- Memória de Curto Prazo: O histórico da conversa atual mantido dentro da janela de contexto.

- Memória de Longo Prazo: Resumos de conversas passadas ou preferências do usuário salvas em bancos de dados vetoriais para consultas futuras.

