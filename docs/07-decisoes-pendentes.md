# Decisões pendentes

Não bloqueiam a arquitetura, mas devem ser resolvidas antes da fase indicada.

| Decisão | Quando | Opções / pergunta |
|---|---|---|
| Nome/papel de Mirrkos | antes do primeiro cartão aplicado | qual objetivo do projeto pode ser citado sem conteúdo sensível? |
| Template final do cartão | Fase 1 | um arquivo por item ou digest diário com links? |
| Vocabulário de intenção | Fase 1 | confirmar `aprender`, `aplicar`, `verificar`, `discordar`, `evitar` e campo livre |
| Retenção do conteúdo bruto | Fase 1 | guardar apenas referência/trecho ou original autorizado completo? por fonte |
| Pesos e limiar de score | Fase 2 | confirmar fórmula e limiar com corpus revisado |
| Cota de discordância | Fase 2 | percentual mínimo de contrapontos/itens fora do padrão |
| Limiar de utilidade | Fase 2 | confirmar ou trocar proposta de 70% |
| Import LinkedIn | Fase 3 | frequência e forma do export manual |
| X API | Fase 3 | aceitar OAuth/custo? qual hard budget? |
| Instagram | Fase 3 | resultado da auditoria oficial de export/API |
| Vetores | após volume real | FTS falhou em qual benchmark e por quanto? |
| Scheduler | Fase 4 | horário, timezone, janela, quota e destino do digest |
| Mutações de conta | decisão separada | existe benefício que justifique risco? quais ações individuais? |
| Empacotamento Dots | antes da demo | skill local, plugin/MCP ou fluxo demonstrativo, conforme capacidade oficial disponível |
| Licença pública | antes de aceitar contribuições | escolher licença explicitamente; ausência de licença não concede reutilização automática |
| Track do hackathon | inscrição | priorizar Memory and Coordination, Agents That Act, ou ambos? |

## Decisões já tomadas

- manual-first;
- repositório como fonte da verdade e vault como caderno;
- Python + SQLite + Markdown;
- FTS5 antes de embeddings;
- pt/en iniciais, expansão conforme seeds;
- curadoria separada de influência sobre feeds;
- mutações de conta e OAuth fora da fase atual;
- nenhuma garantia sobre algoritmos ou cobertura total.
- FalkorDB como camada de contexto central e SQLite apenas operacional/fallback.
- um grafo lógico por usuário/tenant, sem memória compartilhada implícita.
