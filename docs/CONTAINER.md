# Projeto e container

## Decisão
Projeto próprio e separado do gerador, para os agentes não compartilharem código nem deploy com ele. Este repositório (`hello-claude`) serve de rascunho; recomenda-se movê-lo para um repositório novo (ex.: `tomain-agentes`) antes da Fase 1.

## Onde roda
- **Etapa 1 (agora):** sessões Claude Code Remote na sua conta, uma por agente. Já são containers isolados na nuvem; o Orquestrador as controla por ferramentas de sessão. Não precisa de infraestrutura nova.
- **Etapa 2 (quando entrarem os terminais dos funcionários):** um container nosso, no mesmo Google Cloud do gerador mas em **projeto e serviço separados**, com: serviço de entrada (login + formulários), fila de pedidos por agente, e executor dos agentes via Claude Agent SDK.
  O acesso ao GCP hoje é só da conta Workspace do Leonardo; criar o projeto novo exige ele.

## Segredos
Chaves e tokens só no gerenciador de segredos do ambiente, nunca no repositório.
