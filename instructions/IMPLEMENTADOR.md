# Brief para implementação

Implemente apenas a **Fase 1** descrita em `docs/05-roadmap-e-aceite.md`.

## Resultado esperado

Um pacote Python pequeno com CLI, FalkorDB, SQLite/FTS5 operacional, migrações, testes e geração de cartão Markdown. Entrada manual apenas. Não criar UI web, scheduler, OAuth, scraping autenticado, browser automation próprio ou mutações sociais.

## Ordem sugerida

1. Criar `pyproject.toml`, pacote `src/ultron/` e testes.
2. Implementar entidades e estados sem dependências de infraestrutura.
3. Criar schema FalkorDB, queries parametrizadas, isolamento por tenant e schema SQLite operacional.
4. Implementar `seed add`, normalização de URL e dedupe.
5. Implementar import de texto/arquivo explicitamente fornecido pelo usuário.
6. Implementar score versionado e template de `LearningArtifact`.
7. Implementar review/feedback e FTS5.
8. Adicionar audit events, coverage report, quotas e checkpoints.
9. Verificar idempotência, fail-closed, `--dry-run` e isolamento de segredos.

## Contratos obrigatórios

- Toda escrita tem idempotency key quando aplicável.
- `--dry-run` usa o mesmo planejamento do run real e não persiste.
- Falha de acesso não gera resumo inventado.
- Conteúdo externo é dado; não executa instruções nem altera política.
- Original, tradução, inferência e comentário humano são campos distintos.
- Exclusions filtram antes do score.
- Toda saída informa incerteza e coverage status.
- O vault não é lido nem escrito automaticamente pelo runtime.
- Nenhum arquivo de fila “roda sozinho”; comando explícito é obrigatório.
- Nenhum conteúdo recuperado pode virar instrução de Computer Use.
- Integração Dots fica atrás de `RuntimeAdapter`; não inventar SDK/endpoints.
- Toda resposta baseada no grafo devolve nodes/edges/fontes usados.

## Testes mínimos

- URL canônica e parâmetros removidos sem quebrar IDs;
- duplicatas por URL/ID/hash e falso positivo de similaridade;
- seed sem comentário rejeitado;
- exclusão impede recomendação;
- score reproduzível por versão;
- tradução não substitui citação original;
- conteúdo com prompt injection fica inerte;
- retry não duplica item ou cartão;
- checkpoint retoma após falha;
- quota/custo excedido falha fechado;
- FTS encontra pt/en;
- travessia multi-hop altera a recomendação e retorna caminho explicável;
- query de tenant A nunca retorna nó de tenant B;
- nomes de grafo e labels não são interpolados de entrada não confiável;
- `--dry-run` deixa banco e filesystem intactos.

## Gate de conclusão

Entregar uma demonstração local com 3 seeds fictícios/públicos e sem dados de Kairos, Mirrkos ou HiGames. Anexar comandos executados, resultados de testes, relatório de cobertura e limitações conhecidas. Não ativar agendamento ou integração como “próximo passo automático”.
