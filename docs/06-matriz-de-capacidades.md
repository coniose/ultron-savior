# Matriz de capacidades por rede

Estado pesquisado em 2026-10-03. “Documentado” significa que existe evidência oficial; não significa que acesso, termos, custo ou comportamento tenham sido testados nesta máquina.

| Rede | Favoritos/salvos: caminho | Evidência oficial | Estado para o projeto | Lacuna antes de implementar |
|---|---|---|---|---|
| LinkedIn | export de dados da conta contém `Saved Items` com data e URL, não necessariamente texto completo | [Download your data — LinkedIn Help](https://www.linkedin.com/help/linkedin/answer/a1339364) | documentado; bom candidato a import manual de arquivo | solicitar só a categoria necessária, obter amostra real e testar parser sem ingerir o restante do arquivo/PII |
| LinkedIn | Member Data Portability inclui `ACTOR_SAVE_ITEM` e snapshot | [Snapshot domains](https://learn.microsoft.com/en-us/linkedin/dma/member-data-portability/shared/snapshot-domain), [Member Snapshot API](https://learn.microsoft.com/en-us/linkedin/dma/member-data-portability/shared/member-snapshot-api) | documentado, mas não presumido disponível | programa é ligado a elegibilidade UE/EEE/Suíça; confirmar elegibilidade real sem alterar localização ([LinkedIn Help](https://www.linkedin.com/help/sales-navigator/answer/a6214075)) |
| X | `GET /2/users/:id/bookmarks` para usuário autenticado; requer app e OAuth | [Bookmarks — X API](https://docs.x.com/x-api/posts/bookmarks/introduction) | endpoint documentado, não conectado | validar conta de developer, scopes, termos, rate limits e orçamento; não conectar OAuth nesta fase |
| X | limite documentado de bookmarks | [Rate limits — X API](https://docs.x.com/x-api/fundamentals/rate-limits) | documentação indica 180 requests/15 min; não testado | revalidar no plano/console e aplicar limite local menor |
| X | cobrança pay-per-use; own bookmarks aparecem como Owned Read a US$0,001/recurso somente quando usuário autenticado também é owner do app | [Pricing — X API](https://docs.x.com/x-api/getting-started/pricing) | documentado, condicional e sujeito a mudança | não presumir custo/qualificação; consultar console imediatamente antes de habilitar e usar hard budget |
| X | archive da conta em HTML/JSON | [Download your X archive — X Help](https://help.x.com/en/managing-your-account/how-to-download-your-x-archive) | export existe, mas a fonte não garante bookmarks | só implementar após amostra confirmar campo e formato |
| Instagram | entrada manual por URL/texto fornecido | não exige integração | suportado como contrato de MVP | testar ergonomia e campos com amostra do usuário |
| Instagram | Accounts Center permite baixar informações | [Meta Newsroom](https://about.fb.com/news/2023/10/manage-your-information-across-apps/) | export documentado; presença/schema de `Saved` não confirmados | obter amostra mínima do usuário e inspecionar campos antes de prometer import |
| Instagram | API para contas profissionais | [Instagram API — Meta](https://www.postman.com/meta/instagram/documentation/6yqw8pt/instagram-api) | não comprova acesso a feed ou salvos pessoais | considerar indisponível até documentação oficial específica e teste autorizado |

## Operações de conta

Reagir, seguir, deixar de seguir, marcar “não tenho interesse”, enviar mensagem e publicar estão fora do MVP em todas as redes. Sua existência na interface do produto não equivale a capacidade oficial de API. LinkedIn proíbe software/extensões que automatizem ou façam scraping sem autorização ([LinkedIn Help](https://www.linkedin.com/help/linkedin/answer/a1341387/prohibited-software-and-extensions)); X também impõe regras próprias e proíbe likes automatizados ([X automation rules](https://help.x.com/en/rules-and-policies/x-automation)). Cada operação futura precisa de linha própria nesta matriz com fonte oficial, autenticação, escopo, custo, rate limit, risco e resultado de teste.

## Controles de recomendação não são controle total

Instagram documenta controles como Following/Favorites, Not Interested, Hidden Words e reset de recomendações ([Meta Newsroom](https://about.fb.com/news/2024/11/introducing-recommendations-reset-instagram/)). X e LinkedIn explicam fatores de recomendação ([X Help](https://help.x.com/en/rules-and-policies/recommendations), [LinkedIn Help](https://www.linkedin.com/help/linkedin/answer/a1339724)). Isso evidencia sinais e controles parciais, não domínio do algoritmo nem garantia de resultado. Reset não é ação implícita do projeto.

## Fontes externas primárias futuras

O curador pode continuar útil sem acesso aos três feeds. Após o MVP, adapters read-only para fontes primárias como [arXiv RSS](https://github.com/arXiv/arxiv-docs/blob/develop/source/help/rss.md) e [GitHub feeds](https://docs.github.com/en/rest/activity/feeds) podem complementar, nunca substituir, os favoritos manuais.

## Regra de atualização

Capacidades e preços mudam. Antes de implementar qualquer adaptador, registrar data, URL oficial, trecho factual resumido, hipótese, teste de acesso e decisão. Falta de evidência ou teste implica `disabled`. Nenhuma conta real foi testada nesta fase.

Não usar endpoints privados, cookies de sessão, bypass de rate limit ou export completo quando uma categoria mínima basta. Não fabricar sinais ausentes como tempo de visualização, likes ou engagement. OAuth só após aprovação explícita e persistente do escopo mínimo.
