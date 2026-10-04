# Dots, FalkorDB e guardrails

## Tese do produto

Ultron Savior é o **grafo pessoal de aprendizagem acionável** de um usuário do Dots. Ele conecta por que algo foi salvo, quais claims contém, quais evidências sustentam ou contradizem, quais objetivos e projetos toca, o que já foi testado e qual feedback o usuário deu.

FalkorDB não fica “ao lado” do agente. A decisão de recomendar, verificar, aplicar ou pedir revisão depende de travessias no grafo, e o caminho percorrido acompanha a resposta.

## Ajuste ao hackathon

O desafio exige FalkorDB como banco de grafo primário e valor central. O Ultron se alinha principalmente a **Agent Memory and Coordination** e também a **Agents That Act on Connected Data**: memória separada por usuário, estado persistente e ações justificadas por relações multi-hop.

Regras oficiais permitem continuar um projeto existente, mas a submissão e a implementação FalkorDB principal precisam ser trabalho novo durante o evento. Este repositório registra apenas o baseline de arquitetura anterior ao período de implementação.

Fonte: [Graph Hacks — WeMakeDevs](https://www.wemakedevs.org/hackathons/falkordb).

## Dots como runtime nativo

Segundo a documentação oficial, um Dot possui cloud computer/browser, pode usar plugins permitidos e pode acessar um computador local conectado. Essas concessões são independentes; pesquisa proativa é read-only e ações posteriores passam por permissões e revisão.

Fontes oficiais:

- [Meet dots](https://learn.chatgpt.com/docs/dots)
- [Connect computers and apps to your dot](https://learn.chatgpt.com/docs/dots/computers-and-apps)
- [Control your dot](https://learn.chatgpt.com/docs/dots/controls)

Não há nesta documentação uma promessa de SDK público específico para publicar “aplicativos nativos de Dots”. Portanto, a implementação usa um `RuntimeAdapter` e aceita três formas sem acoplamento:

1. skill local no computador conectado;
2. plugin/MCP suportado;
3. adapter demonstrativo que simula o envelope de pedido/resultado.

A forma final será escolhida somente após capacidade oficial verificável.

## Guardrails de privacidade e multi-tenant

- um grafo lógico por tenant; identidade externa vira ID opaco;
- nenhuma query cross-tenant, export global ou ranking compartilhado;
- contexto de um usuário jamais personaliza outro;
- memória do Dots/private notes não é copiada: apenas dados explicitamente entregues pelo runtime entram no grafo;
- export e exclusão por usuário incluem nós, arestas, índices e artefatos derivados;
- logs usam IDs opacos e nunca texto bruto, credenciais ou screenshots por padrão;
- demo pública usa dados sintéticos; projetos reais aparecem apenas como nomes/objetivos genéricos.

## Guardrails contra prompt injection

- página, post, PDF, comentário e resultado de busca são **dados não confiáveis**;
- instruções encontradas no conteúdo nunca escolhem ferramentas, ampliam escopo ou disparam Computer Use;
- separar envelopes `user_intent`, `trusted_policy`, `retrieved_content` e `tool_result`;
- validar toda saída contra schema e allowlist de ação;
- queries Cypher são parametrizadas; labels, nomes de grafo e procedures vêm de allowlist;
- links externos não são abertos em sequência sem orçamento e domínio explícitos;
- conflito entre conteúdo e política gera recusa + evento de auditoria.

## Guardrails de Computer Use

- preferir plugin/API estruturada; Computer Use apenas quando UI for realmente necessária;
- tarefa define app, janela, objetivo, duração e nível de ação;
- princípio “observe → proponha → aprove → aja → verifique”; nada de loops cegos;
- credenciais e OTP são inseridos pelo usuário em fluxo privado/handoff;
- sem terminal, configurações de segurança, password manager, CAPTCHA ou bypass;
- ações externas irreversíveis ou representacionais exigem aprovação no momento;
- screenshots são transitórias e não entram no grafo;
- resultado é verificado na UI/fonte e reconciliado com `ActionProposal`; timeout vira `unknown`, nunca sucesso.

## Guardrails de conhecimento

- cada resposta separa fonte, inferência e preferência humana;
- `coverage_report` explicita o que não foi observado;
- evidência contraditória é preservada, não apagada pelo score;
- “salvo” pode significar discordância, investigação ou exemplo negativo;
- o grafo melhora navegação no corpus autorizado, não produz onisciência.

## Demo segura e convincente

1. Usuário A salva três fontes sintéticas com intenções distintas.
2. Uma fonte contém prompt injection e é tratada como dado.
3. O grafo conecta objetivo → claim → evidência → skill → exercício.
4. Um contraponto muda a recomendação e o caminho é exibido.
5. Usuário B faz a mesma pergunta e recebe apenas seu próprio grafo.
6. O Dot propõe abrir uma ferramenta sandbox via Computer Use; a demo para antes de qualquer efeito externo ou usa uma ação reversível aprovada.

