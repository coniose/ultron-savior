# Roadmap e critérios de aceite

## Fase 0 — arquitetura e documentação (esta entrega)

Aceite:

- repositório e vault separados, sem symlink/nesting/plugins/sync;
- escopo manual-first e limites registrados;
- modelo, interfaces, política, matriz e decisões pendentes documentados;
- nenhuma integração, conta ou automação ativada.
- baseline pré-hackathon identificado; implementação FalkorDB principal ainda não iniciada.

## Fase 1 — vertical slice FalkorDB durante o hackathon

Implementar CLI, FalkorDB, SQLite operacional, migrações e cartões Markdown para seeds inseridos manualmente.

Aceite:

- URL + comentário humano obrigatórios;
- relevância e exclusões opcionais;
- URL canônica, idioma e dedupe determinístico;
- original/referência preservado e tradução separada;
- score versionado, justificável e configurável;
- cartão inclui fonte, incerteza, contraponto, aplicação e exercício;
- rerun idempotente; checkpoints e audit log testados;
- travessia FalkorDB conecta goal → seed → claim → evidence → aplicação e devolve o caminho;
- FTS5 encontra cartões por termo e projeto como fallback/complemento;
- dois tenants sintéticos não retornam nenhum nó um do outro;
- `--dry-run` não grava nem faz chamadas faturáveis;
- testes unitários e integração local passam.

## Fase 2 — avaliação com corpus do usuário

Rodar uma amostra pequena de 20–40 favoritos, incluindo exemplos negativos e o motivo humano, sem agendamento.

Aceite:

- usuário revisa fidelity/relevance/usefulness;
- relatório de precisão, relevância, diversidade e cobertura;
- aplicações reais registradas, sem exigir dados sensíveis;
- false positives, itens inacessíveis e limites de recall visíveis;
- ajustes de score com comparação antes/depois, sem apagar histórico.

Gate: somente avançar se o usuário considerar úteis pelo menos 70% dos cartões revisados e nenhum erro crítico de atribuição ficar sem correção. O limiar é uma proposta a confirmar.

## Fase 3 — imports oficiais read-only

Priorizar import de arquivo exportado oficialmente e minimizado por categoria. LinkedIn Saved Items é candidato inicial; X API exige avaliação de OAuth, custo e quota; Instagram permanece manual até inspeção de uma amostra do export oficial.

Aceite:

- capability e termos revalidados na data da implementação;
- segredo fora de repo/log/prompt;
- quota/custo por job, kill switch e budget hard-limit;
- execução manual e dry-run antes de qualquer scheduler;
- relatório de cobertura e reconciliação por import.

## Fase 4 — scheduler read-only (opcional)

Aceite:

- acesso read-only testado e estável;
- mesmo caso de uso e idempotency key do modo manual;
- janela, timeout, quota, custo e retries limitados;
- alerta sem efeito colateral em falha;
- pausa simples e auditável.

## Fase 5 — propostas de influência (opcional, sem autoexecução)

Gerar sugestões revisáveis de ações específicas. Mutação automática de conta não é meta presumida e exigiria decisão arquitetural e de risco separada.

## Demo pública do hackathon

- dados exclusivamente sintéticos ou públicos e autorizados;
- pelo menos uma decisão muda por causa de relação multi-hop no FalkorDB;
- explicação mostra o caminho no grafo e as fontes;
- demonstração de isolamento entre dois usuários;
- prompt injection de uma página é ignorado e registrado;
- Computer Use é demonstrado apenas em sandbox/conta de teste, sem postagem, mensagem, compra ou exclusão;
- se Dots não estiver disponível à banca, adapter simulado reproduz o mesmo contrato e a limitação é declarada.
