# Ultron Savior

Agente pessoal de contexto para transformar **favoritos escolhidos manualmente** em aprendizagem aplicável. O produto é pensado para usuários de OpenAI Dots: o Dot conversa e usa seus computadores/apps autorizados; o Ultron Savior organiza contexto, evidência, decisões e feedback em um grafo FalkorDB isolado por usuário.

“Ultron” e a “joia da mente” são apenas uma metáfora ficcional para ampliar capacidade de aprender. O sistema não promete saber tudo, resolver todo problema nem controlar algoritmos de redes sociais.

## Escopo inicial

O MVP recebe uma URL, um comentário humano e, opcionalmente, relevância/exclusões. Ele preserva a fonte e o texto original autorizado, identifica idioma, deduplica, pontua com configuração explícita e produz um cartão com:

- resumo fiel e grau de incerteza;
- evidência e fonte primária quando disponível;
- contraponto ou limite relevante;
- aplicação possível em Kairos, Mirrkos ou HiGames, sem copiar dados desses projetos;
- exercício prático pequeno;
- pedido de feedback do usuário.

Entrada manual vem antes de APIs, OAuth ou agendamento. Não há nesta fase reações, follows, unfollows, “não tenho interesse”, mensagens, publicação ou qualquer outra mutação de conta.

## Hackathon FalkorDB

O projeto participará do **Graph Hacks: Context for AI Agents**. FalkorDB será parte central do produto: relações entre objetivos, fontes, claims, evidências, projetos, feedback e artefatos determinam o que o agente recupera, recomenda e explica. O caminho percorrido no grafo acompanha cada resposta.

A implementação principal de FalkorDB será trabalho novo do período do hackathon; este repositório começa com arquitetura, guardrails e baseline documentado. Veja [Dots, FalkorDB e guardrails](docs/08-dots-falkordb-e-guardrails.md).

## Fonte da verdade e caderno

- Este repositório é a fonte da verdade para escopo, contratos, arquitetura, políticas e aceite.
- `C:\obsidian\ultron_project` é o caderno do dono para decisões, ideias e desenhos. Não é runtime, banco, fila automática nem memória vetorial.
- Kairos, Mirrkos e HiGames são vinculados por objetivos e hipóteses de aplicação. Dados de clientes, plantas, conversas, credenciais e notas privadas não entram aqui nem no vault.

## Mapa dos documentos

- [Brief do produto](docs/01-brief-do-produto.md)
- [Arquitetura](docs/02-arquitetura.md)
- [Modelo de dados](docs/03-modelo-de-dados.md)
- [Política de ações](docs/04-politica-de-acoes.md)
- [Roadmap e aceite](docs/05-roadmap-e-aceite.md)
- [Matriz de capacidades por rede](docs/06-matriz-de-capacidades.md)
- [Decisões pendentes](docs/07-decisoes-pendentes.md)
- [Dots, FalkorDB e guardrails](docs/08-dots-falkordb-e-guardrails.md)
- [Brief para implementação](instructions/IMPLEMENTADOR.md)
- [Política de segurança](SECURITY.md)

## Estado

Arquitetura, guardrails e documentação iniciais. Nenhuma integração, automação ou curadoria foi ativada.
