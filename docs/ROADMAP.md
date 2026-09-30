# Roadmap

## Fase 0 — Fundação (agora)
- [x] Repositório central, regras e níveis de acesso definidos
- [ ] Criar sessões dos agentes com tags `agente:<nome>` (ver `agentes/`)
- [ ] Mapear onde ficam hoje os dados de cada área (comercial, jurídico, marketing, assistência)

## Fase 1 — Tudo sob pedido
- [ ] Propostas (Fase A): só observar o gerador; fluxo atual intocado (`docs/GERADOR-EM-PARALELO.md`)
- [ ] Orquestrador: painel diário (sessões, pendências de aprovação, falhas)
- [ ] Comercial, Jurídico, Marketing, Assistência: um caso de uso real por agente, sempre com rascunho + aprovação
- [ ] Melhoria de Sistema e Qualidade: escrever a bateria de testes inicial (`testes/`)
- [ ] Terminais: formulários Airtable por papel para os funcionários

## Fase 1.5 — Gerador em ensaio isolado e integração (Fase B e C do gerador)
- [ ] Réplica de teste do gerador; comparar saída com a produção
- [ ] Autorização do Leonardo para o agente criar pedidos

## Fase 2 — Automatização seletiva
Critério para promover uma tarefa: 5 execuções seguidas aprovadas sem correção. Cada promoção é registrada aqui, com data e regra escrita.

## Perguntas abertas
- "Power" foi tratado como erro de transcrição: o gerador é o do Cloud Run + Airtable descrito na skill. Corrigir se for outro sistema.
- Mover este projeto para um repositório próprio (`tomain-agentes`)?
- Onde estão os dados de assistência técnica, jurídico e marketing (Drive, Airtable, e-mail)?
