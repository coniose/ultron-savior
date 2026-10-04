# Brief do produto

## Problema

Favoritos úteis ficam dispersos nas redes, sem contexto sobre por que foram salvos, sem verificação consistente e sem ponte para prática. O problema controlável é transformar uma seleção humana em aprendizagem rastreável. Influenciar o feed das plataformas é um problema separado, parcial e dependente de ações específicas; não há garantia de alterar recomendações.

## Objetivo

Criar um ciclo diário curto de **selecionar → verificar → sintetizar → aplicar → revisar**, orientado a competências de Forward Deployed Engineer:

1. descobrir e formular problemas reais;
2. entender operação e dados;
3. prototipar com IA e código;
4. entregar, observar e corrigir;
5. desenvolver carreira e oportunidades de negócio.

Projetos-âncora: Kairos (indústria), Mirrkos e HiGames. A ligação é feita por objetivo, padrão ou exercício; nunca por cópia de dados sensíveis.

Para outros usuários, esses projetos não existem por padrão. Cada pessoa configura seus próprios objetivos, idiomas, projetos e exclusões. Nenhum perfil global mistura dados ou preferências entre usuários.

## MVP

### Entrada obrigatória

- URL do favorito;
- comentário humano: “por que salvei?” ou “o que quero aprender?”.

### Entrada opcional

- relevância de 1 a 5;
- intenção (`aprender`, `aplicar`, `verificar`, `discordar`, `evitar` ou livre);
- projeto-âncora;
- exclusões (`não resumir carreira`, `não usar como evidência`, tema indesejado);
- texto original fornecido/autorizado quando a URL não puder ser lida.

### Saída por item

- título e referência à URL;
- idioma original e, se útil, tradução identificada como tradução;
- resumo e claims principais;
- evidência primária encontrada, ausente ou não verificada;
- score explicável por dimensão;
- contraponto, diversidade ou desacordo relevante;
- aplicação possível por projeto, sem presumir contexto privado;
- exercício de até 30 minutos;
- incertezas e próxima verificação;
- pergunta de feedback.

## Fora de escopo nesta fase

- scraping autenticado, OAuth e automação de navegador;
- agendamento, coleta contínua ou monitoramento;
- reação, follow/unfollow, “não tenho interesse”, mensagem ou publicação;
- otimização de tempo no feed, engajamento ou promessa de alterar algoritmo;
- ingestão de dados internos de clientes, fábricas ou conversas;
- embeddings automáticos do vault.
- substituir as permissões, aprovações ou mecanismos de segurança nativos do Dots;
- observar continuamente tela, navegador ou contas sem tarefa e consentimento específicos.

## Princípios de curadoria

- Manual-first e fail-closed.
- Fonte primária acima de autoridade aparente do autor.
- Original preservado; resumo e tradução nunca substituem citação.
- Diversidade intencional: formatos, autores, idiomas, perspectivas e discordâncias.
- Relevância personalizada, mas sem bolha perfeita: reservar espaço para contrapontos.
- Um favorito não é necessariamente aprovação: pode marcar discordância, investigação ou exemplo negativo.
- Pontuação configurável, auditável e revisável.
- O sistema declara alcance: o que viu, o que não conseguiu acessar, o que inferiu e a confiança.

## Métricas de sucesso

Medir em amostra revisada pelo usuário:

- **precisão/fidelidade:** claims do cartão sustentados pela fonte;
- **relevância:** avaliação do usuário por item;
- **diversidade:** distribuição por fonte, autor, formato, idioma e perspectiva;
- **aplicações reais:** exercícios/protótipos concluídos e usados;
- **recall limitado:** favoritos conhecidos processados versus elegíveis; declarar itens inacessíveis e não observados.

Não usar tempo no feed como métrica principal.
