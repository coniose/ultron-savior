# Modelo de dados

Modelo lógico; tipos finais e migrações pertencem à implementação.

## Identidade e isolamento

Todo nó e evento possui `tenant_id` opaco. O nome físico do grafo é derivado no servidor e nunca aceito diretamente da entrada do usuário. Queries recebem o tenant do contexto autenticado; não existe busca cross-tenant no produto.

## Entidades

### `Seed`

- `id`, `url_input`, `url_canonical`, `network`
- `human_comment` (obrigatório)
- `relevance_hint` (1–5, opcional)
- `intent` (opcional; não inferir preferência positiva apenas porque foi salvo)
- `anchor_project` (opcional: Kairos, Mirrkos, HiGames)
- `exclusions[]`, `created_at`, `status`

### `Source`

- `id`, `network`, `native_id`, `canonical_url`
- `author_ref` mínimo, `published_at`, `retrieved_at`
- `access_method`, `authorization_basis`, `terms_snapshot_ref`
- `language_original`, `content_hash`, `content_storage_mode`

### `Item`

- `id`, `seed_id`, `source_id`, `title`
- `original_text_ref` ou `authorized_excerpt`
- `normalized_text`, `translation_ref`
- `dedupe_key`, `duplicate_of`, `ingestion_status`
- `uncertainties[]`, `coverage_status`

### `Review`

- `id`, `item_id`, `reviewer=owner`, `reviewed_at`
- `relevance_rating`, `fidelity_rating`, `usefulness_rating`
- `feedback_text`, `exclusions_added[]`
- `application_status`, `application_note`

### `ActionProposal`

- `id`, `item_id`, `action_type`, `target`
- `intent`, `evidence`, `risk`, `policy_version`
- `required_approval`, `approval_status`, `expires_at`
- `idempotency_key`, `execution_status`

No MVP, `action_type` aceita somente ações internas/read-only, como `create_learning_artifact` e `request_human_review`. Tipos de mutação social podem existir no catálogo futuro, mas ficam desabilitados.

### `LearningArtifact`

- `id`, `item_id`, `template_version`, `created_at`
- `summary`, `claims[]`, `evidence_refs[]`
- `score_total`, `score_dimensions{}`
- `counterpoint`, `project_applications[]`
- `exercise`, `uncertainties[]`, `feedback_prompt`
- `markdown_path`, `generator_metadata`

## Grafo FalkorDB

Nós centrais: `UserContext`, `Goal`, `Project`, `Seed`, `Source`, `Item`, `Claim`, `Evidence`, `Skill`, `LearningArtifact`, `Review`, `ActionProposal` e `Run`.

Relações iniciais:

- `(UserContext)-[:HAS_GOAL]->(Goal)`
- `(Seed)-[:SAVED_BECAUSE {intent, comment}]->(Goal|Project)`
- `(Item)-[:FROM]->(Source)`
- `(Item)-[:MAKES]->(Claim)`
- `(Evidence)-[:SUPPORTS|CONTRADICTS]->(Claim)`
- `(LearningArtifact)-[:DERIVED_FROM]->(Item)`
- `(LearningArtifact)-[:APPLIES_TO]->(Project|Skill)`
- `(Review)-[:EVALUATES]->(LearningArtifact)`
- `(ActionProposal)-[:JUSTIFIED_BY]->(Evidence|Review)`
- `(Run)-[:TRAVERSED]->(Claim|Evidence|Goal|Project)`

Toda resposta guarda o caminho mínimo suficiente para explicação. Arestas derivadas têm `confidence`, `created_at`, `source_ref` e `policy_version` quando aplicável.

## Entidades operacionais de apoio

- `Job`: caso de uso, estado, limites, orçamento e idempotency key.
- `Checkpoint`: job, etapa, cursor e hash de entrada.
- `AuditEvent`: ator, instante, evento, alvo, política, resultado e custo.
- `CoverageReport`: contagens e motivos de não cobertura.
- `ScoringConfig`: pesos versionados e vigência.

## Estados principais

`Seed`: `received → validated → queued → processed | rejected`

`Item`: `discovered → captured → verified | partially_verified | unverified → curated → reviewed`

`ActionProposal`: `draft → awaiting_approval → approved | rejected | expired → executed | failed`

Transições inválidas falham fechado. Aprovação nunca é inferida de ausência de resposta.
