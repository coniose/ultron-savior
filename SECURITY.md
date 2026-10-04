# Security Policy

Ultron Savior está em fase de arquitetura/hackathon. Não use com credenciais, dados de clientes, produção industrial, mensagens privadas ou contas reais até que a implementação correspondente tenha testes e revisão.

## Princípios

- deny by default e menor privilégio;
- isolamento por usuário/tenant;
- conteúdo externo tratado como não confiável;
- nenhuma credencial, cookie, OTP ou screenshot no grafo/log;
- ação externa somente por capacidade autorizada e revisão aplicável;
- falha, timeout ou resultado ambíguo não contam como sucesso;
- exclusão e export devem alcançar dados derivados.

## Relato responsável

Não publique detalhes exploráveis, segredos ou dados pessoais em issues públicas. Contate o mantenedor do repositório por um canal privado do GitHub antes de divulgar uma vulnerabilidade.

## Fora de garantia

Este protótipo não garante alteração de algoritmos de recomendação, cobertura integral de redes, correção de todo conteúdo ou segurança para uso autônomo em contas reais.
